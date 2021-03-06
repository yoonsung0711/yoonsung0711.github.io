---
layout  : wiki
title   : 스위치(2계층 장비)
summary : 
date    : 2021-10-27 09:00:00 +0900
updated : 2021-10-27 09:00:01 +0900
tag     : network
toc     : true
public  : true
parent  : [[/index]]
latex   : true
---
* TOC
{:toc}

![switch](https://user-images.githubusercontent.com/65143458/139073797-326c12ab-7370-407a-bbeb-5c5148a6c3ad.png)


## 개 요

* 폐쇄된 최소 단위의 지능형 네트워크를 구성하는 네트워크 장비

## 네트워크 트래픽 중계 장비와 역할/기능

* 허브

    * 연결된 모든 네트워크 장치를 함께 연결하는 역할/기능 수행

    * 이더넷 연결을 허용하는 포트를 다수 가지고 있음

    * 허브는 선택적으로 데이터를 전달하는 기능이 없어 지능적이지 않다고 간주함

    * 패킷을 다른 포트로 복사 (브로드캐스팅)하는 단순 기능 제공

    * 보안 문제, 대역폭 낭비 발생

    * IP 주소를 읽지 않으므로, 외부와의 연결은 불가능함

* 스위치

    * 허브와 마찬가지로 이더넷 연결을 허용하는 포트를 다수 가지고 있음

    *  스위치는 연결된 네트워크 장치의 물리적 주소(Mac)를 관리하고 선택적으로 데이터를 전달하므로 지능적이다라고 간주함

    * IP 주소를 읽지 않으므로, 외부와의 연결은 불가능함


* 라우터

    * 라우터는 IP 주소를 기반으로 하나의 네트워크에서 다른 네트워크로 데이터를 중계하는 기능 역할을 수행함

    * 데이터 패킷을 수신시에 목적지 IP를 검사한 뒤 내부 네트워크로 전달하고 그렇지 않으면 다른 네트워크로 전달함

    
## 스위치의 동작


* 플러딩

    * 스위치는 자신이 관리하는 MAC 주소 테이블에서 패킷 수신자의 MAC 주소를 확인할 수 없을 때 패킷이 들어온 포트를 제외한 모든 포트로 패킷을 전달함(유니캐스트 플러딩 또는 언노운 유니케스트)

    * 스위치의 유니캐스트 플러딩을 유도해 주변 통신을 모니터링하는 공격 방식을 MAC 플러딩이라고 함

    * MAC 주소 테이블에 MAC 주소와 포트 번호를 짝지워 기록하는 것을 어드레스 러닝이라고 함

    * 어드레스 러닝 과정을 통해 학습한 주소 정보로 수신된 패킷의 선택적 전송 (포워딩 / 필터링)을 함


## 스위치가 사용하는 가상화 기술

* VLAN

    * 논리적인 Network 분리 기술 (라우터는 물리적으로 Network를 분리함)

    * 숫자로 Network 이름을 구분함

## 다중 스위치 구성으로 네트워크 장애를 방지하는 기술

* SPoF / Loop / STP (Spanning Tree Protocol)

    * 단일 장애점으로 네트워크 실패를 방지하기 위한 다중 스위치 사용

    * 다중 스위치 사용시에는 패킷 전송이 구간 내에서 반복되는 루프 발생
        
    * 스패닝 트리 프로토콜(STP)는 루프를 확인하고 이를 예방하는 메커니즘임

* STP 상태 관리

    * BLocking - 패킷 전송을 차단한 상태로 BPDU 대기

    * Listening - BPDU 전송

    * Learning - MAC 주소 매핑

    * Forwarding - 통신 가능

* RSTP (Rapid Spanning Tree Protocol; 향상된 STP)

    * 백업 경로 활성화 시간을 단축하기 위한 메커니즘

    * 2 가지 메시지를 사용하는 STP와는 달리 BPDU 메시지 형식을 다양화(8개)하여 여러 가지 상태 메시지 교환

## 경로 최적화를 위해 스위치가 사용하는 프로토콜

* CST / PVST / MST


