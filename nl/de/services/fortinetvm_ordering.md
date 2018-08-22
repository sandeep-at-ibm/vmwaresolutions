---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# FortiGate Virtual Appliance on IBM Cloud bestellen

Sie können den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## FortiGate Virtual Appliance on IBM Cloud für eine neue Instanz bestellen

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole **FortiGate Virtual Appliance on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **FortiGate Virtual Appliance on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## FortiGate Virtual Appliance on IBM Cloud für eine vorhandene Instanz bestellen

Sie können den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **FortiGate Virtual Appliance on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## FortiGate Virtual Appliance on IBM Cloud - Servicekonfiguration

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### Name

Geben Sie den Servicenamen ein.

### Bereitstellungsgröße

{{site.data.keyword.cloud_notm}} stellt die folgenden Optionen für die Bereitstellungsgröße zur Verfügung:
* S (Klein): 2 vCPUs / 4 GB RAM
* M (Mittel): 4 vCPUs / 6 GB RAM
* L (Groß): 8 vCPUs / 12 GB RAM

### Lizenzmodell

Das Lizenzmodell für FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bietet die folgenden Optionen:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Dieses Produktpaket beinhaltet Paketprüfung mit Zustandsüberwachung, VLAN-Schutz und erweiterte Protokollierung, Regeln für Firewalleingang/-ausgang, SSL/IPSec-VPN-Beendigung sowie 24-Stunden-Support an jedem Tag.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Dieses Produktpaket beinhaltet alle Firewall-Services des Pakets "Standard" sowie zusätzlich NGFW-IPS- und Webfilterung, Viren- und Spamschutz, IP- & Domänenreputation und zentrale FortiCare-Sicherheitsservices.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Dieses Produktpaket beinhaltet neben allen Firewall-Services der Pakete "Standard" und "UTM" die FortiSandbox-Sicherheit für Cloud und Mobilgeräte.</dd>
</dl>

**Wichtig**: Nach der Installation des Service kann das Lizenzmodell nicht mehr geändert werden. Wenn Sie das Lizenzmodell ändern möchten, müssen Sie den vorhandenen Service entfernen und ihn mit einer anderen Lizenzoption erneut installieren.

### Zugehörige Links

* [Übersicht über FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_considerations.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} verwalten](managingfortinetvm.html)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](../sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_addingremovingservices.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_hybrid_addingremovingservices.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Fortinet-Website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
