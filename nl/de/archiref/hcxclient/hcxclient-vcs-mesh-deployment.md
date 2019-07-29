---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Lokales HCX-Servicenetz
{: #hcxclient-vcs-mesh-deployment}

Im folgenden Abschnitt werden die Schritte zum Konfigurieren einer HCX-Clientinstanz ausführlich erläutert.
  1. Standortpaarung für IBM Cloud for VMware Solutions-Umgebung
  2. Erstellen von lokalen HCX-Netzprofilen
  3. Erstellen von lokalen HCX-Rechenprofilen
  4. Erstellen eines HCX-Servicenetzes
  5. Vergrößern der Netze

## Standortpaarung für IBM Cloud for VMware Solutions-Umgebung
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. Melden Sie sich an vSphere Web Client an. 
2. Wählen Sie im Menü **Home** die Option **HCX** aus.
3. Klicken Sie unter **Infrastructure** -> **InterConnect** auf **Add Site Pairing**.
   1. URL der Site: URL des HCX-Cloud-Managers
     * Beispiel: `https://x.x.x.x.x`
   2. Benutzername und Kennwort: Details des Administrators von HCX Manager
     * Admin / Kennwort
   3. Die obigen Details können über das IBM Cloud-Portal unter **Services**, HCX on IBM Cloud**, für die IBM Cloud for VMware Solutions-Instanz abgerufen werden.
4. Klicken Sie auf **Connect**.

### Ergebnisse
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

Die Standortpaarung wurde erfolgreich registriert und wird in der Benutzerschnittstelle angezeigt.

## Erstellen lokaler HCX-Profile
{: #hcxclient-vcs-mesh-deployment-profiles}

## Netzprofile für das lokale Servicenetz
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. Melden Sie sich an vSphere Web Client an. 
2. Wählen Sie im Menü **Home** die Option **HCX** aus.
3. Wählen Sie **Infrastructure** -> **InterConnect** aus.
4. Klicken Sie unter 'Multi-Site Service Mesh' auf **Network Profiles**.
5. Gehen Sie unter **Create Network Profile** wie folgt vor:
   1. Wählen Sie einen Wert für die verteilte Portgruppe aus; Beispiel 'External'.
   2. Geben Sie den IP-Adressbereich der externen IP-Adressen an.
   3. Geben Sie die Präfixlänge des externen Teilnetzes an.
   4. Geben Sie ein externes Gateway an.
   5. Geben Sie DNS-Details an.
   6. Legen Sie als MTU-Wert 1500 fest.
   7. Klicken Sie auf 'Create'.
6. Wiederholen Sie die obigen Schritte für Netze des Typs 'Management' und 'vMotion'.
   Hinweis: für MTU muss 9000 festgelegt sein.

## Ergebnisse
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| Netzname | MTU |
| -----| ----|
| External | 1500|
| Management | 9000|
| vMotion | 9000|

## Rechenprofile für das lokale Servicenetz
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. Melden Sie sich an vSphere Web Client an. 
2. Wählen Sie im Menü **Home** die Option **HCX** aus.
3. Wählen Sie **Infrastructure** -> **InterConnect** aus.
4. Klicken Sie unter 'Multi-Site Service Mesh' auf **Compute Profiles**.
5. Gehen Sie unter **Create Compute Profile** wie folgt vor:
   1. Geben Sie den Namen des Rechenprofils an.
   2. Wählen Sie Alle Services aus, die aktiviert werden sollen, und klicken Sie auf **Continue**.
   3. Wählen Sie den Cluster aus und klicken Sie auf **Continue**.
   4. Wählen Sie den Datenspeicher aus und klicken Sie auf **Continue**.
   5. Wählen Sie das Netzprofil für 'Management' aus und klicken Sie auf **Continue**.
   6. Wählen Sie das Netzprofil für 'External/Uplink' aus und klicken Sie auf **Continue**.
   7. Wählen Sie das Netzprofil für 'vMotion' aus und klicken Sie auf **Continue**.
   8. Wählen Sie das Netzprofil für 'vSphere Replication (Management)' aus und klicken Sie auf **Continue**.
   9. Wählen Sie 'Distribute Switch' für die Erweiterung aus, zum Beispiel 'Private-Switch'.
   10. Klicken Sie auf 'Finish'.

## Ergebnisse
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

Ein Rechenprofil für die Cluster-/Speicherkombination wurde erstellt und ist mit der Erstellung des Servicenetzes verfügbar.

## Lokales HCX-Servicenetz
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## Erstellen des lokalen Servicenetzes
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. Melden Sie sich an vSphere Web Client an. 
2. Wählen Sie im Menü **Home** die Option **HCX** aus.
3. Wählen Sie **Infrastructure** -> **InterConnect** aus.
4. Klicken Sie unter 'Multi-Site Service Mesh' auf **Service Mesh**.
5. Gehen Sie unter **Create Service Mesh** wie folgt vor:
   1. Wählen Sie Sites aus ('On-Premises' oder 'vCloud Organization') und klicken Sie auf 'Continue'.
   2. Wählen Sie das Quellenrechenprofil aus.
   3. Wählen Sie ein fernes Rechenprofil aus. Beispiel: 'CloudCompute'.
   4. Wählen Sie 'All Services' aus und klicken Sie auf 'Continue'.
   5. Klicken Sie auf der Seite 'Advanced Configuration - Override Uplink Network Profiles (Optional)' auf 'Continue'.
   6. Klicken Sie auf 'Continue'.
   7. Klicken Sie auf 'Continue' und lassen Sie den Standardwert auf der Seite 'Advanced Configuration - Configure WAN Optimization Service Bandwidth Limit' unverändert.
   8. Geben Sie den Servicenamen an und klicken Sie auf **Finish**.
6. Überprüfen Sie Taskliste auf die Erstellung des Servicenetzes; am Ende müssen drei HCX-Appliances für den lokalen Standort und drei am Cloudstandort vorhanden sein.

## Ergebnisse
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

Ein HCX-Servicenetz ist eine effektive HCX-Servicekonfiguration für eine Quell- und Zielsite. Ein Servicenetz kann zu einem verbundenen Standortpaar hinzugefügt werden, wenn an beiden Standorten ein gültiges Rechenprofil erstellt wurde.

Mit dem Hinzufügen eines Servicenetzes beginnt die Bereitstellung von virtuellen HCX InterConnect-Appliances an beiden Standorten. Ein Servicenetz für gegenseitige Verbindungen wird immer am Quellenstandort erstellt.

## Netzerweiterung
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## Prozess zur Erweiterung eines Netzes
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

Zum Erweitern eines Netzes (VLAN oder VXLAN) mit HCX führen Sie die folgenden Schritte über die vCenter-Webbenutzerschnittstelle auf Clientseite aus.

1. Melden Sie sich an vSphere Web Client an. 
2. Wählen Sie im Menü **Home** die Option **HCX** aus.
3. Wählen Sie im Menü auf der linken Seite unter **Services** -> **Network Extension** aus.
4. Klicken Sie auf **Extend Network**.
   1. Wählen Sie das zu erweiternde Netz aus.
   2. Geben Sie das aktuelle Standardgateway und die Teilnetzmaske im CIDR-Format ein.
   3. Klicken Sie unten in der Anzeige auf **Erweiterung**, um den Workflow für die Netzerweiterung zu starten.

Der Netzfortschritt wird im Teilfenster für vCenter-Client-Tasks überwacht.

## Konzepte und bewährte Verfahren für die Netzerweiterung
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

Was die Brücke des clientseitigen Netzes zum cloudseitigen VXLAN zusammenhält, ist ein hoch entwickeltes VPN mit mehreren Tunneln, das aus proprietärer HCX-Technologie besteht. Es basiert nicht auf NSX, arbeitet aber mit NSX zusammen und erweitert dessen Funktionalität. Dieser Prozess wird von der clientseitigen vCenter-Webbenutzerschnittstelle (UI) gesteuert, automatisiert die Bereitstellung und führt die beiden Endpunkte auf der Client- und der Cloudseite aus. Die Auswahl des zu erweiternden Netzes geschieht einzeln oder stapelweise.

Zusätzlich erhält NSX im Rahmen des Workflows zur Netzerweiterung auf Cloudseite die Berechtigung zum Erstellen eines VXLAN; dieses wird anschließend mit einer Schnittstelle verbunden, die auf der angegebenen cloudseitigen L3-Einheit (DLR oder ESG in nicht verbundenem Zustand) und der cloudseitigen Appliance für Netzerweiterungen erstellt wird.

Wenn Sie eine bestimmte Anwendung migrieren, müssen zumeist alle Netze, die von den entsprechenden virtuellen Maschinen (VMs) verwendet werden, über die gesamte {{site.data.keyword.cloud}}-Instanz erweitert werden.

Warum "zumeist" und nicht immer? Es kann von Vorteil sein, bestimmten Datenverkehr von der Clientseite zu trennen, nachdem die VM migriert wurde. Beispiel: Backup-Clients für Gast-VMs, die bei der Verschiebung in die Cloud eine hohe Bandbreitennutzung verursachen könnten. Der Client für die Gastmaschine ist bei der VM-Migration nicht erforderlich, da er automatisch von einem moderneren Backup auf Blockebene auf Cloudseite übernommen wird.

Auf den Sicherungsnetzadapter des Clients wird nicht zugegriffen, da dies einen Zugriff auf jede VM bedeuten würde, um den Sicherungszeitplan für den Client auf der Gastmaschine zu beenden. Wenn ein Sicherungsnetz verwendet wird, kann die Sicherung daher fehlschlagen. Diese Situation besteht vorübergehend, bis alle VMs nach der Migration erreichbar sind, um den Sicherungsclient auf der Gastmaschine zu inaktivieren.

Die Bandbreite einer einzelnen Netzerweiterung beträgt theoretisch 4 Gb/s, dies kann jedoch die Grenze für alle erweiterten Netze innerhalb eines einzigen L2C-Paares sein und ist über ein einzelnes erweitertes Netz nicht zu erreichen. Ein einzelnes erweitertes Netz kann ungefähr 1 Gb/s erreichen, da ihm genügend Underlay-Bandbreite zugewiesen und die Latenzzeit mit < ca. 10 ms niedrig ist.

### Option "Proximity Routing"
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

Ohne jede Art von Routenoptimierung werden erweiterte Netze für beliebigen L3-Zugriff zur Clientseite zurück geleitet. Diese Anrufdurchleitung führt zu einem ineffizienten Verkehrsmuster, da Pakete zwischen Client (Quelle) und Cloud hin- und hergesendet werden müssen, selbst in Fällen, wo sich sowohl die Quell- als auch die Ziel-VMs in der Cloud befinden. Die Funktion des Proximity-Routings von HCX wurde in Hinblick auf dieses Problem und auch zur Vermeidung von lokalem Datenverkehr-Egress entwickelt.

## Zugehörige Links
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
