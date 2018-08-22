---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Konfiguration mit mehreren Standorten für Cloud Foundation-Instanzen

Mit {{site.data.keyword.vmwaresolutions_full}} können Sie Instanzen an unterschiedlichen Standorten bereitstellen und zügig betriebsbereit machen.

**Hinweise**:
* VMware Cloud Foundation- und VMware vCenter Server-Instanzen können nicht in einer Konfiguration mit mehreren Standorten verbunden werden.
* Instanzen, die in V2.0 bereitgestellt wurden, können nicht mit Instanzen aus früheren Releases verbunden werden, selbst wenn für diese ein Upgrade auf V2.0 durchgeführt wurde.


## Komponenten von Bereitstellungen mit mehreren Standorten

Eine Bereitstellung mit mehreren Standorten besteht aus den folgenden Komponenten.

* **Primäre Instanz**: Die primäre VMware Cloud Foundation-Instanz weist die folgende Konfiguration auf:
  *  Microsoft Active Directory (AD) und DNS-Rootdomäne
  *  Cloud Foundation-Unterdomäne
  *  SSO-Domäne
  *  SSO-Standortname
* **Sekundäre Instanz(en)**: Eine oder mehrere sekundäre Cloud Foundation-Instanzen sind mit der primären Instanz verbunden und weisen die folgende Konfiguration auf:
   *  SSO-Standortname
   *  Mit der Rootdomäne der primären Instanz verknüpfte DNS-Unterdomäne
   *  Konfigurierte DNS- und AD-Replikation zwischen den virtuellen AD-Maschinen in der primären und der sekundären Instanz
   *  Bereitstellung und Konfiguration von PSC (Platform Services Controller) zur Replikation mit PSC in der primären Instanz
   *  Konfiguration von VMware vCenter in den sekundären Instanzen mit erweitertem Verbindungsmodus zu vCenter in der primären Instanz

## Cloud Foundation-Bereitstellung mit mehreren Standorten

Die Funktion für die Konfiguration mit mehreren Standorten verwendet eine Hub- und Peripherietopologie mit einem primären Standort und maximal sieben sekundären Standorten. Es wird nur eine einzige Schicht von Standorten unterstützt; Sie können also keine nachfolgenden Standorte konfigurieren, die mit anderen sekundären Standorten verknüpft sind. In einer Konfiguration mit mehreren Standorten können insgesamt 128 ESXi-Server in allen Instanzen verwendet werden.

**Hinweis**: Falls Ihre Konfiguration eine Bereitstellung mit mehreren Standorten mit mehr als 128 ESXi-Servern erforderlich macht, bitten Sie den IBM Support um Unterstützung. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html).

Die folgende Abbildung zeigt eine vollständige Cloud Foundation-Bereitstellung mit mehreren Standorten.

Abbildung 1. Cloud Foundation-Bereitstellung mit mehreren Standorten

![Cloud Foundation-Bereitstellung mit mehreren Standorten](multisite-hub-spoke.svg "Cloud Foundation-Bereitstellung mit mehreren Standorten")

Das Modell enthält die folgenden Schichten:

* **Primäre Instanz**: In einer Konfiguration mit mehreren Standorten definieren Sie beim Bereitstellen der ersten Instanz diese Instanz während des Instanzbestellprozesses als primäre Instanz.
* **Sekundäre Instanzen**: In einer Konfiguration mit mehreren Standorten definieren Sie die Instanzen, die der primären Instanz zugeordnet werden sollen, während des Bestellprozesses als sekundäre Instanzen.

Sie können gleichzeitig jeweils nur eine einzige sekundäre Instanz zu einer primären Instanz zuordnen. Die gleichzeitige Zuordnung mehrerer sekundärer Instanzen zu einer primären Instanz ist nicht möglich. Dazu müssen Sie den Bestellprozess erneut durchlaufen und die zuvor definierte primäre Instanz als primäre Instanz für die sekundäre Instanz auswählen. Sie müssen den Prozess für alle sekundären Instanzen wiederholen, die Sie erstellen möchten.

Sie können maximal 8 Instanzen (1 primäre und 7 sekundäre) in einer Konfiguration mit mehreren Standorten bereitstellen.

**Hinweis**: Das Löschen von Cloud Foundation-Instanzen, die Teil einer Konfiguration mit mehreren Standorten sind, erfordert eine besondere Planung. Weitere Informationen hierzu finden Sie im Abschnitt [Cloud Foundation-Instanzen in Konfiguration mit mehreren Standorten löschen](sd_deletinginstance_multi.html).

### Zugehörige Links

* [Assign Primary Role to NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [Configuring Secondary NSX Managers](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [Active Directory Trusts supported with VMware vCenter Single Sign-On](https://kb.vmware.com/kb/2064250){:new_window}
* [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}
