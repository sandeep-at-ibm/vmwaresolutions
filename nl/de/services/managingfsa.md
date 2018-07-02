---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# FortiGate Security Appliance on IBM Cloud verwalten

Nachdem der Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" erfolgreich installiert wurde, können Sie Firewallregeln für FSA über die FortiGate-Konsole verwalten und konfigurieren.

**Wichtig**: Sie müssen sicherstellen, dass die FSA-Firewallregeln so definiert sind, dass abgehende HTTPS-Übertragungen (TCP-Port 443) zulässig sind, die von Managementkomponenten wie der virtuellen Maschine von IBM CloudDriver oder von Zerto Virtual Manager eingeleitet werden, um mit der externen Managementdatenbank in der IBM Cloud-Infrastruktur über das Internet zu kommunizieren. Die abgehende HTTPS-Kommunikation (TCP-Port 443) stammt aus der öffentlichen IP-Adresse der Mangement-Services für VMware NSX Edge Services Gateway (ESG) in Ihrer Instanz.

## Auf die Konsole der FortiGate 300-Serie zugreifen

Um den Service "FortiGate Security Appliance on {{site.data.keyword.cloud}}" zu verwalten, müssen Sie auf eine der folgenden Arten auf die Konsole der FortiGate® 300-Serie zugreifen:
* Melden Sie sich beim FortiOS-Web-Client unter Verwendung der Berechtigungsnachweise an, die auf der Seite mit den Details für den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" zu finden sind.
* Greifen Sie über eine SSH-Verbindung unter Verwendung der Berechtigungsnachweise, die auf der Seite mit den Details für den Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" zu finden sind, auf die Konsole zu.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](../sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_addingremovingservices.html)

## Zugehörige Links

* [Überblick zu FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_considerations.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Website "fortinet.com"](https://www.fortinet.com/)
* [Fortinet technical documentation](http://docs.fortinet.com/fortigate/admin-guides)
