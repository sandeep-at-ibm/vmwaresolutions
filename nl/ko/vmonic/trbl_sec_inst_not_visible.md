---

copyright:

  years:  2016, 2019

lastupdated: "2018-08-16"

---

# vSphere Web Client 자원 명세에 보조 vCenter Server 시스템이 표시되지 않음

## 문제점

다중 사이트 구성에서 새 보조 인스턴스를 추가한 후 이전에 주문된 인스턴스의 VMware vSphere Web Client에 로그인할 때 vCenter Server 시스템이 표시되지 않습니다.

## 해결

이는 VMware 6.5의 알려진 문제입니다.

이 문제점을 해결하려면 vSphere Web Client를 다시 시작해야 합니다.

1. **루트** 계정을 사용하는 경우 **ssh**를 통해 이전에 주문된 vCenter 가상 머신(VM)에 연결하십시오.
2. bash 쉘을 입력하려면 ``shell``을 입력하십시오.
3. 클라이언트를 중지하려면 `service-control --stop vsphere-client`를 입력하십시오.
4. 클라이언트를 다시 시작하려면 `service-control --start vsphere-client`를 입력하십시오.
5. 이전에 주문된 인스턴스의 vSphere Web Client가 다시 시작된 후 새로 추가된 보조 인스턴스의 vCenter Server 시스템이 vSphere Web Client에 표시되는지 확인하십시오.
