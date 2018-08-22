---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-31"

---

# Releaseinformationen für V2.5

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](../vmonic/trbl_fix_spectre.html).

## NSX-Komponentenaktualisierung

Mit diesem Release wird VMware NSX for vSphere 6.4.1 für neue Bereitstellungen von VMware vCenter Server auf {{site.data.keyword.cloud_notm}}, von VMware vCenter Server auf {{site.data.keyword.cloud_notm}} with Hybridity Bundle, von NetApp ONTAP Select sowie von VMware Federal auf {{site.data.keyword.cloud_notm}} installiert.

## Entfernen der Standardsicherungskonfiguration

{{site.data.keyword.vmwaresolutions_short}} bietet zwei integrierte Add-on-Services für die Sicherung an: IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} und Veeam on {{site.data.keyword.cloud_notm}}. Mithilfe dieser Services können Sie Wiederherstellungsfunktionen für Ihre Managementinfrastruktur und Ihre Workload planen und zur Verfügung stellen. Darüber hinaus werden durch IBM Resiliency Services verwaltete Services für Veeam-Sicherungen angeboten.

Ab Release V2.5 führen die Services "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" und "Veeam on {{site.data.keyword.cloud_notm}}", wenn sie bereitgestellt werden, keine Vorkonfiguration der Sicherung von VMs mehr durch. Durch diese Änderung können Sie die ordnungsgemäße Konfiguration aller Aspekte Ihrer Sicherungsjobs, wie Zeitplan, Aufbewahrungsdauer, Verwendung der Deduplizierung, Überwachung und Alerts sowie Management von Verschlüsselungsschlüsseln sicherstellen. Darüber hinaus wird die IBM CloudDriver-VM nicht mehr als persistenter Dateiserver für NSX-Sicherungen konfiguriert.

Sie sind für die Konfiguration, Verwaltung und Überwachung sämtlicher Softwarekomponenten verantwortlich. Dies schließt die Sicherung der Managementinfrastruktur und Workloads sowie die Gewährleistung der Verfügbarkeit dieser Komponenten ein. Weitere Informationen finden Sie unter [Komponenten sichern](../archiref/solution/solution_backingup.html#backing-up-components).

**Hinweis:** Diese Änderung wirkt sich nicht auf Instanzen aus, die vor Version 2.5 bereitgestellt wurden und für die bereits der Service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} oder Veeam on {{site.data.keyword.cloud_notm}} installiert wurde.

## IBM CloudDriver-Ausfallsicherheit

Für Instanzen, die in Version 2.5 oder höheren Releases bereitgestellt oder auf Version 2.5 oder höher aktualisiert werden, wird die IBM CloudDriver-Komponente nicht mehr als virtuelle Maschine (VM) im vSphere-Cluster konfiguriert. Stattdessen wird sie als virtuelle Serverinstanz (VSI) der {{site.data.keyword.cloud_notm}}-Infrastruktur nach Bedarf mit dem neuesten {{site.data.keyword.cloud_notm}} for VMware-Code für Operationen wie die Bereitstellung weiterer Knoten bereitgestellt. Darüber hinaus wurde IBM CloudDriver geändert, um die Kommunikation mit der {{site.data.keyword.cloud_notm}}-Managementebene über das private {{site.data.keyword.cloud_notm}}-Netz einzurichten, sodass die Firewall für NSX Edge Services Gateway (ESG) und die Netzadressumsetzungsregeln (NAT-Regeln), die die ausgehende Kommunikation von IBM CloudDriver mit dem öffentlichen Netz ermöglichten, entfernt wurden.

Einige Add-on-Services wie F5 on {{site.data.keyword.cloud_notm}}, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} und Zerto on {{site.data.keyword.cloud_notm}} erfordern weiterhin Zugriff auf das öffentliche Netz, sodass das NSX-ESG für alle Instanzen bereitgestellt bleibt.

## IAM-basiertes Benutzer- und Zugriffsmanagement

Ab dem Release von Version 2.5 ist {{site.data.keyword.vmwaresolutions_short}} in IBM Identity and Access Management (IAM) integriert, um eine einheitliche Methode für die Verwaltung von Benutzerkonten und Benutzerzugriffen in Ihrem {{site.data.keyword.cloud_notm}}-Konto zur Verfügung zu stellen. Dies hat folgende Konsequenzen:
* Sie können Ihrem {{site.data.keyword.cloud_notm}}-Konto jetzt mehrere Benutzer zur Zusammenarbeit hinzufügen und Sie können deren Zugriff auf die Services und Ressourcen, die in Ihrem Konto bereitgestellt werden, verwalten, indem Sie ihnen verschiedene Plattformzugriffsrollen zuweisen.  
* Instanzen, die in Version 2.5 und höheren Releases bereitgestellt werden, werden automatisch mit dem Benutzerkonto verknüpft, das bei der Bestellung der Instanz verwendet wird.
* Bei Instanzen, die in Version 2.4 und früheren Releases bereitgestellt wurden, können Sie diese auf ein {{site.data.keyword.cloud_notm}}-Konto migrieren und anschließend ebenfalls mithilfe von IAM verwalten.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Benutzer für den Zugriff auf Services und Ressourcen einladen](../vmonic/iamuserinvite.html)
* [Benutzerzugriff mit IAM verwalten](../vmonic/iam.html)

## Änderungen an Benutzerkonten und -gruppen für VMware vCenter Server- und VMware Cloud Foundation-Instanzen

Die Benutzergruppe **ic4v-vCenter** wurde auf dem Microsoft Active Directory-Server erstellt und den globalen Berechtigungen auf vCenter Server und Benutzergruppen für den NSX-Manager hinzugefügt. Die Gruppe enthält das Benutzerkonto **automation** für vCenter Server-Instanzen sowie servicespezifische Benutzerkonten für vCenter Server- und Cloud Foundation-Instanzen.

Bearbeiten Sie keine globalen Berechtigungen der Gruppe **ic4v-vCenter** auf der Seite **Benutzer und Gruppen** auf dem VMware vSphere-Web-Client. Dies könnte sich auf Managementoperationen auswirken.

Verwenden Sie für Cloud Foundation-Instanzen die Hostbenutzer-ID **customerroot** anstelle der Hostbenutzer-ID **root**. Verwenden Sie die Hostbenutzer-ID **root** weiterhin für vCenter Server-Instanzen.

Weitere Informationen zu Benutzerkonten finden Sie in folgenden Abschnitten:

* [Hinweise zum Ändern von vCenter Server-Artefakten](../vcenter/vcenter_chg_impact.html)
* [Hinweise zum Ändern von Cloud Foundation-Artefakten](../sddc/cf_chg_impact.html)

## Updates für Add-on-Services

### IBM Spectrum Protect Plus on IBM Cloud

Ab dem Release von V2.5 wird der Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" bewährten Verfahren entsprechend in zwei separaten VMs bereitgestellt, wobei die eine VM den Spectrum Protect Plus-Server und die andere VM den vSnap-Server und den VADP-Proxy ausführt.

Sie können jetzt bis zu zehn Sicherungsdatenspeicher mit einer Größe von bis zu 120 TB an Sicherungsspeicher bestellen. Die vSnap-VM und die VADP-VM werden abhängig von Ihrer ausgewählten Sicherungsspeichergröße und entsprechend den Informationen in den [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) dimensioniert.

### KMIP for VMware on IBM Cloud

Ein neuer Endpunkt ist jetzt in Deutschland für den Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" verfügbar.

Weitere Informationen enthält der Abschnitt zur [Konfiguration des Service 'KMIP for VMware on {{site.data.keyword.cloud_notm}}'](../services/kmip_ordering.html#kmip-for-vmware-on-ibm-cloud-service-configuration).

## Neue und aktualisierte Dokumentation

### Dokumentation zu angehängtem Speicher

Das technische Dokument zu angehängtem Speicher (Attached Storage) für vCenter Server on IBM Cloud ist jetzt im Abschnitt *Referenzinformationen* der Benutzerdokumentation verfügbar. Dieses Architekturreferenzdokument ist nur in Englisch verfügbar. Weitere Informationen finden Sie unter [Attached storage for vCenter Server on IBM Cloud](../archiref/attached-storage/storage-benefits.html).

### Technische Spezifikationen

Die technischen Spezifikationen für alle Instanztypen und Servicetypen sind jetzt in der Benutzerdokumentation verfügbar und über Links in der Benutzerschnittstelle zugänglich. Weitere Informationen finden Sie in dem entsprechenden Übersichtsabschnitt für Ihre Instanz und Ihren Service.

### Servicedokumentation

Die Informationen zu Services wurden verbessert, sodass sich die Unterstützung eines Service anhand der Releasenummer, unter der er verfügbar gemacht wurde, leicht ermitteln lässt.

Weitere Informationen enthalten die folgenden Abschnitte:

* [Verfügbare Services für vCenter Server-Instanzen](../vcenter/vc_addingremovingservices.html#available-services-for-vcenter-server-instances)
* [Verfügbare Services für vCenter Server with Hybridity Bundle-Instanzen](../vcenter/vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Verfügbare Services für Cloud Foundation-Instanzen](../sddc/sd_addingremovingservices.html#available-services-for-cloud-foundation-instances)

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Wenn Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, das mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpft ist, können Sie jetzt auf die neu hinzugefügte Schaltfläche **Abrufen** auf der Seite **Einstellungen** klicken, um den Benutzernamen und den API-Schlüssel für Ihr Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) automatisch abzurufen.
* Im linken Navigationsfenster der Instanzdetailseite wurde eine neue Registerkarte **Bereitstellungsverlauf** hinzugefügt, auf der Sie den Bereitstellungsverlauf einer Instanz prüfen können.
* Verschiedene Fehlernachrichten und QuickInfos wurden erweitert, um Ihnen bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle zu helfen.
