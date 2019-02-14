---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Einführung in VMware und Concept Car "Skate Advisor"

Die hier vorgestellte Referenzarchitektur ist ein so genanntes "Concept Car", also ein Mechanismus, mit dem in einer Art Designstudie Technologien zur Lösung von realen Problemen herausgestellt und demonstriert werden. Ein Concept Car stellt in keinerlei Hinsicht einen heute einsatzbereiten und verfügbaren Service dar.

Die Referenzarchitektur stellt außerdem die folgenden Informationen bereit:

-   Allgemeine Sprache für die unterschiedlichen Beteiligten
-   Konsistente Implementierung der Technologie zur Problemlösung
-   Unterstützte Validierung von Lösungen anhand einer bewährten Referenzarchitektur
-   Förderung der Einhaltung von allgemeinen Standards, Spezifikationen und Mustern

## Informationen zu Acme Skate Advisor

Es soll auf realistische Weise eine Interaktion zwischen der künstlichen Intelligenz von Watson und maschinellem Lernen veranschaulicht und dabei auch die Skateboarding-Szene eingehender erkundet werden. Die verfügbaren Services und die Cloudinfrastruktur werden durch die Demonstration der technischen Möglichkeiten und Weiterentwicklungen in diesem Bereich auf verständliche Weise erläutert. Die Implementierung der Designstudie erweitert die Demoanwendung "Acme Skateboard" durch das Tool "Skate Advisor". Mit dem Tool "Skate Advisor" können sich Benutzer durch eine Watson-gesteuerte Engine über Skateboard-Tricks austauschen. Bei den folgenden Zitaten handelt es sich um einen Beispieldialog:

-   Watson, zeig mir Kombinationen des Tricks "Casper"
-   Watson, zeig mir öffentliche Spots, an denen man Tricks ausführen kann
-   Watson, zeig mir ein Video des Tricks "Casper"

Acme Skate Advisor nutzt den Watson Discovery-Service zum Aufnehmen von Artikeln, Videos, Blogs und anderem Internetbasierten Inhalt für die Erstellung einer Lerndatenbank mit Tricks, die von der Anwendung abgefragt werden kann.

Die Anwendung "Skate Advisor" wird ebenfalls auf der Anwendungsmodernisierungsplattform implementiert, die containerbasierte Services über {{site.data.keyword.icpfull_notm}} bereitstellt, das auf einer {{site.data.keyword.cloud_notm}} for VMware Services-Plattform gehostet wird.

Acme Skate Advisor nutzt sowohl die Watson-Plattform als auch die Anwendungsmodernisierungsplattform.

## Anwendungsfälle

### Demonstration der Anwendungsmodernisierung

Nachfolgend wird eine Anwendung demonstriert, die für die Anwendungsmodernisierungsplattform bereitgestellt wurde. Die Plattform umfasst {{site.data.keyword.icpfull_notm}}-, CAM- und NSX-Komponenten, für deren Bereitstellung als Basis das Produktangebot "{{site.data.keyword.cloud_notm}} for the VMware vCenter Server on {{site.data.keyword.cloud_notm}}" verwendet wird.

### Watson-Spracherkennung mit Watson Assistant

Acme Skate Advisor kommuniziert mit einem von der Watson-Plattform bereitgestellten Service, der Sprache in Text und Text in Sprache umsetzt.

### Verwendung und Training von Watson Discovery-Services

Acme Skate Advisor überwacht mittels Watson Discovery-Services eine Datenbank von Tricks, auf die eine Klassifizierungssprache angewendet wird und für die Tricks in Online-Services erkannt werden.

### Verwendung von Watson-Services

Acme Skate Advisor wurde unter Verwendung der folgenden Watson-Services erstellt:
-   Watson Text to Speech
-   Watson Speech to Text
-   Watson Advisor
-   Watson Discovery-Service
-   Watson Knowledge Studio

## Anwendungsmodernisierung auf IBM Cloud

Der Begriff "Anwendungsmodernisierung" bezeichnet den Prozess, mit dem vorhandene Anwendungen zur Nutzung neuer Entwicklungs- und Bereitstellungsstrategien in der Cloud geändert werden. Kunden suchen heute nach innovativen und effizienten Methoden, die ihnen helfen, diesen Übergang unter Berücksichtigung der Geschäfts- und Anwendungskomplexität zu ermöglichen.

Unternehmen müssen ihre Produkte heute immer schneller auf den Markt bringen. Ihr Kapital sind dabei nicht nur die Anwendungen, sondern Daten, Prozesse, Geschäftslogik und Benutzerschnittstellen, die sämtlich angepasst werden müssen, um mit neuen Geschäftsanforderungen Schritt zu halten.

Die Anwendungsmodernisierung bietet folgende Vorteile:
- Sie verbessert die Entwicklerproduktivität.
- Sie erhöht die Wirtschaftlichkeit.
- Sie reduziert die Kosten für die Erstellung neuer Features.
- Sie erweitert zeitnah die bereitgestellte Kapazität.

IBM geht davon aus, dass 70 Prozent der eingesetzten privaten Clouds durch die Notwendigkeit der Modernisierung von Anwendungsumgebungen motiviert sind. Die meisten Unternehmen verfolgen bei der Anwendungsmodernisierung jedoch einen stufenweisen Ansatz, was Hybridumgebungen und Umgebungen mit mehreren Clouds erforderlich macht. Die Szenarien zeichnen sich durch folgende Merkmale aus:

- Komplexe und monolithische traditionelle Anwendungen, die in der Regel auf Mainframes oder UNIX-Systemen ausgeführt werden, werden weiterhin lokal betrieben.
- x86-Umgebungen, die für Systems of Record (SoR) verwendet werden, und Anwendungen, die sicherheitskritische und regulierte Workloads beinhalten, werden in eine virtualisierte Infrastruktur oder in eine private Cloud verlegt.
- Anwendungen wie SAP oder High-Performance Computing nutzen Bare-Metal-Ressourcen.
- Sicherheitskritische und einige regulierte Workloads, die in die öffentliche Cloud verlegt werden können, werden in dedizierte Umgebungen verlagert.
- Systems of Engagement (SoE) wie z. B. Web, Mobile, IoT, AI oder Video werden in öffentliche Clouds verlagert.

Ein gängiges Vorgehen ist beispielsweise, die Front-End-SoE-Anwendungen als Container mit Datenbanken bereitzustellen und traditionelle Middleware auf VMs in einer private Cloud bereitzustellen.

Da IT-Infrastruktur und Geschäftsanforderungen für jeden Einzelfall unterschiedlich sein können, muss ein Modernisierungsansatz die folgenden Prioritäten umsetzen:

* Schneller geschäftlicher Nutzen
* Minimale Bereitstellungszeit
* Geringe Risiken
* Erhaltung von bereits erfolgten Investitionen

IBM bietet für die Anwendungsmodernisierung genau diesen Ansatz, der angepasst werden kann, damit er Ihren individuellen geschäftlichen und technologischen Anforderungen entspricht.

Die folgenden Dokumente beschreiben die Technologien, die im Zuge der Anwendungsmodernisierung für {{site.data.keyword.cloud_notm}} zum Einsatz kommen, aus unterschiedlichen Perspektiven:

* [vCenter Server und {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp/vcsicp-intro.html) - Referenzarchitektur für die Bereitstellung der folgenden Plattformen.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server ist ein Angebot von {{site.data.keyword.vmwaresolutions_short}} und stellt eine VMware-basierte Plattform dar, die automatisch auf {{site.data.keyword.cloud_notm}} eingerichtet wird.
   - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} ist eine Anwendungsplattform zur Entwicklung und Verwaltung von containerisierten Anwendungen. Bei {{site.data.keyword.icpfull_notm}} handelt es sich um eine integrierte Umgebung, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole, Überwachungsframeworks und eine grafische Benutzerschnittstelle enthält. Von der Benutzerschnittstelle aus können Sie Ihre Anwendungen zentral bereitstellen, verwalten, überwachen und skalieren.
   - **IBM Cloud Automation Manager** - CAM ist eine auf Unternehmen abgestimmte IaC-Plattform (IaC = Infrastructure as Code), die eine zentrale Bereitstellung von VMware-basierten Workloads neben Kubernetes-basierten Workloads bietet und bei der Sie Vorlagen verwenden können, die in einem Repository gespeichert und versioniert werden.
* [vCenter Server und {{site.data.keyword.containerlong_notm}} Service](/docs/services/vmwaresolutions/archiref/vcsiks/vcsiks-intro.html) - Referenzarchitektur für die Bereitstellung der folgenden Plattformen.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server ist ein Angebot von {{site.data.keyword.vmwaresolutions_short}} und stellt eine VMware-basierte Plattform dar, die automatisch auf {{site.data.keyword.cloud_notm}} eingerichtet wird.
   - **{{site.data.keyword.containerlong_notm}}** – {{site.data.keyword.containerlong_notm}} ist ein verwalteter Service auf {{site.data.keyword.cloud_notm}} der Kubernetes als Orchestrierungsengine für die Automatisierung der Bereitstellung, die Skalierung und den Betrieb von Anwendungscontainern in einem Cluster mit einem Tenant verwendet.
* [vCenter Server networking](/docs/services/vmwaresolutions/archiref/vcsnsxt/vcsnsxt-intro.html) - Schwerpunkt bilden die Netztechnologien, die für die Integration von vCenter Server, {{site.data.keyword.icpfull_notm}} und {{site.data.keyword.containerlong_notm}} genutzt werden (z. B. NSX-V und Calico), sowie eine Technologievorschau für NSX-T.
* _VMware und Concept Car "Skate Advisor" - Leitfaden_ - Diese Referenzarchitektur ist ein so genanntes "Concept Car", also ein Mechanismus, der in einer Art Designstudie Technologien zur Lösung von realen Problemen herausstellt und demonstriert. Sie soll auf realistische Weise eine Interaktion zwischen der Watson AI und maschinellem Lernen veranschaulichen. Anhand der Skateboarding-Szene werden Cloud-Services auf verständliche Weise erläutert. Die Implementierung der Designstudie erweitert die Anwendung "Acme Skateboard" durch das Tool "Skate Advisor". Mit dem Tool "Skate Advisor" können sich Benutzer durch eine Watson-gesteuerte Engine über Skateboard-Tricks austauschen.
* [VMware: Modernisierung der Anwendung "Stock Trader"](/docs/services/vmwaresolutions/archiref/vcscontent/vcscontent-modjourney.html) - Dieser Referenzanwendungsfall beschreibt die Modernisierung einer klassischen WebSphere Application Server-Anwendung mit {{site.data.keyword.cloud_notm}} Private, IBM Middleware-INhalten, {{site.data.keyword.containerlong_notm}} und vCenter Server on {{site.data.keyword.cloud_notm}}. Alle sind auf dem Weg zur Cloud, aber jeder befindet sich an einer anderen Etappe dieser Strecke. Schritt für Schritt wird die bestehende Anwendung "Stock Trader" von der Anwendungsarchitektin Jane und dem Cloudinfrastrukturarchitekten Todd modernisiert. Die Referenz zeigt anhand von Beispielen, wie Sie die einzelnen Schritte im Prozess ausführen und welchen Wert jeder Schritt ungeachtet seiner Größe für Ihr Unternehmen hat. Der Fokus liegt auf vier Themen: Anwendungen, DevOps, Integration und Management. Alle Bereiche sind bei der Umsetzung Ihrer Ziele eng verzahnt. Einen Bereich ohne die anderen zu modernisieren, könnte zu Problemen führen.

### Zugehörige Links

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
