---
layout  : wiki
title   : Vagrant로 Kubernetes 실습 환경 조성하기
summary : virtualbox를 wrapping하는 IaC 툴
date    : 2021-09-26 22:56:28 +0900
updated : 2021-09-26 22:56:29 +0900
tag     : kubernetes
toc     : true
public  : true
parent  : [[/study/kubernetes/index]]
latex   : true
---
* TOC
{:toc}

## 개 요

* Vagrant는 가상머신 애플리케이션(VirtualBox 등)의 할당, 배치, 배포를 자동화 코드로 관리하는(Infrastructure as Code) 프로비저닝 소프트웨어임
    
## 구성 방법

* Vagrant로 자동화할 대상 애플리케이션을 사전에 설치해야 하며, VirtualBox를 설치하도록 함

    ```shell
    $ brew install --cask VirtualBox
    ```

* Vagrant 실행시 발생한 오류와 트러블 슈팅

    * VirtualBox NS_ERROR_FAILURE (0x80004005) macOS

        * 운영체제를 High Sierra에서 Mojave로 업그레이드 하는 과정에서 SIP (System Integrity Protection)와 관련한 문제 발생

        * Mac에서 복구모드로 진입(command + R)하여 SIP(시스템 무결성 보호)를 비활성화하라는 무리한 해법이 있었으나, 해당 내용으로 보아 재설치로 해결이 가능하다고 판단함

        * appCleaner 앱으로 삭제 후 재설치하여 문제 해결

    * Vagrant was unable to mount VirtualBox shared folders. This is usually because the filesystem "vboxsf" is not available. 

        * VirtualBox의 공유폴더가 마운트 되지 않는 오류로, vagrant-vbguest 플러그인 설치로 해결 가능함 (플러그인 설치는 vagrant umount: /mnt 오류 참조)

    * vagrant umount: /mnt: not mounted

        * vagrant-vbguest 플러그인과 관련한 의존성 문제임

        * vagrant-vbguest 플러그인 설치 시 버전을 지정하지 않으면, 현재 0.30 버전이 설치되는데, 아래와 같이 0.21 버전에서만 정상 작동함

            ```shell
            $ vagrant plugin install vagrant-vbguest --plugin-version 0.21
            ```
* Vagrant 명령어

    * vagrant up

    * vagrant ssh

    * vagrant destory

    * vagrant box list
