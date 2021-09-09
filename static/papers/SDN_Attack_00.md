# [New-flow based DDoS attacks in SDN: Taxonomy, rationales, and research challenges](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#d1e833)

## 저널명

Computer Communications Volume 154

## 저자

Maninder PalSingh

## 연도

2020.3

## 키워드

- SDN
- DDoS
- New-Flow
- Security

## 서론

- 기존 네트워크의 제어 로직과 전달 기능이 결합된 설계는 유연성이 저하되고 혁신성이 저해되며 운영 비용이 높아짐
- IoT, 빅테이터, 클라우드 등 차세대 신기술에서 요구하는 고대역폭, 적응성 및 관리 용이성을 충족시킬 수 없음
- 여러 요구를 충족시키기 위한 혁신적인 네트워킹 패러다임으로 SDN이 급부상
- 그러나 중앙 집중화된 특성으로 인해 더욱 지능화되고 있는 DDoS 공격에 취약
- [[6]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b6), [[7]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b7), [[8]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b8), [[9]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b9) 연구에 따르면 OpenFlow에 대한 전역 권한을 갖는 SDN을 DDoS 공격으로부터 방어하는데 활용할 수 있지만, Control Plane과 Data Plane이 분리되어 있기 때문에 SDN 자체도 보안이 필요
- SDN 아키텍처에는 개방형 공격 벡터 및 위협이 여러 개 존재 - [[10]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b10)
- 이 논문은
  - SDN 아키텍처의 다양한 영역과 모듈을 대상으로 New-Flow 기반 DDoS 공격으로 노출된 다양한 종류의 보안 취약점 분류법 제안
  - SDN 아키텍처에 대한 DDoS 공격 탐지에 사용되는 근거와 함께 국방 솔루션에 대한 최신 검토
  - SDN의 보안과 관련된 몇 가지 필수적인 개방형 연구 문제 및 과제에 대해 논의

|                                         Reference                                          | Year | New-Flow based DDoS taxonomy | Classification of security issues in SDN By SDN | Classification of security issues in SDN For SDN | Illustration of DDoS attack vectors on SDN layers - None | Illustration of DDoS attack vectors on SDN layers - Partial | Illustration of DDoS attack vectors on SDN layers | Classification of DDoS attack detection methods | Tables with rationales for detection | Issues & challenges |
| :----------------------------------------------------------------------------------------: | ---- | :--------------------------: | :---------------------------------------------: | :----------------------------------------------: | :------------------------------------------------------: | :---------------------------------------------------------: | :-----------------------------------------------: | :---------------------------------------------: | :----------------------------------: | :-----------------: |
| [[11]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b11) | 2016 |              ✗               |                        ✓                        |                        ✓                         |                            ✗                             |                              ✗                              |                         ✓                         |                        ✓                        |                  ✗                   |          ✓          |
| [[12]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b12) | 2016 |              ✗               |                        ✓                        |                        ✓                         |                            ✗                             |                              ✗                              |                         ✓                         |                        ✓                        |                  ✗                   |          ✗          |
| [[13]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b13) | 2017 |              ✗               |                        ✓                        |                        ✗                         |                            ✗                             |                              ✗                              |                         ✗                         |                        ✓                        |                  ✗                   |          ✓          |
| [[14]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b14) | 2017 |              ✗               |                        ✗                        |                        ✓                         |                            ✗                             |                              ✓                              |                         ✗                         |                        ✓                        |                  ✗                   |          ✗          |
| [[15]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b15) | 2018 |              ✗               |                        ✗                        |                        ✓                         |                            ✗                             |                              ✓                              |                         ✗                         |                        ✓                        |                  ✗                   |          ✗          |
|                                         Our Survey                                         | 2019 |              ✓               |                        ✗                        |                        ✓                         |                            ✗                             |                              ✗                              |                         ✓                         |                        ✓                        |                  ✓                   |          ✓          |

## 이론적 배경

### OpenFlow

- SDN 네트워크에서 컨트롤러와 스위치가 직접 통신할 수 있도록 지원하는 네트워크 통신 프로토콜

### 사전 예방적 접근 방식

- 네트워크 트래픽의 도착 전에 OF스위치에 많은 플로우를 채우는 방식

### 반응적 접근 방식

- 사전 예방적 접근 방식과 반대로 OF스위치의 플로우 규칙을 동적으로 제어하는 접근 방식
- 플로우 규칙을 반응적으로 설정하면 네트워크 스위치가 DDoS 공격에 취약해지는 단점이 있음
  - 예를 들어, New-Flow 기반 DDoS 공격은 OF스위치에서 컨트롤러로 전송되는 스푸피이된 OF_PACKET_IN 플로우의 급증을 유발하여 반응성 플로우 설치 메커니즘을 쉽게 이용할 수 있음

### SDN 아키텍처에 대한 새로운 흐름 기반 DDoS 공격 분류

![01_figure](/static/media/SDN_Attack_00/01_figure.jpg)

#### 스위치 취약점별 분류

##### OpenFlow Agent Overloading

- 스위치는 비용과 제안된 기능으로 인해 저전력 CPU를 가지고 있기 때문에, 공격자는 이를 취약성으로 간주하고 과부하 발생을 이용해 DDoS 공격을 강행
- 스위치의 전반적인 성능을 저하시키는 병목 현상으로 스위치에 연결된 클라이언트에서도 발생

##### Packet Buffer Overflow

- 스위치는 새 패킷을 처음 수신하면 패킷을 버퍼링한 다음 Packet_IN 메세지를 사용하여 패킷 해더만 컨트롤러에 전달하는데, 이 패킷 버퍼가 가득 차면 `ofp_action_output`의 `max_len` 필드가 `oFPCML_NO_BUFFER`로 설정되어 완전한 패킷을 전달해야함 - [[18]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b18)
- 많은 수의 패킷이 제어 채널 대역폭 및 컨트롤러 리소스를 광범위하게 사용하기 시작하여 스위치의 대기 시간과 응답 시간이 증가하고 스위치에 연결된 최종 사용자의 패킷 손실이 발생할 수 있음 - [[24]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b24), [[25]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b25)
- 스위치는 새로운 플로우 항목을 설정하지 못하거나 컨트롤러에 대한 새로운 플로우로 트래픽을 직접 전달하지 못하게 하는 이 공격은 Control Plane에도 심한 정체를 일으키고, 스위치의 취약성을 활용하여 컨트롤러에 손상과 스위치 분리 등 네트워크 전체에 영향을 줄 수 있음

##### Flow Entries Duration

- OF 스위치의 모든 플로우 테이블은 플로우 항목에 대한 `timeout` 메커니즘을 지원
  - `timeout` - 스위치에서 플로우 항목의 수명에 해당
    - `idle_timeout` - 0이 아닌 경우 트래픽이 수신되지 않으면 지정된 값 이후에 플로우 항목 만료
    - `hard_timeout` - 0이 아닌 경우 흐름 항목의 패킷 도착 여부와 관계없이 지정된 값 이후에 플로우 항목 만료
- 그래서 이를 기반으로 플로우 엔트리의 수명을 이용한 새로운 DDoS 공격 발견 - [[28]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b28)
- 저자는 최소 기간 동안 지속적으로 공격 플로우를 전송하는 DDoS 공격을 고안
  - 지능형 지속 공격 APT

##### Flow Table Overload

- DDoS 공격자는 네트워크에서 컨트롤러에 소진하는 공격 리소스에 비해 플로우 테이블을 오버로드하는 데 필요한 공격 리소스가 더 적음
- 새로운 플로우 기반 DDoS 공격은 제한된 용량을 채우고 소진하여 스위치 작동이 중단되어 네트워크 서비스를 손상시킴
- 낮은 사양의 OF 스위치는 새 플로우 항목을 위한 공간이 충분하지 않으면 `OFPMFC_TABLE_FULL` 오류 코드를 포함하는 `OFPET_FLOW_MOD_FAILED` 형식의 `ofp_error_msg`를 보냄
- 최악의 경우 타임아웃 메커니즘으로 인해 올바른 플로우 항목이 플로우 테이블에서 삭제되는 즉시 공격 플로우 항목을 그 자리에 추가하여 네트워크 리소스 및 네트워크를 손상시킴 - 조금 더 세부적인 연구 내용은 [[29]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b29), [[30]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b30), [[31]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b31)
- 플로우 테이블 과부하 공격의 존재 입증 실험을 통해 1,000개 미만의 일반 제품의 스위치를 사용하여 공격 속도 증가에 따라 플로우 테이블의 과부하에 필요한 시간이 감소하는 것을 관찰 - [[29]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b29)
- 네트워크 내부와 외부에 공격자가 존재할 수 있다는 관점에서 플로우 테이블 오버플로우 공격 분석- [[30]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b30)
- TCAM 소진 공격 - 대량의 UDP 패킷을 전송하여 플로우 테이블 공간을 빠르게 차지하려는 공격 - [[31]](https://www.sciencedirect.com/science/article/pii/S0140366419313830?via%3Dihub#b31)

#### 다른 SDN 모듈에 대한 공격 유형별 분류

- 리소스 포화 공격 유형과 대역폭 포화 공격으로 분류

##### 리소스 포화 공격(Resource Saturation Attack)

- 스위치와 컨트롤러와 같은 SDN 네트워크 장치의 리소스(CPU, Memory 등)를 소비하는 공격

###### 스위치 리소스 포화

##### 대역폭 포화 공격(Bandwidth Saturation Attack)

- 대량의 스푸핑된 피킷 Flood를 전송하여 채널의 대역폭 용량을 소모함으로써 SDN 아키텍처에서 다양한 인터페이스를 공격
- SDN 아키텍처에서 공격 대상 : Control Channel(Southbound API), Data Channel, East-West bound Channel, NorthBound Channel

##### SDN의 새로운 플로우 기반 DDoS 위협 벡터

![02_figure](/static/media/SDN_Attack_00/02_figure.jpg)

1. 데이터 평면의 스위치에 대한 공격
2. 스위치 간 데이터 채널에 대한 공격
3. 스위치의 OpenFlow Agent에 대한 공격
4. 스위치의 플로우 테이블에 대한 공격
5. 스위치의 패킷 버퍼에 대한 공격
6. OpenFlow Interface에 대한 공격
7. SDN 컨트롤러에 대한 공격

#### 공격의 영향 및 공격 강도에 따른 분류

## 연구 방법

## 결과

## 논의 및 제한점

## 참조

## Note

- 다양한 이점을 제공하는 SDN의 아키텍처에 의해 노출되고 새로운 흐름 기반 DDoS 공격에 의해 활용되는 보안 취약점 분류
