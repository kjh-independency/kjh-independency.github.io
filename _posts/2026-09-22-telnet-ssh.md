---
title: "6-1. Telnet / SSH"
date: 2026-09-22 16:46:12 +0900
categories: [security]
tags: [network]
---

## Telnet

### 기술적 정의

- Telnet은 **네트워크를  통해 원격 터미널 접속을 제공**하기 위한 애플리케이션 계층 프로토콜
- Telnet은 **TCP 연결**을 기반으로 데이터와 제어 정보를 전달
- 기본적으로 **23번 포트**를 사용

> - 과거에는 다른 운영체제간의 **확장성**(Window ↔ Linux 등)으로 많이 사용
> - 현재는 **보안상 문제**로 현재는 **레거시 시스템이나 테스트 환경 등 제한적 상황에서만 사용** (Windows도 기본 비활성화 상태로 배포)
{: .prompt-warning }

## SSH

### 기술적 정의

- SSH(Secure Shell)은 안전하지 않은 네트워크에서, **안전한** 원격 로그인 및 기타 네트워크 서비스를 제공하기 위한 프로토콜이다
- 기본적으로 **22번 포트**를 사용

### SSH 아키텍쳐

SSH는 단순히 Telnet에 암호화를 추가한 프로토콜이 아니라, **다음과 같은 여러 프로토콜로 구성된 별도의 프로토콜 아키텍쳐**를 갖는다

- SSH Transport Layer Protocol: 서버 인증, 기밀성, 무결성
- SSH User Authentication Protocol: 사용자 인증
- SSH Connection Protocol: 원격 Shell, 원격 명령 실행 등

### SSH 주요 특징

- 암호화: 통신 내용을 암호화
- 무결성 보호: 통신 데이터가 전송 과정에서 변조되었는지 확인
- 서버 인증: 서버의 Host Key 등을 이용하여 서버의 신원을 확인
- 사용자 인증: 비밀번호 뿐 아니라 공개키 기반 인증 등의 방법 사용
- 다양한 기능 제공: SSH Connection Protocol을 통해 하나의 SSH 연결에서 여러 논리적 채널 사용 가능
- 대표 클라이언트: PuTTY(무료, 단순), SecureCRT(유료, 다중 세션 관리), MobaXterm(SSH·SFTP·RDP 통합)


## Telnet/SSH 차이점 정리

**Telnet = 원격 접속 + 평문 통신**

**SSH = 원격 접속 + 암호화·무결성 보호 + 서버/사용자 인증**


### 차이점

| | Telnet | SSH |
|---|---|---|
| 포트 | 23 | 22 |
| 통신 | 평문 | 암호화 |
| 무결성·인증 | 없음 | 제공 |
| 현재 용도 | 레거시·테스트 | 서버·장비 원격 관리 |
