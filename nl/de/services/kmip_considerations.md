---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Überblick zu KMIP for VMware on IBM Cloud

Der Service "KMIP for VMware on {{site.data.keyword.cloud}}" stellt täglich rund um die Uhr einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können, sowie Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und diesen Verschlüsselungsschlüsseln.

**Verfügbarkeit**: Dieser Service ist nur für Instanzen verfügbar, die in V2.2 oder höheren Releases bereitgestellt werden.

## Hinweise zur Installation von KMIP on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} verwendet den Service "IBM Key Protect for IBM Cloud", um Verschlüsselungsschlüssel zu erstellen, zu verschlüsseln und zu entschlüsseln. Daher müssen Sie vor der Installation des Service sicherstellen, dass Sie einen verwendbaren Service "Key Protect" bestellt haben. In der Zwischenzeit haben Sie eine {{site.data.keyword.cloud_notm}}-Service-ID erstellt, indem Sie die Schritte unter [Service-ID erstellen](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id) ausgeführt haben, um auf die von Ihnen erstellte Serviceinstanz von Key Protect zuzugreifen.

Stellen Sie sicher, dass Sie die folgenden Zugriffsebenen für die Service-ID erteilen:
* Auf Plattformzugriffsebene: Anzeigeberechtigung für Ihre Instanz von IBM Key Protect.
* Auf Servicezugriffsebene: Schreibberechtigung für Ihre Instanz von IBM Key Protect

Der API-Schlüssel für die erstellte Service-ID ist zum Bestellen des Service erforderlich.

Der Service setzt voraus, dass Sie bereits mindestens einen Stammschlüssel für Kunden in der Key Protect-Benutzerschnittstelle erstellt haben (die entsprechenden Schritte sind unter [Stammschlüssel erstellen](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) beschrieben) oder dass Sie hierzu die RESTful-API in [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect) verwendet haben.

Der Service kann ohne Stammschlüssel für Kunden nicht bestellt werden. Es wird dringend empfohlen, das Verfahren für die Erstellung eines Stammschlüssels für Kunden unter Verwendung vorhandener Schlüsselinformationen zu verwenden und die erstellten Schlüsselinformationen zu sichern. Dadurch stellen Sie sicher, dass Sie Ihre Schlüssel im Falle eines Totalausfalls des Rechenzentrums, in dem IBM Key Protect Ihre Stammschlüssel für Kunden speichert, wiederherstellen können.

## Wichtige Hinweise zur Verwendung von KMIP for VMware on IBM Cloud

* Zur Verwendung eines bestellten Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" als Schlüsselmanagementserver (Key Management Server, KMS), der bei VMware vCenter Server registriert ist, müssen Sie sicherstellen, dass Netzkonfigurationen vorhanden sind, damit die Netzkonnektivität von vCenter Server zum Endpunkt des bestellten Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" betriebsfähig ist.
* Zur Verwendung des Service für die VMware vSAN-Verschlüsselung müssen Sie sicherstellen, dass die Netzkonnektivität zwischen den Hosts im Ziel-vSAN und dem Endpunkt des bestellten Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" betriebsfähig ist.


## Hinweise zum Entfernen von KMIP on IBM Cloud

Das öffentliche VMware-Zertifikat, das Sie beim Bestellen oder Verwenden des Service angegeben haben, wird als Clientzertifikat für die Kommunikation mit der Serviceinstanz verwendet. Wenn der Service entfernt wird, werden damit auch alle Verschlüsselungsschlüssel entfernt, die von dieser Serviceinstanz für das zugehörige öffentliche VMware-Zertifikat erstellt wurden.

Bevor Sie den Service entfernen, müssen Sie daher sicherstellen, dass keine virtuellen Maschinen oder vSANs mit den vom KMIP-Service erstellten Schlüsseln verschlüsselt werden.

## Zugehörige Links

* [KMIP for VMware on IBM Cloud bestellen](kmip_ordering.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
