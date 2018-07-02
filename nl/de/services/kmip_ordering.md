---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# KMIP for VMware on IBM Cloud bestellen

Sie können den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## KMIP for VMware on IBM Cloud für eine neue Instanz bestellen

Sie können mithilfe der folgenden Methoden eine neue Instanz mit KMIP for VMware on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz über die {{site.data.keyword.vmwaresolutions_full}}-Konsole **KMIP for VMware on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## KMIP for VMware on IBM Cloud für eine vorhandene Instanz bestellen

Sie können den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Service hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **KMIP for VMware on IBM Cloud-Service** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## KMIP for VMware on IBM Cloud - Servicekonfiguration

Geben Sie beim Bestellen des Service die folgenden Einstellungen an:

### Serviceregion

Wählen Sie die {{site.data.keyword.cloud_notm}}-Region aus, in der Ihre KMIP for VMware {{site.data.keyword.cloud_notm}}-Serviceinstanz gehostet werden soll.

{{site.data.keyword.cloud_notm}} verwaltet einen hoch verfügbaren Serviceendpunkt für KMIP for VMware on {{site.data.keyword.cloud_notm}} in jeder Region, in der der Service verfügbar ist.

### Client-SSL-Zertifikat

Für vCenter Server müssen Sie einen KMS-Cluster (KMS = Key Management Server) konfigurieren. Der Endpunkt in der ausgewählten Region stellt eine sichere Verbindung zum KMS über das Client-SSL-Zertifikat her. Den Endpunkt für jede Region können Sie der folgenden Tabelle entnehmen. Diese Endpunkte verwenden selbst signierte Zertifikate, die vom {{site.data.keyword.vmwaresolutions_short}}-Team verwaltet werden. Der Fingerabdruck für die Zertifikate ist `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Tabelle 1: Regionen mit Serviceendpunkten für KMIP for VMware on IBM Cloud

| Region         | Endpunkt               |
|:---------------|:-----------------------|
| Sydney         |  `130.198.73.134:5696` |
| Großbritannien |  `158.175.93.122:5696` |
| US South       |  `169.60.185.42:5696`  |

Diese Einstellung ist bei der Erstkonfiguration optional. Sie können dieses Feld zu diesem Zeitpunkt leer lassen, da das Clientzertifikat des KMS in vCenter Server nach der Bereitstellung Ihrer Instanz bekannt ist. Nach der Bereitstellung Ihrer Instanz müssen Sie das Zertifikat allerdings eingeben, damit Ihre vCenter Server-Verbindung zum KMS erfolgreich hergestellt werden kann.

### API-Schlüssel für Service-ID

Geben Sie den API-Schlüssel für die {{site.data.keyword.cloud_notm}}-Service-ID ein, die für den Zugriff auf die IBM Key Protect Service-Instanz verwendet wird.

### Key Protect-Instanz

Klicken Sie auf **Abrufen**, um eine Liste der verfügbaren IBM Key Protect Service-Instanzen abzurufen und wählen Sie dann die Instanz aus, die für das Schlüsselmanagement verwendet werden soll.

### Stammschlüssel für Kunden

Klicken Sie auf **Abrufen**, um den Stammschlüssel des Kunden abzurufen, der in der ausgewählten IBM Key Protect-Instanz gespeichert ist.



## Zugehörige Links

* [Überblick zu KMIP for VMware on IBM Cloud](kmip_considerations.html)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](../sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_addingremovingservices.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
