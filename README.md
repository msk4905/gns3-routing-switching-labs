# GNS3 라우팅·스위칭 구현 실습

GNS3에서 Cisco IOS 라우터와 스위치 모듈로 24개 네트워크를 직접 구성하고, 동작을 `show` 명령어와 `ping`으로 확인한 기록입니다. 라우팅(RIP, OSPF, EIGRP, IS-IS, IPv6), 경로 재분배, GRE와 IPsec, PAT, VLAN·STP, HSRP를 다룹니다.

## 실습 환경

| 항목 | 내용 |
|---|---|
| 기간 | 2026-08-21 ~ 2026-10-20 (보완 검증 2026-11-09) |
| 시뮬레이터 | GNS3 |
| 장비 | Cisco IOS 라우터(Dynamips), NM-16ESW 스위치 모듈, Cisco ASAv, VPCS |
| 접속 | MobaXterm·PuTTY 콘솔 |
| 규모 | 24개 프로젝트, 대표 사례 8건, 검증 캡처 198장 |

[PDF 보고서 열기](GNS3_라우팅스위칭_구현실습_보고서.pdf)

## 읽는 순서

| 순서 | 문서 | 내용 |
|---|---|---|
| 1 | [실습 요약](실습요약.md) | 24개 프로젝트 목록, 보완 검증 7건 |
| 2 | 대표 사례 | 아래 표의 8건 |
| 3 | [부록 설정 발췌](부록_설정발췌.md) | 대표 사례 장비의 설정 |
| 4 | [전체 증빙 목록](전체증빙/증빙목록.md) | 24개 프로젝트의 토폴로지와 캡처 전체 |

## 대표 사례

| 번호 | 사례 | 핵심 기술 |
|---|---|---|
| 01 | [RIP·OSPF·EIGRP·IS-IS 단계형 경로 재분배](대표사례/01_단계형_경로재분배.md) | OSPF, EIGRP, IS-IS, RIP, 경로 재분배 |
| 02 | [OSPF 다중 Area와 RIP 양방향 재분배](대표사례/02_OSPF_다중Area_RIP재분배.md) | OSPF 다중 Area, Stub, Totally Stubby, RIP, 양방향 재분배 |
| 03 | [GRE 터널과 IPsec(AH) 인증](대표사례/03_GRE_IPsec_AH.md) | GRE, IPsec(AH, ah-md5-hmac), ISAKMP, OSPF, RIP |
| 04 | [STP Root Bridge 우선순위 지정](대표사례/04_STP_루트브릿지.md) | STP(IEEE 802.1D), Root Bridge, 802.1Q Trunk |
| 05 | [PAT와 정적 포트 포워딩](대표사례/05_PAT_정적포트포워딩.md) | 정적 라우팅, PAT(NAT overload), 정적 NAT(포트 매핑) |
| 06 | [IPv6 RIPng·OSPFv3·EIGRP·IS-IS 재분배](대표사례/06_IPv6_다중프로토콜_재분배.md) | IPv6, RIPng, OSPFv3, EIGRP for IPv6, IS-IS(IPv6), 경로 재분배 |
| 07 | [VLAN 분할과 스위치 간 Trunk](대표사례/07_VLAN_Trunk.md) | VLAN, 802.1Q Trunk, 스위치 모듈(NM-16ESW), VPCS |
| 08 | [HSRP 게이트웨이 이중화와 장애 전환](대표사례/08_HSRP_게이트웨이이중화.md) | HSRP, 선점(preempt), RIP offset-list, 장애 전환 시험 |

## 폴더 구조

```
GNS3라우팅스위칭구현실습/
├── README.md
├── 실습요약.md
├── GNS3_라우팅스위칭_구현실습_보고서.pdf
├── 부록_설정발췌.md
├── 대표사례/          사례별 문서 8건
├── 전체증빙/          24개 프로젝트의 토폴로지와 캡처 목록
└── assets/
    ├── topology/      프로젝트별 토폴로지
    └── evidence/      프로젝트별 검증 캡처
```

## 안내

- 문서에 나오는 IP 주소, 계정, 키는 모두 실습 환경에서만 사용한 가상 값입니다.
- 설정 발췌에서는 `enable` 암호, 계정, 사전 공유 키 값을 제외했습니다.
- 캡처는 콘솔 창의 제목줄, 메뉴, 탭, 상태 표시줄을 잘라냈으며 명령어와 출력 내용은 수정하지 않았습니다.
