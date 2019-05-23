---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Benutzer-IDs und Protokollnachrichten zur Bereitstellung für vCenter Server-Instanzen
{: #ibm_use}

Zur Protokollierung von Automatisierungen und Operationen muss {{site.data.keyword.cloud}} auf Ihr Konto zugreifen können.

## Benutzer-IDs
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}} verwaltet eine Gruppe von Benutzern in Ihrem Konto für die Verwendung durch die {{site.data.keyword.cloud_notm}}-Automatisierung, wenn Sie Operationen, wie das Hinzufügen von Hosts, Clustern oder Speicher zu Ihrer VMware-Instanz, ausführen. In den folgenden Abschnitten finden Sie die Benutzer-IDs für die {{site.data.keyword.cloud_notm}}-Automatisierung.

VMware-Instanzoperationen schlagen fehl, wenn die IBM Benutzer-IDs gelöscht oder inaktiviert oder die entsprechenden Kennwörter geändert werden.
{:important}

### Benutzer-IDs für vCenter und Platform Services Controller
{: #ibm_use-user-ids-vcenter-psc}

Ab Version 2.5 verwendet {{site.data.keyword.vmwaresolutions_short}} die folgenden Benutzer-IDs, um eine standardmäßig integrierte Identitätsquelle in vCenter hinzuzufügen.

Tabelle 1. Benutzer-IDs für vCenter und Platform Services Controller

| User     | Benutzer-ID  | Methode| Beschreibung |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Wird für die VMware-Konfiguration verwendet, wie z. B. die Einrichtung von VMware High Availability und die Erstellung verteilter Switches. Wird nach der Bereitstellung verwendet, um primäre und sekundäre vCenter Server-Instanzen zu paaren. |
| Kunde | customerroot | SSH    | Nur für die Verwendung durch den Kunden erstellt. |
| IBM      | automation@``rootdomäne``<br/>(Active Directory-Benutzer) | HTTP | Wird nach der Bereitstellung zum Hinzufügen und Entfernen von Hosts und Clustern und zum Bereitstellen und Konfigurieren virtueller Maschinen für Add-on-Services verwendet. |
| Kunde | Administrator@vsphere.local | HTTP | Nur für die Verwendung durch den Kunden erstellt. |

HTTP wird für die Einrichtung und Konfiguration von vCenter sowie für VMware-Operationen, wie das Hinzufügen von Hosts, Clustern oder Speicher für das Ressorcenmanagement in vCenter, verwendet.
{:note}

### NSX-Manager-Benutzer-IDs
{: #ibm_use-user-ids-nsx-mgr}

NSX-Manager-Benutzer-IDs werden verwendet, um ESG-Regeln für den Service hinzuzufügen.

Tabelle 2. NSX-Manager-Benutzer-IDs

| User     | Benutzer-ID  | Beschreibung |
|:---------|:-------------|:------------|
| IBM      | automation@``rootdomäne``<br/>(Active Directory-Benutzer) | Wird nach der Bereitstellung zum Verwalten von NSX-VTEP-IP-Adressen, zum Verwalten von Host- und Clusterkonfigurationen beim Hinzufügen und Entfernen von Hosts und Clustern und zum Verwalten der ESG-Konfiguration für Add-on-Services verwendet, für die ein öffentlicher Netzzugriff für die Lizenzierung, Lizenzaktivierung oder für Nutzungsberichte erforderlich ist. |
| Kunde | Administrator        | Nur für die Verwendung durch den Kunden erstellt. |

### Benutzer-IDs für ESXi-Hosts
{: #ibm_use-user-ids-esxi}

Die ESXi-Host-Benutzer-IDs werden zum Hinzufügen von Speicher, zum Anwenden von Patches, zum Konfigurieren von vSAN-Clustern und zum Ausführen von Validierungscode für alle Server verwendet.

Tabelle 3. ESXi-Host-Benutzer-IDs

| User     | Benutzer-ID  | Beschreibung |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Wird nach der Bereitstellung zum Hinzufügen von zusätzlichem NFS-Speicher und zum Konfigurieren von Routen für diesen Speicher verwendet. |
| Kunde | root         | Nur für die Verwendung durch den Kunden erstellt. |

### Microsoft Active Directory-Benutzer-IDs
{: #ibm_use-user-ids-ad}

Active Directory-Benutzer-IDs werden zum Festlegen von DNS-Einträgen verwendet.

Tabelle 4. Active Directory-Benutzer-IDs

| User     | Benutzer-ID  | Beschreibung |
|:---------|:------------- |:------------|
| IBM      | automation    | Dient zum Hinzufügen eines Hosts, zum Hinzufügen einer virtuellen Maschine für den Service und zum Festlegen von Active Directory- und DNS-Einträgen. |
| Kunde | Administrator | Nur für die Verwendung durch den Kunden erstellt. |

## Protokollnachrichten für Instanzen
{: #ibm_use-msgs}

Alle Operationen, die {{site.data.keyword.cloud_notm}} für Ihre VMware-Instanz ausführt, werden im Instanzprotokoll protokolliert. Sie können das Instanzprotokoll als Referenz verwenden, um diese Operationen zu überprüfen. Weitere Informationen zum Überprüfen Ihres Instanzprotokolls finden Sie in [Vorgehensweise zum Anzeigen des Bereitstellungsverlaufs für vCenter Server-Instanzen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history).

In den folgenden Abschnitten sind alle möglichen Nachrichten aufgeführt, die in Ihrem Instanzprotokoll ausgegeben werden können.

### Allgemeine Instanzprotokollnachrichten
{: #ibm_use-msgs-general}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für allgemeine Aktionen aus:

* ``Die Erstellung des Instanzbenutzers und der erforderlichen Services wird gestartet...``
* ``Die Erstellung des Instanzbenutzers und der erforderlichen Services ist abgeschlossen.``
* ``vCenter Server-Lizenz wird bestellt...``
* ``VMware-Lizenzen werden bestellt...``
* ``Bestellung der VMware-Lizenzen abgeschlossen.``
* ``<quantity> Aufpreise werden bestellt...``
* ``Die Installation und Konfiguration von <environment> wird gestartet...``
* ``Die Installation und Konfiguration von <environment> ist abgeschlossen.``
* ``VMware-Komponenten werden gestartet...``
* ``Die Bereitstellung der Instanz wird gestartet...``
* ``Die <instance_name>-Instanz kann jetzt verwendet werden.``
* ``Upgrade auf <version> wird gestartet...``
* ``Das Upgrade auf <version> ist abgeschlossen.``
* ``Das Upgrade der VMware-Komponente ist abgeschlossen.``
* ``Der Löschvorgang für die <instance_name>-Instanz wird gestartet...``
* ``Die <instance_name>-Instanz wurde erfolgreich gelöscht.``
* ``Die sichere Bereinigung der Instanz ist abgeschlossen.``
* ``vCenter-Lizenz wird storniert...``
* ``Der Instanzbenutzer und die erforderlichen Services werden storniert...``
* ``Aufpreise für <environment> werden storniert...``
* ``Stornierung der VMware-Lizenz wird durchgeführt...``
* ``Die Stornierung der VMware-Lizenz ist abgeschlossen.``
* ``Die SoftLayer-Bestellung ist fehlgeschlagen oder hat das zulässige Zeitlimit überschritten.``

### Protokollnachrichten für Cluster
{: #ibm_use-msgs-cluster}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für vCenter Server-Cluster aus:

* ``Clusterkonfiguration wird gestartet...``
* ``Clusterkonfiguration für <cluster_name> wird gestartet...``
* ``Die Clusterkonfiguration ist abgeschlossen.``
* ``Der <cluster_name>-Cluster kann jetzt verwendet werden.``
* ``Der neue Cluster wird in vCenter hinzugefügt...``
* ``Der neue Cluster wurde in vCenter hinzugefügt.``
* ``Der Löschvorgang für den <cluster_name>-Cluster wird gestartet...``
* ``Der <cluster_name>-Cluster wird aus vCenter gelöscht...``
* ``Der <cluster_name>-Cluster wurde aus vCenter gelöscht.``
* ``Der <cluster_name>-Cluster wurde gelöscht.``

### Protokollnachrichten für Virtual Server-Instanzen (VSIs)
{: #ibm_use-msgs-vsi}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für Virtual Server-Instanzen (VSIs) aus:

* ``Neue Virtual Server-Instanz für IBM CloudDriver wird bestellt...``
* ``Die Virtual Server-Instanz für IBM CloudDriver (<ip_address>) wurde bereitgestellt.``
* ``Die Virtual Server-Instanz für IBM CloudDriver (<ip_address>) wird storniert...``
* ``Bestellung für die Microsoft Windows-VSI für Microsoft Active Directory/DNS wird gestartet...``
* ``Die Bestellung der Microsoft Windows-VSI für Active Directory/DNS wird überprüft...``
* ``Die Microsoft Windows-VSI für Active Directory/DNS ist betriebsbereit.``
* ``Die VSI wird storniert...``
* ``Zugehörige VSIs werden storniert...``
* ``Die Stornierung der VSI ist abgeschlossen.``

### Protokollnachrichten für IBM CloudDriver
{: #ibm_use-msgs-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für IBM CloudDriver aus:

* ``IBM CloudDriver wird vorbereitet...``
* ``IBM CloudDriver ist betriebsbereit.``
* ``IBM CloudDriver <ip_address> kann jetzt verwendet werden.``
* ``Status von IBM CloudDriver wird überprüft...``
* ``Vorhandener IBM CloudDriver <ip_address> wird wiederverwendet...``
* ``Vorhandener IBM CloudDriver wird wiederverwendet (in Bereitstellung)...``
* ``IBM CloudDriver wird freigegeben...``
* ``IBM CloudDriver <ip_address> wird freigegeben...``
* ``Löschvorgang für IBM CloudDriver wird gestartet...``
* ``Der Löschvorgang für IBM CloudDriver ist abgeschlossen.``

### Protokollnachrichten für ESXi-Server
{: #ibm_use-msgs-esxi}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für für ESXi-Server aus:

* ``Bestellung für <quantity> ESXi-Server wird gestartet...``
* ``Bestellung für ESXi-Server wird überprüft...``
* ``Die ESXi-Server mit der privaten IP-Adresse <ip_addresses> sind bereit.``
* ``Alle ESXi-Server wurden zurückgefordert.``
* ``ESXi-Server werden zur vCenter Server-Instanz hinzugefügt...``
* ``Die ESXi-Server wurden erfolgreich aktualisiert.``
* ``Die Bestellung von ESXi-Servern für den Cluster wird gestartet...``
* ``Die Bestellung für <quantity> ESXi-Server für den <Cluster Name>-Cluster wird gestartet...``
* ``Die ESXi-Server für den Cluster sind bereit.``
* ``ESXi-Server mit der privaten IP-Adresse <ip_addresses> sind für den Cluster bereit.``
* ``Der ESXi-Server ist bereit.``
* ``Die ESXi-Serverkonfiguration ist abgeschlossen.``
* ``Der ESXi-Server wurde erfolgreich mit der Eigenschaft hinzugefügt.``
* ``Alle Anforderungen zum Hinzufügen von ESXi-Servern wurden erfolgreich abgeschlossen.``
* ``Der ESXi-Server wird hinzugefügt...``
* ``Bare-Metal-Server für den ESXi-Server wird bestellt...``
* ``Neue ESXi-Server werden zu vCenter hinzugefügt.``
* ``Das Hinzufügen von Services zu den neuen ESXi-Servern wird gestartet...``
* ``Die ausgewählten ESXi-Server wurden erfolgreich storniert.``
* ``Neue ESXi-Server werden bereitgestellt.``
* ``Neue ESXi-Server wurden geprüft und sind bereit.``
* ``Die Bestellung für <quantity> neue ESXi-Server für den <cluster_name>-Cluster wird gestartet...``
* ``Die ausgewählten ESXi-Server wurden aus vCenter Server entfernt.``
* ``Das Entfernen von Services zum Entfernen von ESXi-Servern wird gestartet...``
* ``ESXi-Server für den <cluster_name>-Cluster werden geprüft ...``
* ``Die neuen Cluster-ESXi-Server haben die Überprüfung erfolgreich bestanden.``
* ``Die neue ESXi-Serverbestellung wird überprüft...``
* ``Die Überprüfung der ESXi-Serverbestellung ist fehlgeschlagen.``
* ``Batchanforderung zum Hinzufügen von ESXi-Servern wird aufgeteilt.``
* ``Alle Anforderungen zum Entfernen von ESXi-Servern wurden erfolgreich ausgeführt.``
* ``Der Host wurde erfolgreich hinzugefügt.``
* ``Die Hosts wurden erfolgreich entfernt.``
* ``Stornierung des Bare-Metal-Servers wird durchgeführt...``
* ``Die Stornierung der Bare-Metal-Server ist abgeschlossen.``
* ``ESXi-Server werden aus der vCenter Server-Instanz entfernt...``
* ``Der ESXi-Server wird entfernt.``
* ``Der ESXi-Server <server_id> wird entfernt.``
* ``Ausgewählte ESXi-Server werden aus vCenter Server entfernt...``
* ``Die ESXi-Server werden storniert...``
* ``Die ausgewählten ESXi-Server werden storniert...``

### Protokollnachrichten für IBM CloudBuilder
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für IBM CloudBuilder aus:

* ``Bestellung für die IBM CloudBuilder-VSI wird überprüft...``
* ``Bestellung für die IBM CloudBuilder-VSI wird gestartet...``
* ``Die IBM CloudBuilder-VSI ist bereit.``
* ``IBM CloudBuilder ist betriebsbereit.``
* ``Die IBM CloudBuilder-VSI wird geschlossen...``

### Protokollnachrichten für Speicher
{: #ibm_use-msgs-storage}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für Speichereinstellungen aus:

* ``vSAN-Lizenz wird bestellt...``
* ``vSAN-Lizenz wird storniert...``
* ``Die Stornierung der VSAN-Lizenz ist abgeschlossen.``
* ``<quantity> NFS-Speicher für den <cluster_name>-Cluster wird/werden bestellt.``
* ``Der neue NFS-Speicher wurde hinzugefügt und kann verwendet werden.``
* ``Der Speicher für NFS-Managementressourcen wird storniert...``
* ``Der ausgewählte NFS-Speicher wurde gelöscht.``
* ``Die Bestellung für den Endurance-Speicher wird gestartet...``
* ``Der Endurance-Speicher wird storniert...``

### Protokollnachrichten für Netze
{: #ibm_use-msgs-network}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für Netzeinstellungen aus:

* ``Die Bestellung für das öffentliche VLAN wird gestartet...``
* ``VLAN-Konfiguration erfolgreich abgeschlossen.``
* ``Zusätzliches privates VLAN wird bestellt...``
* ``Zusätzliches privates VLAN wurde bereitgestellt.``
* ``Eine zusätzliche VSI für privates VLAN wurde bereitgestellt.``
* ``Trunking für zusätzliche private VLANs zu Bare-Metal-Servern wird durchgeführt...``
* ``Erfolgreiches Trunking für das zusätzliche private VLAN zu Bare-Metal-Servern.``
* ``VSI für privates VLAN wird storniert...``
* ``VLANs werden storniert...``
* ``Stornierung des VLAN wird durchgeführt...``
* `Die Stornierung des VLAN ist abgeschlossen.`
* ``NSX-Lizenz des Typs <type> für zwei Sockets wird bestellt...``
* ``Die NSX-Konfiguration für den neuen Cluster ist abgeschlossen.``
* ``NSX-Lizenz für zwei Sockets wird storniert...``
* ``Die NSX-Lizenz wurde erfolgreich storniert.``
* ``Die Bestellung für Teilnetze wird gestartet...``
* ``Das Teilnetz ist bereit.``
* ``Das portierbare private Teilnetz ist bereit.``
* ``Neuer Teilnetzzugriff auf NFS-Speicher wird erteilt...``
* ``Teilnetze werden storniert...``
* ``Stornierung des Teilnetzes wird durchgeführt...``
* ``Portierbares privates Teilnetz für Kunden wird storniert...``
* ``Portierbares öffentliches Teilnetz für Kunden wird storniert...``
* ``Privates Teilnetz für Endurance-Speicher wird storniert...``
* ``Portierbares öffentliches Teilnetz wird storniert...``
* ``Das portierbare öffentliche Teilnetz ist bereit.``
* ``Die Bestellung für das portierbare öffentliche Teilnetz wird gestartet...``
* ``Die Stornierung des Teilnetzes ist abgeschlossen.``
* ``Netzspeicher wird storniert...``

### Protokollnachrichten für Services
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für Services aus:

* ``Einrichtung der Management-Services wird gestartet...``
* ``Serviceeinträge werden bestellt ...``
* ``Bestellung der Serviceeinträge abgeschlossen.``
* ``IBM Betriebsservices sind aktiv.``
* ``Standardservices werden aktiviert...``
* ``Die Standardservices wurden erfolgreich aktiviert.``
* ``Stornierung der Serviceeinträge wird durchgeführt...``
* ``Die Stornierung der Serviceeinträge ist abgeschlossen.``

### Protokollnachrichten für vCenter Server with Hybridity Bundle
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für die vCenter Server with Hybridity Bundle-Instanzen aus:

* ``vCenter Server with Hybridity Bundle-Lizenzen werden bestellt...``
* ``Konvertierung für vCenter Server with Hybridity Bundle wird gestartet...``
* ``Die Konvertierung für vCenter Server with Hybridity Bundle ist abgeschlossen.``
* ``vCenter Server with Hybridity Bundle wird entfernt...``
* ``vCenter Server with Hybridity Bundle wurde erfolgreich entfernt.``
* ``Konvertierung für vCenter Server with Hybridity Bundle wird abgebrochen...``

### Protokollnachrichten für Cloud Foundation
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für Cloud Foundation-Instanzen aus:

* ``Die Bestellung für die Cloud Foundation-Instanz wird gestartet...``
* ``Die Bestellung für Cloud Foundation wurde empfangen.``
* ``Die Bestellung für Cloud Foundation wird verarbeitet...``
* ``Virtueller Server für die Cloud Foundation-Konfiguation wird bestellt...``
* ``Die Bestellung des virtuellen Servers für die Cloud Foundation-Konfiguation ist abgeschlossen.``
* ``Die Bestellung des virtuellen Servers für die Cloud Foundation-Konfiguation wurde überprüft.``
* ``Bare-Metal-Server für die Cloud Foundation-Konfiguation werden bestellt...``
* ``Die Bestellung der Bare-Metal-Server für die Cloud Foundation-Konfiguation ist abgeschlossen.``
* ``Cloud Foundation-Netzbetrieb wird konfiguriert...``
* ``Die Konfiguration für den Cloud Foundation-Netzbetrieb ist abgeschlossen.``
* ``Cloud Foundation-Teilnetze werden bestellt...``
* ``Bestellung der Cloud Foundation-Teilnetze abgeschlossen``
* ``Cloud Foundation-Instanz wird konfiguriert...``
* ``Komponenten der Cloud Foundation-Instanz werden angepasst und optimiert...``
* ``Die Bereinigung von Cloud Foundation wird durchgeführt...``
* ``Die Bereinigung von Cloud Foundation ist abgeschlossen.``
* ``Die Cloud Foundation-Instanz kann jetzt verwendet werden.``
* ``Die Cloud Foundation-Instanz wird angepasst und optimiert...``
* ``Die Konfiguration der Cloud Foundation-Instanz ist abgeschlossen.``
* ``Das Anpassen und Optimieren der Cloud Foundation-Instanz ist abgeschlossen.``
* ``Die Bestellung der Cloud Foundation-Komponenten ist abgeschlossen.``
* ``Der Löschvorgang für die Cloud Foundation-Instanz ist abgeschlossen.``
* ``Die Cloud Foundation-Instanz wurde gelöscht.``

### Fehlermeldungen
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Instanzprotokollfehlernachrichten aus:

* ``Fehler beim Bestellen eines virtuellen Servers für die Cloud Foundation-Konfiguration. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler: SoftLayer konnte keinen virtuellen Server für die Cloud Foundation-Konfiguration bereitstellen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Bare-Metal-Servern für die Cloud Foundation-Konfiguration. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von VLANs für die Cloud Foundation-Konfiguration. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Konfigurieren des Cloud Foundation-Netzbetriebs. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Cloud Foundation-Teilnetzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Erstellen von Verwaltungsservices für die Cloud Foundation-Instanz. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen der VMware-Lizenzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Teilnetzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Konfigurieren der Cloud Foundation-Instanz. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Anpassen und Optimieren der Cloud Foundation-Instanz. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler: Der SoftLayer-API-Schlüssel ist nicht gültig. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler: Das SoftLayer-Rechenzentrum ist nicht gültig. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Verwenden eines gemeinsam genutzten Image im bereitgestellten SoftLayer-Konto. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Serviceeinträgen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Teilnetzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Lizenzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Services. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``


## Zugehörige Links
{: #ibm_use-related}

* [Hinweise zum Ändern von vCenter Server-Artefakten](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
