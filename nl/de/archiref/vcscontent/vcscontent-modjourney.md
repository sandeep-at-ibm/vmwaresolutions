---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Modernisierungsprozess
{: #vcscontent-modjourney}

Dies ist ein Referenzanwendungsfall für die Modernisierung einer klassischen WebSphere Application Server-Anwendung, bei der {{site.data.keyword.cloud}} Private, IBM Middleware-Inhalt, der {{site.data.keyword.containerlong_notm}} und VMware vCenter Server on {{site.data.keyword.cloud_notm}} zum Einsatz kommen.

## Modernisierung umfasst nicht nur Anwendungen
{: #vcscontent-modjourney-modernization}

Alle sind auf dem Weg zur Cloud, aber jeder befindet sich an einer anderen Etappe dieser Strecke. Schwerpunkt dieses Anwendungsfalls ist die von der Anwendungsarchitektin Jane und dem Cloudinfrastrukturarchitekten Todd geplante schrittweise Modernisierung einer vorhandenen Anwendung namens "Stock Trader". Dieser Anwendungsfall zeigt anhand von Beispielen, wie Sie die einzelnen Schritte im Prozess ausführen und welchen Wert jeder Schritt ungeachtet seiner Größe für Ihr Unternehmen hat.

Bei dem hier vorgestellten Prozess liegt der Schwerpunkt auf der Modernisierung der Anwendung "Stock Trader". Zur vollständigen Modernisierung eines Unternehmens in ein cloudnatives Unternehmen müssen aber auch Aspekte wie Anwendungen, DevOps, Integration und Management erörtert werden. Alle Bereiche sind bei der Umsetzung Ihrer Ziele eng verzahnt. Einen Bereich ohne die anderen zu modernisieren, könnte zu Problemen führen.

## Gründe für die Modernisierung
{: #vcscontent-modjourney-reasons}

### Anwendungsmodernisierung
{: #vcscontent-modjourney-app-mod}

Ziel sind cloudnative Anwendungen, die skalierbar sind und auf schnelle Bedarfsänderungen reagieren können.

* Sie müssen vorhandene Anwendungen modernisieren und neue cloudnative Anwendungen erstellen, um Faszination bei Ihren Kunden zu wecken.
* Sie benötigen Anwendungen, die skalierbar und weltweit einsetzbar sind, an den Bedarf angepasst werden und schnell geändert, erweitert und verlagert werden können.

### DevOps-Modernisierung
{: #vcscontent-modjourney-devops-mod}

Im Zuge der Anwendungsmodernisierung wird mit dem Verfahren, das Sie zur Bereitstellung der Anwendung nutzen, auch die gesamte Delivery Pipeline modernisiert, damit sich die von Ihren Anwendungsentwicklern aufgebaute cloudnative Kultur auch auf die Art der Anwendungsbereitstellung erstrecken kann.

* Sie müssen die Kultur für Entwicklung und Betrieb (DevOps) sowie auch der Sicherheit modernisieren, wenn Sie Ihre Anwendungen modernisieren.
* Sie benötigen DevOps-Teams, die skalierbar und weltweit einsetzbar sind, an den Bedarf angepasst werden und schnell geändert, erweitert und verlagert werden können.

###  Integrationsmodernisierung
{: #vcscontent-modjourney-integration-mod}

Im Zuge des Modernisierungsprozesses müssen Ihre Teams vorhandene Assets, neue Cloud-Services, Ihre Daten und neue Erkenntnisse aus Analysen integrieren, die für diese Daten ausgeführt wurden.

* Sie müssen Ihre vorhandenen Assets bei diesem Prozess in einer Weise einsetzen, die skalierbar und weltweit einsetzbar ist, an den Bedarf angepasst werden sowie schnell geändert, erweitert und verlagert werden kann.
* Sie müssen in jedem Schritt dieses Prozesses eine Anreicherung durch neue Cloud-Services vornehmen.
* Sie müssen Ihre Daten und die Erkenntnisse integrieren, die Sie durch die Anwendung von Analysen auf Ihre Daten gewinnen.

### Management
{: #vcscontent-modjourney-mgmt}

Die Modernisierung der Managementpraxis ist ein weiterer paralleler Prozess, den Sie beim Modernisieren Ihrer Anwendungen vollziehen müssen. Tools, Kultur und Kernverhalten bei der Verwaltung und Wartung einer modernisierten Anwendung unterscheiden sich stark vom bisher üblichen.

* Sie müssen Ihre Mikroservices und containerisierte Middleware unter Verwendung von integrierter Orchestrierung, Protokollierung und Überwachung verwalten.
* Sie müssen Ihre Multi-Cloud-Hybridplattformen an weltweit verteilten Standorten in einer Weise verwalten, die skalierbar und weltweit einsetzbar ist, an den Bedarf angepasst werden sowie schnell geändert, erweitert und verlagert werden kann.
* Sie müssen das Verfahren für das Management von mehreren Clouds und den in ihnen ausgeführten Anwendungen und Middlewarekomponenten automatisieren.

## Wir stellen vor: Todd und Jane
{: #vcscontent-modjourney-todd-jane}

Beim Prozess für Stock Trader gibt es zwei Hauptpersonen namens Todd und Jane. Todd ist Leiter der IT-Abteilung beim Unternehmen "Acme" und für die Infrastruktur, Sicherheit, Cloudumgebungen und Richtlinien verantwortlich, die sicherstellen, dass die ausgeführten Workloads verschiedenen Regelungen entsprechen.

Jane ist die Entwicklungsleiterin für die Lösung "Stock Trader" und nun für die Modernisierung von Stock Trader zuständig. Dies bedeutet, dass sie mit ihren Entwicklerteams gemeinsam an der Änderung der Entwicklungstools, Kultur und Plattformen arbeiten muss, damit die vorhandene monolithische Lösung "Stock Trader" zu einer gut funktionierenden cloudnativen Lösung modernisiert wird.

## Wir stellen vor: Stock Trader
{: #vcscontent-modjourney-meet-stock-trader}

Todd und Jane haben eine in WebSphere ausgeführte Anwendung namens "Stock Trader" erstellt. Mit einer Basisbenutzerschnittstelle ist sie eine zuverlässige Anwendung, in der Portfolio-Manager Portfolios verwalten können, wozu auch Aktienankäufe und -verkäufe sowie das Anzeigen von internen Kundentreuestufen gehören.

Stock Trader wird unter WebSphere ausgeführt, besteht aus einigen wenigen Dateien ".war" und verwendet eine konventionelle Db2-Datenbank, die in dem seit Jahren genutzten Rechenzentrum ausgeführt wird. Aufgrund der Abhängigkeiten zwischen Infrastrukturteams, Entwicklerteams und Datenteams dauert die Erweiterung dieser Anwendung sehr lange.

Nun ist Stock Trader zwar ein gutes Produkt, aber alle beteiligten Personen im Unternehmen wünschen sich eine bessere Lösung. Produktmanager möchten soziale Medien in ihr Kundentreueprogramm einbeziehen. Für Jane ist dies kein Problem, denn sie kann die Anwendung durch ein Refactoring in Mikroservices umwandeln, was eine kontinuierliche Bereitstellung von erweiterter Funktionalität mit weniger Abhängigkeiten ermöglicht. Todd ist vom Potenzial der Cloud angetan, benötigt jedoch weiterhin Steuerungsmöglichkeiten, damit die Einhaltung der Unternehmensrichtlinien gewährleistet wird.

## Schritte im Prozess
{: #vcscontent-modjourney-steps}

Todd und Jane wissen aus Erfahrung, dass ein guter Prozess für die Modernisierung von Lösungen mit einer Roadmap beginnt. Pläne können sich jederzeit ändern und es ist immer sinnvoll, die Wunschvorstellung zu durchdenken und einen realistischen Plan für ihre Umsetzung zu definieren. Jeder Schritt muss einen Wert für das Unternehmen mit sich bringen, zudem dürfen die Schritte nicht so bedeutend sein, dass sie kostenintensive Unterbrechungen für die Kunden zur Folge haben.

Für Todd und Jane ergeben sich im Prozess für Stock Trader die folgenden Schritte:
1. Die virtuellen Maschinen für Stock Trader müssen in die {{site.data.keyword.cloud_notm}} verlagert werden. Durch diesen Schritt kann Todd die erforderliche Verwaltung seiner eigenen Hardware und des VMware-Inhalts im lokalen Rechenzentrum reduzieren.

2. Stock Trader in WebSphere Application Server muss in Stock Trader in Containern umgewandelt werden. Dieser Schritt erhöht die Ausfallsicherheit, da die Ausführung von Containern in Kubernetes die Orchestrierung und weiteres Cloudverhalten mit sich bringt. Zu diesem Zweck muss Todd eine {{site.data.keyword.cloud_notm}} Private-Instanz in seiner VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Umgebung vorbereiten und anschließend zusammen mit Jane und Transformation Advisor die Anwendung "Stock Trader" containerisieren.

3. Es muss ein Refactoring ausgeführt und Middleware in {{site.data.keyword.cloud_notm}} Private hinzugefügt werden. Dieser Schritt versetzt die vorhandene Middleware in eine Cloudumgebung und optimiert das Cloudverhalten. Außerdem optimiert er die Lizenzierung und bereitet die Lösung für eine vollständige Portierbarkeit zur Verwendung in anderen Kubernetes-Umgebungen vor.

4. Es muss eine Anreicherung mit Watson und anderen öffentlichen Cloud-Services stattfinden. Dieser Schritt kann Stock Trader durch die Einbindung von AI-Services und die Fähigkeit zur Kommunikation mit Cloudrechenzentren auf der ganzen Welt in exponentiellem Maßstab aufwerten.

5. Es muss eine echte Hybridumgebung mit dem {{site.data.keyword.cloud_notm}} Kubernetes-Service entstehen. Dieser Schritt ermöglicht für Todd einen verwalteten Kubernetes-Service, der weiterhin mit derselben Cloudregion wie seine {{site.data.keyword.cloud_notm}} Private-Instanz verbunden ist. Außerdem können die Entwicklerteams von Jane hierdurch einen Entwicklungs- und Testcluster für Experimente nutzen, während sie gleichzeitig auf dieselbe Datenquelle wie ihr zentraler {{site.data.keyword.cloud_notm}} Private-Cluster zugreifen.

6. Es muss eine Modernisierung von DevOps stattfinden. Während dieses Prozesses verbessert Jane das Verfahren, mit dem sie Stock Trader bereitstellt.

7. Das Management muss modernisiert werden. Todd und Jane haben daran gearbeitet, die Verwaltung von Stock Trader und der zugrunde liegenden Plattform zu verbessern, sogar in mehreren Clustern und Cloudumgebungen.
