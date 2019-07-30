---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# IBM Cloud Private Hosted bestellen
{: #icp_ordering}

Sie können den Service "{{site.data.keyword.cloud}} Private Hosted" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## IBM Cloud Private Hosted für eine neue Instanz bestellen
{: #icp_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit dem enthaltenen Service "{{site.data.keyword.cloud_notm}} Private Hosted" bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz von der {{site.data.keyword.vmwaresolutions_short}}-Konsole **IBM Cloud Private Hosted** im Abschnitt **Optionale Services** aus.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **IBM Cloud Private Hosted**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## IBM Cloud Private Hosted für eine vorhandene Instanz bestellen
{: #icp_ordering-existing}

Sie können den Service "{{site.data.keyword.cloud_notm}} Private Hosted" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **IBM Cloud Private Hosted**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## Konfiguration des IBM Cloud Private Hosted-Service
{: #icp_ordering-config}

Geben Sie beim Bestellen des Service die folgenden Einstellungen an:
* Wählen Sie **Produktion** oder **Entwicklung/Test** entsprechend Ihren Anforderungen aus.
* Wählen Sie das erforderliche Kontrollkästchen aus, um zu bestätigen, dass Sie bereits über die Lizenz verfügen, die für die Bereitstellung des Service "{{site.data.keyword.cloud_notm}} Private Hosted" erforderlich ist.

## Zusätzliche Knoten bereitstellen
{: #icp_ordering-deploy-nodes}

Wenn Sie zusätzliche Knoten bereitstellen möchten, lesen Sie die folgenden Informationen:
* Verwenden Sie die Ubuntu-Vorlage für {{site.data.keyword.cloud_notm}} Private (Ubuntu1604), die mit der ursprünglichen {{site.data.keyword.cloud_notm}} Private Hosted-Installation bereitgestellt wird.
* Um die Ubuntu-Vorlage zu finden, rufen Sie in VMware vSphere Web Client die Registerkarte **VMs und Vorlagen** unter dem Ordner `cam` auf.
* Das Standardkennwort für die Ubuntu-Vorlage ist `icponcloud`. Es wird empfohlen, dieses Kennwort vor Verwendung der Vorlage zu ändern.
* {{site.data.keyword.vmwaresolutions_short}} bietet keine Unterstützung für die Anwendung von Updates und Patches für die Ubuntu-Vorlage. Sie müssen diese Updates selbst überwachen und anwenden.

## Zugehörige Links
{: #icp_ordering-related}

* [Übersicht über IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
