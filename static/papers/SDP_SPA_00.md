# [소프트웨어 정의 경계의 단일 패킷 인증 및 네트워크 접근통제 보안관리 개선](https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE09286810)

## 저널명

한국콘텐츠학회

## 저자

정진교 / 전남대학교

## 연도

2019.12

## 키워드

- SDP
- SAP
- NAC
- 제로트러스트
- 접근통제
- 접근정책관리
- Zero-Trust
- Access Control
- Access Policy Management

## 서론

- 클라우드 확산, 스마트워크 등 네트워크 구성은 더욱 복잡해지고, 새로운 기술 적용이 확산됨에 따라 새로운 형태의 보안과 개인정보보호 문제가 대두
- 변화하는 기업의 IT 환경에 맞춰 보안성과 편의성을 제공할 수 있는 SDP의 개선된 네트워크 접근통제 방법을 제안
  - CSA(Cloud Security Alliance)의 SDP Spec 1.0의 구성 요소 및 동작 원리 분석을 통해 장치 등록 방법을 보완
  - 장치인증 단계의 핵심 기술인 SPA
  - 키의 생성 및 공유방법과 동적 방화벽 기술 활용

## 이론적 배경

### 1. 기업 네트워크 접근통제 취약성 사례

- 2017년 KISA에서 주요 기업 해킹사례 3건 분석 결과 중 2건의 사례는 접근통제 취약점과 연관된 기업 내부망에 침투한 후 추가적인 공격대상을 식별하고 침해를 확산한 사례

- 맥아피가 발표한 클라우드 활용과 위협 보고서(Cloud Adoption and Risk Report)에 따르면 클라우드 도입 기업 80%는 한 달에 한 번 이상 계정탈취 공격을 받음

  - 클라우드 보안위협은 전년 대비 27.7% 증가

### 2. 기존 네트워크 접근통제 기술과 한계

1. NAC(Network Access Control)

   - 인증 후 네트워크의 접속을 강제함으로써 보안성을 높임

   - but, 최근 외부에서의 접근 요구가 증가하는 기업 환경에서는 효과성이 떨어짐

   - 클라우드 환경에는 NAC 기술이 불가

1. 기존 네트워크 방화벽

   - 통합 정책 관리의 난해함으로 사용자 접급정책 관리 어려움

     - 네트워크 접정 증가, 망 구성의 복잡성 증가, 이기종 장비의 증가 등

   - 기존 IP, Port 기반 접근 정책의 어려움 증폭

     - 사용 장치의 증가 및 모바일 요구

1. VPN(Virtual Private Network)

   - 외부에서 내부망에 접속 시 활용

   - but, 외부에 VPN 서버가 노출될 수 밖에 없는 취약점 존재

   - 사용자의 인증 정보(ID/PW)가 노출되면 외부 해커의 접속을 위한 경유지로 활용될 수 있는 위험성 존재

1. 클라우드 서비스의 접근통제 방식

   - 기업 내부의 데이터센터가 클라우드로 이전함에 따라 가상 네트워크 및 컴퓨팅 인스턴스들을 보호하기 위하여 클라우드 플랫폼 사업자가 제공하는 ACL, Security Group, VPN, 상호인증 기술 등을 사용한 접근통제 방식을 활용

   - but, 대부분의 보안 서비스는 IP 주소 및 서비스 포트 기반의 접근통제 방식 활용하기 때문에 기존 문제점과 한계를 그대로 가지고 있음

### 3. 제로트러스트와 소프트웨어 정의 경계

#### 제로 트러스트 보안 모델

- 2010년 IT 시장 조사 기관인 포레스터 리서치의 보고서에서 처음 언급 - [7]

  - 2000년대 수많은 보안 사고와 보안 비효율성의 근본 원인을 경계부 보안 모델이 신뢰구간과 비신뢰 구간으로 나누고 네트워크에 임의의 권한을 암묵적으로 부여하였기 때문이라고 진단

- 제로트러스트 보안 모델의 세 가지 방법 제안

  1. 모든 자원 접근에 대한 검증 및 보호

  1. 최소 권한 부여 전략의 적용 및 엄격한 접근통제 정책

  1. 모든 트래픽에 대한 모니터링과 로깅 실시

#### Software Defined Perimeter

- Cloud Security Alliance에서 제로 트러스트 개념에 따라 SDP Spec 1.0 - [8]을 발표

- SDP는 장치의 인증을 수행 후 자원에 대한 네트워크 연결을 허용함으로써 공격 받을 수 있는 대상을 감춘다는 점에서 기존 보안 방법과 근본적 차이를 갖음

- SDP가 설계된 목적

  - 네트워크에서 서비스 격리

  - 어플리케이션 오너에게 논리적 접근 통제 권한 제공

  - 장치 및 사용자 신원 확인 후 네트워크 접근

  - 모든 트래픽 암호화

- SDP 구성 요소

  - SDP Controller

    - SDP 호스트 간의 통신 여부 결정

    - 다양한 데이터 참조를 통한 의사결정 수립

  - Initiating SDP HOST ( IH )

    - 통신을 요청하는 호스트

    - Controller에게 통신 가능한 AH 목록을 요청

  - Accepting SDP Host ( AH )

    - 서비스를 제공하는 호스트

    - Controller의 지시에 따라 IH의 요청을 수락

#### SPA (Sing Packet Authorization) 접근통제 기술

- SDP의 중요 핵심 기술 중 하나로 장치에 대한 인증 기능 제공

- SDP의 컨트롤러, IH, AH 모두 인증 단계를 거쳐 통신이 이루어 지는데, SDP의 인증은 SPA 방식을 사용하여 수행 - [8][9][10]

- RFC 4226에 정의된 HOTP(HMAC-Based One-Time Password Algorithm) 프로토콜 기반

- 동작 방법

  1. SPA에서 통신 당사자는 비밀 시드 공유

     - 비밀 시드는 카운터와 함께 일회용 암호(OTP)를 만드는데 사용

  1. 접속을 원하는 SPA 클라이언트는 SPA 서버와 통신이 필요할 때마다 카운터, OTP를 패킷에 포함하여 단일 패킷으로 전송 - [10]

  1. SPA 서버는 전송된 OTP를 검증하고 성공적이면 응답

- 패킷 포맷

  | IP  | TCP | AID (32-bit) | Password (32-bit) | Counter (64-bit) |
  | --- | --- | ------------ | ----------------- | ---------------- |

- SPA의 이점

  - 서버 스캐닝, 비인가 접근 등으로부터 안전

    - 컨트롤러나 AH는 유효한 SPA 패킷을 수신하는 경우를 제외하고 모든 연결 시도에 응답하지 않음

  - DoS 공격 완화

    - 유효하지 않은 패킷은 기본적으로 차단

  - 보안 위협 탐지에 도움

    - SPA 패킷으로 시작하지 않는 연결 시도는 비정상 접근이라 판단하기 때문

- SPA의 문제점 - [14]

  - 키 생성 및 공유와 접근정책 통합 관리 문제 - [12][13]

    - SPA 패킷 암호화 및 검증에 활용하는 키를 SPA 클라이언트에서 생성

    - 접근통제 설정을 수작업으로 저장하는 방식

  - 통신이 단절될 수 있는 구조

    - 동적 정책 생성 시 Timeout 반영

  - 게이트웨이만 적용 시 내부의 East-West 구간 위협 노출

    - AH / AH 그룹 상단 게이트웨이에 적용

  - 정책을 클라이언트에서 생성하기 때문에 신뢰성 문제 발생 가능

    - 클라이언트에서 접근 정책 생성

## 연구 방법

- 주요기업의 해킹사례를 조사하고, 기존 연구와 논문에서 제안하는 방법과의 비교를 통하여 보안 안정성 및 정책관리 효율성을 따짐

- SDP와 SPA의 문제점을 해결하는 방법 제안

  - SDP Spec 1.0에서 장치 사전 등록 절차, 인증 후 실제 정책이 어떻게 관리되고 배포되는지에 대한 설명 부족

  - SPA 패킷 암호화 및 인증을 위해 사용되는 키를 누가 어던 절차를 통해 생성하는지, 어떤 방식으로 최초 공유하는지에 대한 세부적인 정의 및 명시가 없음

- 관리 업무 개선 효과, 보안 안정성을 기존 방법과 비교 분석

## 결과

- 수작업 비중이 높은 네트워크 접근정책 변경 작업을 중앙에서 통합 관리하고 자동화를 통한 보안 위협과 보안 담당자의 업무 부담을 최소화할 수 있는 개선된 접근통제 방법이 필요

- 등록된 장치에서 사용자 인증 후 접근을 원하는 대상 서비스로의 정책이 동적으로 반영될 수 있도록 사용자 역할에 따라 접근 허용 및 정책 삭제 자동화

- 네트워크 접근정책을 통합 관리하여 작업의 업무 부담 최소화

- but, 역할기반접근통제(RBAC)을 기준 모델로 삼아 최근 기업의 사업 및 외부 위협이 더욱 복잡해지는 동적인 성격을 띄어 정적인 접근통제 모델보다 동적 접근 통제 모델을 SDP 환경에 적용하기 위한 추가적인 연구 필요

## 논의 및 제한점

## 참조

- [1] Abdallah Moubayed, Ahned Refaey, and Abdallah Shami, “Software Defined Perimeter : State of the Art Secure Solution for Modern Networks,” IEEE Network, Vol.33, Issue 5, pp.226-233, 2009.

- [2] https://www.linuxjournal.com/article/9565

- [3] https://www.zdnet.co.kr/view/?no=20180528103548

- [4] McAfee, Cloud Adoption and Risk Report, McAfee, 2019.

- [5] Firemon, State of the Firewall, Firemon, 2018.

- [6] Jason Garbis and Puneet Thapliyal, Software Defined Perimeter for Infrastructure as a Service, Cloud Security Alliance, 2016.

- [7] John Kindervag, Build Security Into Your Network’s DNA: The Zero Trust Network Architecture, Forrester Research, 2010.

- [8] Brent Bilger, Alan Boehme, Bob Folres, Zvi Guterman, Mark Hoover, Michaela Iorga, Junaid Islam, Marc Kolenko, Juanita Koilpilla, Gabor Lengyel, Gram Ludlow, Ted Schroeder, and Jeff Schweitzer, SDP Specification 1.0, CSA, 2014.

- [9] Jason Garbis and Juanita Koilpollai, Software Defined Perimeter Architecture Guide, CSA, 2019.

- [10] 정진교, 김용민, “제로트러스트 보안모델과 접근통제 적용 연구,” 정보보호학회 하계학술대회 논문집, Vol.29, No.1, 2019.

- [11] Fotios-Dimitrios Tsokos, Development of a Software Defined Security Perimeter, University of the Thessaly, 2018.

- [12] http://www.cipherdyne.org/fwknop

- [13] 이상구, 정진교, 김용민, “SDP 단일 패킷 인증의 접근통제 개선 방안,” 한국콘텐츠학회 종합학술대회 논문집, pp.311-312, 2019.

- [14] 이상구, 김용민, 단일 패킷 인증 프로토콜을 이용한 네트워크 접근통제 방법, 전남대학교, 석사학위논문, 2019.

- [15] D. Puthal, S. P. Mohanty, P. Nanda, and U. Choppali, “Building Security Perimeters to protect network systems against cyber threats,” IEEE Consumer Electronics Magazine, Vol.6, Issue 4, pp.24-27, 2017.

- [16] 강남길, 권태욱, “SDN 환경에서 비인가 소프트웨어 차단 기법,” 한국정보보호학회논문지, 제29권, 제2호, pp.393-399, 2019.

- [17] 최상용, 정기문, “안전한 클라우드 컴퓨팅 환경을 위한 보안 아키텍처,” 한국컴퓨터정보학회논문지, 제23권, 제12호, pp.81-87, 2018.

## Note
