---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Releaseinformationen für V2.4

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](../vmonic/trbl_fix_spectre.html).

## Unterstützung in der Landessprache

Ab dem Release von V2.4 ist die Unterstützung in der Landessprache (National Language Support, NLS) für IBM Cloud for VMware-Lösungen verfügbar.
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

**Hinweis**: Die Referenzdokumente zur Architektur sind nur in Englisch verfügbar.

## Unterstützung für Skylake Xeon-CPU

Ab dem Release von V2.4 sind die folgenden neuen Bare Metal Server-CPU-Modelle zur Bereitstellung für VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}-, VMware vSphere on {{site.data.keyword.cloud_notm}}- und VMware Federal on {{site.data.keyword.cloud_notm}}-Instanzen und -Cluster verfügbar:

* Dual Intel Skylake Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz
* Dual Intel Skylake Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz
* Dual Intel Skylake Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz

Weitere Informationen enthält der Abschnitt *Einstellungen für Bare Metal Server* unter:

* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [VMware Federal-Instanzen bestellen](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## Updates für VMware vCenter Server-Instanzen

### Leistungsverbesserung für Network File System

Die Leistungsstufe von 10 E/A-Operationen pro Sekunde und GB, die für die anspruchsvollsten Workloadtypen konzipiert ist, ist nicht mehr auf bestimmte {{site.data.keyword.CloudDataCent_notm}} begrenzt, sondern ist nun für alle Rechenzentren verfügbar. Weitere Informationen finden Sie im Abschnitt *Speicher* unter [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html#vcenter-server-technical-specifications).

## Updates für VMware Federal-Instanzen

### Neue Option für IBM Cloud Data Center

Sie können VMware Federal-Instanzen nun für das {{site.data.keyword.CloudDataCent_notm}} "DAL08 - Dallas, TX" bereitstellen. Weitere Informationen finden Sie im Abschnitt *Verfügbarkeit des IBM Cloud-Rechenzentrums* unter [Voraussetzungen und Planung für VMware Federal-Instanzen](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability).

## Updates für Add-on-Services

### IBM Spectrum Protect Plus on IBM Cloud

Das aktuelle Release installiert IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 auf allen neu bereitgestellten Instanzen. Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.1 Patch 1 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

Bei der Bestellung dieses Service steht Ihnen nun eine neue Option für die Auswahl zwischen öffentlichem Netz und privatem Netz für HCX-Verbindungen zur Verfügung. Weitere Informationen enthält der Abschnitt [VMware HCX on IBM Cloud bestellen](../services/hcx_ordering.html).

## Neue und aktualisierte Dokumentation

### Referenzdokumentation zur Architektur

Das Dokument zur {{site.data.keyword.vmwaresolutions_short}}-Architektur steht nun im Abschnitt *Referenz* der Benutzerdokumentation zur Verfügung. Das Referenzdokument zur Architektur ist nur in Englisch verfügbar. Weitere Informationen enthält der Abschnitt [Lösungsübersicht](../archiref/solution/solution_overview.html).

### Servicedokumentation

Die Serviceinformationen wurden neu strukturiert und die Navigation wurde verbessert, damit relevante Informationen beim Bestellen von Services leicht gefunden werden können.

Weitere Informationen enthalten die folgenden Abschnitte:

* [F5 on IBM Cloud bestellen](../services/f5_ordering.html)
* [FortiGate Security Appliance on IBM Cloud bestellen](../services/fsa_ordering.html)
* [FortiGate Virtual Appliance on IBM Cloud bestellen](../services/fortinetvm_ordering.html)
* [Hytrust CloudControl on IBM Cloud bestellen](../services/htcc_ordering.html)
* [Hytrust DataControl on IBM Cloud bestellen](../services/htdc_ordering.html)
* [IBM Spectrum Protect Plus on IBM Cloud bestellen](../services/spp_ordering.html)
* [KMIP for VMware on IBM Cloud bestellen](../services/kmip_ordering.html)
* [Veeam on IBM Cloud bestellen](../services/veeam_ordering.html)
* [Zerto on IBM Cloud bestellen](../services/zerto_ordering.html)

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Bei den Teilfenstern zum Hinzufügen von Clustern und Hinzufügen von Services wird nun ein Seitenformat mit besser strukturiertem Aufbau verwendet, der ein effizienteres Ausführen von Aufgaben ermöglicht.
* Die Funktionalität der Seite **Bereitgestellte Instanzen** wurde um Funktionen für die Suche, Paginierung und Sortierung erweitert. Durch diese Verbesserungen können Sie Ihre Instanzen sehr schnell finden.
* Auf der Seite mit den Instanzdetails wird links nun ein Navigationsmenü verwendet, über das Sie schnell und einfach auf die Instanzinformationen zugreifen können.
* Verschiedene Fehlernachrichten und QuickInfos wurden erweitert, um Ihnen bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle zu helfen.
