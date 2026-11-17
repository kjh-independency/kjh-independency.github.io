---
title: "4. Scope(서비스의 범위)"
date: 2026-11-17 22:33:00 +0900
categories: [aws, aws global infrastructure]
tags: [aws]
---

**Part 1: AWS 글로벌 인프라 구조 (Global Infrastructure)** — [1. Region](/posts/aws-region/) · [2. Availability Zone](/posts/aws-availability-zone/) · [3. Edge Locations](/posts/aws-edge-locations/) · **4. Scope(서비스의 범위)**

**서비스의 범위 (Scope)**: 글로벌 서비스(Global Services)와 리전 단위 서비스(Region-scoped Services)의 구분과 특징

- AWS의 모든 서비스는 작동하는 지리적 범위(Scope)에 따라 크게 두 가지로 나뉨 (글로벌 서비스, Region 서비스)

## 4-1. 글로벌 서비스 (Global Services)

- 특정 리전에 종속되지 않고 AWS 계정 전체에서 하나의 설정으로 관리되는 서비스입니다.
- 쉽게 말해, 글로벌 서비스 서비스/리소스의 관리 범위가 특정 Region에 종속되지 않는다는 것입니다.

### 대표적인 예시

- **IAM** → 사용자, 권한 관리
- **Route 53** → AWS의 **DNS 서비스**
- **CloudFront** → AWS의 **CDN 서비스**

### 실제 현상

- IAM 콘솔에 들어가 보면 우측 상단 리전 선택창이 비활성화되어 'Global'로 고정되어 있습니다. 여기서 생성한 유저나 그룹은 전 세계 모든 리전에서 즉시 공통으로 사용 가능합니다.

## 4-2. 리전 단위 서비스 (Region-scoped Services)

- 특정 AWS 리전에 종속되어 관리되는 서비스

### 대표적인 예시

- **Amazon EC2** → 가상 서버
- **Amazon RDS** → 관계형 데이터베이스
- **AWS Lambda** → 서버리스 함수
- **Amazon VPC** → 가상 네트워크

### 실제 현상

서울 리전에서 EC2를 생성한 후 파리 리전으로 전환하면, 서울에서 생성한 EC2는 파리 리전의 EC2 목록에 자동으로 나타나지 않습니다. 서울 리전으로 다시 전환하면 기존 EC2를 확인할 수 있습니다.

> **[참고] EC2가 사라진 게 아니라 현재 선택한 Region에 존재하지 않는 것**
>
> 예를 들어:
>
> ```text
> 서울 Region
> └── EC2
>     └── Web Server
> ```
>
> 리전을 파리로 변경하면:
>
> ```text
> 파리 Region
> └── EC2
>     └── 없음
> ```
>
> 다시 서울로 돌아오면:
>
> ```text
> 서울 Region
> └── EC2
>     └── Web Server
> ```
>
> 이렇게 보이게 됩니다.
{: .prompt-info }

## 4-3. Scope 요약

- AWS의 모든 서비스는 작동하는 지리적 범위(Scope)에 따라 크게 두 가지로 나뉨 (글로벌 서비스, Region 서비스)
- 글로벌 서비스: 특정 리전에 종속되지 않고 AWS 계정 전체에서 하나의 설정으로 관리되는 서비스입니다. (IAM, Route 53, CloudFront)
- 리전 단위 서비스: 특정 AWS 리전에 종속되어 관리되는 서비스 (EC2, RDS, Lambda, VPC)
- EC2가 사라진 게 아니라 현재 선택한 Region에 존재하지 않는 것
