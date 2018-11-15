---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

# Einführung in vCenter Server und IBM Cloud Private

Dieses Dokument enthält eine Übersicht über den Prozess der Anwendungsmodernisierung auf IBM Cloud. Dabei liegt der Fokus auf den Cloud-Management-Komponenten, damit eine integrierte Umgebung mit mehreren Clouds für die Anwendungsmodernisierung genutzt werden kann:

- **VMware vCenter Server on IBM Cloud** - VCS ist ein Angebot von IBM Cloud for VMware Solutions und stellt eine VMware-basierte Plattform dar, die automatisch auf IBM Cloud eingerichtet wird.

- **IBM Cloud Private** - ICP ist eine Anwendungsplattform für die Entwicklung und Verwaltung von containerisierten Anwendungen, die so konzipiert sind, dass sie auf virtualisierten Infrastrukturplattformen, wie z. B. VMware, bereitgestellt werden können.

- **IBM Kubernetes Services** - IKS ist ein verwalteter Service auf IBM Cloud, der Kubernetes als Orchestrierungsengine für die Automatisierung der Bereitstellung, die Skalierung und den Betrieb von Anwendungscontainern in einem Cluster mit einem Tenant verwendet.

- **IBM Multi-Cluster Manager** – MCM bietet Benutzertransparenz, anwendungsorientiertes Management (Richtlinien, Bereitstellungen, Vitalität, Betrieb) und die richtlinienbasierte Konformität über Clouds und Cluster hinweg. Mit MCM erhalten Sie die Kontrolle über Ihre Kubernetes-Cluster.

- **IBM Cloud Automation Manager** – CAM ist eine Self-Service-Managementplattform für mehrere Clouds, die unter ICP ausgeführt wird und die Entwickler und Administratoren dabei unterstützt, die Anforderungen Ihres Unternehmens zu erfüllen.

## Anwendungsmodernisierung auf IBM Cloud
Anwendungsmodernisierung beschreibt den Prozess der Veränderung vorhandener Anwendungen zur Nutzung neuer Möglichkeiten in der Cloud. Kunden suchen heute nach innovativen, effizienten Ansätzen, die ihnen helfen, diesen Übergang anhängig von der Geschäfts- und Anwendungskomplexität zu ermöglichen.

Unternehmen müssen ihre Produkte heute immer schneller auf den Markt bringen. Ihr Kapital sind dabei nicht nur die Anwendungen, sondern Daten, Prozesse, Geschäftslogik und Benutzerschnittstellen, die alle angepasst werden müssen, um neue Geschäftsanforderungen zu erfüllen.

Die Anwendungsmodernisierung bietet u. a. folgende Vorteile:
- Verbesserte Entwicklerproduktivität
- Erhöhte betriebliche Effizienz
- Geringere Kosten für den Aufbau neuer Funktionalität
- Bereitstellung von mehr Kapazität in kurzer Zeit

IBM geht davon aus, dass 70% der eingesetzten Private Clouds durch die Notwendigkeit der Modernisierung von Anwendungsumgebungen motiviert sind. Die meisten Unternehmen verfolgen bei der Anwendungsmodernisierung jedoch einen stufenweisen Ansatz, was Hybridumgebungen und Umgebungen mit mehreren Clouds erforderlich macht. Die Szenarien zeichnen sich durch folgende Merkmale aus:
- Komplexe und monolithische traditionelle Anwendungen, die in der Regel auf Mainframes oder UNIX-Systemen ausgeführt werden, werden weiterhin lokal betrieben.
- x86-Umgebungen, die für Systems of Record (SoR) verwendet werden, oder Anwendungen, die sicherheitskritische oder regulierte Workloads beinhalten, werden in eine virtualisierte Infrastruktur oder in eine private Cloud verlegt.
- Anwendungen wie SAP oder High-Performance Computing nutzen Bare-Metal-Ressourcen.
- Sicherheitskritische und einige regulierte Workloads, die in die öffentliche Cloud verlegt werden können, werden in dedizierte Umgebungen verlagert.
- Systems des Engagements (SoE) wie z. B. Web, Mobile, IoT, AI oder Video werden in öffentliche Clouds verlagert.

Ein gängiges Vorgehen ist beispielsweise, die Front-End-SOE-Anwendungen als Container mit Datenbanken bereitzustellen und traditionelle Middleware auf VMs in einer private Cloud bereitzustellen.

Da Ihre IT-Infrastruktur und Ihre Geschäftsanforderungen individuell sind, benötigen Sie einen Modernisierungsansatz, der die Bereitstellung des geschäftlichen Nutzens beschleunigt, Ihre Risiken mindert und Ihre vorhandenen Investitionen schützt. IBM bietet genau diesen Ansatz, der angepasst werden kann, sodass er Ihren individuellen geschäftlichen und technologischen Anforderungen hinsichtlich der Anwendungsmodernisierung entspricht.

Dieses Dokument ist eine von fünf Veröffentlichungen, die die verschiedenen Technologien, die bei der Anwendungsmodernisierung hin zur IBM Cloud verwendet werden, aus verschiedenen Blickwinkeln beleuchten:

Leitfaden zur Referenzarchitektur, VCS – ICP und CAM - aktueller Abschnitt.

Eine Referenzarchitektur für die Bereitstellung der folgenden Plattformen:
  - **VMware vCenter Server on IBM Cloud** - ein Angebot von IBM Cloud for VMware Solutions, das eine VMware-basierte Plattform darstellt, die automatisch auf IBM Cloud eingerichtet wird.
  - **IBM Cloud Private** - eine Anwendungsplattform für die Entwicklung und Verwaltung von containerisierten Anwendungen. Dabei handelt es sich um eine integrierte Umgebung, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole, Überwachungsframeworks und eine grafische Benutzerschnittstelle enthält, von der aus Sie Ihre Anwendungen zentral bereitstellen, verwalten, überwachen und skalieren können.
  - **IBM Cloud Automation Manager** – eine auf Unternehmen abgestimmte IaC-Plattform (IaC = Infrastructure as Code), die eine zentrale Bereitstellung von VMware-basierten Workloads neben Kubernetes-basierten Workloads bietet und bei der Sie einfach Vorlagen verwenden können, die in einem Repository gespeichert und versioniert werden.

[Leitfaden zur Referenzarchitektur, VCS - IKS](../vcsiks/vcsiks-intro.html)

  Eine Referenzarchitektur für die Bereitstellung der folgenden Plattformen:
  - **VMware vCenter Server on IBM Cloud** - ein Angebot von IBM Cloud for VMware Solutions, das eine VMware-basierte Plattform darstellt, die automatisch auf IBM Cloud eingerichtet wird.
  - **IBM Cloud Kubernetes Service** – ein verwalteter Service auf IBM Cloud, der Kubernetes als Orchestrierungsengine für die Automatisierung der Bereitstellung, die Skalierung und den Betrieb von Anwendungscontainern in einem Cluster mit einem Tenant verwendet.

[Leitfaden zur Referenzarchitektur, VCS – Networking](../vcsnsxt/vcsnsxt-intro.html)

Das vorliegende Dokument konzentriert sich auf die Netztechnologien, die in VCS, ICP und IKS eingesetzt werden (z. B. NSX-V, NSX-T und Calico).

[Leitfaden zur Referenzarchitektur, Watson and Sk8boarding Concept Car](../vcscar/vcscar-intro.html)

Dieses Dokument verwendet einen “Concept Car”-Ansatz, um eine Interaktion zwischen Watson AI und maschinellem Lernen zu demonstrieren.

Das Dokument beschreibt besonders die folgenden Technologien:
  - **Pepper** - eine Schnittstelle, die die Möglichkeit zur Integration in die Cloud-Umgebung zur Ausführung von Anwendungs- und Suchoperationen enthält.
  - **VMware vCenter Server on IBM Cloud** - wird verwendet, um Elemente der Anwendung, wie z. B. die Datenbankworkloads, zu hosten.
  - **IBM Cloud Kubernetes Service** - wird verwendet, um die containerisierten Elemente der Anwendung zu verwalten.
  - **IBM Cloud Private** - wird genutzt, um die Plattform- und Service-Level-Orchestrierung zur Verfügung zu stellen, einschließlich der Möglichkeit, die Anwendung auf VM- und Containerplattformen zu hosten und zu skalieren. Diese Komponente ermöglicht auch die Aktivierung der Watson-Entwicklerservices für die Plattform, wodurch der Zugriff auf die KI-Funktionen möglich ist.

[Leitfaden zur Referenzarchitektur, VCS – Content](../vcscontent/vcscontent-intro.html)

Dieses Dokument konzentriert sich auf die folgenden Typen von Inhalten, die in IBM Cloud Automation Manager verfügbar sind:
- Interne Kataloginhalte, wie "vordefinierte" Helm-Diagramme, Terraform-Vorlagen und Chef-Rezepte
- Serviceinhalte, wie z. B. Blockchain- und Watson-Services

### Zugehörige Links

  * [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
