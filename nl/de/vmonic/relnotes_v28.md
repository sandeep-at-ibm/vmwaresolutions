---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-28"

---

# Releaseinformationen für Version 2.8

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung

Mit der Single-node Trial für Migration und Anwendungsmodernisierung können Sie {{site.data.keyword.cloud_notm}} sehr schnell dahingehend testen, ob VMware-Workloads in {{site.data.keyword.cloud_notm}} migriert werden, und anschließend Workloads mithilfe von Containern modernisieren. Diese Testversion ist eine Version von {{site.data.keyword.icpfull_notm}}, gehostet auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} und mit der Kubernetes-Managementplattform, die mit den gleichen Tools wie in lokalen Umgebungen verwaltet werden kann.

Weitere Informationen finden Sie unter [Single-node Trial für Migration und Anwendungsmodernisierung - Übersicht](/docs/services/vmwaresolutions/vcenter/cloud_modern_bundle_overview.html).

## Speicher für Network File System (NFS) hinzufügen und entfernen

Ab dem Release V2.8 können Sie jetzt NFS-Speicher (Network File System) zu einem vorhandenen NFS- oder vSAN vCenter Server-Cluster hinzufügen und auch NFS-Dateiressourcen aus einem vorhandenen vCenter Server-Cluster entfernen.

Die folgenden Optionen für angepassten, gemeinsam genutzten Speicher auf Dateiebene sind nun verfügbar: 

* Gemeinsam genutzte NFS-Ressourcen mit einer Größe von 20 GB bis zu 12 TB in einzelnen GB-Schritten
* 0,25 IOPS/GB

Weitere Informationen finden Sie in den Abschnitten *NFS-Speicher zu vCenter Server-Instanzen hinzufügen* und *NFS-Speicher aus vCenter Server-Instanzen entfernen* unter [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html#adding-nfs-storage-to-vcenter-server-instances).

## Unterstützung SAP-zertifizierter Broadwell E5-2690- und E7-8890-Server

Ab dem Release V2.8 stehen die folgenden neuen {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU-Modelle für die Bereitstellung auf Instanzen und Clustern von VMware vCenter Server on {{site.data.keyword.cloud_notm}} und VMware vSphere on {{site.data.keyword.cloud_notm}} zur Verfügung:

* Dual Intel Xeon E5-2690 v4-Prozessor / 28 Kerne insgesamt, 2,60 GHz / 512 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,20 GHz / 1024 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,20 GHz / 2048 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,20 GHz / 4096 GB RAM

Weitere Informationen enthält der Abschnitt *{{site.data.keyword.baremetal_short_sing}}-Einstellungen* unter:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Unterstützung von Broadwell E7-4820- und E7-4850-Servern

Ab dem Release V2.8 stehen die folgenden neuen {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}}-CPU-Modelle zur Bereitstellung auf Instanzen und Clustern von vCenter Server, vCenter Server mit Hybridity Bundle, Cloud Foundation und vSphere on {{site.data.keyword.cloud_notm}} zur Verfügung:

* Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 2,0 GHz
* Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,1 GHz

Weitere Informationen enthält der Abschnitt *{{site.data.keyword.baremetal_short_sing}}-Einstellungen* unter:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter/vc_hybrid_orderinginstance.html#bare-metal-server-settings)
* [Cloud Foundation-Instanzen bestellen](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Integrierter Platform Services Controller

Ab dem Release V2.8 wird vCenter Server mit einem integrierten PSC (Platform Services Controller) bereitgestellt, das heißt, vCenter Server, die vCenter Server-Komponenten und der PSC werden auf einer einzigen virtuellen Maschine bereitgestellt. Diese Änderung bezieht sich auf alle neu bereitgestellten Instanzen von vCenter Server, vCenter Server with Hybridity und NetApp.

Bei Instanzen, für die ein Upgrade von einem früheren Release auf Version 2.8 durchgeführt wurde, ist der PSC nicht in vCenter Server integriert. Wenn Sie einen integrierten PSC verwenden möchten, müssen Sie die Konvertierung von einem externen zu einem integrierten PSC selbst vornehmen.

In einer Konfiguration mit mehreren Standorten, in der die primäre Instanz eine Instanz ist, für die der PSC manuell von extern in integriert konvertiert wurde, besitzen alle neu bereitgestellten sekundären V2.8-Instanzen den integrierten PSC.

Weitere Informationen finden Sie im Abschnitt *vCenter Server-Architektur* unter [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#vcenter-server-architecture).

## Updates für VMware vCenter Server-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.5 Update P3 (Build 6.5.0-10884925)
* vCenter Server 6.5 Update 2d (Build 6.5.0-10964411)
* Platform Services Controller 6.5 Update 2d (Build 6.5.0-10964411)

## Updates für VMware Cloud Foundation-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.5 Update EP11 (Build 6.5.0-10719125)
* vCenter Server 6.5 U2c (Build 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (Build 6.5.0-9451637)

## Updates für Add-on-Services

### IBM Spectrum Protect Plus on IBM Cloud

Das aktuelle Release installiert IBM Spectrum Protect™ Plus V10.1.2 auf allen neu bereitgestellten Instanzen. eitere Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.2 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}.

### KMIP for VMware on IBM Cloud

Zuvor konnten Sie eine Cloud Foundation- oder vCenter Server-Instanz mit integriertem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" bestellen oder den Service nach der Erstbereitstellung zu einer vorhandenen Cloud Foundation- oder vCenter Server-Instanz hinzufügen.

Ab dem Release V2.8 ist der Service als eigenständiger Service verfügbar, ohne einer VMware-Instanz zugeordnet zu sein. Jede Instanz des Service kann eine oder mehrere Cloud Foundation-Instanzen, vCenter-Serverinstanzen oder vSphere-Cluster bedienen.

**Hinweis**: In diesem Release ist KMIP for VMware on {{site.data.keyword.cloud_notm}} ausschließlich auf die vSphere-Verschlüsselung begrenzt.

Weitere Informationen finden Sie unter [KMIP for VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html).

## Referenzdokumentation zur Architektur

Ein neues technisches Dokument zur KMIP for VMware on {{site.data.keyword.cloud_notm}}-Lösungsarchitektur steht im Abschnitt *Referenzinformationen* der Benutzerdokumentation zur Verfügung. Weitere Informationen finden Sie unter [Übersicht über KMIP for VMware](/docs/services/vmwaresolutions/archiref/kmip/overview.html).

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
