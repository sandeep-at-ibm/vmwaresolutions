---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-02"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Activity Tracker-Ereignisse
{: #at-events}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um zu verfolgen, wie Benutzer und Anwendungen mit {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}} interagieren.

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service zeichnet benutzerinitiierte Aktivitäten auf, die den Status eines Service in {{site.data.keyword.cloud_notm}} ändern. Weitere Informationen finden Sie unter [Informationen zu IBM® Cloud Activity Tracker mit LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#gs_ov).

## Activity Tracker-Ereignistabelle
{: #at-events-table}

Überprüfen Sie die folgende Tabelle auf die Beschreibung der Spalten in der Activity Tracker-Ereignistabelle.

| Spalte                | Werttyp | Beschreibung |
|:----------------------|:-----------|:------------|
| Zeit                  | Nicht zutreffend        | Datum und Uhrzeit der Erstellung des Ereignisses. |
| initiator.name        | Zeichenfolge     | Die IBMid des Benutzers, der die Aktion initiiert. |
| target_name           | Zeichenfolge     | Die Ressource, für die die Aktion ausgeführt wird. |
| target.typeURI        | Zeichenfolge     | Die UUID (Universally Unique Identifier) des Ziels, für das die Aktion ausgeführt wird. |
| action                | Zeichenfolge     | Die Aktion, die das Ereignis auslöst. Gültige Werte sind `create`, `update` und `delete`. |
| outcome               | Zeichenfolge     | Das Ergebnis der Aktion. Werte sind `success`, `failure` oder `pending`. |
| reason_reasonCode     | Ganzzahl    | Der Ursachencode für das Ergebnis. |
| initiator_host_address| Zeichenfolge     | Die IP-Adresse, von der die Anforderung stammt. |
{: caption="Tabelle 1. Beschreibung der Activity Tracker-Ereignistabelle" caption-side="top"}

Weitere Informationen finden Sie unter [Ereignisfelder](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-event).

## Instanz-Managementereignisse verfolgen
{: #at-events-instance-mgmt}

Wenn Sie Benutzerkonten, Instanzen, Cluster und Services in {{site.data.keyword.vmwaresolutions_short}} verwalten, wird ein Ereignis generiert und an die **Kontodomäne** in Activity Tracker gesendet.

Überprüfen Sie die folgende Tabelle auf die Aktionen, die Managementereignisse generieren und an Activity Tracker senden.

| Aktion                                   | Beschreibung | Ergebnis |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` | Der Infrastruktur-API-Schlüssel für ein Konto wird aktualisiert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | Die Benachrichtigungseinstellung für ein Konto wird aktualisiert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | Die sicheren Daten der Instanz werden gelöscht. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	Eine Instanz wird auf ein BSS-Konto migriert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` | Eine vCenter Server-Instanz wird erstellt. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete` | Eine vCenter Server-Instanz wird gelöscht. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` | Ein Host wird zu einer vCenter Server-Instanz hinzugefügt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` | Ein Host wird von einer vCenter Server-Instanz entfernt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update` | Eine vCenter Server-Instanz wird aktualisiert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create` | Für eine vCenter Server-Instanz wird ein Cluster erstellt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete` | Ein Cluster für eine vCenter Server-Instanz wird gelöscht. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update` | Die NSX-Lizenz für eine vCenter Server-Instanz wird aktualisiert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add` | Für eine vCenter Server-Instanz wird ein Upgrade für Hybridity Bundle durchgeführt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove` | Hybridity Bundle wird aus einer vCenter Server-Instanz entfernt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add` | NFS-Speicher wird zu einer vCenter Server-Instanz hinzugefügt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove` | NFS-Speicher wird aus einer vCenter Server-Instanz entfernt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update` | Der Plan einer vCenter Server-Instanz wird aktualisiert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create` | Eine vSphere-Instanz wird erstellt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update` | Eine vSphere-Instanz wird aktualisiert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` | Eine vSphere-Vorlage wird entfernt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create` | Ein Service wird erstellt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete` | Ein Service wird gelöscht. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` | Für Hybridity Bundle wird ein Upgrade auf `version` durchgeführt. | `pending`<br>`success`<br>`failure` |
{: caption="Tabelle 2. Beschreibung von Aktionen, die Managementereignisse generieren" caption-side="top"}

## Ereignisse für den Service "KMIP for VMware on IBM Cloud" verfolgen
{: #at-events-kmip}

Wenn Sie Schlüssel für den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" verwalten, wird ein Ereignis generiert und an die **Kontodomäne** in Activity Tracker gesendet.

Überprüfen Sie die folgende Tabelle auf die Aktionen, die Ereignisse für den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" generieren und senden.

| Aktion                                      | Beschreibung                              | Ergebnis |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |Ein KMIP-Schlüssel wird erstellt. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |Ein KMIP-Schlüssel wird abgerufen. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |Die Attribute eines KMIP-Schlüssels werden abgerufen. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |Ein KMIP-Schlüssel wird aktiviert. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |Ein KMIP-Schlüssel wird widerrufen. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |Ein KMIP-Schlüssel wird gelöscht. | `pending`<br>`success`<br>`failure` |
{: caption="Tabelle 3. Beschreibung der Aktionen, die Ereignisse für den Service 'KMIP for VMware on {{site.data.keyword.cloud_notm}}' generieren" caption-side="top"}

## Ort zum Anzeigen der Ereignisse
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der {{site.data.keyword.cloudaccesstrailshort}} **Kontodomäne** verfügbar, die ihrerseits in der {{site.data.keyword.cloud_notm}}-Region verfügbar ist, in der die Ereignisse generiert werden.

Verwenden Sie {{site.data.keyword.cloud_notm}} Activity Tracker mit LogDNA zum Anzeigen der Instanz. Weitere Informationen hierzu finden Sie unter [Ereignisse anzeigen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events).

## Zugehörige Links
{: #at-events-related}

* [Instanz bereitstellen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Zur Webbenutzerschnittstelle navigieren](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
