---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Protokollnachrichten für Instanzen
{: #audit_messages}

Alle Operationen, die {{site.data.keyword.cloud_notm}} für Ihre VMware-Instanz ausführt, werden im Instanzprotokoll protokolliert. Sie können das Instanzprotokoll als Referenz verwenden, um diese Operationen zu überprüfen. Weitere Informationen zum Überprüfen Ihres Instanzprotokolls finden Sie in [Vorgehensweise zum Anzeigen des Bereitstellungsverlaufs für vCenter Server-Instanzen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history).

In den folgenden Abschnitten sind alle möglichen Nachrichten aufgeführt, die in Ihrem Instanzprotokoll ausgegeben werden können.

## Allgemeine Instanzprotokollnachrichten
{: #audit_messages-general}

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

## Instanzfehlernachrichten
{: #audit_messages-error}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Instanzprotokollfehlernachrichten aus:

* ``Fehler beim Bestellen der VMware-Lizenzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Teilnetzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler: Der SoftLayer-API-Schlüssel ist nicht gültig. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler: Das SoftLayer-Rechenzentrum ist nicht gültig. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Verwenden eines gemeinsam genutzten Image im bereitgestellten SoftLayer-Konto. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Serviceeinträgen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Teilnetzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Lizenzen. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``
* ``Fehler beim Bestellen von Services. Um Unterstützung zu erhalten, öffnen Sie ein Service-Ticket.``

## Protokollnachrichten für Cluster
{: #audit_messages-cluster}

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

## Protokollnachrichten für ESXi-Server
{: #audit_messages-esxi}

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

## Netzprotokollnachrichten
{: #audit_messages-network}

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
* ``Die Stornierung des VLAN ist abgeschlossen.``
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

## Protokollnachrichten für Virtual Server-Instanzen (VSIs)
{: #audit_messages-vsi}

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

## Protokollnachrichten für IBM CloudBuilder
{: #audit_messages-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für IBM CloudBuilder aus:

* ``Bestellung für die IBM CloudBuilder-VSI wird überprüft...``
* ``Bestellung für die IBM CloudBuilder-VSI wird gestartet...``
* ``Die IBM CloudBuilder-VSI ist bereit.``
* ``IBM CloudBuilder ist betriebsbereit.``
* ``Die IBM CloudBuilder-VSI wird geschlossen...``

## Protokollnachrichten für IBM CloudDriver
{: #audit_messages-clouddriver}

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

## Protokollnachrichten für Speicher
{: #audit_messages-storage}

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

## Protokollnachrichten für Services
{: #audit_messages-services}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für Services aus:

* ``Einrichtung der Management-Services wird gestartet...``
* ``Serviceeinträge werden bestellt ...``
* ``Bestellung der Serviceeinträge abgeschlossen.``
* ``IBM Betriebsservices sind aktiv.``
* ``Standardservices werden aktiviert...``
* ``Die Standardservices wurden erfolgreich aktiviert.``
* ``Stornierung der Serviceeinträge wird durchgeführt...``
* ``Die Stornierung der Serviceeinträge ist abgeschlossen.``

## Protokollnachrichten für vCenter Server with Hybridity Bundle
{: #audit_messages-hybridity}

{{site.data.keyword.vmwaresolutions_short}} gibt die folgenden Nachrichten für die vCenter Server with Hybridity Bundle-Instanzen aus:

* ``vCenter Server with Hybridity Bundle-Lizenzen werden bestellt...``
* ``Konvertierung für vCenter Server with Hybridity Bundle wird gestartet...``
* ``Die Konvertierung für vCenter Server with Hybridity Bundle ist abgeschlossen.``
* ``vCenter Server with Hybridity Bundle wird entfernt...``
* ``vCenter Server with Hybridity Bundle wurde erfolgreich entfernt.``
* ``Konvertierung für vCenter Server with Hybridity Bundle wird abgebrochen...``

## Zugehörige Links
{: #audit_messages-related}

* [Hinweise zum Ändern von vCenter Server-Artefakten](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
