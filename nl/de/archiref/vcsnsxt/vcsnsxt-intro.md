---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Einführung in den vCenter Server-Netzbetrieb

Dieses Dokument enthält eine Übersicht über den Prozess der Anwendungsmodernisierung auf {{site.data.keyword.cloud}}. Der Schwerpunkt liegt hier auf den Netzaspekten der folgenden Plattformen, damit eine integrierte Umgebung mit mehreren Clouds für die Anwendungsmodernisierung genutzt werden kann:

- **VMware vCenter Server on IBM Cloud** - Ein Angebot von {{site.data.keyword.vmwaresolutions_short}} und stellt eine VMware-basierte Plattform dar, die automatisch auf {{site.data.keyword.cloud_notm}} eingerichtet wird.
- **IBM Cloud Private** - Eine Anwendungsplattform für die Entwicklung und Verwaltung von containerisierten Anwendungen, die auf einer virtualisierten Infrastrukturplattform wie VCS oder in einer lokalen vSphere-Umgebung bereitgestellt werden.
- **IBM Kubernetes Services** - Ein verwalteter Service auf {{site.data.keyword.cloud_notm}}, der Kubernetes als Orchestrierungsengine für die Automatisierung der Bereitstellung, die Skalierung und den Betrieb von Anwendungscontainern in einem Cluster mit einem Tenant verwendet.

Die größten Herausforderungen ergeben sich bei der Anwendungsmodernisierung im Zusammenhang mit der Migration, dem Netzbetrieb und der Sicherheit. VCS, VMware Hybrid Cloud Extension (HCX), VMware NSX, IKS und ICP helfen dabei, einige dieser Herausforderungen zu bewältigen. Die folgende Netzarchitektur beschreibt am Beispiel von Acme Skateboards einen Ansatz, bei dem Komponenten miteinander verbunden sind, die auf Cloudumgebungen und lokale Umgebungen verteilt sind.

Der Abschnitt [Technologische
Neuentwicklung bei NSX-T](vcsnsxt-techpreview.html) enthält eine Technologievorschau, die die Verwendung von VMware NSX-T (NSX Transformers) in einer künftigen Referenzarchitektur beschreibt. NSX-T wurde für Anwendungsframeworks und Architekturen mit heterogenen Endpunkten und Technologiestacks entworfen. Neben vSphere können diese Umgebungen weitere Hypervisoren, KVM, Container und Bare-Metal-Instanzen enthalten. NSX-T ermöglicht IT- und Entwicklungsteams die Auswahl der für ihre Anwendungen am besten geeigneten Technologien. NSX-T kann neben Netzbetriebsteams auch von Entwicklungsorganisationen bei Verwaltung, Betrieb und Verarbeitung eingesetzt werden.

## Anwendungsmodernisierung auf IBM Cloud

Der Begriff "Anwendungsmodernisierung" bezeichnet den Prozess, mit dem vorhandene Anwendungen zur Nutzung neuer Entwicklungs- und Bereitstellungsstrategien in der Cloud geändert werden. Kunden suchen heute nach innovativen und effizienten Methoden, die ihnen helfen, diesen Übergang unter Berücksichtigung der Geschäfts- und Anwendungskomplexität zu ermöglichen.

Unternehmen müssen ihre Produkte heute immer schneller auf den Markt bringen. Ihr Kapital sind dabei nicht nur die Anwendungen, sondern Daten, Prozesse, Geschäftslogik und Benutzerschnittstellen, die sämtlich angepasst werden müssen, um mit neuen Geschäftsanforderungen Schritt zu halten.

Die Anwendungsmodernisierung bietet u. a. folgende Vorteile:

- Sie verbessert die Entwicklerproduktivität.
- Sie erhöht die Wirtschaftlichkeit.
- Sie reduziert die Kosten für die Erstellung neuer Funktionalität.
- Sie erweitert zeitnah die bereitgestellte Kapazität.

IBM geht davon aus, dass 70% der eingesetzten privaten Clouds durch die Notwendigkeit der Modernisierung von Anwendungsumgebungen motiviert sind. Die meisten Unternehmen verfolgen bei der Anwendungsmodernisierung jedoch einen stufenweisen Ansatz, was Hybridumgebungen und Umgebungen mit mehreren Clouds erforderlich macht. Die Szenarien zeichnen sich durch folgende Merkmale aus:

- Komplexe und monolithische traditionelle Anwendungen, die in der Regel auf Mainframes oder UNIX-Systemen ausgeführt werden, werden weiterhin lokal betrieben.
- x86-Umgebungen, die für Systems of Record (SoR) verwendet werden, oder Anwendungen, die sicherheitskritische oder regulierte Workloads beinhalten, werden in eine virtualisierte Infrastruktur oder in eine private Cloud verlegt.
- Anwendungen wie SAP oder High-Performance Computing nutzen Bare-Metal-Ressourcen.
- Sicherheitskritische und einige regulierte Workloads, die in die öffentliche Cloud verlegt werden können, werden in dedizierte Umgebungen verlagert.
- Systems of Engagement (SoE) wie z. B. Web, Mobile, IoT, AI oder Video werden in öffentliche Clouds verlagert.

Ein gängiges Vorgehen ist beispielsweise, die Front-End-SoE-Anwendungen als Container mit Datenbanken bereitzustellen und traditionelle Middleware auf VMs in einer private Cloud bereitzustellen.

Da Ihre IT-Infrastruktur und Ihre Geschäftsanforderungen individuell sind, benötigen Sie einen Modernisierungsansatz, der die Wertschöpfung für das Unternehmen beschleunigt, die Bereitstellungszeit verringert, Ihre Risiken mindert und Ihre bereits getätigten Investitionen schützt. IBM bietet für die Anwendungsmodernisierung genau diesen Ansatz, der angepasst werden kann, damit er Ihren individuellen geschäftlichen und technologischen Anforderungen entspricht.

Das vorliegende Dokument beschreibt die Technologien, die im Zuge der Anwendungsmodernisierung für {{site.data.keyword.cloud_notm}} zum Einsatz kommen, unter verschiedenen Gesichtspunkten:

* [vCenter Server und {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - Ein Leitfaden als Referenzarchitektur für die Bereitstellung der folgenden Plattformen:
   - **VMware vCenter Server on IBM Cloud** - Ein Angebot von {{site.data.keyword.vmwaresolutions_short}} und stellt eine VMware-basierte Plattform dar, die automatisch auf {{site.data.keyword.cloud_notm}} eingerichtet wird.
   - **IBM Cloud Private** - ICP ist eine Anwendungsplattform für die Entwicklung und Verwaltung von containerisierten Anwendungen. Dabei handelt es sich um eine integrierte Umgebung, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole, Überwachungsframeworks und eine grafische Benutzerschnittstelle enthält, von der aus Sie Ihre Anwendungen zentral bereitstellen, verwalten, überwachen und skalieren können.
   - **IBM Cloud Automation Manager** - CAM ist eine auf Unternehmen abgestimmte IaC-Plattform (IaC = Infrastructure as Code), die eine zentrale Bereitstellung von VMware-basierten Workloads neben Kubernetes-basierten Workloads bietet und bei der Sie einfach Vorlagen verwenden können, die in einem Repository gespeichert und versioniert werden.
* [vCenter Server und IBM Kubernetes Service](../vcsiks/vcsiks-intro.html) - Leitfaden in Form einer Referenzarchitektur für die Bereitstellung der folgenden Plattformen:
   - **VMware vCenter Server on IBM Cloud** - Ein Angebot von {{site.data.keyword.vmwaresolutions_short}} und stellt eine VMware-basierte Plattform dar, die automatisch auf {{site.data.keyword.cloud_notm}} eingerichtet wird.
   - **IBM Cloud Kubernetes Service** - Ein verwalteter Service auf {{site.data.keyword.cloud_notm}}, der Kubernetes als Orchestrierungsengine für die Automatisierung der Bereitstellung, die Skalierung und den Betrieb von Anwendungscontainern in einem Cluster mit einem Tenant verwendet.
* _vCenter Server-Netzbetrieb_ - Schwerpunkt des aktuellen Dokuments bilden die Netztechnologien, die für die Integration von VCS, ICP und IKS genutzt werden (z. B. NSX-V und Calico), sowie eine Technologievorschau für NSX-T.
* [VMware und Concept Car "Skate Advisor"](../vcscar/vcscar-intro.html) - Diese Referenzarchitektur ist ein so genanntes "Concept Car", also ein Mechanismus, der in einer Art Designstudie Technologien zur Lösung von realen Problemen herausstellt und demonstriert. Sie soll auf realistische Weise eine Interaktion zwischen Watson AI und maschinellem Lernen veranschaulichen. Vorrangig anhand der Skateboarding-Szene werden Cloud-Services auf verständliche Weise erläutert. Die Implementierung der Designstudie erweitert die Anwendung "Acme Skateboard" durch das Tool "Skate Advisor". Mit dem Tool "Skate Advisor" können sich Benutzer durch eine Watson-gesteuerte Engine über Skateboard-Tricks austauschen. 
* [VMware: Modernisierung der Anwendung "Stock Trader"](../vcscontent/vcscontent-modjourney.html) - Dieser Referenzanwendungsfall beschreibt die Modernisierung einer klassischen WebSphere Application Server-Anwendung mit {{site.data.keyword.cloud_notm}} Private, IBM Middleware-Inhalten, {{site.data.keyword.cloud_notm}} Kubernetes Service und vCenter Server on {{site.data.keyword.cloud_notm}}. Alle sind auf dem Weg zur Cloud, aber jeder befindet sich an einer anderen Etappe dieser Strecke. Schritt für Schritt wird die bestehende Anwendung "Stock Trader" von der Anwendungsarchitektin Jane und dem Cloudinfrastrukturarchitekten Todd modernisiert. Die Referenz zeigt anhand von Beispielen, wie Sie die einzelnen Schritte im Prozess ausführen und welchen Wert jeder Schritt ungeachtet seiner Größe für Ihr Unternehmen hat. Der Fokus liegt auf vier Themen: Anwendungen, DevOps, Integration und Management. Diese Bereiche sind bei der Umsetzung Ihrer Ziele eng verzahnt und die Modernisierung lediglich eines einzigen Bereiches führt faktisch zu Problemen in allen Bereichen.

### Zugehörige Links

* [Übersicht über VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
