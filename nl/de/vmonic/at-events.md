---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Activity Tracker-Ereignisse
{: #at-events}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um zu verfolgen, wie Benutzer und Anwendungen mit {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}} interagieren.

{{site.data.keyword.at_full_notm}} zeichnet benutzerinitiierte Aktivitäten auf, die den Status eines Service in der {{site.data.keyword.cloud_notm}} ändern. Sie können diesen Service verwenden, um eine abnormale Aktivität und kritische Aktionen zu untersuchen und die regulatorischen Prüfvorschriften zu erfüllen. Darüber hinaus können Sie zeitnah auf ausgeführte Aktionen aufmerksam gemacht werden. Die erfassten Ereignisse entsprechen dem CADF-Standard (Standard Cloud Auditing Data Federation). Weitere Informationen finden Sie unter [{{site.data.keyword.cloud_notm}} Activity Tracker mit LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Instanz-Managementereignisse verfolgen
{: #at-events-instance-mgmt}

Wenn Sie Benutzerkonten, Instanzen, Cluster und Services in {{site.data.keyword.vmwaresolutions_short}} verwalten, wird ein Ereignis generiert und an eine globale Domäne oder an eine Instanz des Service an dem Standort gesendet, an dem der Service bereitgestellt wird. Weitere Informationen finden Sie unter [Globale und standortbezogene Ereignisse überwachen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

Die folgende Tabelle enthält die Aktionen, die Managementereignisse generieren und an Activity Tracker senden.

| Aktion                                   | Beschreibung |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | Der Infrastruktur-API-Schlüssel für ein Konto wird aktualisiert. |
| `vmware-solutions.account-notification.update` | Die Benachrichtigungseinstellung für ein Konto wird aktualisiert. |
| `vmware-solutions.instance-secure-data.wipe` | Die sicheren Daten der Instanz werden gelöscht. |
| `vmware-solutions.instance-bss-account.migrate` |	Eine Instanz wird auf ein BSS-Konto migriert. |
| `vmware-solutions.vcs.create` | Eine vCenter Server-Instanz wird erstellt. |
| `vmware-solutions.vcs.delete` | Eine vCenter Server-Instanz wird gelöscht. |
| `vmware-solutions.vcs-host.add` | Ein Host wird zu einer vCenter Server-Instanz hinzugefügt. |
| `vmware-solutions.vcs-host.remove` | Ein Host wird von einer vCenter Server-Instanz entfernt. |
| `vmware-solutions.vcs.update` | Eine vCenter Server-Instanz wird aktualisiert. |
| `vmware-solutions.vcs-cluster.create` | Für eine vCenter Server-Instanz wird ein Cluster erstellt. |
| `vmware-solutions.vcs-cluster.delete` | Ein Cluster für eine vCenter Server-Instanz wird gelöscht. |
| `vmware-solutions.vcs-nsx-license.update` | Die NSX-Lizenz für eine vCenter Server-Instanz wird aktualisiert. |
| `vmware-solutions.vcs-nfs-storage.add` | NFS-Speicher wird zu einer vCenter Server-Instanz hinzugefügt. |
| `vmware-solutions.vcs-nfs-storage.remove` | NFS-Speicher wird aus einer vCenter Server-Instanz entfernt. |
| `vmware-solutions.vcs-plan.update` | Der Plan einer vCenter Server-Instanz wird aktualisiert. |
| `vmware-solutions.vss.create` | Eine vSphere-Instanz wird erstellt. |
| `vmware-solutions.vss.update` | Eine vSphere-Instanz wird aktualisiert. |
| `vmware-solutions.vss-template.remove` | Eine vSphere-Vorlage wird entfernt. |
| `vmware-solutions.service.create` | Ein Service wird erstellt. |
| `vmware-solutions.service.delete` | Ein Service wird gelöscht. |
{: caption="Tabelle 1. Beschreibung von Aktionen, die Managementereignisse generieren" caption-side="top"}

## Ereignisse für den Service "KMIP for VMware on IBM Cloud" verfolgen
{: #at-events-kmip}

Wenn Sie Schlüssel für den KMIP für VMware on {{site.data.keyword.cloud_notm}}-Service verwalten, wird ein Ereignis generiert und an eine globale Domäne oder an eine Instanz des Service an dem Standort gesendet, an dem der Service bereitgestellt wird. Weitere Informationen finden Sie unter [Globale und standortbezogene Ereignisse überwachen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

Die folgende Tabelle enthält die Aktionen, die Ereignisse für den KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service generieren und senden.

| Aktion                                      | Beschreibung                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | Ein KMIP-Schlüssel wird erstellt. |
| `vmware-solutions.kmip-key.retrieve` | Ein KMIP-Schlüssel wird abgerufen. |
| `vmware-solutions.kmip-key-attributes.retrieve` | Die Attribute eines KMIP-Schlüssels werden abgerufen. |
| `vmware-solutions.kmip-key.activate` | Ein KMIP-Schlüssel wird aktiviert. |
| `vmware-solutions.kmip-key.revoke` | Ein KMIP-Schlüssel wird widerrufen. |
| `vmware-solutions.kmip-key.destroy` | Ein KMIP-Schlüssel wird gelöscht. |
{: caption="Tabelle 2. Beschreibung der Aktionen, die Ereignisse für den KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service generieren" caption-side="top"}

## Ort zum Anzeigen der Ereignisse
{: #at-events-viewing}

Ereignisse sind am Standort **Frankfurt** verfügbar.

Es gibt nur eine {{site.data.keyword.at_full_notm}}-Instanz pro Standort. Zum Anzeigen von Ereignissen müssen Sie auf die Webbenutzerschnittstelle des {{site.data.keyword.at_full_notm}}-Service am Standort **EU-DE** zugreifen. Weitere Informationen finden Sie unter [Webbenutzerschnittstelle über die IBM Cloud-Benutzerschnittstelle starten](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## Zugehörige Links
{: #at-events-related}

* [Instanz bereitstellen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Zur Webbenutzerschnittstelle navigieren](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
