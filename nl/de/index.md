---

copyright:

  years: 2016, 2018

lastupdated: "2018-08-27"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Einführung in IBM Cloud for VMware Solutions

In diesem Einführungslerntext erfahren Sie, wie Sie eine Instanz sowie verfügbare Add-on-Services für diese Instanz bestellen können.
{:shortdesc}

## Vorbereitende Schritte
{: #prereqs}

Informieren Sie sich vor der Arbeit mit {{site.data.keyword.vmwaresolutions_full}} über die folgenden wichtigen Informationen zu Browseranforderungen, Benutzerkonten, Bereitstellungsoptionen und Add-on-Services.

### Browseranforderungen

Die folgenden Browser werden unterstützt:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

**Hinweis**: Microsoft Internet Explorer wird nicht unterstützt.

Optimale Anzeige- und Arbeitsbedingungen für die {{site.data.keyword.vmwaresolutions_short}}-Konsole erreichen Sie, indem Sie mindestens eine Bildschirmauflösung von 1024 Pixel Breite mal 500 Pixel Höhe verwenden.

### Benutzerkonten

Sie benötigen ein {{site.data.keyword.cloud_notm}}-Konto und ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer). Diese Konten müssen bestimmte Anforderungen erfüllen.

   Tabelle 1. Erforderliche Benutzerkonten
   <table>
   <tr>
      <th>Konto</th>
      <th>Beschreibung</th>
   </tr>
   <tr>
      <td>IBMid</td>
      <td>Die **IBMid** ermöglicht es Ihnen, einen einzigen Anmeldebenutzernamen für alle genutzten IBM Produkte und Services, einschließlich {{site.data.keyword.cloud_notm}}, zu verwenden. {{site.data.keyword.vmwaresolutions_short}} wird als Infrastrukturlösung im {{site.data.keyword.cloud_notm}}-Katalog bereitgestellt. Um auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole zugreifen zu können, müssen Sie über eine **IBMid** verfügen.<br><br>Damit Sie Ihre **IBMid** zur Anmeldung bei der Konsole von {{site.data.keyword.vmwaresolutions_short}} verwenden können, müssen Sie die **IBMid** einem {{site.data.keyword.cloud_notm}}-Konto zuordnen. Wenn Sie sich zum ersten Mal bei der Konsole anmelden, müssen Sie entweder Ihre vorhandene **IBMid** einem {{site.data.keyword.cloud_notm}}-Konto zuordnen oder sich für ein neues {{site.data.keyword.cloud_notm}}-Konto registrieren. Das neue {{site.data.keyword.cloud_notm}}-Konto wird dann automatisch Ihrer **IBMid** zugeordnet. Dieses Verfahren müssen Sie nur einmal durchlaufen.<br><br>Wenn Sie Probleme beim Zuordnen Ihrer **IBMid** zu einem {{site.data.keyword.cloud_notm}}-Konto haben, lesen Sie die Informationen im Abschnitt [Fehlerbehebung beim Zugriff auf {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html).</td>
   </tr>
   <tr>
      <td>IBM Cloud-Konto</td>
      <td>Zum Bestellen und Verwenden von {{site.data.keyword.cloud_notm}}-Services benötigen Sie ein {{site.data.keyword.cloud_notm}}-Konto. Abrechnungsinformationen werden dem {{site.data.keyword.cloud_notm}}-Konto zugeordnet. Die Kosten für die physische und virtuelle Infrastruktur sowie die daraus resultierenden Lizenzen werden Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt.</td>
   </tr>
   <tr>
      <td>Konto für die IBM Cloud-Infrastruktur (SoftLayer)</td>
      <td>Das Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) wurde früher als IBM SoftLayer-Konto bezeichnet.  Weitere Informationen zu den Anforderungen, die das Konto erfüllen muss, finden Sie unter [Anforderungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto](vmonic/slaccountrequirement.html).<br><br>Sie können Konten für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit {{site.data.keyword.cloud_notm}}-Konten verknüpfen, um kombinierte Infrastructure as a Service-Ressourcen (IaaS) und Platform as a Service-Ressourcen (PaaS) zu nutzen. Anschließend können Sie auf IaaS-Ressourcen und PaaS-Ressourcen über ein und dieselbe Anmeldung zugreifen. Das Verknüpfen Ihrer Konten hat außerdem zur Folge, dass Sie nur eine Rechnung für alle PaaS- und IaaS-Ressourcen erhalten, die Sie nutzen.<ul><li>Wenn Sie kein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, können Sie eines anfordern, indem Sie die unter [Für ein IBM Cloud-Infrastrukturkonto (SoftLayer-Konto) registrieren](vmonic/signing_softlayer_account.html) beschriebene Prozedur ausführen, und anschließend Ihr Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen, indem Sie die unter [IBMid-Konten verknüpfen](https://console.bluemix.net/docs/account/softlayerlink.html) beschriebene Prozedur ausführen.</li><li>Wenn Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, können Sie es mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen, indem Sie die unter [IBMid-Konten verknüpfen](https://console.bluemix.net/docs/account/softlayerlink.html) beschriebene Prozedur ausführen.</li></ul></td>
   </tr>
   </table>

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Für erforderliche Konten registrieren](vmonic/signing_softlayer_account.html)
* [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto](vmonic/slaccountrequirement.html)

### Bereitstellungsangebote

Wählen Sie nach Durchsicht der folgenden Tabelle das von Ihnen gewünschte Bereitstellungsangebot aus.

  Tabelle 2. Bereitstellungsangebote
  <table>
    <tr>
       <th>Bereitstellungsangebot</th>
       <th>Beschreibung</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](vcenter/vc_vcenterserveroverview.html)</td>
       <td>Mit dem vCenter Server-Produktangebot können Sie eine virtuelle VMware-Umgebung unter Verwendung von angepassten Rechen-, Speicher- und Netzressourcen bereitstellen und so Ihre Geschäftsanforderungen optimal erfüllen.</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](vcenter/vc_hybrid_overview.html)</td>
       <td>Das vCenter Server with Hybridity-Angebot ist eine gehostete private Cloud und unterstützt Sie bei der schnellen und einfachen Erweiterung Ihrer lokalen Infrastruktur in die Cloud. Die VMware-Umgebung basiert auf den von IBM bereitgestellten VMware Software Defined Data Center-Lizenzen und umfasst VMware Hybrid Cloud Extension (HCX). Mithilfe von HCX können Sie eine sichere Verbindung einer lokalen vSphere 5.0+-Umgebung mit {{site.data.keyword.cloud_notm}}-Standorten zur Erreichung einer reibungslosen Hybridität der Infrastruktur und einer realen Anwendungsmobilität herstellen.</td>
    </tr>
    <tr>
       <td>[VMware Cloud Foundation on IBM Cloud](sddc/sd_cloudfoundationoverview.html)</td>
       <td>Das Cloud Foundation-Produktangebot stellt eine einheitliche virtuelle VMware-Umgebung unter Verwendung von {{site.data.keyword.cloud_notm}}-Standardressourcen für Rechenleistung, Speicher und Netzbetrieb zur Verfügung, die für jede Benutzerbereitstellung dediziert sind.</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](vsphere/vs_vsphereclusteroverview.html)</td>
       <td>Das Produktangebot "vSphere on {{site.data.keyword.cloud_notm}}" bietet einen anpassbaren Virtualisierungsservice, der zum Aufbau Ihrer eigenen von IBM gehosteten VMware-Umgebung mit VMware kompatible {{site.data.keyword.baremetal_short}}-Instanzen, Hardwarekomponenten und Lizenzen kombiniert.</td>
    </tr>
    <tr>
       <td>[NetApp ONTAP Select](netapp/np_netappoverview.html)</td>
       <td>Das Produktangebot "NetApp ONTAP Select" ermöglicht Ihnen die Bereitstellung eines softwaredefinierten Speicherclusters, der Ihren Bedarf für eine dedizierte und hoch verfügbare Speicher-Appliance auf der Basis von NetApp ONTAP Select abdeckt.</td>
    </tr>
    <tr>
       <td>[VMware Federal on IBM Cloud](vcenter/vc_fed_overview.html)</td>
       <td>Das Produktangebot "VMware Federal on {{site.data.keyword.cloud_notm}}" unterstützt die Bestellung einer vCenter Server-Basisinstanz. Außerdem haben Sie die Möglichkeit, die bereitgestellten Instanzen zu schützen, sensible Informationen zu entfernen sowie die offene Managementverbindung für den kontinuierlichen Zugriff von Managementfunktionen auf die Instanz zu unterbrechen.</td>
    </tr>
  </table>

### Add-on-Services

Wählen Sie nach Durchsicht der folgenden Tabelle Add-on-Services für Ihr Bereitstellungsangebot aus.

  Tabelle 3. Verfügbare Add-on-Services für Bereitstellungsangebote
  <table>
    <tr>
       <th>Servicename</th>
       <th>Beschreibung</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](services/f5_considerations.html)</td>
       <td>Der Service "F5 on {{site.data.keyword.cloud_notm}}" (F5 BIG-IP® Virtual Edition) stellt lokal und global einsetzbare intelligente Services für den L4-L7-Lastausgleich, einen stabilen Firewallschutz für Netze und Webanwendungen sowie einen sicheren und eingebundenen Anwendungszugriff zur Verfügung.</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](services/fsa_considerations.html)</td>
       <td>Der Service "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" stellt ein Paar von Einheiten der FortiGate Security Appliance (FSA) 300-Serie in einem Hochverfügbarkeitsmodus bereit, um Firewall-, Routing-, NAT- und VPN-Services für den Schutz aller Server und virtuellen Maschinen im öffentlichen VLAN Ihrer Instanzen zur Verfügung zu stellen.</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](services/fortinetvm_considerations.html)</td>
       <td>Der Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" stellt ein Paar von FortiGate Virtual Appliances für Ihre Umgebung bereit, mit dessen Hilfe Sie durch die Implementierung von kritischen Sicherheitsmaßnahmen in Ihrer virtuellen Infrastruktur Risiken verringern können.</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](services/htcc_considerations.html)</td>
       <td>Der Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" erzwingt und steuert die Einhaltung der Sicherheitsstandards und stellt detaillierte Funktionen für die rollenbasierte Zugriffssteuerung (RBAC = Role-Based Access Control) sowie für die Genehmigung und Überprüfung zur Verfügung. In Kombination mit HyTrust DataControl kann der Service sicherstellen, dass virtuelle Maschinen und Workloaddaten eine bestimmte Region, einen bestimmten Cluster oder einen bestimmten ESXi-Server innerhalb von {{site.data.keyword.CloudDataCent_notm}} nicht verlassen.</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](services/htdc_considerations.html)</td>
       <td>Der Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service kann die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereitstellen. Dies bedeutet, dass alle Verzeichnisse, Ordner oder Dateien innerhalb einer Workload ver- und entschlüsselt werden können.</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](services/managing_icp.html)</td>
       <td>Der Service "{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}}" stellt die Leistungsfähigkeit von Mikroservices und Containern in Ihrer VMware-Umgebung unter {{site.data.keyword.cloud_notm}} zur Verfügung. Mit diesem Service können Sie den Einsatz des bereits vertrauten VMware- und {{site.data.keyword.cloud_notm}} Private-Betriebsmodells und der zugehörigen Tools von Ihrem lokalen Standort (On-Premises) auf {{site.data.keyword.cloud_notm}}-Umgebungen ausdehnen.</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](services/spp_considerations.html)</td>
       <td>Der Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" bietet eine effiziente und skalierbare Datensicherungs-, Datenwiederverwendungs- und Datenwiederherstellungslösung für virtuelle Umgebungen. Er kann als eigenständige Lösung implementiert oder in Ihre IBM Spectrum Protect-Umgebung integriert werden, um Kopien für die Langzeitspeicherung und Datengovernance auszulagern.</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](services/kmip_considerations.html)</td>
       <td>Der Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" stellt einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können. Außerdem stellt er Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit.</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](services/veeam_considerations.html)</td>
       <td>Der Service "Veeam on {{site.data.keyword.cloud_notm}}" wird nahtlos und direkt in Ihre VMware-Hypervisoren integriert und fördert so die Hochverfügbarkeit in Ihrem Unternehmen. Dieser Service kann Wiederherstellungspunkte und Zeitziele für Ihre Anwendungen und Daten bereitstellen. Die Wiederherstellungspunkte und Zeitziele können in weniger als 15 Minuten nach Abschluss der Konfiguration bereitgestellt werden. Durch die Verwendung dieses Service können Sie die Sicherung und Wiederherstellung aller virtuellen Maschinen für Ihre Infrastruktur direkt von der Veeam-Konsole aus steuern.</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](services/hcx_considerations.html)</td>
       <td>Der Service "HCX on {{site.data.keyword.cloud_notm}}" kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist.</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](services/addingzertodr.html)</td>
       <td>Der Service "Zerto on {{site.data.keyword.cloud_notm}}" stellt Replikations- und Disaster-Recovery-Funktionen bereit, die in die Bereitstellungsangebote integriert werden können, um Daten in Ihrer virtuellen VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu schützen und wiederherzustellen.</td>
    </tr>
   </table>

## Schritt 1: Auf die Konsole von IBM Cloud for VMware Solutions zugreifen

Die Konsole von {{site.data.keyword.vmwaresolutions_short}} ist die Schnittstelle, über die Sie Ihre Bereitstellungen bestellen und verwalten. Jede Bereitstellung wird in der Konsole als Instanz verwaltet. Die Konsole ist eine eigenständige, vom Kundenportal der {{site.data.keyword.cloud_notm}}-Infrastruktur getrennte Benutzerschnittstelle.

Greifen Sie wie im Folgenden beschrieben auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu:
1. Rufen Sie die Adresse "https://console.ng.bluemix.net/infrastructure/vmware-solutions/console" auf.
2. Melden Sie sich mit Ihrer **IBMid** bei der Konsole an.

## Schritt 2: Benutzerkonto und -einstellungen konfigurieren

Geben Sie vor dem Bestellen einer Instanz den Benutzernamen und den API-Schlüssel Ihres Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) auf der Seite **Einstellungen** der Konsole ein.

Informationen zum Konfigurieren des Benutzerkontos und der zugehörigen Einstellungen finden Sie in [Benutzerkonten und -einstellungen verwalten](vmonic/useraccount.html).

## Schritt 3: Instanz bestellen

Nehmen Sie den Bestellprozess in Angriff, wenn Sie sich für ein Bereitstellungsangebot, bei dem es sich um eine Instanz in der Konsole handelt, entschieden haben.

Informationen zum Bestellen einer Instanz finden Sie je nach dem von Ihnen ausgewählten Bereitstellungsangebot in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](vcenter/vc_orderinginstance.html)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](vcenter/vc_hybrid_orderinginstance.html)
* [Cloud Foundation-Instanzen bestellen](sddc/sd_orderinginstance.html)
* [Neue vSphere-Cluster bestellen](vsphere/vs_orderinginstances.html)
* [NetApp ONTAP Select-Instanzen bestellen](netapp/np_orderinginstances.html)  
* [VMware Federal-Instanzen bestellen](vcenter/vc_fed_orderinginstance.html)

## Schritt 4: Instanz anzeigen

Sobald Sie wie unter **Schritt 3** beschrieben eine Instanz bestellt haben, wird die Bereitstellung der Instanz automatisch gestartet. Sie können den Status der Bereitstellung verfolgen, indem Sie die Instanzdetails anzeigen. Nach der Instanzbereitstellung können Sie eine Zusammenfassung sowie detaillierte Informationen zu der Instanz und den zugehörigen Add-on-Services auch auf der Seite mit den Instanzdetails anzeigen.

Informationen zum Anzeigen der bestellten Instanz finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen anzeigen](vcenter/vc_viewinginstances.html)
* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](vcenter/vc_hybrid_viewinginstances.html)
* [Cloud Foundation-Instanzen anzeigen](sddc/sd_viewinginstances.html)
* [NetApp ONTAP Select-Instanzen anzeigen](netapp/np_viewinginstances.html)
* [VMware Federal-Instanzen anzeigen](vcenter/vc_fed_viewinginstance.html)

## Schritt 5: Add-on-Services für die Instanz verwalten

Wenn Sie Add-on-Services für Ihre Instanz bestellt haben, können Sie auch diese Services verwalten.

Informationen zum Verwalten der Services finden Sie in den folgenden Abschnitten:
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](vcenter/vc_addingremovingservices.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](vcenter/vc_hybrid_addingremovingservices.html)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](sddc/sd_addingremovingservices.html)

## Nächster Schritt

Nun können Sie Ihre Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole oder VMware vSphere Web Client verwalten.
