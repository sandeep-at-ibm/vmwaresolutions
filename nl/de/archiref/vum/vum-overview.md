---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Übersicht über VMware Update Manager
{: #vum-overview}

VMware Update Manager (VUM) verwendet einen mehrstufigen Prozess, um vSphere-Objekte zu aktualisieren und Patches oder Erweiterungen anzuwenden. Dieser Prozess ermöglicht eine reibungslose Aktualisierungsprozedur mit minimaler Systemausfallzeit. Zum Verständnis dieses Prozesses sind folgende Begriffe wichtig:
* **Bestandsobjekt** - Ein Objekt in vCenter, wie z. B. eine virtuelle Maschine, eine virtuelle Appliance oder ein vSphere ESXi-Host.
* **Baseline** - Baselines enthalten eine Sammlung von Patches, Erweiterungen, Service-Packs, Fehlerkorrekturen oder Upgrades und können als Patch-, Erweiterungs- oder Upgrade-Baselines klassifiziert werden. Es gibt zwei Klassifizierungen von Baselines: Host und VM/VM. Beide verfügen über von VMware vordefinierte Baselines und benutzerdefinierte Baselines können nach Bedarf hinzugefügt werden:
  - Vordefinierte Host-Baselines:
    - Kritische Host-Patches
    - Nicht kritische Host-Patches

  - Vordefinierte VM/VA-Baseline:
    - VA-Upgrade auf neueste Version
    - VM-Hardware-Upgrade übereinstimmend mit Host
    - VMware Tools-Upgrade übereinstimmend mit Host

* **Baselinegruppe** - Eine Gruppe von nicht in Konflikt stehenden Baselines, die verschiedene Typen von Baselines kombiniert und ein Bestandsobjekt für sie alle zusammen prüft und korrigiert. Wenn eine Baselinegruppe sowohl Upgrade- als auch Patch- oder Erweiterungsbaselines enthält, wird das Upgrade zuerst ausgeführt.
* **Prüfung** - Der Prüfvorgang (Scanning) ist der Prozess, bei dem das Bestandsobjekt oder die Bestandsobjekte anhand der Baseline oder Baselinegruppe ausgewertet wird/werden.
* **Staging** - Staging stellt sicher, dass die Patches und Erweiterungen vor der Korrektur auf die vSphere ESXi-Hosts heruntergeladen werden. Dies ist ein optionaler Schritt, um die Zeit zu minimieren, in der sich die Hosts im Wartungsmodus befinden.
* **Korrektur** - Die Korrektur (Remediation) ist der Prozess, in dem VUM Patches, Erweiterungen und Upgrades auf das Bestandsobjekt oder die Bestandsobjekte anwendet.

Daher läuft der VUM-Prozess wie folgt ab:
* Ein Bestandsobjekt oder eine Gruppe von Objekten wird auf Konformität mit einer Baseline oder einer Baselinegruppe geprüft.
* Nach einer Überprüfung können Patches und Erweiterungen optional zwischengespeichert werden, bevor eine Korrektur durchgeführt wird.

Das Herunterladen von Upgrades, Host-Patches, Erweiterungen und zugehörigen Metadaten ist ein vordefinierter automatischer Prozess, der geändert werden kann. Standardmäßig nimmt VUM in regelmäßigen konfigurierbaren Intervallen Kontakt zu VMware oder Drittanbieterquellen auf, um folgende Metadaten zu verfügbaren Upgrades, Patches oder Erweiterungen zu erfassen:

* Metadaten über alle ESXi 5.5- und ESXi 6.x-Patches unabhängig davon, ob es Hosts dieser Versionen in Ihrer Umgebung gibt.
* Metadaten zu ESXi 5.5- und ESXi 6.x-Patches und zu Erweiterungen von URL-Adressen von Drittanbietern.
* Benachrichtigungen, Alerts und Patchrückrufe für ESXi 5.5- und ESXi 6.x-Hosts.
* Metadaten zu Upgrades für virtuelle Appliances.

VUM unterstützt den Rückruf von Patches für Hosts, auf denen ESXi 5.0 oder höher ausgeführt wird. Ein Patch wird zurückgerufen, wenn bei dem freigegebenen Patch Probleme oder potenzielle Probleme auftreten. Nachdem Sie die Hosts in Ihrer VMware vCenter Server on {{site.data.keyword.cloud}}-Instanz geprüft haben, werden Sie von VUM benachrichtigt, wenn das zurückgerufene Patch auf einem bestimmten Host installiert wird. Zurückgerufene Patches können nicht mit VUM auf Hosts installiert werden. VUM löscht außerdem alle zurückgerufenen Patches aus dem Patch-Repository. Nachdem ein Patch zur Behebung des Problems freigegeben wurde, lädt VUM das neue Patch in sein Patch-Repository herunter. Wenn Sie das problematische Patch bereits installiert haben, benachrichtigt VUM Sie darüber, dass ein Fix freigegeben wurde, und fordert Sie auf, das neue Patch anzuwenden.

Die VUM-Clientschnittstelle bietet zwei Hauptansichten:
*	Administrationsansicht
*	Konformitätsansicht

##	Administrationsansicht
{: #vum-overview-admin-view}

Sie rufen die Administrationsansicht auf, indem Sie zu **Home** > **Update Manager** navigieren und die IP-Adresse der Update Manager-Instanz auswählen. In der Administrationsansicht können Sie die folgenden Tasks ausführen:
*	Einstellungen für Update Manager konfigurieren
*	Baselines und Baselinegruppen erstellen und verwalten
*	Update Manager-Ereignisse anzeigen
*	Patch-Repository und verfügbare Upgrades für virtuelle Appliance ansehen
*	Benachrichtigungen ansehen und überprüfen
*	ESXi-Images importieren

##	Konformitätsansicht
{: #vum-overview-compliance-view}

Sie rufen die Konformitätsansicht eines ausgewählten Bestandsobjekts auf, indem Sie zu **Hosts und Cluster** oder **VMs und Vorlagen** navigieren und auf die Registerkarte **Update Manager** klicken. In der Konformitätsansicht können Sie die folgenden Tasks ausführen:
*	Konformitäts- und Prüfergebnisse für jedes ausgewählte Bestandsobjekt anzeigen
*	Baselines und Baselinegruppen aus einem ausgewählten Bestandsobjekt anhängen und abhängen
*	Ausgewähltes Bestandsobjekt prüfen
*	Patches oder Erweiterungen auf Hosts zwischenspeichern
*	Ausgewähltes Bestandsobjekt korrigieren

## Zugehörige Links
{: #vum-overview-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demonstrationen)
