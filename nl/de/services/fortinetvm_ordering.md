---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance on IBM Cloud bestellen
{: #fortinetvm_ordering}

Sie können den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## FortiGate Virtual Appliance on IBM Cloud für eine neue Instanz bestellen
{: #fortinetvm_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole **FortiGate Virtual Appliance on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **FortiGate Virtual Appliance on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## FortiGate Virtual Appliance on IBM Cloud für eine vorhandene Instanz bestellen
{: #fortinetvm_ordering-existing}

Sie können den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **FortiGate Virtual Appliance on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## FortiGate Virtual Appliance on IBM Cloud - Servicekonfiguration
{: #fortinetvm_ordering-config}

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### FortiGuard-Netzverbindung
{: #fortinetvm_ordering-config-network-connect}

Wählen Sie **Öffentliches Netz** oder **Privates Netz** für FortiGuard aus. Wenn der Zielcluster nur mit privaten Netzschnittstellen konfiguriert ist, ist nur die Option **Privates Netz** verfügbar. Diese Auswahl bestimmt, wie FortiGuard eine Verbindung zum Fortinet-Lizenzserver herstellt, um die Lizenz zu aktivieren und die Sicherheitspatches herunterzuladen, und wirkt sich nicht auf die Workloaddatenebene aus.

Bei Auswahl von **Privates Netz** müssen Sie folgende Einstellungen angeben:
* **Proxy-IP-Adresse**: Die IPv4-Adresse des Proxy-Servers.
* **Proxy-Portnummer**: Die Portnummer des Proxy-Servers, normalerweise 8080 oder 3128.
* **Proxy-Benutzername**: Wenn Sie eine Proxy-Authentifizierung benötigen, geben Sie den Benutzernamen des Proxy-Servers ein.
* **Proxy-Kennwort**: Wenn Sie eine Proxy-Authentifizierung benötigen, geben Sie das Kennwort des Proxy-Servers ein.

### Name
{: #fortinetvm_ordering-config-name}

Geben Sie den Servicenamen ein.

### Bereitstellungsgröße
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}} stellt die folgenden Optionen für die Bereitstellungsgröße zur Verfügung:
* S (Klein): 2 vCPUs / 4 GB RAM
* M (Mittel): 4 vCPUs / 6 GB RAM
* L (Groß): 8 vCPUs / 12 GB RAM

### Lizenzmodell
{: #fortinetvm_ordering-config-license}

Das Lizenzmodell für FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bietet die folgenden Optionen:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Dieses Produktpaket beinhaltet Paketprüfung mit Zustandsüberwachung, VLAN-Schutz und erweiterte Protokollierung, Regeln für Firewalleingang/-ausgang, SSL/IPSec-VPN-Beendigung sowie 24x7-Support.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Dieses Bundle enthält alle Standard-Firewall-Services zusätzlich zum Services Advanced Malware Protection (AMP)-Service. Enthalten sind Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service und Content Disarm & Reconstruct. Zudem umfasst es die Services Web Filterung, IPS, Antispam, Application Control und FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Dieses Bundle enthält alle Standard-Firewall- und UTM-Services zusätzlich zu folgenden Services:<ul><li>Cloud Access Security Broker (CASB) - Dieser Service bietet Transparenz, Konformität, Datensicherheit und Schutz vor Bedrohungen für cloudbasierte Services.</li><li>Industrial Security - Dieser Service stellt Signaturen für gängige ICS/SCADA-Protokolle bereit.</li><li>Security Rating- Dieser Service stellt Prüffunktionen zur Erkennung von kritischen Sicherheitslücken und Konfigurationsschwachstellen sowie zur Implementierung von Best-Practice-Empfehlungen zur Verfügung.</li></ul></dd>
</dl>

Im 3. Quartal 2018 hat Fortinet drei neue Services (CASB, Industrial Security und Security Rating) in sein Enterprise-Bundle aufgenommen. Diese Services sind nur auf FortiGate 6.0 verfügbar.
{:note}

Sie können das Lizenzmodell nach der Serviceinstallation nicht mehr ändern. Wenn Sie das Lizenzmodell ändern möchten, müssen Sie den vorhandenen Service entfernen und ihn mit einer anderen Lizenzoption erneut installieren.
{:important}

## Zugehörige Links
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet-Website](https://www.fortinet.com/){:new_window}
* [Dokumentbibliothek zu Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:new_window}
