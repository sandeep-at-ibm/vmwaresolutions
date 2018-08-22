---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# F5 on IBM Cloud bestellen

Sie können den Service "F5 on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz mit enthaltener BIG-IP Virtual Edition (VE) oder durch Hinzufügen von BIG-IP VE zu Ihrer vorhandenen Instanz bestellen.

## F5 on IBM Cloud für eine neue Instanz bestellen

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit F5 on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz von der {{site.data.keyword.vmwaresolutions_short}}-Konsole **F5 on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **F5 on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## F5 on IBM Cloud für eine vorhandene Instanz bestellen

Sie können den Service "F5 on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **F5 on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## F5 on IBM Cloud - Servicekonfiguration

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### Name

Geben Sie den Servicenamen ein.

### Lizenzmodell

Das Lizenzmodell für den Service "F5 on {{site.data.keyword.cloud_notm}}" bietet die folgenden Optionen:
<dl class="dl">
        <dt class="dt dlterm">Gut</dt>
        <dd class="dd">Dieses Angebot nutzt den als Vollproxyarchitektur betriebenen BIG-IP Local Traffic Manager™ (LTM) VE, um ein intelligentes lokales Datenverkehrsmanagement, die Sichtbarkeit des gesamten SSL-Datenverkehrs sowie Analyse und Zustandsüberwachung bereitzustellen, damit Anwendungsserver jederzeit für Ihre Benutzer verfügbar sind.</dd>
        <dt class="dt dlterm">Besser</dt>
        <dd class="dd">Dieses Angebot ergänzt die Option **Gut** durch Module für BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM) und BIG-IP Application Acceleration Manager™ (AAM). Es stellt Services für das globale Datenverkehrsmanagement, eine Optimierung der Anwendungsleistung sowie erweiterte Funktionalität für Netzfirewalls und Entschärfung von DDoS-Attacken (Distributed Denial of Service) bereit.</dd>
        <dt class="dt dlterm">Optimal</dt>
        <dd class="dd">Dieses Angebot ergänzt die Optionen **Gut** und **Besser** durch BIG-IP Application Security Manager™ (ASM) mit einem umfassenden Anwendungsschutz vor L7 DDoS-Attacken und durch Open Web Application Security Project (OWASP) mit einem Schutz vor den 10 wichtigsten Sicherheitsbedrohungen und allgemeinen Anwendungssicherheitslücken. Durch die Einbindung von Funktionen wie Single Sign-on und Mehrfaktorauthentifizierung ermöglicht BIG-IP Access Policy Manager™ (APM) Benutzern einen sicheren und einfachen Zugriff auf Anwendungen, die sich an einer beliebigen Stelle in Mehrcloudumgebungen befinden können.</dd>
</dl>

**Wichtig**: Nach der Installation des Service kann das Lizenzmodell nicht mehr geändert werden. Wenn Sie das Lizenzmodell ändern möchten, müssen Sie den vorhandenen Service entfernen und den Service mit einem anderen Lizenzmodell erneut installieren.

### Maximale Bandbreite

Geben Sie den maximalen Durchsatz der F5 BIG–IP-Appliance an.

### Zugehörige Links

* [Übersicht über F5 on {{site.data.keyword.cloud_notm}}](f5_considerations.html)
* [F5 on {{site.data.keyword.cloud_notm}} verwalten](managing_f5.html)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](../sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_addingremovingservices.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_hybrid_addingremovingservices.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
