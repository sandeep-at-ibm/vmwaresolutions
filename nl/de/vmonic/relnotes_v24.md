---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Releaseinformationen für V2.4
{: #relnotes_v24}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Unterstützung in der Landessprache
{: #relnotes_v24-nls}

Ab dem Release von V2.4 ist die Unterstützung in der Landessprache (National Language Support, NLS) für {{site.data.keyword.vmwaresolutions_short}} verfügbar.
Daher sind alle Funktionen in der Konsole, einschließlich der Benutzerdokumentation, in mehreren Sprachen verfügbar.

Die folgenden Sprachen werden neben Englisch unterstützt:
* Deutsch
* Spanisch
* Französisch
* Italienisch
* Japanisch
* Koreanisch
* Portugiesisch (Brasilien)
* Vereinfachtes Chinesisch
* Traditionelles Chinesisch

## Unterstützung für Skylake Xeon-CPU
{: #relnotes_v24-skylake}

Ab dem Release von V2.4 sind die folgenden neuen Bare Metal Server-CPU-Modelle zur Bereitstellung für VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}- und VMware vSphere on {{site.data.keyword.cloud_notm}}-Instanzen und -Cluster verfügbar:

* Dual Intel Skylake Xeon Silver 4110-Prozessor / 16 Cores insgesamt, 2,1 GHz
* Dual Intel Skylake Xeon Gold 5120-Prozessor / 28 Cores insgesamt, 2,2 GHz
* Dual Intel Skylake Xeon Gold 6140-Prozessor / 36 Cores insgesamt, 2,3 GHz

Weitere Informationen finden Sie im Abschnitt mit den [Einstellungen für Bare-Metal-Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-bare-metal-settings).

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v24-vcs}

### Leistungsverbesserung für Network File System
{: #relnotes_v24-nfs}

Die Leistungsstufe von 10 E/A-Operationen pro Sekunde und GB, die für die anspruchsvollsten Workloadtypen konzipiert ist, ist nicht mehr auf bestimmte {{site.data.keyword.CloudDataCent_notm}} begrenzt, sondern ist nun für alle Rechenzentren verfügbar. Weitere Informationen finden Sie im Abschnitt [Speicher](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vc_vcenterserveroverview-storage).

## Updates für Add-on-Services
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

Das aktuelle Release installiert IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.1 Patch 1 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

Bei der Bestellung dieses Service steht Ihnen nun eine neue Option für die Auswahl zwischen öffentlichem Netz und privatem Netz für HCX-Verbindungen zur Verfügung. Weitere Informationen enthält der Abschnitt [VMware HCX on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering).

## Neue und aktualisierte Dokumentation
{: #relnotes_v24-new-docs}

### Referenzdokumentation zur Architektur
{: #relnotes_v24-ref-archi}

Das Dokument zur {{site.data.keyword.vmwaresolutions_short}}-Architektur steht nun im Abschnitt *Referenz* der Benutzerdokumentation zur Verfügung. Weitere Informationen enthält der Abschnitt [Lösungsübersicht](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

### Servicedokumentation
{: #relnotes_v24-docs-services}

Die Informationen zu den Services sind neu strukturiert und die Navigation ist verbessert, damit Sie beim Bestellen von Services relevante Informationen leicht finden.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [F5 on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Veeam on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Zerto on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v24-ui}

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Bei den Teilfenstern zum Hinzufügen von Clustern und Hinzufügen von Services wird nun ein Seitenformat mit besser strukturiertem Aufbau verwendet, der ein effizienteres Ausführen von Aufgaben ermöglicht.
* Die Funktionalität der Seite **Ressourcen** wurde um Funktionen für die Suche, Paginierung und Sortierung erweitert. Aufgrund dieser Verbesserungen können Sie Ihre Instanzen schnell finden.
* Auf der Seite mit den Instanzdetails wird links nun ein Navigationsmenü verwendet, über das Sie schnell und einfach auf die Instanzinformationen zugreifen können.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
