---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Allgemeine Architekturübersicht
{: #vcsnsxt-overview}

Der folgende Abschnitt enthält weitere Details zu der Netzarchitektur, die in dieser Referenzarchitektur verwendet wird. Es besteht aus den folgenden Abschnitten:
* **VMware vCenter Server on {{site.data.keyword.cloud}} - Übersicht ** – Beschreibt die Schwerpunkte der vCenter Server-Plattform.
* **Netzübersicht** – Bietet Informationen zu den Netzkomponenten, die in dieser Referenzarchitektur eingesetzt werden:
  - **{{site.data.keyword.cloud_notm}}-Netzbetrieb** – {{site.data.keyword.cloud_notm}} stellt das physische Netz zur Verfügung und wird vollständig durch {{site.data.keyword.cloud_notm}} verwaltet. Lesen Sie die Beschreibung der Schlüsselmerkmale des {{site.data.keyword.cloud_notm}}-Netzbetriebs, um die Netzflüsse zwischen lokalen und fernen Standorten und zwischen Workloads nachzuvollziehen, die in unterschiedlichen Services gehostet werden.
  - **NSX-V** – Die Basis des vCenter Server-Netzbetriebs bildet das {{site.data.keyword.cloud_notm}}-Netz; hinzu kommt hier ein Overlay, das von VMware NSX-V bereitgestellt wird. Dieses Overlay segmentiert den Datenverkehr aus dem Underlay-Netz von {{site.data.keyword.cloud_notm}}, was eine größere Steuerung und Konfigurierbarkeit (einschließlich BYOIP, "Bring Your Own IP") ermöglicht.
  - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} verwendet Calico als Schnittstellen-Plug-in für das Containernetz.
  - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} verwendet Calico als Schnittstellen-Plug-in für das Containernetz.

* **Integration** - Beschreibt die Architektur der Netzbetriebskomponenten, die die erforderlichen Datenflüsse und Adressierungen für den Datenaustausch im Netz ermöglichen:
  - IP-Adresszuordnung
  - Datenflüsse des Netzverkehrs

## Übersicht über vCenter Server
{: #vcsnsxt-overview-vcs-ovw}

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle ist eine gehostete private Cloud, die Sie bei der schnellen und einfachen Erweiterung Ihrer lokalen Infrastruktur in die Cloud unterstützt. Dies ermöglicht eine sichere und nahtlose Hybridinfrastruktur und echte Anwendungsmobilität.

vCenter Server Hybridity Bundle wird auf mindestens vier {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen bereitgestellt, bietet dedizierten Speicher über ein Virtual Storage Area Network (VSAN) und beinhaltet die automatische Bereitstellung und Konfiguration einer einfach zu verwaltenden softwaredefinierten Netzinfrastruktur (NSX-V). vCenter Server Hybridity Bundle ist eine Referenzarchitektur, die automatisch bereitgestellt wird, um Konsistenz, Leistung und Konformität sicherzustellen. In zahlreichen Fällen kann die gesamte Umgebung in weniger als einem Tag bereitgestellt werden und die Bare-Metal-Infrastruktur kann die Rechen- und Speicherkapazität nach Bedarf schnell und flexibel skalieren.

Es stehen zahlreiche Optionen zur Verfügung, um vCenter Server Hybridity Bundle zu verbessern und zu erweitern. Die {{site.data.keyword.cloud_notm}}-Serviceangebote umfassen nicht nur Add-on-Speicheroptionen und verschiedene öffentliche und private WAN-Konnektivitätsoptionen, sondern richten sich auch an Bereiche wie Plattformsicherheit, Netzsicherheit, Lastausgleich des Datenverkehrs bis hin zur Sicherung und Disaster-Recovery.

Zu den Plattformsicherheitsservices gehört auch HyTrust CloudControl on {{site.data.keyword.cloud_notm}}. Dieser Service bietet eine automatisierte Sicherheits- und Konformitätsunterstützung und ermöglicht eine bessere Transparenz und Kontrolle über Ihre Cloudumgebung und Administratoren. HyTrust DataControl on {{site.data.keyword.cloud_notm}} bietet Datenschutz mit leistungsstarker Verschlüsselung und skalierbarem Schlüsselmanagement, um Ihre Workloads über den gesamten Lebenszyklus hinweg zu schützen. {{site.data.keyword.cloud_notm}} Secure Virtualization vereinfacht die Konformität und schützt Ihre Daten mit Verschlüsselung, Geofencing-Richtlinien und Mechanismen für die rollenbasierte Zugriffssteuerung, während KMIP for VMware on {{site.data.keyword.cloud_notm}} ein Angebot für das Lifecycle-Management von Verschlüsselungsschlüsseln ist, das die von {{site.data.keyword.cloud_notm}}-Services oder kundenintegrierten Anwendungen verwendeten Verschlüsselungsschlüssel verwaltet.

Netzsicherheitsoptionen sind zum einen die FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, die ein hoch verfügbares Paar von FortiGate Security Appliance-Geräten bereitstellt, um den Datenaustausch im Netz zu analysieren und Ihre virtuelle Infrastruktur zu schützen, sowie zum anderen die FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, die ein hoch verfügbares Paar von FortiGate-VMs in {{site.data.keyword.cloud_notm}} bereitstellt, mit dessen Hilfe Sie durch die Implementierung von kritischen Sicherheitsmaßnahmen in Ihrer virtuellen Infrastruktur Risiken verringern können. Weitere Netzsicherheitsangebote befinden sich in der Entwicklung.

Der Network Load Balancer-Service von F5 on {{site.data.keyword.cloud_notm}} optimiert die Leistung und sorgt für die Verfügbarkeit und Sicherheit Ihrer wichtigsten Anwendungen mit der F5 BIG-IP-Suite.

Angebote für Sicherung und Disaster-Recovery von IBM, Veeam und Zerto geben Ihnen die nötige Sicherheit und ermöglichen eine Fortsetzung des Betriebs, wenn ein Störfall eintritt. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} ist eine Lösung für Datenschutz und Datenverfügbarkeit für virtuelle Umgebungen. Veeam on {{site.data.keyword.cloud_notm}} ermöglicht die Verfügbarkeit für das Always-On Enterprise™ mit integrierter Sicherung, Wiederherstellung und Replikation in {{site.data.keyword.cloud_notm}}. Zerto on {{site.data.keyword.cloud_notm}} bietet Kunden, die die lokale Lösung oder {{site.data.keyword.cloud_notm}} verwenden, eine sichere, flexible und skalierbare Disaster-Recovery-Lösung.

vCenter Server Hybridity Bundle ist kein verwalteter Service, Sie können aber von IBM verwaltete Services hinzufügen, wenn Sie die Routineabläufe und die Wartung der Virtualisierung, des Gastbetriebssystems oder der Anwendungsschichten auslagern möchten. Das Team von {{site.data.keyword.cloud_notm}} Professional Services kann Ihnen durch Migrations-, Implementierungs-, Planungs- und Onboarding-Services ebenfalls dabei helfen, Ihren Einstieg in die Cloud zu beschleunigen.

Die Plattformintegrationsoptionen von vCenter Hybridity Bundle sind nicht auf die Optionen beschränkt, die von VMware bereitgestellt werden (z. B. vRealize Suite oder vSphere with Operations Management), sondern umfassen mehrere {{site.data.keyword.cloud_notm}}-Serviceangebote wie zum Beispiel [vCenter Server und {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) und [vCenter Server und {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro), die sich zum Verwalten und Bereitstellen von "Infrastructure as Code" (IaC) der Open-Source-Lösung Terraform bedienen.

Das umfangreiche Portfolio von Services und Angeboten mit mehreren integrierten Optionen, die für vCenter Server Hybridity Bundle zur Verfügung stehen, bieten eine echte Hybridplattform, die "Hybridity as a Service" zur Verfügung stellt.

## Zugehörige Links
{: #vcsnsxt-overview-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
