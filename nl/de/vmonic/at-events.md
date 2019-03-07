---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-14"

---

# Activity Tracker-Ereignisse
{: #at-events}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um zu verfolgen, wie Benutzer und Anwendungen mit {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.Bluemix_notm}} interagieren.

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service zeichnet benutzerinitiierte Aktivitäten auf, die den Status eines Service in {{site.data.keyword.Bluemix_notm}} ändern. Weitere Informationen finden Sie unter [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla).

## Activity Tracker-Ereignistabelle
{: #at-events-table}

Überprüfen Sie die folgende Tabelle auf die Beschreibung der Spalten in der Activity Tracker-Ereignistabelle.

Tabelle 1. Beschreibung der Activity Tracker-Ereignistabelle

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

Weitere Informationen finden Sie unter [Activity Tracker-Ereignisfelder](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event).

## Instanz-Managementereignisse verfolgen
{: #at-events-instance-mgmt}

Wenn Sie Benutzerkonten, Instanzen, Cluster und Services in {{site.data.keyword.vmwaresolutions_short}} verwalten, wird ein Ereignis generiert und an die **Kontodomäne** in Activity Tracker gesendet.

Überprüfen Sie die folgende Tabelle auf die Aktionen, die Managementereignisse generieren und an Activity Tracker senden.

Tabelle 2. Beschreibung von Aktionen, die Managementereignisse generieren

| Aktion                                   | Beschreibung | Ergebnis |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>Die Anforderung zum Aktualisieren des Benutzerkontos wird empfangen.</li><li>Die Anforderung zum Aktualisieren des Benutzerkontos wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>Die Anforderung zum Aktualisieren von Benachrichtigungen wird empfangen.</li><li>Die Anforderung zum Aktualisieren von Benachrichtigungen wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>Die Anforderung zum Bereinigen von gesicherten Daten wird empfangen.</li><li>Die Anforderung zum Bereinigen von gesicherten Daten wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>Die Anforderung zum Migrieren auf ein bss-Konto wird empfangen.</li><li>Die Anforderung zum Migrieren auf ein bss-Konto wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.order`                 | <ul><li>Die Anforderung zum Bestellen einer Cloud Foundation-Instanz wird empfangen.</li><li>Die Anforderung zum Bestellen einer Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>Die Anforderung zum Löschen einer Cloud Foundation-Instanz wird empfangen.</li><li>Die Anforderung zum Löschen einer Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>Die Anforderung zum Hinzufügen von ESXi-Servern zu einer Cloud Foundation-Instanz wird empfangen.</li><li>Die Anforderung zum Hinzufügen von ESXi-Servern zu einer Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>Die Anforderung zum Löschen von ESXi-Servern aus einer Cloud Foundation-Instanz wird empfangen.</li><li>Die Anforderung zum Löschen von ESXi-Servern aus einer Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>Die Anforderung zum Erstellen eines Clusters für eine Cloud Foundation-Instanz wird empfangen.</li> <li>Die Anforderung zum Erstellen eines Clusters für eine Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>Die Anforderung zum Löschen eines Clusters aus einer Cloud Foundation-Instanz wird empfangen.</li><li>Die Anforderung zum Löschen eines Clusters aus einer Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>Die Anforderung zum Planen einer Aktualisierung für eine Cloud Foundation-Instanz wird empfangen.</li><li>Die Anforderung zum Planen einer Aktualisierung für eine Cloud Foundation-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>Die Anforderung zum Bestellen einer vCenter Server-Instanz wird empfangen.</li><li>Die Anforderung zum Bestellen einer vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>Die Anforderung zum Löschen einer vCenter Server-Instanz wird empfangen.</li><li>Die Anforderung zum Löschen einer vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>Die Anforderung zum Hinzufügen von ESXi-Servern zu einer vCenter Server-Instanz wird empfangen.</li><li>Die Anforderung zum Hinzufügen von ESXi-Servern zu einer vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>Die Anforderung zum Löschen von ESXi-Servern von einer vCenter Server-Instanz wird empfangen.</li><li>Die Anforderung zum Löschen von ESXi-Servern von einer vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>Die Anforderung zum Planen einer Aktualisierung für eine vCenter Server-Instanz wird empfangen.</li><li>Die Anforderung zum Planen einer Aktualisierung für eine vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>Die Anforderung zum Erstellen eines Clusters für eine vCenter Server-Instanz wird empfangen.</li><li>Die Anforderung zum Erstellen eines Clusters für eine vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>Die Anforderung zum Löschen eines Clusters aus einer vCenter Server-Instanz wird empfangen.</li> <li>Die Anforderung zum Löschen eines Clusters aus einer vCenter Server-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>Die Anforderung zum Aktualisieren der VMware NSX-Lizenz wird empfangen.</li><li>Die Anforderung zum Aktualisieren der VMware NSX-Lizenz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>Die Anforderung für ein Upgrade einer vCenter Server-Instsanz mit Hybridity Bundle-Instanz wird empfangen.</li><li>Die Anforderung für ein Upgrade einer vCenter Server-Instsanz mit Hybridity Bundle-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>Die Anforderung zum Bestellen eines vSphere-Clusters wird empfangen.</li><li>Die Anforderung zum Bestellen eines vSphere-Clusters wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>Die Anforderung zum Aktualisieren eines vSphere-Clusters wird empfangen.</li><li>Die Anforderung zum Aktualisieren eines vSphere-Clusters wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>Die Anforderung zum Speichern eines vSphere-Clusters wird empfangen.</li><li>Die Anforderung zum Speichern eines vSphere-Clusters wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>Die Anforderung zum Bestellen einer NetApp ONTAP Select-Instanz wird empfangen.</li><li>Die Anforderung zum Bestellen einer NetApp ONTAP Select-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>Die Anforderung zum Löschen einer NetApp ONTAP Select-Instanz wird empfangen.</li><li>Die Anforderung zum Löschen einer NetApp ONTAP Select-Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>Die Anforderung zum Aktualisieren der Konfiguration eines Service wird empfangen.</li><li>Die Anforderung zum Aktualisieren der Konfiguration eines Service wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>Die Anforderung, einen Service für eine Instanz zu bestellen, wird empfangen.</li><li>Die Anforderung, einen Service für eine Instanz zu bestellen, wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>Die Anforderung zum Löschen eines Service aus einer Instanz wird empfangen.</li><li>Die Anforderung zum Löschen eines Service aus einer Instanz wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>Die Anforderung, ein Upgrade einer vorhandenen vCenter Server-Instanz auf einen vCenter Server mit Hybridity Bundle-Instanz durchzuführen, wird empfangen.</li><li>Die Anforderung, ein Upgrade einer vorhandenen vCenter Server-Instanz auf einen vCenter Server mit Hybridity Bundle-Instanz durchzuführen, wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.service.deploy` | Die Aktion zum Implementieren eines Service für eine Instanz wird ausgeführt. | `erfolgreich` |
| `vmware-solutions.service.undeploy` | Die Aktion zum Entfernen eines Service aus einer Instanz wird ausgeführt. | `erfolgreich` |

## Ereignisse für den Service "KMIP for VMware on IBM Cloud" verfolgen
{: #at-events-kmip}

Wenn Sie Schlüssel für den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" verwalten, wird ein Ereignis generiert und an die **Kontodomäne** in Activity Tracker gesendet.

Überprüfen Sie die folgende Tabelle auf die Aktionen, die Ereignisse für den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" generieren und senden.

Tabelle 3. Beschreibung der Aktionen, die Ereignisse für den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" generieren

| Aktion                                      | Beschreibung                               | Ergebnis |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>Die Anforderung zum Erstellen eines Schlüssels wird empfangen.</li><li>Die Anforderung zum Erstellen eines Schlüssels wird beantwortet.</li></ul> | <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>Die Anforderung zum Abrufen des Inhalts eines Schlüssels wird empfangen.</li><li>Die Anforderung zum Abrufen des Inhalts eines Schlüssels wird beantwortet.</li></ul> |  <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>Die Anforderung zum Abrufen der Attribute eines Schlüssels wird empfangen.</li><li>Die Anforderung zum Abrufen der Attribute eines Schlüssels wird beantwortet.</li></ul> |  <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>Die Anforderung zum Aktivieren eines Schlüssels wird empfangen.</li><li>Die Anforderung zum Aktivieren eines Schlüssels wird beantwortet.</li></ul> |  <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>Die Anforderung zum Widerrufen eines Schlüssels wird empfangen.</li><li>Die Anforderung zum Widerrufen eines Schlüssels wird beantwortet.</li></ul> |  <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>Die Anforderung zum Löschen eines Schlüssels wird empfangen.</li><li>Die Anforderung zum Löschen eines Schlüssels wird beantwortet.</li></ul> |  <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>Die Anforderung zum Suchen der Version des KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service wird empfangen.</li><li>Die Anforderung zum Suchen der Version des KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service wird beantwortet.</li></ul> |  <ul><li>`anstehend`</li><li>`erfolgreich` oder `fehlgeschlagen`</li></ul> |

## Ort zum Anzeigen der Ereignisse
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der {{site.data.keyword.cloudaccesstrailshort}} **Kontodomäne** verfügbar, die ihrerseits in der {{site.data.keyword.Bluemix_notm}}-Region verfügbar ist, in der die Ereignisse generiert werden.

## Zugehörige Links
{: #at-events-related}

* [Activity Tracker bereitstellen](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [Zum Activity Tracker-Dashboard in der {{site.data.keyword.cloud_notm}}-Konsole navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
