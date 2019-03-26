---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 on IBM Cloud bestellen
{: #f5_ordering}

Sie können den Service "F5 on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## F5 on IBM Cloud für eine neue Instanz bestellen
{: #f5_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit F5 on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz von der {{site.data.keyword.vmwaresolutions_short}}-Konsole **F5 on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **F5 on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## F5 on IBM Cloud für eine vorhandene Instanz bestellen
{: #f5_ordering-existing}

Sie können den Service "F5 on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **F5 on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## F5 on IBM Cloud - Servicekonfiguration
{: #f5_ordering-config}

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### Verbindung zu F5-Lizenzaktivierung
{: #f5_ordering-config-license}

Wählen Sie **Öffentliches Netz** oder **Privates Netz** für die Lizenzaktivierung aus. Wenn der Zielcluster nur mit privaten Netzschnittstellen konfiguriert ist, ist nur die Option **Privates Netz** verfügbar. Diese Auswahl bestimmt, wie die virtuellen F5-Server eine Verbindung zum F5-Lizenzserver herstellen, und sie wirkt sich nicht auf die Workloaddatenebene aus.

Bei Auswahl von **Privates Netz** müssen Sie folgende Einstellungen vornehmen:
* **Proxy-IP-Adresse**: Die IPv4-Adresse des Proxy-Servers.
* **Proxy-Portnummer**: Die Portnummer des Proxy-Servers, normalerweise 8080 oder 3128.

Ein authentifizierter Proxy wird nicht unterstützt.
{:note}

### Name
{: #f5_ordering-config-name}

Geben Sie den Servicenamen ein.

### Maximale Bandbreite
{: #f5_ordering-config-bandwidth}

Geben Sie den maximalen Durchsatz der F5 BIG-IP-Appliance an.

### Lizenzmodell
{: #f5_ordering-config-license-model}

Das Lizenzmodell für den Service "F5 on {{site.data.keyword.cloud_notm}}" bietet die folgenden Optionen:
<dl class="dl">
        <dt class="dt dlterm">Gut</dt>
        <dd class="dd">Dieses Angebot nutzt den als Vollproxy-Architektur betriebenen BIG-IP Local Traffic Manager™ (LTM) VE, um ein intelligentes lokales Datenverkehrsmanagement, die Sichtbarkeit des gesamten SSL-Datenverkehrs sowie Analyse und Zustandsüberwachung bereitzustellen, um sicherzustellen, dass die Anwendungsserver jederzeit für Ihre Benutzer verfügbar sind.</dd>
        <dt class="dt dlterm">Besser</dt>
        <dd class="dd">Dieses Angebot ergänzt die Option **Gut** durch Module für BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM) und BIG-IP Application Acceleration Manager™ (AAM). Es stellt Services für das globale Datenverkehrsmanagement, eine Optimierung der Anwendungsleistung sowie erweiterte Funktionalität für Netzfirewalls und Entschärfung von DDoS-Attacken (Distributed Denial of Service) bereit.</dd>
        <dt class="dt dlterm">Optimal</dt>
        <dd class="dd">Dieses Angebot ergänzt die Optionen **Gut** und **Besser** durch BIG-IP Application Security Manager™ (ASM) mit einem umfassenden Anwendungsschutz vor L7 DDoS-Attacken und durch Open Web Application Security Project (OWASP) mit einem Schutz vor den 10 wichtigsten Sicherheitsbedrohungen und allgemeinen Anwendungssicherheitslücken. Durch die Einbindung von Funktionen wie Single Sign-on und Mehrfaktorauthentifizierung ermöglicht BIG-IP Access Policy Manager™ (APM) Benutzern einen sicheren und einfachen Zugriff auf Anwendungen, die sich an einer beliebigen Stelle in Mehrcloudumgebungen befinden können.</dd>
</dl>

Sie können das Lizenzmodell nach der Serviceinstallation nicht mehr ändern. Wenn Sie das Lizenzmodell ändern möchten, müssen Sie den vorhandenen Service entfernen und den Service mit einem anderen Lizenzmodell erneut installieren.
{:important}

## Zugehörige Links
{: #f5_ordering-releated}

* [F5 on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [F5 on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
