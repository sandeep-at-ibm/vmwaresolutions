---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# 완전 분배
{: #caveonix-fully}

자산 수와 데이터 유지 요구사항에 따라 추가 기본 가상 머신(VM)과 스케일 확장 VM을 추가합니다.

표 1. 기본 - 사용자 인터페이스

|매개변수	|값|
|---|---|
|유형	| Base|
|VM 수량	|2|
|vCPU	|2|
|RAM	|6GB|
|디스크	|60GB|
|OS	|CentOS 7|
|설치된 애플리케이션 컴포넌트	|UI|

표 2. 기본 - 애플리케이션 및 플러그인

|매개변수	|값|
|---|---|
|유형	| Base|
|VM 수량	|2|
|vCPU	|8|
|RAM	| 16GB|
|디스크	|500GB|
|OS	|CentOS 7|
|설치된 애플리케이션 컴포넌트	|App, Plugins|

표 3. 기본 - 중앙 콜렉터

|매개변수	|값 |
|---|---|
|유형	| Base |
|VM 수량	| 3 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|500GB |
|OS	|CentOS 7 |
|설치된 애플리케이션 컴포넌트	|중앙 콜렉터(클러스터) |

표 4. 기본 - 관계형 데이터베이스

|매개변수	|값 |
|---|---|
|유형	| Base |
|VM 수량	|2 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|1TB |
|OS	C|entOS 7 |
|설치된 애플리케이션 컴포넌트	|Relational Datastore(Primary / Secondary) |

표 5. 기본 - 메시징 데이터 저장소

|매개변수	|값 |
|---|---|
|유형	| Base |
|VM 수량	| 3 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|1TB |
|OS	|CentOS 7 |
|설치된 애플리케이션 컴포넌트	|Messaging Datastore(Cluster) |

표 6. 기본 - 인덱스 데이터 저장소(마스터 노드)

|매개변수	|값 |
|---|---|
|유형	| Base |
|VM 수량	| 3 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|1TB |
|OS	|CentOS 7 |
|설치된 애플리케이션 컴포넌트	|Index Datastore(Master Nodes) |

표 7. 데이터베이스 - 인덱스 데이터 저장소(데이터 노드)

|매개변수	|값 |
|---|---|
|유형	| Base |
|VM 수량	|5 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|4TB |
|OS	|CentOS 7 |
|설치된 애플리케이션 컴포넌트	|Index Datastore(Data Nodes) |

스케일 확장 VM 세부사항은 다음 표에서 설명합니다.

표 8. 스케일 확장 - 데이터 노드

|매개변수	|값 |
|---|---|
|유형	|Scale-out |
|VM 수량 28 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|4TB |
|OS	|CentOS 7 |
|설치된 애플리케이션 컴포넌트	|Data Nodes(scale-out) |

원격 콜렉터 VM 세부사항은 다음 표에 표시되어 있습니다.

표 9. 원격 콜렉터

|매개변수	|값 |
|---|---|
|VM 수량	|As required |
|vCPU	|8 |
|RAM	| 8GB |
|디스크	|1TB |
|OS	|CentOS 7 |
|설치된 애플리케이션 컴포넌트	|원격 콜렉터 |
