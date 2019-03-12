---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-21"

---

# 자동화 사용자 비밀번호 만기

## 문제점

VMware Cloud Foundation 인스턴스에서 VMware 자동화 사용자 비밀번호가 만료되어 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 수행되는 오퍼레이션에 장애가 발생할 수 있습니다. 이 문제점은 인스턴스 V1.9 이하에서 발생합니다.

## 해결

VMware vSphere Web Client의 자동화 사용자가 표시됩니다. 사용자, 비밀번호 및 정책은 변경하면 안 됩니다. 그렇지 않으면 {{site.data.keyword.vmwaresolutions_short}} 콘솔을 통해 제공된 자동화된 오퍼레이션이 실패할 수 있습니다.
