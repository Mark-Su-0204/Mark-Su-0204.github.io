---
title: >-
  NSDI22: Packet Order Matters! Improving Application Performance by
  Deliberately Delaying Packets
date: 2023-01-31 14:35:52
tags:
---

pdf, slides, video: https://www.usenix.org/conference/nsdi22/presentation/ghasemirahni

### 摘要

数据中心越来越多地使用通用服务器+高速网络借口来实现低延迟通信。但同时满足低延迟和高吞吐取决于流量（traffic）和系统缓存（cache）的交互方式。当处理方式相同的packet连续到达时，即拥有良好的时、空局部性，cache的性能会更好。

本文研究了数据的时空局部性对高速网口通用服务器性能的影响，结果显示：1）数据局部性的降低会显著影响应用的性能。2）实际trace显示，在协议、驱动、交换机纤维的作用下，流量的局部性会变差。因此本文提出Reframer，一种软件的解决方案，通过刻意延迟一些packet的发送来重排包以提高局部性，尽管对某些包有微妙级的延迟，但可以提高总体网络服务链的吞吐（throughput）、降低单个服务器上的流完成时间（flow completion time）
