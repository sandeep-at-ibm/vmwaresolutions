---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Übersicht über die Anwendungsmodernisierung

Das folgende Diagramm zeigt die Referenzarchitektur der Anwendungsmodernisierung, die Acme Skateboards bereitstellt und die in dieser Reihe von Dokumenten eingehend beschrieben wird.

Abbildung 1. Architekturübersicht
![Diagramm der Architekturübersicht](vcsnsxt-aod.svg)

Durch diese Hybridarchitektur erhält Acme Skateboards folgende Möglichkeiten:
- Migration von virtuellen VMware-Maschinen aus der lokalen Umgebung auf {{site.data.keyword.cloud}} mit geringer oder ganz ohne Ausfallzeit und ohne erneute Anwendungskonfiguration.
-	Möglichkeit zum Starten des Anwendungsmodernisierungsprozesses, indem der Fokus darauf gelegt wird, die einfacheren Webschnittstellen und Middleware zu containerisieren, während komplexere Datenbanken als VMs erhalten bleiben.
-	Nutzung von Cloud Automation Manager (CAM) zum Scripten von "Infrastructure as Code" (IaC), um Services zusammenzustellen und zu orchestrieren, die aus VMs und Containern bestehen, damit eine Integration mit den vorhandenen DevOps-Toolchains und der ITSM-Lösung ermöglicht wird.

Hinsichtlich der Netzarchitektur setzt sich die Referenzarchitektur aus den folgenden Schlüsselkomponenten zusammen:
- **Lokale Virtualisierung** - Dies ist ein VMware-Cluster, der momentan die VMs von Acme Skateboards hostet. Es sind diese VMs, die derzeit die zu modernisierenden Anwendungen hosten. Dieser Cluster ist erforderlich, um die im Dokument [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) beschriebenen Voraussetzungen zu erfüllen, damit HCX ausgeführt werden kann. HCX erweitert die lokalen Netze in die {{site.data.keyword.cloud_notm}}. Das ermöglicht es den Kunden, VMs in die VCS-Instanz zu migrieren, die auf {{site.data.keyword.cloud_notm}} ausgeführt wird (eine Migration zurück ist bei Bedarf ebenfalls möglich).
- **VMware vCenter Server on IBM Cloud** - VCS stellt die grundlegenden VMware-Bausteine bereit: wie z. B. vSphere, vCenter Server, NSX-V und Speicheroptionen, einschließlich vSAN oder {{site.data.keyword.cloud_notm}} Endurance-Speicher, die für die automatische Bereitstellung einer VMware Software Defined Data Center-Lösung (SDDC) erforderlich sind. Dieser VMware-Cluster ist das Ziel für die migrierten VMs sowie einige der modernisierten Anwendungen in Containern, die in ICP gehostet werden. 

  Die Schlüsselkomponenten der Architektur sind Folgende:
 - **NSX-V** - NSX-V stellt die Schicht zur Netzvirtualisierung in VCS bereit, die ein Netzoverlay für die VMs von Acme Skateboards bietet. NSX-V aktiviert BYOIP und isoliert die Workloadnetze von den {{site.data.keyword.cloud_notm}}-Netzen. NSX-V wird von HCX programmiert, um die Netze zu erstellen, die bei Acme Skateboards aus der lokalen Umgebung erweitert werden sollen.
 - **IBM Cloud Private** - ICP ist eine Anwendungsplattform für die Entwicklung und Verwaltung von containerisierten Anwendungen. Es handelt sich hierbei um eine integrierte Umgebung, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole, Überwachungsframeworks und eine grafische Benutzerschnittstelle enthält, von der aus Acme Skateboards Anwendungen zentral bereitstellen, verwalten, überwachen und skalieren kann. Die VCS-Instanz hostet die ICP-Komponenten, die Masterknoten, die Workerknoten usw. und führt sie als VMs aus. 
  -	**IBM Cloud Automation Manager** - CAM ist eine auf Unternehmen abgestimmte IaC-Plattform (IaC = Infrastructure as Code), die eine zentrale Bereitstellung von VM-Workloads neben Kubernetes-Workloads bietet und bei der Sie einfach Vorlagen verwenden können. CAM ist eine für Docker vorbereitete Anwendung, die über ICP ausgeführt wird und nahtlos für die Autorisierung, rollenbasierte Zugriffssteuerung (RBAC) und andere Funktionen integriert ist.
  - **IBM Kubernetes Service** - IKS gibt Acme Skateboards die Möglichkeit, die vorhandenen modernisierten Anwendungen in Docker-Containern zu bereitzustellen, die in Kubernetes-Clustern ausgeführt werden. Die Masterknoten werden von IBM vollständig verwaltet, während die Workerknoten im Worker-Pool in demselben {{site.data.keyword.cloud_notm}}-Konto wie die VCS-Instanz bereitgestellt werden. Workerknoten sind Bare Metal Server, öffentliche oder dedizierte virtuelle Serverinstanzen. Calico wird automatisch in IKS installiert und konfiguriert. Calico bietet sichere Netzkonnektivität für Container und ist so in IKS konfiguriert, dass es die IP-in-IP-Kapselung zum Kapseln von Paketen verwendet, die die Teilnetze durchqueren, und NAT für abgehende Verbindungen von den Containern nutzt.
  - **Direct Link** - {{site.data.keyword.cloud_notm}} Direct Link verwendet den WAN-Provider von Acme Skateboard, um das Rechenzentren des Unternehmens mit {{site.data.keyword.cloud_notm}} zu verbinden, sodass eine zuverlässige und sichere Netzverbindung mit geringer Latenzzeit bereitgestellt wird. Diese Verbindung bietet folgende Möglichkeiten:
      - Zugriff Ihrer Unternehmensbenutzer auf die von der Cloud gehosteten Anwendungen
      - Datenverkehr zwischen lokalen VMs und Cloud-VMs
      - Datenverkehr zwischen traditionellen Systemen im lokalen Rechenzentrum und Cloud-VMs

## Wichtige Vorteile für Acme Skateboards

-	Beschleunigte Lieferung von IT-Projekten für Entwickler und Geschäftsbereiche durch Verringerung des Zeitaufwands für Beschaffung, Architektur, Implementierung und Bereitstellung von Ressourcen von Wochen oder sogar Monaten auf Stunden. Netz- oder Sicherheitsteams, die Services wie Lastverteilungsfunktionen, Firewalls, Switches und Router bereitstellen, tragen zur Verringerung der Wertschöpfungszeit bei. 
-	Verbesserte Sicherheit mit dedizierten Bare Metal Servern in einer gehosteten privaten Cloud, einschließlich Bereitstellung über einen privaten Endpunkt an {{site.data.keyword.cloud_notm}}-Services wie beispielsweise IKS und KMIP.
-	Konsistente Management- und Governance-Funktionalität der bereitgestellten Hybrid-Cloud durch Bereitstellung eines vollständigen Verwaltungszugriffs auf das Virtualisierungsmanagement, sodass vorhandene VMware-Tools, Scripts und Investitionen in Schulungen ihren Wert behalten.
-	Globale Nutzung von VMware-Know-how mit IBM Professional Services und IBM Managed Services, die weltweit mehr als 30 {{site.data.keyword.CloudDataCents_notm}} umfassen.

Kunden, die sich für cloudnative Anwendungsplattformen wie ICP und IKS interessieren, legen besonderen Wert auf Geschwindigkeit und Innovation und berücksichtigen weniger die Aspekte der Sicherheit und des Netzbetriebs. Diese Referenzarchitektur zeigt, wie VCS, ICP und IKS das Unternehmen Acme Skateboards zuverlässig beim Prozess der Anwendungsmodernisierung unterstützen.

## Zugehörige Links

* [Übersicht über VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
