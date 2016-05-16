---
layout:     post
title:      "服务端与客户端视频流的生成"
subtitle:   "Ubuntu"
date:       2015-01-29 12:00:00
author:     "Jason Tang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 服务器 
    - 流媒体
---

> 最近在做SDN相关的实验，实验需要生成流量来测试网络性能，其中包括了视频流的流量生成。
 
## 使用到的工具：
 
**vlc**
 
> VLC多媒体播放器（最初命名为VideoLAN客户端）是VideoLAN计划的多媒体播放器。它支持众多音频与视频解码器及文件格式，并支持DVD影音光盘，VCD影音光盘及各类流式协议。它也能作为unicast或 multicast的流式服务器在IPv4或 IPv6的高速网络连接下使用。它融合了FFmpeg计划的解码器与libdvdcss程序库使其有播放多媒体文件及加密DVD影碟的功能。
 
我们将使用vlc推送视频TS流。通常可以使用下述四种方式来推送：
 
* UDP
 
* RTP
 
* RTSP
 
* HTTP
 
我的主要目的是做实验，所以选择实现简单的第一种方式UDP。
 
 
### UDP方式
 
这里要分服务端和客户端，服务端使用vlc推送视频流到客户端的某个端口（PORT1）,而客户端同时也使用vlc从相应的端口（PORT1）接受来自服务端的视频流。代码如下所示：
 
服务端：
 
```shell
vlc test.ts --sout "#standard{mux=ts{pid-video=100,pid-audio=101,pid-pmt=98},access=udp,dst=10.22.76.103:3940}" --sout-all --sout-keep --loop
```
 
客户端：
 
```shell
vlc udp://@:3940
```
 
#### Sample
