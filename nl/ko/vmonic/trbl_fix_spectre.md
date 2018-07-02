---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# 스펙터(Spectre) 및 멜트다운(Meltdown) 취약점 해결

스펙터(Spectre) 및 멜트다운(Meltdown) 취약점을 해결하려면 특정 주문에서 다수의 패치를 적용해야 합니다.

## 펌웨어 업데이트

펌웨어 업데이트에 대한 최신 정보는 [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)를 참조하십시오.

## V2.0 이상에 배치된 인스턴스 업데이트

V2.0 이상의 인스턴스가 VMware vSphere 6.5 및 VMware vCenter Server 6.5로 배치되었습니다. 두 소프트웨어 컴포넌트 모두에 패치가 필요합니다.

### V2.0 이상에 배치된 vCenter Server 인스턴스

VMware vSphere 6.5의 경우:
* 새 V2.3 인스턴스의 경우, ESXi650-201712101-SG, ESXi650-201803401-BG 및 ESXi650-201803402-BG 패치가 적용된 vSphere가 배치됩니다.  
* V2.3 이전에 배치된 모든 기존 인스턴스의 경우, ESXi650-201712101-SG, ESXi650-201803401-BG 및 ESXi650-201803402-BG 패치로 모든 새 클러스터 및 ESXi 서버가 업데이트됩니다.
* 모든 기존 ESXi 서버, 그리고 V2.3으로 업그레이드하기 전까지 배치할 클러스터 또는 ESXi 서버의 경우에는 [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에 있는 ESXi650-201712101-SG, ESXi650-201803401-BG 및 ESXi650-201803402-BG 패치를 적용해야 합니다.

VMware vCenter Server 6.5의 경우:
* 모든 새 V2.3 인스턴스의 경우, vCenter 6.5 U1g 패치가 적용된 vCenter Server가 배치됩니다.
* V2.3 이전에 배치된 모든 기존 인스턴스의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에 있는 vCenter 6.5 U1g 패치를 적용해야 합니다.

### V2.0 이상에 배치된 Cloud Foundation 인스턴스

VMware vSphere 6.5 및 VMware vCenter Server 6.5의 필수 패치를 적용하려면 Cloud Foundation 인스턴스를 현재 V2.3 버전으로 업그레이드해야 합니다.

기존 모든 인스턴스 및 ESXi 서버의 경우, {{site.data.keyword.vmwaresolutions_full}} 콘솔의 **업데이트 및 패치** 페이지에 있는 패치(vSphere용 ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG 및 vCenter Server용 vCenter 6.5 U1g)를 적용하도록 프롬프트가 표시됩니다. 자세한 정보는 [Cloud Foundation 인스턴스에 업데이트 적용](../sddc/sd_applyingupdates.html)을 참조하십시오.

### V2.0 이상에 배치된 VMware vSphere 클러스터

VMware vSphere 6.5의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에 있는 ESXi650-201712101-SG, ESXi650-201803401-BG 및 ESXi650-201803402-BG 패치를 새로 배치되거나 기존에 있던 모든 vSphere 클러스터 및 ESXi 서버에 적용해야 합니다.

VMware vCenter Server 6.5의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에 있는 vCenter 6.5 U1g 패치를 새로 배치되거나 기존에 있던 모든 vCenter 서버에 적용해야 합니다.

## V1.9 이전에 배치된 인스턴스

V1.9 이전의 VMware vSphere를 비롯한 Cloud Foundation 및 vCenter Server 인스턴스는 VMware vSphere 6.0 및 VMware vCenter Server 6.0으로 배치되었습니다.

### V1.9 이전에 배치된 vCenter Server 인스턴스

VMware vSphere 6.0 및 VMware vCenter Server 6.0의 경우 모두, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에 있는 패치(vSphere용 ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG 및 vCenter Server용 vCenter 6.0 U3e)를 새로 배치되거나 기존에 있던 모든 인스턴스 및 ESXi 서버에 적용해야 합니다.

### V1.9 이전에 배치된 Cloud Foundation 인스턴스

인스턴스에 대한 업데이트는 인스턴스에 따라 달라지는 필수 공급업체 업데이트가 릴리스될 때 사용 가능합니다.

### V1.9 이전에 배치된 VMware vSphere 클러스터

VMware vSphere 6.0 및 VMware vCenter Server 6.0의 경우 모두, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에 있는 패치(vSphere용 ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG 및 vCenter Server용 vCenter 6.0 U3e)를 새로 배치되거나 기존에 있던 모든 클러스터 및 ESXi 서버에 적용해야 합니다.

## 관련 링크

* [업데이트를 Cloud Foundation 인스턴스에 적용](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)
