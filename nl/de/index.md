---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Einführung in IBM Cloud for VMware Solutions
{: #getting-started}

In diesem Einführungslerntext für {{site.data.keyword.vmwaresolutions_full}} erfahren Sie, wie Sie eine Instanz sowie verfügbare Add-on-Services für diese Instanz bestellen können.
{:shortdesc}

## Vorbereitende Schritte
{: #getting-started-prereqs}

Informieren Sie sich vor der Arbeit mit {{site.data.keyword.vmwaresolutions_short}} über die folgenden wichtigen Informationen zu Browseranforderungen, Benutzerkonten, Bereitstellungsoptionen und Add-on-Services.

### Browseranforderungen
{: #getting-started-browser-req}

Die folgenden Browser werden unterstützt:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer wird nicht unterstützt.
{:note}

Optimale Anzeige- und Arbeitsbedingungen für die {{site.data.keyword.vmwaresolutions_short}}-Konsole erreichen Sie, indem Sie mindestens eine Bildschirmauflösung von 1024 Pixel Breite mal 500 Pixel Höhe verwenden.

### Benutzerkonten
{: #getting-started-user-accts}

Sie benötigen ein {{site.data.keyword.cloud_notm}}-Konto und ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur. Diese Konten müssen bestimmte Anforderungen erfüllen.

| Konto | Beschreibung |
|:------- |:---------- |
| IBMid | Die **IBMid** ermöglicht es Ihnen, einen einzigen Anmeldebenutzernamen für alle genutzten IBM Produkte und Services, einschließlich {{site.data.keyword.cloud_notm}}, zu verwenden. {{site.data.keyword.vmwaresolutions_short}} wird als Infrastrukturlösung im {{site.data.keyword.cloud_notm}}-Katalog bereitgestellt. Um auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole zugreifen zu können, müssen Sie über eine **IBMid** verfügen.<br><br>Damit Sie Ihre **IBMid** zur Anmeldung bei der Konsole von {{site.data.keyword.vmwaresolutions_short}} verwenden können, müssen Sie die **IBMid** einem {{site.data.keyword.cloud_notm}}-Konto zuordnen. Wenn Sie sich zum ersten Mal bei der Konsole anmelden, müssen Sie entweder Ihre vorhandene **IBMid** einem {{site.data.keyword.cloud_notm}}-Konto zuordnen oder sich für ein neues {{site.data.keyword.cloud_notm}}-Konto registrieren. Das neue {{site.data.keyword.cloud_notm}}-Konto wird dann automatisch Ihrer **IBMid** zugeordnet. Dieses Verfahren müssen Sie nur einmal durchlaufen.<br><br>Wenn Sie Probleme beim Zuordnen Ihrer **IBMid** zu einem {{site.data.keyword.cloud_notm}}-Konto haben, lesen Sie die Informationen im Abschnitt [Fehlerbehebung beim Zugriff auf {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-accessing#accessing). |
| IBM Cloud-Konto | Zum Bestellen und Verwenden von {{site.data.keyword.cloud_notm}}-Services benötigen Sie ein {{site.data.keyword.cloud_notm}}-Konto. Abrechnungsinformationen werden dem {{site.data.keyword.cloud_notm}}-Konto zugeordnet. Die Kosten für die physische und virtuelle Infrastruktur sowie die daraus resultierenden Lizenzen werden Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt. |
| IBM Cloud-Infrastrukturkonto | Informationen zu den Voraussetzungen für ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).<br><br>Sie können Konten für die {{site.data.keyword.cloud_notm}}-Infrastruktur mit {{site.data.keyword.cloud_notm}}-Konten verknüpfen, um kombinierte Infrastructure as a Service-Ressourcen (IaaS) und Platform as a Service-Ressourcen (PaaS) zu nutzen. Anschließend können Sie auf IaaS-Ressourcen und PaaS-Ressourcen über ein und dieselbe Anmeldung zugreifen. Das Verknüpfen Ihrer Konten hat außerdem zur Folge, dass Sie nur eine Rechnung für alle PaaS- und IaaS-Ressourcen erhalten, die Sie nutzen:<br>Wenn Sie kein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur haben, können Sie eines anfordern, indem Sie die unter [Für ein IBM Cloud-Infrastrukturkonto registrieren](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts#signing_required_accounts-infra) beschriebene Prozedur ausführen. Verknüpfen Sie anschließend Ihr Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur mit Ihrem {{site.data.keyword.cloud_notm}}-Konto, indem Sie die unter [Zur IBMid wechseln und Konten verknüpfen](/docs/account?topic=account-unifyingaccounts#unifyingaccounts) beschriebene Prozedur ausführen.<br>Wenn Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur haben, können Sie es mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen, indem Sie die unter [Zur IBMid wechseln und Konten verknüpfen](/docs/account?topic=account-unifyingaccounts#unifyingaccounts) beschriebene Prozedur ausführen.
{: caption="Tabelle 1. Erforderliche Benutzerkonten" caption-side="top"}

### Bereitstellungsangebote
{: #getting-started-depl-offerings}

Wählen Sie nach Durchsicht der folgenden Tabelle das von Ihnen gewünschte Bereitstellungsangebot aus.

| Bereitstellungsangebot | Beschreibung |
|:------------------- |:----------- |
| [VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview) | Mit dem vCenter Server-Produktangebot können Sie eine virtuelle VMware-Umgebung unter Verwendung von angepassten Rechen-, Speicher- und Netzressourcen bereitstellen und so Ihre Geschäftsanforderungen optimal erfüllen.
| [VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview) | Das vCenter Server with Hybridity-Angebot ist eine gehostete private Cloud und unterstützt Sie bei der schnellen und einfachen Erweiterung Ihrer lokalen Infrastruktur in die Cloud. Die VMware-Umgebung basiert auf den von IBM bereitgestellten VMware Software Defined Data Center-Lizenzen und umfasst VMware Hybrid Cloud Extension (HCX). Mithilfe von HCX können Sie eine sichere Verbindung einer lokalen vSphere 5.0+-Umgebung mit {{site.data.keyword.cloud_notm}}-Standorten zur Erreichung einer reibungslosen Hybridität der Infrastruktur und einer realen Anwendungsmobilität herstellen.
| [VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview) | Das Produktangebot "vSphere on {{site.data.keyword.cloud_notm}}" bietet einen anpassbaren Virtualisierungsservice, der zum Aufbau Ihrer eigenen von IBM gehosteten VMware-Umgebung mit VMware kompatible {{site.data.keyword.baremetal_short}}-Instanzen, Hardwarekomponenten und Lizenzen kombiniert. |
| [NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview) | Das Produktangebot "NetApp ONTAP Select" ermöglicht Ihnen die Bereitstellung eines softwaredefinierten Speicherclusters, der Ihren Bedarf für eine dedizierte und hoch verfügbare Speicher-Appliance auf der Basis von NetApp ONTAP Select abdeckt. |
{: caption="Tabelle 2. Bereitstellungsangebote" caption-side="top"}

### Add-on-Services
{: #getting-started-add-on-services}

Wählen Sie nach Durchsicht der folgenden Tabelle Add-on-Services für Ihr Bereitstellungsangebot aus.

| Servicename | Beschreibung |
|:------------ |:----------- |
| [F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | Der Service "F5 on {{site.data.keyword.cloud_notm}}" (F5 BIG-IP® Virtual Edition) stellt lokal und global einsetzbare intelligente Services für den L4-L7-Lastausgleich, einen stabilen Firewallschutz für Netze und Webanwendungen sowie einen sicheren und eingebundenen Anwendungszugriff zur Verfügung. |
| [FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) | Der Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" stellt ein Paar von Einheiten der FortiGate Security Appliance (FSA) 300-Serie in einem Hochverfügbarkeitsmodus bereit, um Firewall-, Routing-, NAT- und VPN-Services für den Schutz aller Server und virtuellen Maschinen im öffentlichen VLAN Ihrer Instanzen zur Verfügung zu stellen. |
| [FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | Der Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" stellt ein Paar von FortiGate Virtual Appliances für Ihre Umgebung bereit, mit dessen Hilfe Sie durch die Implementierung von kritischen Sicherheitsmaßnahmen in Ihrer virtuellen Infrastruktur Risiken verringern können. |
| [HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | Der Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" erzwingt und steuert die Einhaltung der Sicherheitsstandards und stellt detaillierte Funktionen für die rollenbasierte Zugriffssteuerung (RBAC = Role-Based Access Control) sowie für die Genehmigung und Überprüfung zur Verfügung. In Kombination mit HyTrust DataControl kann der Service sicherstellen, dass virtuelle Maschinen und Workloaddaten eine bestimmte Region, einen bestimmten Cluster oder einen bestimmten ESXi-Server innerhalb von {{site.data.keyword.CloudDataCent_notm}} nicht verlassen. |
| [HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations) | Der Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service kann die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereitstellen. Dies bedeutet, dass alle Verzeichnisse, Ordner oder Dateien innerhalb einer Workload ver- und entschlüsselt werden können.|
| [HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | Der Service "HyTrust KeyControl on {{site.data.keyword.cloud_notm}}" vereinfacht das Management verschlüsselter Workloads durch Automatisierung und Vereinfachung des Lebenszyklus von Verschlüsselungsschlüsseln. Der Service kann mithilfe der FIPS 140-2-konformen Verschlüsselung ohne großen Aufwand skalierbare Verschlüsselungsschlüssel verwalten. |
| [IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | Der Service "{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}}" stellt die Leistungsfähigkeit von Mikroservices und Containern in Ihrer VMware-Umgebung unter {{site.data.keyword.cloud_notm}} zur Verfügung. Mit diesem Service können Sie den Einsatz des bereits vertrauten VMware- und {{site.data.keyword.cloud_notm}} Private-Betriebsmodells und der zugehörigen Tools von Ihrem lokalen Standort (On-Premises) auf {{site.data.keyword.cloud_notm}}-Umgebungen erweitern. |
| [IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | Der Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" bietet eine effiziente und skalierbare Datensicherungs-, Datenwiederverwendungs- und Datenwiederherstellungslösung für virtuelle Umgebungen. Er kann als eigenständige Lösung implementiert oder in Ihre IBM Spectrum Protect-Umgebung integriert werden, um Kopien für die Langzeitspeicherung und Datengovernance auszulagern. |
| [KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | Der Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" stellt einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können. Außerdem stellt er Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit. |
| [Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | Der Service "Veeam on {{site.data.keyword.cloud_notm}}" wird nahtlos und direkt in Ihre VMware-Hypervisoren integriert und fördert so die Hochverfügbarkeit in Ihrem Unternehmen. Dieser Service kann Wiederherstellungspunkte und Zeitziele für Ihre Anwendungen und Daten bereitstellen. Die Wiederherstellungspunkte und Zeitziele können in weniger als 15 Minuten nach Abschluss der Konfiguration bereitgestellt werden. Durch die Verwendung dieses Service können Sie die Sicherung und Wiederherstellung aller virtuellen Maschinen für Ihre Infrastruktur direkt von der Veeam-Konsole aus steuern. |
| [VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | Der Service "HCX on {{site.data.keyword.cloud_notm}}" kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist.|
| [Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | Der Service "Zerto on {{site.data.keyword.cloud_notm}}" stellt Replikations- und Disaster-Recovery-Funktionen bereit, die in die Bereitstellungsangebote integriert werden können, um Daten in Ihrer virtuellen VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu schützen und wiederherzustellen. |
{: caption="Tabelle 3. Verfügbare Add-on-Services für Bereitstellungsangebote" caption-side="top"}

## Schritt 1: Auf die Konsole von IBM Cloud for VMware Solutions zugreifen
{: #getting-started-step1}

Die Konsole von {{site.data.keyword.vmwaresolutions_short}} ist die Schnittstelle, über die Sie Ihre Bereitstellungen bestellen und verwalten. Jede Bereitstellung wird in der Konsole als Instanz verwaltet. Die Konsole ist eine eigenständige, vom Kundenportal der {{site.data.keyword.cloud_notm}}-Infrastruktur getrennte Benutzerschnittstelle.

Greifen Sie wie im Folgenden beschrieben auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu:
1. Rufen Sie "https://cloud.ibm.com/infrastructure/vmware-solutions/console" auf.
2. Melden Sie sich mit Ihrer **IBMid** bei der Konsole an.

## Schritt 2: Benutzerkonto und -einstellungen konfigurieren
{: #getting-started-step2}

Geben Sie vor dem Bestellen einer Instanz den Benutzernamen und den API-Schlüssel Ihres Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** der Konsole ein.

Informationen zum Konfigurieren des Benutzerkontos und der zugehörigen Einstellungen finden Sie in [Benutzerkonten und -einstellungen verwalten](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Schritt 3: Instanz bestellen
{: #getting-started-step3}

Nehmen Sie den Bestellprozess in Angriff, wenn Sie sich für ein Bereitstellungsangebot, bei dem es sich um eine Instanz in der Konsole handelt, entschieden haben.

Informationen zum Bestellen einer Instanz finden Sie je nach dem von Ihnen ausgewählten Bereitstellungsangebot in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [NetApp ONTAP Select-Instanzen bestellen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Schritt 4: Instanz anzeigen
{: #getting-started-step4}

Sobald Sie wie unter **Schritt 3** beschrieben eine Instanz bestellt haben, wird die Bereitstellung der Instanz automatisch gestartet. Sie können den Status der Bereitstellung verfolgen, indem Sie die Instanzdetails anzeigen. Nach der Instanzbereitstellung können Sie eine Zusammenfassung sowie detaillierte Informationen zu der Instanz und den zugehörigen Add-on-Services auch auf der Seite mit den Instanzdetails anzeigen.

Informationen zum Anzeigen der bestellten Instanz finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [NetApp ONTAP Select-Instanzen anzeigen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
