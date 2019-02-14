---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen

Sie können Services für Ihre VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanzen bestellen, beispielsweise eine Disaster-Recovery-Lösung. Sobald Sie diese Services nicht mehr benötigen, können Sie sie aus Ihrer Instanz entfernen.

## Verfügbare Services für vCenter Server with Hybridity Bundle-Instanzen

In der folgenden Tabelle sind die Services aufgeführt, die für vCenter Server with Hybridity Bundle-Instanzen verfügbar sind, sowie die installierten Serviceversionen.

Tabelle 1. Verfügbare Services für vCenter Server with Hybridity Bundle-Instanzen

| Servicename | Aktuelle Serviceversion | Instanzversion |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_considerations.html)                                 | BIG-IP VE V13.1.1.2 | V1.9 und höher |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fsa_considerations.html)       | 300 Series | V1.8 und höher |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_considerations.html) | 6.0.3 | V2.0 und höher |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html)              | 5.4.0 | V2.3 und höher |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html)              | 4.2.1 | V2.3 und höher |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html)              | 4.2 | V2.5 und höher |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services/icp_overview.html) | 3.1 | V2.7 und höher |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/spp_considerations.html)  | 10.1.2 | V2.2 und höher |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)                  | 2.0  | Nicht zutreffend |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/veeam_considerations.html)                           | 9.5u3 | V1.8 und höher |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/hcx_considerations.html)                        | 3.5.1 | V2.3 und höher |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/addingzertodr.html)                                  | 6.0 Update 3 | V1.2 und höher |

## Vorgehensweise zum Hinzufügen von Services zu vCenter Server with Hybridity Bundle-Instanzen

Klicken Sie zum Hinzufügen eines Service zu Ihrer vCenter Server with Hybridity Bundle-Instanz auf die entsprechenden Links in der Tabelle, um die Hinweise zu dem Service zu prüfen. Überprüfen Sie anschließend die bereitgestellten Komponenten und folgen Sie den Anweisungen in den Abschnitten zum Bestellen, um Ihre Bestellung aufzugeben.

### Ergebnisse der Serviceinstallation

Nachdem die Installation des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird auf der Registerkarte **Services** der Instanzdetails mit dem Status **Installiert** angezeigt.

## Vorgehensweise zum Anzeigen von Services für vCenter Server with Hybridity Bundle-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie Services anzeigen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Klicken Sie auf der Seite **Services** auf einen Service, um die zugehörigen Informationen, beispielsweise den Servicestatus und andere Details, zu prüfen.
5. Je nach dem angezeigten Service können Sie über die in den Servicedetails bereitgestellten Berechtigungsnachweise auf die Servicekonsolen zugreifen und den Service von hier aus verwalten.

## Vorgehensweise zum Entfernen von Services für vCenter Server with Hybridity Bundle-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie Services entfernen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Suchen Sie auf der Seite **Services** die Serviceinstanz, die entfernt werden soll, und klicken Sie anschließend auf das Symbol **Löschen**.
5. Prüfen Sie die gegebenenfalls im Fenster **Service löschen** angezeigten Hinweise oder Warnungen. Wählen Sie **Zur Kenntnis genommen** aus und klicken Sie auf **Löschen**.

### Ergebnisse der Servicelöschung

Nachdem Ihre Anforderung zum Entfernen des Service akzeptiert wurde, ändert sich der Servicestatus in **Wird entfernt**.

Nachdem die Entfernung des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird von der Seite **Services** der Instanz entfernt.

Die entfernten Services werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
{:note}

### Zugehörige Links

* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic/faq.html)
