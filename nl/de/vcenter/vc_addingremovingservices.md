---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen

Sie können Services für Ihre VMware vCenter Server-Instanzen bestellen, beispielsweise eine Disaster-Recovery-Lösung. Sobald Sie diese Services nicht mehr benötigen, können Sie sie aus Ihren Instanzen entfernen.

## Verfügbare Services für vCenter Server-Instanzen

In der folgenden Tabelle sind die Services aufgeführt, die für vCenter Server-Instanzen verfügbar sind.

Tabelle 1. Verfügbare Services für vCenter Server-Instanzen

| Servicename                                                                            | Verfügbarkeit    |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)                                 | Ja              |
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)       | Ja              |
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html) | Ja              |
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)              | Ja              |
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)              | Ja              |
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)         | Ja              |
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)                  | Ja              |
| [Veeam on IBM Cloud](../ services/veeam_considerations.html)                           | Ja              |
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                         | Nein              |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                 | Ja              |


## Services zu vCenter Server-Instanzen hinzufügen

Klicken Sie zum Hinzufügen eines Service zu Ihrer vCenter Server-Instanz auf den entsprechenden Service-Link in der vorherigen Tabelle, um die Hinweise zu dem Service zu prüfen und die bereitgestellten Komponenten zu überprüfen. Befolgen Sie anschließend die Anweisungen im Abschnitt zum Bestellen von Services, um den Service Ihrer Instanz hinzuzufügen.

### Ergebnisse der Serviceinstallation

Nachdem die Installation des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird auf der Seite **Services** der Instanz mit dem Status **Installiert** angezeigt.

## Services für vCenter Server-Instanzen anzeigen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie Services anzeigen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Klicken Sie auf der Seite **Services** auf einen Service, um die zugehörigen Informationen, beispielsweise den Servicestatus und andere Details, zu prüfen.
5. Je nach dem angezeigten Service können Sie über die in den Servicedetails bereitgestellten Berechtigungsnachweise auf die Servicekonsolen zugreifen und den Service von hier aus verwalten.

## Services für vCenter Server-Instanzen entfernen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie Services entfernen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Suchen Sie auf der Seite **Services** die Serviceinstanz, die entfernt werden soll, und klicken Sie anschließend auf das Symbol **Löschen**.
5. Prüfen Sie die gegebenenfalls im Fenster **Service löschen** angezeigten Hinweise oder Warnungen. Wählen Sie **Zur Kenntnis genommen** aus und klicken Sie auf **Löschen**.

### Ergebnisse der Servicelöschung

Nachdem Ihre Anforderung zum Entfernen des Service akzeptiert wurde, ändert sich der Servicestatus in **Wird entfernt**.

Nachdem die Entfernung des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird von der Seite **Services** der Instanz entfernt.

**Achtung** Die entfernten Services werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.

## Zugehörige Links

* [Häufig gestellte Fragen](../vmonic/faq.html)
