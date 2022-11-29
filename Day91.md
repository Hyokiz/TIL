# 20221129 TIL

# 알고리즘 특강

# 목차

> 자료구조

- Tree
- Sagment Tree
- Fenwick Tree

# Tree

> Tree란

- 노드 간 계층과 1:N 관계를 갖는 자료구조

> Tree - Degree(차수)

- 노드에 연결된 자식 노드의 개수

> Tree - Level, Height, Depth(레벨, 높이, 깊이)

- 일반적으로 루트 노드부터 가장 높은 레벨

> Binary Tree

- 모든 노드가 최대 2개의 자식 노드를 가질 수 있는 트리

> Binary Tree -  노드의 개수 구하기

- 레벨/높이 H 일때 => 최소 H + 1개, 최대 2^H+1 - 1개

> Binary Tree - Complete Binary Tree (완전이진트리)

- 높이가 H이고 노드의 개수가 N일때, 빈 자리 없이 채워지는 트리
- 단 노드의 개수 <= N < 2^(H + 1) - 1

> Binary Tree - Skewed Binary Tree (편향 이진 트리)

- 높이가 H일때, 최소 노드 개수를 가지면서 한쪽 방향으로 노드는 가지는 트리

> Binary Tree - Traversal(순회)

- Traversal(순회) 란 트리의 각 노드를 중복되지 않게 전부 방문하는 것.
- 비 선형 구조로 선형 구조처럼 선후 연결 관계를 알 수 없다.

# Tree - 순회

> Binary Tree - Traversal(순회)

- 트리의 순회 방법

  - 전위 순회 : 부모 노드 방문 후, 좌/우 순서로 방문
  - 중위 순회 : 왼쪽 자식 노드 방문 후 부모 노드/오른쪽 자식 노드 방문
  - 후위 순회 : 좌/우 자식노드 방문 후 부모노드 방문

> Binary Tree - 전위 순회

- 전위 순회 방법

  - 현재 노드 n 을 방문하여 처리한다 > V
  - 현재 노드 n의 왼쪽 서브 트리로 이동한다 > L
  - 현재 노드 n의 오른쪽 서브 트리로 이동한다 > R

    ```java
    preorder_traverse(T) {
        if (T is not null) {
            visit(T)
            preorder_traverse(T.left)
            perorder_traverse(T.right)
        }
    }
    ```

# Sagment Tree

> Segment Tree 란?

- 어떤 데이터가 존재할 때 특정 구간의 결과값을 구하는데 사용하는 자료구조

- 배열의 크기가 커지면?

  - 구간별 합을 구해 저장해두면 빠르게 찾을 수 있다.

- Sagment Tree는 Binary Tree(이진 트리) 구조를 가지고 있다.

# Fenwick Tree

> Fenwick Tree란?

- Segment Tree처럼 구간에 대한 연산을 저장하는 트리
- Segment Tree 보다 적은 메모리로 사용 가능하다.
- 비트를 이용한 구간 연산을 진행

---

# AWS

> AWS 역사와 소개

- 클라우드란?

  - 프로그래밍 방식으로 인프라를 관리
  - 유연한 인프라
  - 사용하는 만큼 비용을 내는 구조
  - 필요한 인프라를 빠르게 구매
  - 글로벌 인프라 이용

> Amazon Web Services

- AWS는 컴퓨팅, 스포리지, 데이터베이스와 같은 인프라 기술부터 기계 학습 및 인공지능, 데이터 레이크 및 분석, 사물 인터넷을 IT 서비스로 제공

> AWS를 사용하는 방법 3가지

- Management Console
- AWS CLI
- AWS SDK

> Management Console

- 사용이 간편하다
- GUI라 보기가 쉽다
- 사용자 지정 비밀번호로 로그인할 수 있다.

> AWS CLI

- AWS CLI는 Linux, macOS 또는 Windows 명령 프로그램에서 실행될 수 있는 유틸리티 묶음을 제공합니다.

> AWS SDK

- 선호하는 개발 언어 또는 플랫폼으로 AWS 서비스에 엑세스하고 관리합니다.

# AWS 글로벌 인프라

> AWS 리전

- 최소 3개의 가용영약으로 구성되어 있는 AWS 인프라 단위
- 현재 29개의 리전 보유

> AWS 가용 영역

- AWS 의 데이터센터 모음
- 다른 가용영역 간의 장애로부터 자유로움

> AWS 엣지 로케이션

- 리전과 비교했을 때 최종 사용자와 더 가까이 존재하는 글로벌 인프라
- 보안, 가용성, 비용 효율성, 속도 면에서 향상된 성능

# IP 주소와 IPv4

> IP주소 

- 인터넷에서 서로 통신하기 위해 부여하는 고유한 주소
- 두 가지 종류: IPv4, IPv6
- 두 가지 종류: 사설 IP, 공인 IP

> IPv4

- 총 32비트로 구성 = 4,294,967,296개
- 약 6억개는 예약되어 있음
- 인터넷의 폭발적인 성장으로 인해 가용한 IP주소가 거의 고갈
- 128비트를 사용하는 IPv6가 새로운 표준으로 제안

# AWS 기초 서비스

- Amazon Elastic Compute Cloud (EC2)
- Virtual Private Cloud (VPC)

  - 실습 : 첫 VPC 생성하기 및 웹 서버 배포하기

- Simple Storage Service (S3)

> CIDR(Classless Inter Domain Routing)

- VLSM(Variable Length Subnet Mask)
- Network prefix와 Host id로 구성
- 서브넷 마스크를 /X 노테이션을 사용해 표현

  - X : 마스크 비트 수 
  - ex. 255.255.0.0 -> /16, 255.255.255.0 -> /24

- 한 블록 안에서 첫번째, 마지막 IP는 예약되어 있어 사용 불가

  - 첫 번째 IP는 네트워크 자체를 가르키는 IP(호스트 id 비트가 모두 0)
  - 마지막 IP는 Broadcast IP

- AWS에서는 총 5개의 Address를 예약

  - 0: 네트워크 어드레스, 1: VPC Router, 2: DNS, 3: Future use, 마지막 : Broadcast

> VPC(Virtual Private Cloud)

- VPC 란?

  - AWS 클라우드 안의 사용자가 정의한 가상의 네트워크
  - VPC 안에서 내 리소스를 생성 가능
  - 한 리전 안에 5개까지 생성 가능
  - 네트워크를 IP 주소 범위로 격리시킴

- Internet Gateway란?

  - 수평 확장되고 가용성이 높은 중복 VPC 구성 요소로, VPC와 인터넷 간에 통신을 하게 해줍니다.
  - 인터넷 게이트웨이를 생성하는 경우 비용이 별도로 발생하지는 않으나, 외부와 인터넷 통신을 원하지 않는 경우 사용하지 않을 수 있습니다.

> VPC 보안

- 보안그룹이란?

  - EC2 혹은 다른 AWS 리소스에 도달하고 나갈 수 있는 트래픽을 제어
  - 포트넘버 / 프로토콜 / 소스 IP 주소 등을 활용 해 트래픽 제어

> AWS EC2

- 컴퓨팅 파워의 규모를 자유자재로 변경할 수 있는 컴퓨팅 서비스
- 새로운 서버 인스턴스 확보 및 부팅 시간을 단축
- Virtual Machine
- Linux 또는 Windows, Ubuntu 등 다양한 OS 지원
- 사용하는 용량만큼 비용 지불

