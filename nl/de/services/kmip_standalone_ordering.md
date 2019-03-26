---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

# KMIP for VMware on IBM Cloud-Instanzen bestellen
{: #kmip_standalone_ordering}

Sie können eine KMIP for VMware on {{site.data.keyword.cloud}}-Instanz bestellen, ohne sie einer VMware-Instanz für die flexible Verwaltung des Service und der Instanzen zuzuordnen.

## Vorbereitende Schritte
{: #kmip_standalone_ordering-req}

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
* Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Sie haben alle Hinweise im Abschnitt [Hinweise zur Installation von KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations-install) gelesen.

## Vorgehensweise zum Bestellen von KMIP for VMware on IBM Cloud-Instanzen
{: #kmip_standalone_ordering-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einführung**.
2. Klicken Sie im Bereich **Zusätzliche Services bestellen** auf **KMIP for VMware on IBM Cloud**.
3. Konfigurieren Sie auf der Seite **KMIP for VMware on IBM Cloud** die Serviceeinstellungen wie erforderlich.
4. Klicken Sie auf **Bereitstellung**.

## KMIP for VMware on IBM Cloud - Servicekonfiguration
{: #kmip_standalone_ordering-config}

Geben Sie beim Bestellen des Service die folgenden Einstellungen an:

### Instanzname
{: #kmip_standalone_ordering-config-instance-name}

Geben Sie einen Namen für Ihre KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz an. 

### Serviceregion
{: #kmip_standalone_ordering-config-service-region}

Wählen Sie die {{site.data.keyword.cloud_notm}}-Region aus, in der Ihre KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz gehostet werden soll. 

{{site.data.keyword.cloud_notm}} verwaltet einen hoch verfügbaren Netzserviceendpunkt für KMIP for VMware on {{site.data.keyword.cloud_notm}} in jeder Region, in der der Service verfügbar ist. 

Tabelle 1. Netzserviceendpunkte und Regionen für KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Region         | Endpunkte               |
|:---------------|:-----------------------|
| Deutschland        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Sydney        |  <ul><li><code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokio          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| USA (Süden)       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### API-Schlüssel für Service-ID
{: #kmip_standalone_ordering-config-api-key}

Geben Sie den API-Schlüssel für die {{site.data.keyword.cloud_notm}}-Service-ID ein, die für den Zugriff auf die IBM Key Protect Service-Instanz verwendet wird.

### Key Protect-Instanz
{: #kmip_standalone_ordering-config-key-protect}

Klicken Sie auf **Abrufen**, um eine Liste der verfügbaren IBM Key Protect Service-Instanzen abzurufen und wählen Sie dann die Instanz aus, die für das Schlüsselmanagement verwendet werden soll.

### Stammschlüssel für Kunden
{: #kmip_standalone_ordering-config-root-key}

Klicken Sie auf **Abrufen**, um den Stammschlüssel für Kunden abzurufen, der in der ausgewählten Schlüsselmanagerinstanz gespeichert ist. 

## Ergebnisse
{: #kmip_standalone_ordering-results}

Die Bestellung der KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bestellung prüfen, indem Sie die Instanzdetails anzeigen.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Installiert** und Sie empfangen per E-Mail eine Benachrichtigung.

## Nächste Schritte
{: #kmip_standalone_ordering-next}

Fügen Sie Clientzertifikate für die bestellte KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz hinzu. Weitere Informationen finden Sie unter [Zertifikate für KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert).

## Zugehörige Links
{: #kmip_standalone_ordering-related}

* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen anzeigen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
