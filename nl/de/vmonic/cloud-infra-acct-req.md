---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

keywords: user account, user permissions, VRF account

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Anforderungen für das IBM Cloud-Infrastrukturkonto
{: #cloud-infra-acct-req}

Um {{site.data.keyword.vmwaresolutions_full}} für die Bestellung von Instanzen verwenden zu können, müssen Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur besitzen. Die Kosten der Komponenten, die in Ihren Instanzen bestellt werden, werden diesem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt.

## Berechtigungen für das IBM Cloud-Infrastrukturkonto
{: #cloud-infra-acct-req-permissions}

Das von Ihnen verwendete {{site.data.keyword.cloud_notm}}-Infrastrukturkonto muss bestimmte Berechtigungen besitzen, damit in Ihrem Namen die Komponenten in Ihren Instanzen bestellt und Operationen ausgeführt werden können. Die Berechtigungsanforderungen gelten für alle Typen von Instanzen und Services, die Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen.

Berechtigte Benutzer können die Berechtigungen für ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto im {{site.data.keyword.slportal}} prüfen und aktualisieren. Weitere Informationen hierzu finden Sie im Abschnitt [Kundenportalberechtigungen eines Benutzers bearbeiten](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}.

Tabelle 1. Erforderliche Berechtigungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto

| Berechtigung         | Details                                 |
|:------------------ |:--------------------------------------- |
| Server hinzufügen | Diese Berechtigung ist für die folgenden Operationen erforderlich: {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen bestellen, auf denen VMware ESXi ausgeführt wird, und stündlich virtuelle Server bereitstellen, die für Operationen zur Konfiguration, zur Verwaltung und zum Support für Instanzen verwendet werden. |
| Server stornieren | Diese Berechtigung ist erforderlich, um {{site.data.keyword.baremetal_short}}-Instanzen, auf denen VMware ESXi ausgeführt wird, freizugeben und zurückzufordern. Wenn Sie Ihre Instanz löschen, werden die bestellten Komponenten automatisch in der richtigen Abhängigkeitsfolge freigegeben. |
| Virtual Server-Details anzeigen | Diese Berechtigung ist erforderlich, um die Details für die Servereinrichtung abzurufen, die für die Validierung der Bestellung und die automatisierte Konfiguration benötigt werden. |
| Speicher hinzufügen | Diese Berechtigung ist erforderlich, um den Sicherungsspeicher und den gemeinsam genutzten Speicher für die Instanz zu bestellen. |
| Speicher verwalten | Diese Berechtigung ist erforderlich, um den Sicherungsspeicher und den gemeinsam genutzten Speicher für die Instanz zu verwalten. |
| Hardware Firewall | Diese Berechtigung ist erforderlich, um die Firewallprotokolldateien und -einstellungen des Service "Fortinet on {{site.data.keyword.cloud_notm}}" anzuzeigen und zu bearbeiten, wenn dieser Service in Ihrer Instanz installiert ist. |
| Rechenressourcen mit öffentlichem Netzport hinzufügen | Diese Berechtigung ist erforderlich, um Hardware und Virtual Server-Instanzen (VSIs) mit öffentlichen Netzports zu bestellen. |
| IP-Adressen hinzufügen | Diese Berechtigung ist erforderlich, um portierbare private Teilnetzbereiche in Ihrem Namen zu bestellen, die für das Management der in einem vSphere-Cluster ausgeführten virtuellen Maschinen benötigt werden. Sobald Sie weitere Services zu Ihrer Instanz hinzufügen, werden die portierbaren privaten IP-Adressen zu VMware ESXi-Servern zugeordnet, um Bandbreite zu isolieren und zuzuordnen. |
| Tickets hinzufügen | Diese Berechtigung ist erforderlich, um Service-Tickets in Ihrem Namen zu öffnen. Tickets können für die folgenden Operationen erstellt werden: Einleitung von Wiederherstellungsoperationen und automatische Einleitung von Problemlösungsprozessen bei der Feststellung von Problemen. |
| Tickets bearbeiten | Diese Berechtigung ist erforderlich, um die Service-Tickets zu bearbeiten, die in Ihrem Namen erstellt wurden. |
| Tickets anzeigen | Diese Berechtigung ist erforderlich, um die Service-Tickets zu überwachen, die sich bei Verzögerungen und Problemen hinsichtlich der {{site.data.keyword.cloud_notm}}-Infrastrukturbereitstellung auf die Komponenten in Ihrer Instanz beziehen. |
| Hardwaredetails anzeigen | Diese Berechtigung ist erforderlich, um die Hardwaredetails abzurufen, die für die Validierung der Bestellung und die automatisierte Konfiguration benötigt werden. |
| Warmstart/Steuerung | Diese Berechtigung ist erforderlich, um die Hardware während des Löschvorgangs für die Hardware auszuschalten, wenn Sie eine Instanz löschen. |
| Lizenzen anzeigen | Diese Berechtigung ist erforderlich, um die Lizenzen abzurufen und zu validieren, die von Ihrer Instanz verwendet werden. |
| Kennwörter anzeigen | Diese Berechtigung ist erforderlich, um die bestellten VSIs zu verwalten. |
| Serverüberwachung verwalten | Diese Berechtigung ist nicht erforderlich, um eine Bestellung aufzugeben, sie wird jedoch benötigt, um den Überwachungsstatus der {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen abzurufen und zu validieren, auf denen die VMware ESXi-Server in Ihrer Instanz ausgeführt werden. |

## VRF mit aktivierten Serviceendpunkten
{: #cloud-infra-acct-req-vrf-se}

Bei Ihrem {{site.data.keyword.cloud_notm}}-Infrastrukturkonto muss es sich um ein VRF-Konto (Virtual Routing and Forwarding) handeln. Wenn Ihr Konto kein VRF-Konto ist, müssen Sie es in ein VRF-Konto konvertieren. Darüber hinaus ist es empfehlenswert, Ihr VRF-Konto für die Verwendung von Serviceendpunkten zu aktivieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Übersicht über VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Konto für die Verwendung von Serviceendpunkten aktivieren](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## Zugehörige Links
{: #cloud-infra-acct-req-related}

* [Voraussetzungen für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Benutzerkonten und -einstellungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [Übersicht über VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
