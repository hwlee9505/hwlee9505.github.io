---
layout: default
title: Network
parent: CS 지식
nav_order: 12
---

# Operating System
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## OSI (Open System Interconnection)

표준화, program, 다기종/멀티 배드의 상호운용성

|층 | 계층                        | 데이터             | 장비         | 프로토콜                             |
|:-|:---------------------------|:------------------|:-----------|:-----------------------------------|
|7 | 응용 계층                    |                   |             | DHCP, DNS, FTP, HTTP, SMTP        |
|6 | 표현 계층                    | message, data     |             | JPEG, MPEG, AFP                   |
|5 | 세션 계층                    |                   |             | SSH, TLS                          |
|4 | 전송 계층                    | segment           | 게이트 웨이    | TCP, UDP, ARP                     |
|3 | 네트워크 계층                  | packet, datagram | 라우터        | IP, ICMP, IGMP                    |
|2 | 데이터 계층                   | frame             | 브리지, 스위치 | MAC, PPP                          |
|1 | 물리 계층(물리적, 기능적, 절차적)  | bit               | 허브, 리피터  | Ethernet(802..), wifi, bluetooth...|
