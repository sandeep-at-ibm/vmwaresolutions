---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Konfiguration mit mehreren Standorten für vCenter Server with Hybridity Bundle-Instanzen

Mit {{site.data.keyword.vmwaresolutions_full}} können Sie Instanzen an unterschiedlichen Standorten bereitstellen und zügig betriebsbereit machen.

## Komponenten von Bereitstellungen mit mehreren Standorten

Eine Bereitstellung mit mehreren Standorten besteht aus den folgenden Komponenten.

* **Primäre Instanz**: Die primäre vCenter Server with Hybridity Bundle-Instanz weist die folgende Konfiguration auf:
  *  Microsoft Active Directory (AD) und DNS-Rootdomäne
  *  vCenter Server-Unterdomäne
  *  SSO-Domäne
  *  SSO-Standortname
* **Sekundäre Instanz(en)**: Einzelne oder mehrere sekundäre vCenter Server with Hybridity Bundle-Instanzen sind mit der primären Instanz verbunden und weisen die folgende Konfiguration auf:
   *  SSO-Standortname
   *  Mit der Rootdomäne der primären Instanz verknüpfte DNS-Unterdomäne
   *  Konfigurierte DNS- und AD-Replikation zwischen den virtuellen AD-Maschinen in der primären und der sekundären Instanz
   *  Bereitstellung und Konfiguration von PSC (Platform Services Controller) zur Replikation mit PSC in der primären Instanz
   *  Konfiguration von VMware vCenter in den sekundären Instanzen mit erweitertem Verbindungsmodus zu vCenter in der primären Instanz

## vCenter Server with Hybridity Bundle-Bereitstellung mit mehreren Standorten

Die Funktion für die Konfiguration mit mehreren Standorten verwendet eine Hub- und Peripherietopologie mit einem primären Standort und maximal sieben sekundären Standorten. Es wird nur eine einzige Schicht von Standorten unterstützt; Sie können also keine nachfolgenden Standorte konfigurieren, die mit anderen sekundären Standorten verknüpft sind. In einer Konfiguration mit mehreren Standorten können insgesamt 128 ESXi-Server in allen Instanzen verwendet werden.

Falls Ihre Konfiguration eine Bereitstellung mit mehreren Standorten mit mehr als 128 ESXi-Servern erforderlich macht, bitten Sie den IBM Support um Unterstützung. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html).
{:note}

Die folgende Abbildung zeigt eine Gesamtübersicht über die vCenter Server with Hybridity Bundle-Bereitstellung mit mehreren Standorten.

Abbildung 1. vCenter Server with Hybridity Bundle-Bereitstellung mit mehreren Standorten

![vCenter Server with Hybridity Bundle-Bereitstellung mit mehreren Standorten](../sddc/multisite-hub-spoke.svg "vCenter Server with Hybridity Bundle-Bereitstellung mit mehreren Standorten")

Das Modell enthält die folgenden Schichten:

* **Primäre Instanz**: In einer Konfiguration mit mehreren Standorten definieren Sie beim Bereitstellen der ersten Instanz diese Instanz während des Instanzbestellprozesses als primäre Instanz.
* **Sekundäre Instanzen**: In einer Konfiguration mit mehreren Standorten definieren Sie die Instanzen, die der primären Instanz zugeordnet werden sollen, während des Bestellprozesses als sekundäre Instanzen.

Sie können gleichzeitig jeweils nur eine einzige sekundäre Instanz zu einer primären Instanz zuordnen. Die gleichzeitige Zuordnung mehrerer sekundärer Instanzen zu einer primären Instanz ist nicht möglich. Dazu müssen Sie den Bestellprozess erneut durchlaufen und die zuvor definierte primäre Instanz als primäre Instanz für die sekundäre Instanz auswählen. Sie müssen den Prozess für alle sekundären Instanzen wiederholen, die Sie erstellen möchten.

Sie können maximal 8 Instanzen (1 primäre und 7 sekundäre) in einer Konfiguration mit mehreren Standorten bereitstellen.

Das Löschen von vCenter Server with Hybridity Bundle-Instanzen, die Teil einer Konfiguration mit mehreren Standorten sind, erfordert eine besondere Planung. Weitere Informationen hierzu finden Sie im Abschnitt [vCenter Server with Hybridity Bundle-Instanzen in einer Konfiguration mit mehreren Standorten löschen](vc_hybrid_deletinginstance_multi.html).
{:note}

### Zugehörige Links

* [Assign Primary Role to NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [Configuring Secondary NSX Managers](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [AD trusts supported with vCenter Single Sign-On](https://kb.vmware.com/kb/2064250){:new_window}
* [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}
