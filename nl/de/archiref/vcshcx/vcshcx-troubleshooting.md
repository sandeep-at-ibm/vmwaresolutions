---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

# Fehlerbehebung für HCX
{: #vcshcx-troubleshooting}

Folgende Themen enthalten Informationen zu häufigen Problemen mit HCX und ihrer Korrektur.

## Probleme mit der HCX-Clientbenutzerschnittstelle
{: #vcshcx-troubleshooting-hcx-client-issues}

### Zeitlimitüberschreitung des Tokens für die HCX-Benutzerschnittstelle
{: #vcshcx-troubleshooting-hcx-ui-issues}

Eine Zeitlimitüberschreitung in der HCX-Benutzerschnittstelle tritt typischerweise dann auf, wenn die vCenter-Benutzerschnittstelle (UI) eine Zeitlang geöffnet war. Der Grund ist, dass das Anmeldetoken für den HCX-Manager-Server das zulässige Zeitlimit überschritten hat. Melden Sie sich von der vSphere-Webbenutzerschnittstelle ab und wieder an, um das Token zu aktualisieren.

### HCX-Clientbenutzerschnittstelle zeigt "NaN" für alle Metriken im Dashboard-Bildschirm an
{: #vcshcx-troubleshooting-nan-display}

Dieses Problem hängt mit den Berechtigungen des aktuell bei vCenter angemeldeten Kontos zusammen. Stellen Sie sicher, dass die Gruppe "Unternehmensadministrator" in der Benutzerschnittstelle der HCX-cloudseitigen Appliance festgelegt ist.

## Migrationsprobleme
{: #vcshcx-troubleshooting-mig-issues}

Migrationsprobleme in den aktuellen Versionen von HCX sind in der Regel einer von drei Kategorien zuzuordnen: Lizenzierung, Netzkonnektivität des Cloud-Gateways und Kompatibilität der Zielhardware.

### Lizenzierung
{: #vcshcx-troubleshooting-licensing}

Wenn eine Migration aufgrund eines Lizenzierungsproblems fehlschlägt, zeigen aktuelle Versionen von HCX dies als Fehlernachricht in Bezug auf die Client-Webbenutzerschnittstelle innerhalb der vCenter-Benutzerschnittstelle an.

### Netzkonnektivität (WAN)
{: #vcshcx-troubleshooting-wan-connect}

Wenn ein Problem mit der WAN-Konnektivität auftritt, überprüfen Sie die Anzeige **Verbindung -> HCX-Komponenten** in der HCX-Benutzerschnittstelle für den Tunnelstatus. Im Allgemeinen müssen Paketkomponenten nicht zurückgesetzt oder neu gestartet werden. Sobald die WAN-Verbindung wiederhergestellt wird, stellen sie automatisch eine Verbindung her.

Wenn es Fixes und Aktualisierungen gibt, die auf die HCX-Manager (Client und Cloud) angewendet wurden, und diese Aktualisierungen auch Programmkorrekturen an den Paketkomponenten bewirken, müssen Sie das Cloud-Gateway und alle bereitgestellten L2Cs erneut bereitstellen. Es ist möglich, ein weiteres Debugging des Tunnelstatus vorzunehmen, indem eine Verbindung zum HCX-Manager über einen SSH-Client wie z. B. 'ccli' hergestellt wird.  

1. Stellen Sie eine SSH-Verbindung zum HCX-Manager mithilfe des Administratorkontos und des angegebenen Kennworts her.
2. Führen Sie den Befehl `su –` aus und geben Sie das Kennwort des Benutzers `root` (identisch mit dem Administratorkennwort) ein, um zu 'Root' zu wechseln.
3. Ändern Sie das Verzeichnis in `/opt/vmware/bin` und führen Sie den Befehl `./ccli` aus. Wenn dies nicht erfolgreich ist, weil die Umgebung nicht für 'Root' konfiguriert ist, führen Sie den Befehl `./ccliSetup.pl` aus.
4. Führen Sie den Befehl `list` in der `ccli`-Shell aus, um die Paketkomponenten aufzulisten, die beim HCX-Manager registriert sind.
5. Geben Sie die Paket-ID für `ccli` an, indem Sie die für die Paketkomponente aufgelistete ID eingeben. Beispiel: `go 8`.
6. Führen Sie den Befehl `debug remoteaccess enable` aus, um über SSH eine Verbindung zu der gewünschten Paketkomponente herzustellen.
7. Verlassen Sie `ccli` und stellen Sie über SSH eine Verbindung zu der IP-Adresse der SSH-fähigen Paketkomponente her.
9. Fahren Sie mit der Fehlerbehebung fort.
10. Kehren Sie zu `ccli` zurück und inaktivieren Sie den `ssh`-Service für die Komponente.
11. Verwenden Sie bei Bedarf den ccli-Befehl `hc`, um eine Zustandsprüfung der Komponenten auszuführen.

## Kompatibilitätsproblem mit der Zielhardware
{: #vcshcx-troubleshooting-hw-compatibility}

Die vMotion-Migration kann zu Problemen führen, wenn die Clientquellenseite eine neuere Hardwareversion und ein neueres vSphere-Release aufweist als die Cloud. Da bei der replikationsbasierten Migration Daten auf eine neu erstellte virtuelle Maschine (VM) auf der Zielseite kopiert werden, sollte die Änderung des Migrationstyps in "Massenmigration" in den meisten Fällen dazu führen, dass die Migration gelingt.

## Probleme mit erweitertem L2-Konzentrator
{: #vcshcx-troubleshooting-stretched-l2}

Beim Betrieb des L2-Konzentrators (L2C) sind nur sehr wenige Probleme aufgetreten. Ähnlich wie beim CGW wird bei einem Verbindungsverlust des L2C automatisch die Verbindung wiederhergestellt, nachdem die Netzkonnektivität wiederhergestellt wurde. Verwenden Sie die ccli-Shell, um den Zustand und den Betrieb zu übeprüfen. Nach der SSH-Aktivierung und dem Anschluss von L2C führen Sie die Befehle `ip tunnel` und `ip link |grep t_` aus, um den Status der Tunnel anzuzeigen.

## Zugehörige Links
{: #vcshcx-troubleshooting-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
