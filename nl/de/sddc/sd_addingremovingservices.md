---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen

Sie können Services für Ihre VMware Cloud Foundation-Instanzen bestellen, beispielsweise eine Disaster-Recovery-Lösung. Sobald Sie diese Services nicht mehr benötigen, können Sie sie aus Ihren Instanzen entfernen.

## Verfügbare Services für Cloud Foundation-Instanzen

In der folgenden Tabelle sind die Services aufgeführt, die für Cloud Foundation-Instanzen verfügbar sind.

Tabelle 1. Verfügbare Services für Cloud Foundation-Instanzen

| Servicename | Verfügbarkeit | Unterstützte Instanzen |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](../services/f5_considerations.html)                                 | Ja | V1.9 und höher |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html)       | Ja | V1.8 und höher |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | Ja | V2.0 und höher |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | Ja | V2.3 und höher |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | Ja | V2.3 und höher |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)         | Ja | V2.2 und höher |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  | Ja | V2.2 und höher |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                          | Ja | V1.8 und höher |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)                         | Nein | Nicht zutreffend |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                 | Ja | V1.2 und höher |

## Services zu Cloud Foundation-Instanzen hinzufügen

Klicken Sie zum Hinzufügen eines Service zu Ihrer Cloud Foundation-Instanz auf den entsprechenden Service-Link in der vorherigen Tabelle, um die Hinweise zu dem Service zu prüfen und die bereitgestellten Komponenten zu überprüfen. Befolgen Sie anschließend die Anweisungen im Abschnitt zum Bestellen von Services, um den Service Ihrer Instanz hinzuzufügen.

### Ergebnisse der Serviceinstallation

Nachdem die Installation des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird auf der Seite **Services** der Instanz mit dem Status **Installiert** angezeigt.

## Services für Cloud Foundation-Instanzen anzeigen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die Sie Services anzeigen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Klicken Sie auf der Seite **Services** auf einen Service, um die zugehörigen Informationen, beispielsweise den Servicestatus und andere Details, zu prüfen.
5. Je nach dem angezeigten Service können Sie über die in den Servicedetails bereitgestellten Berechtigungsnachweise auf die Servicekonsolen zugreifen und den Service von hier aus verwalten.

## Services für Cloud Foundation-Instanzen entfernen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die Sie Services entfernen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Suchen Sie auf der Seite **Services** die Serviceinstanz, die entfernt werden soll, und klicken Sie anschließend auf das Symbol **Löschen**.
5. Prüfen Sie die gegebenenfalls im Fenster **Service löschen** angezeigten Hinweise oder Warnungen. Wählen Sie **Zur Kenntnis genommen** aus und klicken Sie auf **Löschen**.

### Ergebnisse der Servicelöschung

Nachdem Ihre Anforderung zum Entfernen des Service akzeptiert wurde, ändert sich der Servicestatus in **Wird entfernt**.

Nachdem die Entfernung des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird von der Seite **Services** der Instanz entfernt.

**Achtung** Die entfernten Services werden Ihnen bis zum Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus berechnet.

### Zugehörige Links

* [Häufig gestellte Fragen](../vmonic/faq.html)
