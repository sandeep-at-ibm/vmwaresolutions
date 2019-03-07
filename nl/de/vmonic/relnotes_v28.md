---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

---

# Releaseinformationen für Version 2.8
{: #relnotes_v28}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #relnotes_v28-single-node-trial}

Mit der Single-node Trial für Migration und Anwendungsmodernisierung können Sie {{site.data.keyword.cloud_notm}} sehr schnell dahingehend testen, ob VMware-Workloads in {{site.data.keyword.cloud_notm}} migriert werden, und anschließend Workloads mithilfe von Containern modernisieren. Diese Testversion ist eine Version von {{site.data.keyword.icpfull_notm}}, gehostet auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} und mit der Kubernetes-Managementplattform, die mit den gleichen Tools wie in lokalen Umgebungen verwaltet werden kann.

Weitere Informationen finden Sie unter [Single-node Trial für Migration und Anwendungsmodernisierung - Übersicht](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-single-node-trial-for-migration-and-app-modernization-overview).

## Speicher für Network File System (NFS) hinzufügen und entfernen
{: #relnotes_v28-nfs}

Ab dem Release V2.8 können Sie jetzt NFS-Speicher (Network File System) zu einem vorhandenen NFS- oder vSAN vCenter Server-Cluster hinzufügen und auch NFS-Dateiressourcen aus einem vorhandenen vCenter Server-Cluster entfernen.

Die folgenden Optionen für angepassten, gemeinsam genutzten Speicher auf Dateiebene sind nun verfügbar:

* Gemeinsam genutzte NFS-Ressourcen mit einer Größe von 20 GB bis zu 12 TB in einzelnen GB-Schritten
* 0,25 IOPS/GB

Weitere Informationen finden Sie in den Abschnitten *NFS-Speicher zu vCenter Server-Instanzen hinzufügen* und *NFS-Speicher aus vCenter Server-Instanzen entfernen* unter [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).

## Unterstützung SAP-zertifizierter Broadwell E5-2690- und E7-8890-Server
{: #relnotes_v28-broadwell-e5-e7}

Ab dem Release V2.8 stehen die folgenden neuen {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU-Modelle für die Bereitstellung auf Instanzen und Clustern von VMware vCenter Server on {{site.data.keyword.cloud_notm}} und VMware vSphere on {{site.data.keyword.cloud_notm}} zur Verfügung:

* Dual Intel Xeon E5-2690 v4-Prozessor / 28 Kerne insgesamt, 2,60 GHz / 512 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,20 GHz / 1024 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,20 GHz / 2048 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,20 GHz / 4096 GB RAM

Weitere Informationen enthält der Abschnitt *{{site.data.keyword.baremetal_short_sing}}-Einstellungen* unter:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Unterstützung von Broadwell E7-4820- und E7-4850-Servern
{: #relnotes_v28-broadwell-e7}

Ab dem Release V2.8 stehen die folgenden neuen {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}}-CPU-Modelle zur Bereitstellung auf Instanzen und Clustern von vCenter Server, vCenter Server mit Hybridity Bundle, Cloud Foundation und vSphere on {{site.data.keyword.cloud_notm}} zur Verfügung:

* Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 2,0 GHz
* Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,1 GHz

Weitere Informationen enthält der Abschnitt *{{site.data.keyword.baremetal_short_sing}}-Einstellungen* unter:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [Cloud Foundation-Instanzen bestellen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Integrierter Platform Services Controller
{: #relnotes_v28-psc}

Ab dem Release V2.8 wird vCenter Server mit einem integrierten PSC (Platform Services Controller) bereitgestellt, das heißt, vCenter Server, die vCenter Server-Komponenten und der PSC werden auf einer einzigen virtuellen Maschine bereitgestellt. Diese Änderung bezieht sich auf alle neu bereitgestellten Instanzen von vCenter Server, vCenter Server with Hybridity und NetApp.

Bei Instanzen, für die ein Upgrade von einem früheren Release auf Version 2.8 durchgeführt wurde, ist der PSC nicht in vCenter Server integriert. Wenn Sie einen integrierten PSC verwenden möchten, müssen Sie die Konvertierung von einem externen zu einem integrierten PSC selbst vornehmen.

In einer Konfiguration mit mehreren Standorten, in der die primäre Instanz eine Instanz ist, für die der PSC manuell von extern in integriert konvertiert wurde, besitzen alle neu bereitgestellten sekundären V2.8-Instanzen den integrierten PSC.

Weitere Informationen finden Sie im Abschnitt *vCenter Server-Architektur* unter [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture).

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v28-vcs}

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.5 Update P3 (Build 6.5.0-10884925)
* vCenter Server 6.5 Update 2d (Build 6.5.0-10964411)
* Platform Services Controller 6.5 Update 2d (Build 6.5.0-10964411)

## Updates für VMware Cloud Foundation-Instanzen
{: #relnotes_v28-cf}

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.5 Update EP11 (Build 6.5.0-10719125)
* vCenter Server 6.5 U2c (Build 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (Build 6.5.0-9451637)

## Updates für Add-on-Services
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

Das aktuelle Release installiert IBM Spectrum Protect™ Plus V10.1.2 auf allen neu bereitgestellten Instanzen. eitere Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.2 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

Zuvor konnten Sie eine Cloud Foundation- oder vCenter Server-Instanz mit integriertem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" bestellen oder den Service nach der Erstbereitstellung zu einer vorhandenen Cloud Foundation- oder vCenter Server-Instanz hinzufügen.

Ab dem Release V2.8 ist der Service als eigenständiger Service verfügbar, ohne einer VMware-Instanz zugeordnet zu sein. Jede Instanz des Service kann eine oder mehrere Cloud Foundation-Instanzen, vCenter-Serverinstanzen oder vSphere-Cluster bedienen.

Weitere Informationen finden Sie unter [KMIP for VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations).

## Referenzdokumentation zur Architektur
{: #relnotes_v28-ref}

(Aktualisiert am 08. Februar 2019) Die folgenden technischen Dokumente stehen nun im Abschnitt *Referenz* der Benutzerdokumentation zur Verfügung:

* [{{site.data.keyword.vmwaresolutions_short}} mit NSX-T-Architektur](/docs/services/vmwaresolutions/archiref/vcsarch?topic=vmware-solutions-vcsarch-overview)
* [Caveonix RiskForesight-Referenzarchitektur](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [HCX on {{site.data.keyword.cloud_notm}} - Handbuch zur Bereitstellung und Inbetriebnahme](/docs/services/vmwaresolutions/archiref/vcshcx?topic=vmware-solutions-vcshcx-intro)

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v28-ui}

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
