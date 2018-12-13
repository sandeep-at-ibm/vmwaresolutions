---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# vSAN-Cluster aktualisieren

vSAN generiert Systembaselines und Baselinegruppen für die Verwendung mit VUM; Sie können diese empfohlenen Referenzkonfigurationen verwenden, um Software, Patches und Erweiterungen für die vSphere ESXi-Hosts in Ihrer vCenter-Serverinstanz mit vSAN zu aktualisieren. vSAN 6.6.1 und höher generiert automatisierte Buildempfehlungen für vSAN-Cluster. vSAN kombiniert Informationen im VMware-Kompatibilitätshandbuch und im vSAN-Versionskatalog mit Informationen zu den installierten vSphere ESXi-Releases.

Diese empfohlenen Updates bieten das beste verfügbare Release, um Ihre Hardware in einem unterstützten Status zu halten.
* **vSAN-Systembaselines** - vSAN-Buildempfehlungen werden über vSAN-Systembaselines für VUM zur Verfügung gestellt. vSAN generiert eine Baselinegruppe für jeden vSAN-Cluster. vSAN-Systembaselines werden im Teilfenster "Baselines" der Registerkarte "Baselines und Gruppen" aufgelistet. VUM prüft automatisch jeden vSAN-Cluster, um die Konformität anhand der Baselinegruppe zu überprüfen. Um ein Upgrade Ihres Clusters durchzuführen, müssen Sie die Systembaseline manuell über den VUM korrigieren. Sie können die vSAN-Systembaseline auf einem einzelnen Host oder auf dem gesamten Cluster korrigieren.
* **vSAN-Versionskatalog** - Der vSAN-Versionskatalog verwaltet Informationen zu verfügbaren Releases, zur bevorzugten Reihenfolge der Releases und zu kritischen Patches, die für das jeweilige Release erforderlich sind. vSAN benötigt für den Zugriff auf den Versionskatalog eine Internetverbindung. Sie müssen nicht beim Customer Experience Improvement Program (CEIP) für vSAN registriert sein, um Zugriff auf den Versionskatalog zu erhalten.
* **Mit vSAN-Buildempfehlungen arbeiten** - VUM überprüft die installierten ESXi-Releases anhand der Informationen in der HCL (Hardware Compatibility List) im VMware-Kompatibilitätshandbuch. Er bestimmt den richtigen Upgradepfad für jeden vSAN-Cluster basierend auf dem aktuellen vSAN-Versionskatalog. vSAN enthält auch die erforderlichen Treiber und Patch-Updates für das empfohlene Release in der Systembaseline. vSAN-Buildempfehlungen stellen sicher, dass für jeden vSAN-Cluster der aktuelle Hardwarekompatibilitätsstatus erhalten bleibt oder verbessert wird. Wenn Hardware im vSAN-Cluster nicht in der HCL enthalten ist, empfiehlt vSAN ein Upgrade auf das neueste Release.

Die Tasks des vSAN-Cluster-Upgrades werden in der folgenden Reihenfolge ausgeführt:
* **Aktivierung des vSAN Online Health Workflow** - Dieser Workflow aktiviert die vSAN-Baselines in VUM, sodass Updates überprüft und korrigiert werden können. Er muss zunächst nur ausgeführt werden, um vSAN mit VUM zu aktivieren.
* **Voraussetzungen** - Ermitteln Sie die Voraussetzungen, den Prozess und eventuelle Einschränkungen.
* **Upgrade der vCenter Server Appliance**. Weitere Informationen finden Sie unter [VCSA-Update und über SSO angebundene vCenter](vum-updating-vcsa.html).
* **Upgrade der vSphere ESXi-Hosts** - Weitere Informationen finden Sie unter [Baselines erstellen und an Bestandsobjekte anhängen](vum-baselines.html).
* **Upgrade des vSAN-Plattenformats** - Weitere Informationen finden Sie unter "Upgrade des vSAN-Plattenformats durchführen". Das Upgrade des Plattenformats ist optional, aber für ein bestmögliches Ergebnis sollten Sie ein Upgrade der Objekte durchführen, um die neueste Version zu verwenden. Das On-Disk-Format macht Ihre Umgebung für das gesamte Feature-Set von vSAN verfügbar.

## vSAN Online Health Workflow aktivieren

Durch Ausführung der Tasks in diesem Abschnitt werden die vSAN-Baselines in VUM verfügbar gemacht. vSAN 6.6.1 und höher bietet einen nahtlosen automatisierten Aktualisierungsprozess, der sicherstellt, dass ein vSAN-Cluster stets über das beste erhältliche Release verfügt, damit sich die VMware vCenter Server on {{site.data.keyword.cloud}}-Instanz in einem unterstützten Status befindet:
* **vSAN-Versionsempfehlungen** - werden automatisch generiert, indem Informationen aus dem VMware-Kompatibilitätshandbuch, dem vSAN-Versionskatalog und Kenntnisse über die zugrunde liegende Hardwarekonfiguration verwendet werden. Dies umfasst auch die erforderlichen Treiber und Patch-Updates für das empfohlene Release in der Systembaseline.
* **vSAN-Buildempfehlungen** - stellen sicher, dass für die Cluster der aktuelle Hardwarekompatibilitätsstatus erhalten bleibt oder verbessert wird.

Stellen Sie sicher, dass die VCSA über vCenter 6.5 Patch 2 oder eine neuere Version verfügt, bevor Sie den Vorgang fortsetzen, da hierdurch bestimmte Probleme beim Proxy-Einsatz behoben werden. Weitere Informationen finden Sie unter [VCSA-Update und über SSO angebundene vCenter](vum-updating-vcsa.html).

Um die vSAN-Updates in VUM sehen zu können, muss der vSAN Online Health Workflow befolgt werden. Daher muss vSAN Online Health eine Verbindung zu den Sites `vcsa.vmware.com` und `vmware.com` herstellen, um diese Onlinestatusprüfungen durchführen zu können. Zum Aktivieren von vSAN Online Health Workflow sind folgende Aktivitäten erforderlich:
* VCSA für die Verwendung des Proxys konfigurieren
* vSAN für die Verwendung des Proxys konfigurieren
* Customer Experience Improvement Program (CEIP) aktivieren
* Test-Upload ausführen und prüfen, ob er erfolgreich war

Der erste Schritt besteht darin, Ihre my.vmware.com-Berechtigungsnachweise zur vSAN Build Recommendation Engine hinzuzufügen. Nach erfolgreicher Anmeldung generiert vSAN eine Baselinegruppe empfohlener Updates für jeden vSAN-Cluster. vSAN-Systembaselines werden im Teilfenster "Baselines" der Registerkarte "Baselines und Gruppen" aufgelistet.

### VCSA für die Verwendung des Proxys konfigurieren

1.	Stellen Sie von Ihrem Jump-Server-Web-Browser eine Verbindung zur VCSA-Managementschnittstelle `https://<vCenter ip>:5480` her.
2.	Melden Sie sich mit den Berechtigungsnachweisen von der IC4VS-Konsole bei der VCSA-Managementschnittstelle als Root an.
3.	Klicken Sie in der vCenter Server Appliance-Managementschnittstelle auf **Vernetzung** und dann auf **Verwalten**.
4.	Wenn Sie einen Proxy-Server konfigurieren möchten, klicken Sie im Teilfenster "Proxy-Einstellungen" auf **Bearbeiten**.
5.	Wählen Sie **Proxy-Server verwenden** aus, geben Sie die Einstellungen für den Proxy-Server ein und klicken Sie auf **OK**.

Es gibt Berichte, in denen angegeben wird, dass die Proxy-Informationen nur für HTTP und nicht für HTTPS definiert sind. Damit die Proxy-Informationen auch für den HTTPS-Datenverkehr konfiguriert werden können, muss zuerst eine entsprechende Aktivierung erfolgen. Nachdem Sie sich bei der VCSA über SSH angemeldet haben, verwenden Sie den Befehl proxy.get, um die Konfiguration anzuzeigen und sicherzustellen, dass die HTTPS-Parameter nicht definiert sind.

Wenn die HTTPS-Parameter nicht definiert sind, verwenden Sie den folgenden Befehl:
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### vSAN für die Verwendung des Proxys konfigurieren
1. Navigieren Sie zu **Home** > **Hosts und Cluster**, wählen Sie **vSAN-Cluster** im Navigationsfenster aus, wählen Sie dann die Registerkarte **Konfigurieren** aus und navigieren Sie zu **vSAN** und dann zu **Allgemein**. Blättern Sie zum Abschnitt **Internetkonnektivität** und klicken Sie auf **Bearbeiten**.
2. Geben Sie die IP-Adresse und die Portnummer des Proxys ein und klicken Sie auf **OK**.

### Customer Experience Improvement Program (CEIP) aktivieren

Dieser Schritt ist optional. Navigieren Sie mit dem vSphere-Web-Client zu **Home** > **Administration** > **Customer Experience Improvement Program** und klicken Sie dann auf **Teilnehmen**.

### Test-Upload ausführen und prüfen, ob er erfolgreich war
1. Bei Verwendung des vSphere Web Client wechseln Sie zu **Home** > **Hosts und Cluster**. Wählen Sie den erforderlichen Cluster aus und wählen Sie anschließend die Registerkarte **Überwachen** und die Seite **vSAN** aus. Klicken Sie anschließend auf **Status**. Klicken Sie auf **Onlinestatus aktivieren**.
2. Klicken Sie auf die Schaltfläche **Erneut testen** und warten Sie, bis der Prozess abgeschlossen ist.
3. Eine neue Option _"Onlinestatuskonnektivität"_ wird im Status angezeigt und die Schaltfläche "Onlinestatus aktivieren" ändert sich in "Mit Onlinestatus erneut testen" erneut.
4. Klicken Sie auf die Schaltfläche **Mit Onlinestatus erneut testen**, um den ersten Upload auszulösen, und warten Sie, bis der Prozess abgeschlossen ist, indem Sie den Status im Teilfenster "Letzte Tasks" überprüfen. Der Testname sollte sich in "Onlinestatus" ändern (Letzte Prüfung: gerade eben) ändern.
5. Wenn der Prozess abgeschlossen ist, navigieren Sie zum Fenster "Status", erweitern Sie die vSAN-Buildempfehlung und klicken Sie auf **vSAN Build Recommendation Engine-Status**.
6. Klicken Sie auf **Anmeldung bei my.vmware.com** und geben Sie Ihre Berechtigungsnachweise ein. Wenn der Prozess abgeschlossen ist, ändert sich das **Testergebnis** in den Status **Bestanden**.
7. Klicken Sie auf die Registerkarte **Update Manager**. Sie sollten jetzt sehen, dass der vSAN-Cluster zu den Baselines hinzugefügt wurde.

## Voraussetzungen

Stellen Sie vor dem Starten des vSAN-Upgradeprozesses sicher, dass die folgenden Voraussetzungen erfüllt sind:
* Sie haben sich die Artikel in der VMware Knowledge Base angesehen und sich über alle bekannten Kompatibilitätsprobleme zwischen Ihrer aktuellen vSAN-Version und der gewünschten vSAN-Zielversion informiert.
* **Die vSphere-Umgebung ist auf dem aktuellen Stand.**:
  - Die VCSA muss denselben oder einen höheren Patch-Level aufweisen als die vSphere ESXi-Hosts. Falls erforderlich, müssen Sie die VCSA aktualisieren.
  - Alle Hosts sollten mit demselben Build von ESXi ausgeführt werden. Wenn die vSphere-ESXi-Hostversionen nicht übereinstimmen, nehmen Sie eine Aktualisierung vor.
* **Alle vSAN-Platten sollten sich in einwandfreiem Zustand befinden**:
  - Es darf keine Platte ausfallen oder fehlen. Dieser Wert kann über die Ansicht **vSAN-Plattenmanagement** im vSphere Web Client bestimmt werden. Navigieren Sie zu **Home** > **Hosts und Cluster**, wählen Sie **vSAN-Cluster** aus, klicken Sie auf die Registerkarte **vSAN** und anschließend auf **Physische Platten**. Navigieren Sie durch alle Platten und überprüfen Sie den vSAN-Zustand.
  - Es sollten keine nicht zugänglichen vSAN-Objekte vorhanden sein. Sie können dies mit dem **vSAN Health Service** überprüfen, indem Sie auf **Home** > **Hosts und Cluster** klicken und dann den **vSAN-Cluster** auswählen. Klicken Sie auf die Registerkarte **Überwachen**, auf **vSAN** und anschließend auf **Status**. Überprüfen Sie die Testergebnisse.
  - Es darf keine aktive Resynchronisation am Anfang des Upgradeprozesses geben. Klicken Sie auf **Home** > **Hosts und Cluster**, wählen Sie dann den **vSAN-Cluster** aus und klicken Sie auf die Registerkarte **vSAN** und anschließend auf **Komponenten resynchronisieren**. _Die Anzahl der Resynchronisationskomponenten sollte 0 sein_. Dabei ist zu beachten, dass eine gewisse Resynchronisationsaktivität während des Upgradeprozesses erwartet wird, da die Daten nach Hostwarmstarts synchronisiert werden müssen.
* **vSphere ESXi-Hostvorbereitung** - Wenn Sie einen Host in einem vSAN-Cluster in den Wartungsmodus versetzen, stehen Ihnen drei Optionen zur Auswahl:
  - **Keine Datenmigration** - Wenn Sie diese Option auswählen, evakuiert vSAN keine Daten von diesem Host. Wenn Sie den Host ausschalten oder aus dem Cluster entfernen, sind danach manche virtuelle Maschinen (VMs) möglicherweise nicht mehr zugänglich.
  - **Verfügbarkeit sicherstellen** - Wenn Sie diese Option auswählen, können Sie mit vSAN den Host schneller in den Wartungsmodus versetzen als bei der vollständigen Datenmigration und den Zugriff auf die virtuellen Maschinen (VMs) in der Umgebung ermöglichen.
  - **Vollständige Datenmigration**
* **Wartungsmodus beenden und resynchronisieren** - Wenn der vSphere ESXi-Host aufgerüstet und aus dem Wartungsmodus versetzt wurde, erfolgt eine Resynchronisation. Sie können dies über den Web-Client sehen. Stellen Sie sicher, dass der Vorgang abgeschlossen ist, bevor Sie zum nächsten Host übergehen. Eine Resynchronisation wird ausgeführt, weil der aktualisierte Host nun wieder zu dem vSAN-Datenspeicher beitragen kann. Es ist wichtig zu warten, bis die Resynchronisation abgeschlossen ist, um sicherzustellen, dass es keinen Datenverlust gibt.
* **Gehen Sie nach dem Starten des vSAN-Cluster-Upgrades wie folgt vor**:
  - Versuchen Sie nicht, ein Upgrade eines Clusters durchzuführen, indem Sie neue Versionen für den Cluster einführen und Workloads migrieren.
  - Wenn Sie neue Hosts einführen, stellen Sie sicher, dass sie dieselbe Anfangsversion aufweisen, und führen Sie das Upgrade auch für den übrigen Cluster durch.
  - Wenn Sie bei einem Upgrade Platten hinzufügen oder ersetzen, stellen Sie sicher, dass sie mit der richtigen On-Disk-Formatversion formatiert sind (falls zutreffend).
  - Da bestimmte vSAN-Verhaltensänderungen durch das On-Disk-Format gesteuert werden, ist es wichtig, dass neuere On-Disk-Formatversionen nicht in einen Cluster mit unterschiedlichen Versionen eingeführt werden.

## Upgrade für vCenter Server Appliance durchführen

Weitere Informationen finden Sie unter [VCSA-Update und über SSO angebundene vCenter](vum-updating-vcsa.html).

##	Upgrade für vSphere ESXi-Hosts durchführen

Weitere Informationen finden Sie unter [Baselines erstellen und an Bestandsobjekte anhängen](vum-baselines.html).

##	Upgrade des vSAN-Plattenformats durchführen

Ruby vSphere Console (RVC) ist eine Ruby-basierte Befehlszeilenschnittstelle für vSphere und kann zur Verwaltung von VMware vSphere ESXi und vCenter verwendet werden. Der vSphere-Bestand wird in einer Baumstruktur dargestellt, die es Ihnen ermöglicht, zu navigieren und Befehle für vCenter-Objekte auszuführen.

Viele grundlegende Verwaltungstasks können so wesentlich effizienter ausgeführt werden, als wenn Sie sich durch den vSphere-Client klicken. RVC ist in der VCSA vollständig implementiert. Der Zugriff erfolgt über eine SSH-Verbindung auf die Appliance.
1. Greifen Sie über SSH auf die VCSA zu und melden Sie sich als Rootbenutzer mit dem Kennwort an, das auf der ICVS-Konsole bereitgestellt wird.
2. Geben Sie an der Eingabeaufforderung Folgendes ein:
  `rvc Administrator@vsphere.local@localhost`. Drücken Sie anschließend die **Eingabetaste**.
3. Geben Sie das Kennwort des Administrators ein, das auf der ICVS-Konsole bereitgestellt wird. Sie befinden sich nun im Stammverzeichnis des virtuellen Dateisystems. Geben Sie "ls" ein und drücken Sie dann die **Eingabetaste**. Sie sollten Folgendes sehen:
  `0 /
  1 localhost/``

5. Geben Sie `cd 1` ein und drücken Sie die Eingabetaste. Geben Sie anschließend `ls` ein und drücken Sie die **Eingabetaste**. Sie sollten Folgendes sehen:
  ` 0/datacenter1 (datacenter) `

6. Geben Sie `cd 0` ein und drücken Sie die Eingabetaste. Geben Sie anschließend `ls` ein und und drücken Sie die **Eingabetaste**. Sie sollten Folgendes sehen:

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. Geben Sie `cd 1` ein und drücken Sie die **Eingabetaste**. Geben Sie anschließend `ls` ein und drücken Sie die **Eingabetaste**. Daraufhin sollte Ihr Cluster angezeigt werden:
  `0 cluster1 (cluster)``

8. Es sollen jetzt die VSAN-Befehle für diesen Cluster verwendet werden. Um den Plattenstatus zu prüfen, geben Sie `vsan.disks_stats 0` ein und drücken Sie die **Eingabetaste**.

9. Stellen Sie sicher, dass der Zustand aller Platten "OK" ist. Starten Sie anschließend das Upgrade, indem Sie `vsan.ondisk_upgrade 0` eingeben und dann die **Eingabetaste** drücken.

10. Abhängig von der vSAN-Größe kann diese Task viel Zeit in Anspruch nehmen. Geben Sie nach Abschluss der Task `vsan.objstatusreport 0` ein und drücken Sie dann die **Eingabetaste**, um zu überprüfen, ob für die Objektversionen ein Upgrade auf das neue On-Disk-Format durchgeführt wird.

11. Das Upgrade des VSAN-Clusters ist nun abgeschlossen. Geben Sie `exit` ein und drücken Sie die **Eingabetaste**, um RVC zu verlassen.

### Zugehörige Links

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
