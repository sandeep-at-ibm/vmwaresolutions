---

copyright:

  years:  2016, 2019

lastupdated: "2018-09-20"

---

# 스펙터(Spectre) 및 멜트다운(Meltdown) 취약점 해결

스펙터(Spectre) 및 멜트다운(Meltdown) 취약점을 해결하려면 특정 주문에서 다수의 패치를 적용해야 합니다.

## 펌웨어 업데이트

펌웨어 업데이트에 대한 최신 정보는 [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)를 참조하십시오.

## V2.0 이상에 배치된 인스턴스 업데이트

V2.0 이상의 인스턴스가 VMware vSphere 6.5 및 VMware vCenter Server 6.5로 배치되었습니다. 두 소프트웨어 컴포넌트 모두에 패치가 필요합니다.

### V2.0 이상에 배치된 vCenter Server 인스턴스

#### VMware vSphere 6.5의 경우

* 모든 새 V2.6 인스턴스의 경우, ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG 및 ESXi650-201808403-BG 패치가 적용된 vSphere가 배치됩니다.
* V2.5 이전에 배치되었지만 V2.5로 업그레이드된 기존의 모든 인스턴스의 경우, 모든 새 클러스터 및 ESXi 서버는 ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG 및 ESXi650-201808403-BG 패치를 사용하여 업데이트됩니다.
* 기존의 모든 ESXi 서버 및 V2.5로 업그레이드하기 전까지 계속 배치하는 클러스터 또는 ESXi 서버의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG 및 ESXi650-201808403-BG 패치를 적용해야 합니다.

#### VMware vCenter Server 6.5의 경우

* 모든 새 V2.6 인스턴스의 경우, vCenter Server는 vCenter 6.5 U2c 누적 패치를 적용하여 전개됩니다.
* V2.6 이전에 배치된 기존의 모든 인스턴스의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 vCenter 6.5 U2c 패치를 적용해야 합니다.

### V2.0 이상에 배치된 Cloud Foundation 인스턴스

VMware vSphere 6.5 및 VMware vCenter Server 6.5의 필수 패치를 적용하려면 Cloud Foundation 인스턴스를 최신 VMware 패치 번들로 업그레이드해야 합니다. 기존의 모든 인스턴스 및 ESXi 서버의 경우, {{site.data.keyword.vmwaresolutions_full}} 콘솔의 **업데이트 및 패치** 페이지에서 패치를 적용하도록 프롬프트가 표시됩니다. 자세한 정보는 [Cloud Foundation 인스턴스에 업데이트 적용](../sddc/sd_applyingupdates.html)을 참조하십시오.

### V2.0 이상에 배치된 VMware vSphere 클러스터

모든 새 VMware vSphere 6.5 클러스터 및 ESXi 서버의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 ESXi650-201808401-BG, ESXi650-201808402-BG 및 ESXi650-201808403-BG 패치를 적용해야 합니다.

기존의 모든 VMware vSphere 6.5 클러스터의 경우 [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG 및 ESXi650-201808403-BG 패치를 적용해야 합니다.

VMware vCenter Server 6.5의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 vCenter 6.5 U2c 패치를 새로 배치되거나 기존 서버인 모든 vCenter Server에 적용해야 합니다.

## V1.9 이전에 배치된 인스턴스

V1.9 이전의 VMware vSphere 클러스터, Cloud Foundation 인스턴스 및 vCenter Server 인스턴스는 VMware vSphere 6.0 및 VMware vCenter Server 6.0으로 배치되었습니다.

### V1.9 이전에 배치된 vCenter Server 인스턴스

VMware vSphere 6.0 및 VMware vCenter Server 6.0의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 새로 배치되거나 기존의 모든 인스턴스 및 ESXi 서버에 패치(vSphere의 경우 ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG 및 ESXi600-201808403-BG 및 vCenter Server의 경우 vCenter 6.0 U3h)를 적용해야 합니다.

### V1.9 이전에 배치된 Cloud Foundation 인스턴스

인스턴스에 대한 업데이트는 인스턴스에 따라 달라지는 필수 공급업체 업데이트가 릴리스될 때 사용 가능합니다.

### V1.9 이전에 배치된 VMware vSphere 클러스터

VMware vSphere 6.0 및 VMware vCenter Server 6.0의 경우, [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)에서 새로 배치되거나 기존의 모든 vSphere 클러스터 및 ESXi 서버에 패치(vSphere의 경우 ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG 및 ESXi600-201808403-BG 및 vCenter Server의 경우 vCenter 6.0 U3h)를 적용해야 합니다.

### 관련 링크

* [업데이트를 Cloud Foundation 인스턴스에 적용](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware 제품 패치 사이트](https://my.vmware.com/group/vmware/patch)
