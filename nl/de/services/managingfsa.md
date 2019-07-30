---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate Security console, FortiGate 300 console, login FortiGate console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Security Appliance on IBM Cloud verwalten
{: #managingfsa}

Nachdem der Service "FortiGate Security Appliance on {{site.data.keyword.cloud}}" erfolgreich installiert wurde, können Sie Firewallregeln für FSA über die FortiGate-Konsole verwalten und konfigurieren.

Sie müssen sicherstellen, dass die FSA-Firewallregeln so definiert sind, dass abgehende HTTPS-Übertragungen (TCP-Port 443) zulässig sind, die von Managementkomponenten wie Zerto Virtual Manager eingeleitet werden, um mit der externen Managementdatenbank in der {{site.data.keyword.cloud_notm}}-Infrastruktur über das Internet zu kommunizieren. Die abgehende HTTPS-Kommunikation (TCP-Port 443) stammt aus der öffentlichen IP-Adresse der Management-Services für VMware NSX Edge Services Gateway (ESG) in Ihrer Instanz.
{:important}

## Auf die Konsole der FortiGate 300-Serie zugreifen
{: #managingfsa-access-console}

Um den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" zu verwalten, müssen Sie auf eine der folgenden Arten auf die Konsole der FortiGate® 300-Serie zugreifen:
* Melden Sie sich beim FortiOS-Web-Client unter Verwendung der Berechtigungsnachweise an, die auf der Seite mit den Details für den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" zu finden sind.
* Greifen Sie über eine SSH-Verbindung unter Verwendung der Berechtigungsnachweise, die auf der Seite mit den Details für den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" zu finden sind, auf die Konsole zu.

Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Zugehörige Links
{: #managingfsa-related}

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Website "fortinet.com"](https://www.fortinet.com/){:external}
* [Dokumentbibliothek für Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:external}
