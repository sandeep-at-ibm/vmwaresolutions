---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations}

Der Service "FortiGate Security Appliance on {{site.data.keyword.cloud}}" stellt ein Paar von Einheiten der FortiGate Security Appliance (FSA) 300-Serie in einem Hochverfügbarkeitsmodus bereit, um Firewall-, Routing-, NAT- und VPN-Services für den Schutz aller Server und virtuellen Maschinen im öffentlichen VLAN Ihrer Instanzen zur Verfügung zu stellen.

Zur Verwaltung dieses Service können Sie FortiOS Web Client oder die Befehlszeilenschnittstelle über SSH verwenden.

Dieser Service ist nur für Instanzen verfügbar, die in V1.8 und höheren Releases bereitgestellt werden.
{:note}

## Technische Spezifikationen für FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-specs}

Mit dem Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### Hardware
{: #fsa_considerations-hardware}

Die FortiGate 300 Series Security Appliance.

### Hochverfügbarkeit
{: #fsa_considerations-ha}

Zwei Appliances werden in einer Aktiv/Passiv-Konfiguration bereitgestellt.

### Vernetzung
{: #fsa_considerations-networking}

* Dual 1 GbE (mit Bonding) für vorgelagerte und nachgelagerte Netze
* 1 neues vorgelagertes öffentliches {{site.data.keyword.cloud_notm}}-VLAN
* 1 vorhandenes nachgelagertes öffentliches {{site.data.keyword.cloud_notm}}-VLAN

## Wichtige Hinweise zur Installation von FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-install}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" installieren:
* Stellen Sie sicher, dass das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, über die Berechtigung **Hardware Firewall** verfügt. Diese Berechtigung ist erforderlich, um die Firewallprotokolle und -einstellungen des Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" Ihrer Instanz anzuzeigen und zu bearbeiten.
* Wenn Sie den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" zu einer bereitgestellten Instanz hinzufügen wollen, müssen Sie sicherstellen, dass noch keine andere Firewall aus der {{site.data.keyword.cloud_notm}}-Infrastruktur im öffentlichen VLAN der Instanz vorhanden ist.
* Bei der Installation des Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" wird ein neues öffentliches VLAN hinzugefügt.
* Während der Servicebereitstellung kann Ihre Instanz möglicherweise vorübergehend nicht auf das Internet zugreifen.
* Nachdem der Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" erfolgreich installiert wurde, können Sie Firewallregeln für FSA über die FortiGate-Konsole verwalten und konfigurieren. Sie müssen sicherstellen, dass die FSA-Firewallregeln definiert sind, um abgehende HTTPS-Übertragungen (TCP-Port 443) zu ermöglichen, die von Managementkomponenten wie Zerto Virtual Manager gestartet werden, um mit der externen Managementdatenbank in {{site.data.keyword.cloud_notm}} über das internet zu kommunizieren. Die abgehende HTTPS-Kommunikation (TCP-Port 443) stammt aus der öffentlichen IP-Adresse der Management-Services für VMware NSX Edge Services Gateway (ESG) in Ihrer Instanz.
* Sie müssen die FortiGate Security Appliance-Konfiguration sorgfältig verwalten, damit nur die erforderliche Kommunikation zulässig ist und jede andere Kommunikation zurückgewiesen wird.
* Wenn Sie zusätzliche Cluster bestellen, enthalten die öffentlichen VLANs für diese neu hinzugefügten Cluster nicht das Hochverfügbarkeitspaar von Security Appliances.

## Hinweise zum Entfernen von FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-remove}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" entfernen:
* Beim Entfernen des Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" wird das hinzugefügte öffentliche VLAN entfernt.
* Während des Entfernens des Service kann Ihre Instanz möglicherweise vorübergehend nicht auf das Internet zugreifen.
* Alle FortiGate-Regeln für das Zulassen, Untersuchen, Sperren und Weiterleiten von NAT-Datenverkehr werden zusammen mit dem Fortinet-Service entfernt. Falls Sie NAT-Regeln verwendet haben, müssen Sie diese neu konfigurieren.

## Zugehörige Links
{: #fsa_considerations-related}

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet-Website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
