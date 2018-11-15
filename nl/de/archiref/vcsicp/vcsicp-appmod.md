---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# Übersicht über die Anwendungsmodernisierung

Das folgende Diagramm zeigt die Referenzarchitektur der Anwendungsmodernisierung, die Acme Skateboards bereitstellt und die in dieser Reihe von Dokumenten eingehend beschrieben wird.

Abbildung 1. Diagramm mit Architekturübersicht

![Diagramm mit Architekturübersicht](vcsicp-arch-overview.svg)

Durch diese Hybridarchitektur erhält Acme Skateboards folgende Möglichkeiten:
- Migration von VMware-VMs aus der lokalen Umgebung auf IBM Cloud mit geringer oder ganz ohne Ausfallzeit und ohne erneute Anwendungskonfiguration.
- Möglichkeit zum Starten des Anwendungsmodernisierungsprozesses, indem der Fokus darauf gelegt wird, die einfacheren Webschnittstellen und Middleware zu containerisieren, während komplexere Datenbanken als VMs erhalten bleiben.
- Nutzung von Cloud Automation Manager (CAM) zum Scripten von "Infrastructure as Code" (IaC), um Services zusammenzustellen und zu orchestrieren, die aus VMs und Containern bestehen, um eine Integration mit den vorhandenen DevOps-Toolchains und der ITSM-Lösung zu ermöglichen.

Die Referenzarchitektur setzt sich aus den folgenden Schlüsselkomponenten zusammen:
- **Lokale Virtualisierung** - Dies ist ein VMware-Cluster, der momentan die VMs von Acme Skateboards hostet. Es sind diese VMs, die derzeit die zu modernisierenden Anwendungen hosten. Dieser Cluster ist erforderlich, um die Voraussetzungen der Architektur von [IBM Cloud vCenter Server with Hybridity Bundle](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) zu erfüllen, damit HCX ausgeführt werden kann. HCX erweitert die lokalen Netze in die IBM Cloud. Das ermöglicht es den Kunden, VMs in die VMware vCenter Server on IBM Cloud-Instanz (VCS) zu migrieren, die auf IBM Cloud ausgeführt wird (eine Migration zurück ist bei Bedarf ebenfalls möglich).

- **IBM Cloud for VMware Solutions** - Die VCS-Instanz stellt die grundlegenden VMware-Bausteine bereit, wie z. B. vSphere, vCenter Server, NSX-V und Speicheroptionen, einschließlich vSAN oder IBM Cloud Endurance-Speicher, die für die automatische Bereitstellung einer VMware Software Defined Data Center-Lösung (SDDC) erforderlich sind. Der VMware-Cluster ist das Ziel für die migrierten VMs sowie einige der modernisierten Anwendungen in Containern, die in ICP gehostet werden. Die Schlüsselkomponenten in VCS sind:
    - **NSX-V** - NSX-V ist die Schicht zur Netzvirtualisierung in VCS, die ein Netzoverlay für die VMs von Acme Skateboards zur Verfügung stellt. NSX-V aktiviert BYOIP und isoliert die Workloadnetze von den IBM Cloud-Netzen. NSX-V wird von HCX programmiert, um die Netze zu erstellen, die bei Acme Skateboards aus der lokalen Umgebung erweitert werden sollen.

    - **NSX-T** - NSX-T bietet eine gemeinsame Gruppe von Tools für das Netz- und Sicherheitsmanagement bei Containern und VMs. NSX-T ist voll kompatibel mit Kubernetes Container Networking Interface (CNI) und wird in CNI integriert, um die Containervernetzung zu ermöglichen. NSX-T stellt das Overlay-Netz zur Verfügung, das von den modernisierten Anwendungen genutzt wird, und ersetzt Calico, das nativ von ICP und IKS verwendet wird.

- **IBM Cloud Private** - ICP ist eine Anwendungsplattform für die Entwicklung und Verwaltung von containerisierten Anwendungen. ICP ist eine integrierte Umgebung, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole, Überwachungsframeworks und eine grafische Benutzerschnittstelle enthält, von der aus Acme Skateboards Anwendungen zentral bereitstellen, verwalten, überwachen und skalieren kann. Die VCS-Instanz hostet die ICP-Komponenten, die Masterknoten, die Workerknoten usw. und führt sie als VMs aus. ICP hostet:
    - **IBM Cloud Automation Manager** – CAM ist eine auf Unternehmen abgestimmte IaC-Plattform (IaC = Infrastructure as Code), die eine zentrale Bereitstellung von VM-Workloads (lokal oder auf VCS) neben Kubernetes-Workloads (in ICP oder IKS) bietet und bei der Sie einfach Vorlagen verwenden können. CAM ist eine für Docker vorbereitete Anwendung, die über ICP ausgeführt wird und nahtlos für die Autorisierung, rollenbasierte Zugriffssteuerung (RBAC) und andere Funktionen integriert ist.
    - Die containerisierten Anwendungen von Acme Skateboards, die in dieser Umgebung bereitgestellt werden sollen.

- **IBM Kubernetes Service** – IKS gibt Acme Skateboards die Möglichkeit, die vorhandenen modernisierten Anwendungen in Docker-Containern zu bereitzustellen, die in Kubernetes-Clustern ausgeführt werden. Die Masterknoten werden von IBM vollständig verwaltet, während die Workerknoten im Worker-Pool in demselben IBM Cloud-Konto wie die VCS-Instanz bereitgestellt werden. Workerknoten können Bare Metal Server, öffentliche oder dedizierte virtuelle Serverinstanzen sein. Calico wird automatisch in IKS installiert und konfiguriert. Calico bietet sichere Netzkonnektivität für Container und ist so in IKS konfiguriert, dass es die IP-in-IP-Kapselung für Pakete verwendet, die die Teilnetze durchqueren, und dass es NAT für abgehende Verbindungen von den Containern verwendet.

- **Direct Link** - IBM Cloud Direct Link verwendet den WAN-Provider von Acme Skateboard, um das Rechenzentren des Unternehmens mit IBM Cloud zu verbinden, sodass eine zuverlässige und sichere Netzverbindung mit geringer Latenzzeit bereitgestellt wird. Diese Verbindung bietet folgende Möglichkeiten:
    - Zugriff Ihrer Unternehmensbenutzer auf die von der Cloud gehosteten Anwendungen
    - Datenverkehr zwischen lokalen VMs und Cloud-VMs
    - Datenverkehr zwischen traditionellen Systemen im lokalen Rechenzentrum und Cloud-VMs

## Wichtige Vorteile für Acme Skateboards

VMware vCenter Server on IBM Cloud (VCS) stellt die grundlegenden Bausteine zur Verfügung, wie z. B. VMware vSphere, vCenter Server, NSX und gemeinsame Speicheroptionen, einschließlich vSAN, die erforderlich sind, um eine VMware SDDC-Lösung (Software Defined Data Center) zu konzipieren, die den Workloads des Kunden möglichst optimal entspricht.

Zusammengefasst bieten die IBM Cloud for VMware-Angebote folgende Vorteile:

* Beschleunigte Lieferung von IT-Projekten für Entwickler und Geschäftsbereiche durch Verringerung des Zeitaufwands für Beschaffung, Architektur, Implementierung und Bereitstellung von Ressourcen von Wochen oder Monaten auf Stunden.
* Verbesserte Sicherheit mit dedizierten Bare Metal Servern in einer gehosteten privaten Cloud, einschließlich Bereitstellung über einen privaten Endpunkt an IBM Cloud-Services (wie z. B. IKS und KMIP).
* Konsistente Management- und Governance-Funktionalität der bereitgestellten Hybrid-Cloud durch Bereitstellung eines vollständigen Verwaltungszugriffs auf das Virtualisierungsmanagement, sodass vorhandene VMware-Tools, Scripts und Investitionen in Schulungen ihren Wert behalten.
* Globale Nutzung von VMware-Know-how mit IBM Professional Services und IBM Managed Services, die weltweit mehr als 30 IBM Cloud-Rechenzentren umfassen.

Kunden, die sich für Cloud-native Anwendungsplattformen wie ICP und IKS interessieren, legen besonderen Wert auf Geschwindigkeit und Innovation und berücksichtigen weniger die Aspekte der Sicherheit und des Netzbetriebs. Netz- oder Sicherheitsteams, die Services wie Lastverteilungsfunktionen, Firewalls, Switches und Router bereitstellen, tragen zur Verringerung der Wertschöpfungszeit der Anwendungen bei. Diese Referenzarchitektur zeigt, wie VCS, ICP und IKS das Unternehmen Acme Skateboards zuverlässig beim Prozess der Anwendungsmodernisierung unterstützen.

## Zugehörige Links

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
