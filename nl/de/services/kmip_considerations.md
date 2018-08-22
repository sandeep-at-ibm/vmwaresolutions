---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Übersicht über KMIP for VMware on IBM Cloud

Der Service "KMIP for VMware on {{site.data.keyword.cloud}}" stellt täglich rund um die Uhr einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können. Außerdem stellt er Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit.

**Verfügbarkeit**: Dieser Service ist nur für Instanzen verfügbar, die in V2.2 oder höheren Releases bereitgestellt werden.

## Technische Spezifikationen für KMIP for VMware on IBM Cloud

Die folgenden Spezifikationen werden mit dem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" einbezogen:

* Ein VMware-kompatibles Key Management Interoperability Protocol (KMIP)
* Ein verwalteter Service
* Verfügbar in mehreren geografischen Regionen weltweit
* Hochverfügbarer KMIP-Serviceendpunkt in jeder Region

## Hinweise zur Installation von KMIP on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} verwendet den Service "IBM Key Protect for {{site.data.keyword.cloud_notm}}", um Verschlüsselungsschlüssel zu erstellen, zu verschlüsseln und zu entschlüsseln. Daher müssen Sie vor dem Installieren von KMIP for VMware on {{site.data.keyword.cloud_notm}} Folgendes sicherstellen:
* Sie haben einen verwendbaren Key Protect-Service bestellt.
* Es wurde eine {{site.data.keyword.cloud_notm}}-Service-ID unter Beachtung der Schritte in [Service-ID erstellen](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id) erstellt. Diese Service-ID wird verwendet, um auf die von Ihnen Instanz des Key Protect-Service zuzugreifen.
* Sie haben die folgenden Zugriffsebenen für die Service-ID erteilt:
   * Auf Plattformzugriffsebene: Anzeigeberechtigung für Ihre Instanz von IBM Key Protect.
   * Auf Servicezugriffsebene: Schreibberechtigung für Ihre Instanz von IBM Key Protect
* Sie verfügen über einen API-Schlüssel für die erstellte Service-ID. Der Schlüssel ist zum Bestellen des Service erforderlich.
* Sie haben mindestens einen Stammschlüssel für Kunden (Customer Root Key, CRK) in der Key Protect-Benutzerschnittstelle erstellt. Dazu haben Sie die entsprechenden Schritte wie in [Stammschlüssel erstellen](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) beschrieben ausgeführt oder Sie haben die REST-API in [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect) verwendet.

   **Wichtig**: Der Service kann nicht ohne Stammschlüssel für Kunden (Customer Root Key, CRK) bestellt werden. Es wird dringend empfohlen, das Verfahren für die Erstellung eines Stammschlüssels für Kunden unter Verwendung vorhandener Schlüsselinformationen zu verwenden und die erstellten Schlüsselinformationen zu sichern. Dadurch stellen Sie sicher, dass Sie Ihre Schlüssel im Falle eines Ausfalls des Rechenzentrums, in dem IBM Key Protect Ihre Stammschlüssel für Kunden speichert, wiederherstellen können.

## Wichtige Hinweise zur Verwendung von KMIP for VMware on IBM Cloud

* Zur Verwendung eines bestellten Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" als Schlüsselmanagementserver (Key Management Server, KMS), der bei VMware vCenter Server registriert ist, müssen Sie sicherstellen, dass die Netzkonnektivität von vCenter Server zum Endpunkt des bestellten Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" betriebsfähig ist.
* Zur Verwendung des Service für die VMware vSAN-Verschlüsselung müssen Sie sicherstellen, dass die Netzkonnektivität zwischen den Hosts im Ziel-vSAN und dem Endpunkt des bestellten Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" betriebsfähig ist.

## Hinweise zum Entfernen von KMIP on IBM Cloud

Das öffentliche VMware-Zertifikat, das Sie beim Bestellen oder Verwenden des Service angegeben haben, wird als Clientzertifikat für die Kommunikation mit der Serviceinstanz verwendet. Wenn der Service entfernt wird, werden damit auch alle Verschlüsselungsschlüssel entfernt, die von dieser Serviceinstanz für das zugehörige öffentliche VMware-Zertifikat erstellt wurden.

Bevor Sie den Service entfernen, müssen Sie sicherstellen, dass keine virtuellen Maschinen oder vSANs mit den vom KMIP-Service erstellten Schlüsseln verschlüsselt werden.

### Zugehörige Links

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} bestellen](kmip_ordering.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
