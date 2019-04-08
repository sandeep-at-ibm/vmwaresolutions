---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# Hybrid-Services installieren und konfigurieren
{: #hcx-archi-install-cfg-hybrid}

Das Installationsprogramm stellt für jede virtuelle Service-Appliance eine virtuelle Maschine bereit und konfiguriert diese. Die virtuellen Servicemaschinen werden sowohl lokal als auch in der Cloud bereitgestellt.

## Voraussetzungen
{: #hcx-archi-install-cfg-hybrid-prereq}

* Der HCX-Manager muss lokal installiert und bei einem für VCF/VCS HCX aktivierten Cloud-Endpunkt registriert werden.
* Das virtuelle Zieldatenzentrum muss über genügend Ressourcen verfügen.

## Konfigurationsübersicht
{: #hcx-archi-install-cfg-hybrid-config-ovw}

Für den Konfigurationsvorgang wird davon ausgegangen, dass alle virtuellen Service-Appliances konfiguriert werden. Es sind jedoch nicht alle erforderlich.
* Das Hybrid-Cloud-Gateway ist erforderlich.
* Die Installation des WAN-Optimierungsprogramms erfolgt durch das Prüfen des Feldes für den WAN-Optimierungsservice während der Installation. Es ist keine weitere Konfiguration erforderlich.
* Informationen zum Konfigurieren des Netzerweiterungsservice finden Sie im Abschnitt _Network Extension Service konfigurieren_. Die Implementierung der optionalen Appliance kann verzögert werden, indem Sie zur Seite "Hybrid-Services" zurückkehren und die Appliance später installieren.

## Installation und Konfiguration der virtuellen Hybrid-Services-Appliance starten
{: #hcx-archi-install-cfg-hybrid-start-hsva}

Die einfache Webschnittstelle wird zum Installieren der virtuellen Service-Appliance und zum Konfigurieren weiterer Layer-2-Konzentratoren verwendet.

Der HCX-Manager muss installiert und bei dem für VCF/VCS HCX aktivierten Cloud-Endpunkt registriert sein.

### Vorgehensweise zur Installation und Konfiguration der virtuellen Hybrid-Services-Appliance
{: #hcx-archi-install-cfg-hybrid-proc-install}

1. Melden Sie sich bei vSphere Web Client an.
2. Klicken Sie auf der Registerkarte **Home** auf das Symbol **Hybrid-Cloud-Services**.
3. Klicken Sie auf die Registerkarte **Hybrid-Services**.
4. Klicken Sie auf **Service installieren**.
5. Wählen Sie auf der Seite **Hybrid-Services wählen** die zu installierenden Services aus und klicken Sie auf **Weiter**.

### Nächste Schritte
{: #hcx-archi-install-cfg-hybrid-start-hsva-next}

1. Der nächste Schritt besteht in der Konfiguration des Hybrid-Cloud-Gateways, falls erforderlich.
2. Zu einer vorhandenen Installation kann jederzeit ein Layer-2-Konzentrator hinzugefügt werden, sofern genügend Ressourcen zur Unterstützung der Erweiterung verfügbar sind.

## Hybrid-Cloud-Gateway konfigurieren
{: #hcx-archi-install-cfg-hybrid-config-hcg}

Konfigurieren Sie die virtuelle Hybrid-Cloud-Gateway-Service-Appliance. Bevor Sie beginnen, befolgen Sie die Schritte im Abschnitt _Installation und Konfiguration der virtuellen Hybrid-Services-Appliance starten_ und überprüfen Sie das Hybrid-Cloud-Gateway.

### Vorgehensweise zur Konfiguration des Hybrid-Cloud-Gateways
{: #hcx-archi-install-cfg-hybrid-proc-config-hcg}

Geben Sie auf der Seite **Hybrid-Cloud-Gateway** die folgenden Werte an und klicken Sie auf **Weiter**:
* **Netz** - Der Switch, der die Verbindung zur Managementschnittstelle des Hybrid-Cloud-Gateways herstellt. In den Anwendungsfällen 1 und 2 kann es sich um einen standardmäßigen virtuellen Switch oder um einen virtuellen verteilten Switch handeln. Für jede Konfiguration, die die Layer-2-Erweiterung verwendet, muss es sich um einen virtuellen verteilten Switch handeln.
* **Cluster/Host** - Wählen Sie den Cluster oder Host aus, in dem das Cloud-Gateway bereitgestellt werden soll.
* **Datenspeicher** - Wählen Sie den Datenspeicher aus, in dem das Cloud-Gateway bereitgestellt werden soll.
* **VM/Hostname** - Dieser Wert ist optional.
* Geben Sie die IP-Adresse/CIDR, das Standardgateway und den DNS-Server an, die für die Managementschnittstelle des Cloud-Gateways verwendet werden sollen.
* Wenn Sie mehrere Adressen für den DNS-Server eingeben, trennen Sie sie durch Kommas.
* Unter **Erweitert (optional)** wählen Sie gegebenenfalls das vMotion-Netz und legen die Kennwörter für **admin** und **root** fest. Diese Kennwörter sind speziell für die Appliance "Hybrid-Cloud-Gateway" vorgesehen. Der Benutzername und das Kennwort müssen nicht mit denen für die Hybrid-Cloud-Services-Appliance konfigurierten übereinstimmen.

## Network Extension Service konfigurieren
{: #hcx-archi-install-cfg-hybrid-config-nes}

Konfigurieren Sie einen Network Extension Service entweder für die Einzelpfadbereitstellung oder für eine eigenständige Netzerweiterung in einem alternativen Pfad. Bevor Sie beginnen, wählen Sie den Network Extension Service aus. Wenn die Einzelpfadkonfiguration installiert ist, ist **Network Extension** die einzig verfügbare Auswahl.

### Vorgehensweise zur Konfiguration des Network Extension Service
{: #hcx-archi-install-cfg-hybrid-proc-config-nes}

1. Wählen Sie auf der Seite **Network Extension Service** einen virtuellen verteilten Switch aus dem Menü **Verteilter Switch** aus. Wenn Sie einen Standard-Layer-2-Konzentrator installieren, ist das Kontrollkästchen **Erweiterte Netze über das Hybrid-Cloud-Gateway weiterleiten** verfügbar. Für den Layer-2-Konzentrator mit hohem Durchsatz (High Throughput L2C) ist es nicht verfügbar.
2. Wenn **Erweiterte Netze über das Hybrid-Cloud-Gateway weiterleiten** ausgewählt ist, bestimmt das Installationsprogramm für den Layer-2-Konzentrator (auf Grundlage des Switch) eine sinnvolle Platzierung und befüllt die entsprechenden Angaben. Andernfalls müssen die Platzierungsinformationen im nächsten Schritt manuell eingegeben werden.
3. Legen Sie die Route für die Platzierung des L2-Konzentrators fest. Wenn **Erweiterte Netze über das Hybrid-Cloud-Gateway weiterleiten** ausgewählt wurde, können diese Werte nicht bearbeitet werden.
  * **Netz** - Das Bereitstellungsnetz für die Managementschnittstelle des Layer-2-Konzentrators.
  * **Berechnung** - Der Bereitstellungscluster oder -host für den Layer-2-Konzentrator.
  * **Datenspeicher** - Der Bereitstellungsdatenspeicher für den Layer-2-Konzentrator.
  * **VM/Hostname** - Dieser Wert ist optional.
4. Geben Sie die Netzparameter für den lokalen Layer-2-Konzentrator an.
  * Wenn diese Option inaktiviert ist, verwenden Sie die Standardparameter, die vom Installationsprogramm angegeben werden.
  * Wenn die auf der Seite "Hybrid-Cloud-Gateway" im Menü **Netz** gewählte Portgruppe nicht Teil des verteilten Switch ist, aktivieren Sie das Kontrollkästchen **Netzparameter für den lokalen Layer-2-Konzentrator angeben** und bearbeiten Sie die Textfelder für **Erweiterte Konfigurationen**.
5. (Optional) **Erweiterte Konfigurationen** - Legen Sie das **admin**- und das **root**-Kennwort für diesen einen Layer-2-Konzentrator fest.
6. Klicken Sie auf **Weiter**. Auf der Seite **Bereit zum Abschließen** prüfen Sie die Angaben und klicken Sie auf **Fertigstellen**.

## Bereitstellung der Service-Appliance überwachen
{: #hcx-archi-install-cfg-hybrid-monitor}

Über die Taskkonsole kann der Fortschritt der Bereitstellung einer virtuellen Servicemaschine überwacht werden.

### Vorgehensweise zur Überwachung der Bereitstellung einer Service-Appliance
{: #hcx-archi-install-cfg-hybrid-monitor-proc}

1. Melden Sie sich bei vSphere Web Client an. Klicken Sie auf der Registerkarte **Home** auf das Symbol **Hybrid-Cloud-Services**.
2. Klicken Sie im Teilfenster **Hybrid-Cloud-Services** auf die Registerkarte **Hybrid-Services**. Die Bereitstellung der virtuellen Appliance kann über die Taskkonsole überwacht werden.
3. Rufen Sie das Teilfenster **Letzte Tasks** auf und zeigen Sie **Tasks aller Benutzer** an.
4. Klicken Sie auf **Weitere Tasks**, um die Taskkonsole zu öffnen.
5. In der Taskkonsole beobachten Sie die Bereitstellungstasks.
6. Wenn alle Tasks abgeschlossen sind, rufen Sie die Bestandsliste auf und klicken Sie auf **Hybrid-Cloud-Services**.
7. Im mittleren Teilfenster klicken Sie auf die Registerkarte **Hybrid-Services**.
8. Überprüfen Sie die Konfigurationszusammenfassung für die virtuellen Hybrid-Services-Appliances.

## Tunnelstatus anzeigen
{: #hcx-archi-install-cfg-hybrid-view-tunnel}

Zeigen Sie den Status des Cloud-Gateway-Tunnels an. Der Network Extension Service muss aktiv sein, damit Sie ein Netz erweitern können.

### Vorgehensweise zur Anzeige des Tunnelstatus
{: #hcx-archi-install-cfg-hybrid-proc-view-tunnel}

1. Zum Überprüfen des Tunnelstatus über den Web-Client wählen Sie im Bestand die Option **Hybrid-Cloud-Services** aus und klicken Sie auf die Registerkarte **Hybrid-Services**.
2. Um die erfolgreiche Erstellung eines Hybrid-Cloud-Gateway-Tunnels zu bestätigen, wird der Status des CGW (Akronym für das Hybrid-Cloud-Gateway) als **Aktiv** angezeigt. Ganz rechts ist der Tunnel grün dargestellt.

## Layer-2-Netz hin zu IBM Cloud erweitern

Sie können ein Layer-2-Netz vom lokalen Rechenzentrum aus in eine VCF/VCS HCX-fähige Cloud hinein erweitern.
{: #hcx-archi-install-cfg-hybrid-stretch-layer-2}

### Voraussetzungen für die Erweiterung eines Layer-2-Netzes hin zu IBM Cloud
{: #hcx-archi-install-cfg-hybrid-prereq-stretch-layer-2}

* Nur mit VLAN-Tagging versehene Portgruppen (also nicht VLAN-Typ "None" oder VLAN-ID = 0) können erweitert werden. VXLANs werden als VLANs betrachtet.
* Bei dieser Vorgehensweise wird der Assistent **Netz erweitern** verwendet. Dieser Assistent muss über die Netz-Bestandsansicht in vSphere® Web Client ausgeführt werden. Wenngleich der Assistent auch in anderen Ansichten angezeigt wird, muss er aus dem Bestandskontext heraus ausgeführt werden, damit die richtigen Informationen angezeigt werden.

### Vorgehensweise zum Vergrößern eines Layer-2-Netzes hin zu IBM Cloud
{: #hcx-archi-install-cfg-hybrid-proc-stretch-layer-2}

1. Melden Sie sich bei vSphere Web Client an. Klicken Sie im mittleren Teilfenster **Home** in der Liste **Bestand** auf das Symbol **Vernetzung**.
2. Suchen Sie in der Hierarchie **Vernetzung** die Portgruppe für das zu erweiternde Netz.
3. Klicken Sie mit der rechten Maustaste auf die Portgruppe, wählen Sie aus dem Menü **Hybriditäts-Aktionen** und dann **Netz erweitern**.
4. Bestätigen Sie auf der Seite **Quellenportgruppen auswählen** die Angaben zur Portgruppe und geben Sie die **IP-Adresse des Gateways** und das Präfix für das Netz ein. Klicken Sie auf **Weiter**.
5. Führen Sie auf der Seite **Zielgateway auswählen** die folgenden Schritte durch:
  1. Wählen Sie im Menü **Organisation** die Option "VCF/VCS Hybrid-Cloud-Services Cloud Organization".
  2. Wählen Sie das virtuelle VCF/VCS Hybrid-Cloud-Services Cloud-Rechenzentrum aus dem Menü.
  3. Belassen Sie **Proximity Routing** inaktiviert, um zu erzwingen, dass eine VM innerhalb einer für VCF/VCS Hybrid-Cloud-Services aktivierten Cloud für den Zugang zum Internet stets das lokale Gateway nutzt. Standardmäßig traversiert Datenverkehr, der von einer VM in einer für VCF/VCS Hybrid-Cloud-Services aktivierten Cloud stammt, durch den Layer-2-Datenpfad zurück in das lokale Rechenzentrum und in das Standardgateway. Wenn **Proximity Routing** aktiviert ist, kann eine VM innerhalb einer für Hybrid-Cloud-Services aktivierten VCF/VCS-Cloud ohne Traversieren des Layer-2-Datenpfads zu vSphere auf das Internet zugreifen.
  4. Wählen Sie das ferne Zielgateway aus der Liste der Gateways aus, indem Sie auf die entsprechende Zeile klicken. Klicken Sie auf **Weiter**.
6. Überprüfen Sie auf der Seite **Bereit zum Abschließen** alle angegeben Werte. Klicken Sie auf **Fertigstellen**.
7. Um den Fortschritt der Netzerweiterung zu verfolgen, gehen Sie zum Fenster **Letzte Tasks**, klicken auf die Registerkarte **Alle** und zeigen Sie die Ansicht **Tasks aller Benutzer** an.
8. Zum Öffnen der Taskkonsole klicken Sie auf **Weitere Tasks**. Die Netzerweiterung ist abgeschlossen, wenn der Taskstatus **Netz erweitern** mit **Abgeschlossen** angezeigt wird.

## Zugehörige Links
{: #hcx-archi-install-cfg-hybrid-related}

* [HCX ändern oder deinstallieren](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
