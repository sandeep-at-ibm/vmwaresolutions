---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über KMIP for VMware on IBM Cloud

Der Service "KMIP for VMware on {{site.data.keyword.cloud}}" stellt täglich rund um die Uhr einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können. Außerdem stellt er Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit.

Der Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" ist als eigenständiger Service verfügbar, ohne einer VMware-Instanz zugeordnet zu sein. Jede Instanz des Service kann eine oder mehrere Cloud Foundation-Instanzen, vCenter-Serverinstanzen oder vSphere-Cluster bedienen.

**Hinweis**: In diesem Release ist KMIP for VMware on {{site.data.keyword.cloud_notm}} ausschließlich auf die vSphere-Verschlüsselung begrenzt. 

## Technische Spezifikationen für KMIP for VMware on IBM Cloud

Die folgenden Spezifikationen werden mit dem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" einbezogen:

* Ein VMware-kompatibles Key Management Interoperability Protocol (KMIP)
* Ein verwalteter Service
* Verfügbar in mehreren geografischen Regionen weltweit
* Zwei KMIP-Serviceendpunkte in jeder Region für hohe Verfügbarkeit

## Hinweise zur Installation von KMIP for VMware on IBM Cloud-Instanzen

Lesen Sie die folgenden Hinweise, bevor Sie eine KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz installieren:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} verwendet den Service "IBM Key Protect for {{site.data.keyword.cloud_notm}}", um Verschlüsselungsschlüssel zu erstellen, zu verschlüsseln und zu entschlüsseln. Daher müssen Sie vor der Installation von KMIP for VMware on {{site.data.keyword.cloud_notm}} Folgendes sicherstellen:
   * Sie haben einen verwendbaren Key Protect-Service in der {{site.data.keyword.cloud_notm}}-Region bestellt, in der Ihre KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz gehostet werden soll. Weitere Informationen finden Sie unter [Service bereitstellen](/docs/services/key-protect/provision.html).
   * Es wurde eine {{site.data.keyword.cloud_notm}}-Service-ID unter Beachtung der Schritte in [Service-ID erstellen](/docs/iam/serviceid.html) erstellt. Diese Service-ID wird verwendet, um auf die von Ihnen erstellte Instanz des Key Protect-Service zuzugreifen.
   * Sie haben die folgenden Zugriffsebenen für die Service-ID erteilt:
      * Auf Plattformzugriffsebene: Anzeigeberechtigung für Ihre Instanz von IBM Key Protect.
      * Auf Servicezugriffsebene: Verwaltungsberechtigung für Ihre Instanz von IBM Key Protect.
   * Sie verfügen über einen API-Schlüssel für die erstellte Service-ID. Der Schlüssel ist zum Bestellen des Service erforderlich.
   * Sie haben mindestens einen Stammschlüssel für Kunden (Customer Root Key, CRK) in der Key Protect-Benutzerschnittstelle erstellt. Dazu haben Sie die entsprechenden Schritte wie in [Stammschlüssel erstellen](/docs/services/keymgmt/keyprotect_create_root.html) beschrieben ausgeführt oder Sie haben die REST-API in [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect) verwendet.

     **Wichtig:** Der Service kann nicht ohne Stammschlüssel für Kunden (Customer Root Key, CRK) bestellt werden. Es wird dringend empfohlen, das Verfahren für die Erstellung eines Stammschlüssels für Kunden unter Verwendung vorhandener Schlüsselinformationen zu verwenden und die erstellten Schlüsselinformationen zu sichern. Dadurch stellen Sie sicher, dass Sie Ihre Schlüssel im Falle eines Ausfalls des Rechenzentrums, in dem IBM Key Protect Ihre Stammschlüssel für Kunden speichert, wiederherstellen können.
* Stellen Sie sicher, dass Ihr {{site.data.keyword.cloud_notm}}-Infrastrukturkonto für Virtual Routing and Forwarding (VRF) und für die Verbindung zu Serviceendpunkten aktiviert ist. Weitere Informationen finden Sie in den folgenden Abschnitten:
   * [Virtual Routing and Forwarding (VRF) on IBM Cloud - Übersicht](/docs/infrastructure/direct-link/vrf-on-ibm-cloud.html)
   * [Konto für die Verwendung von Serviceendpunkten unter Verwendung der IBM Cloud-CLI aktivieren](/docs/services/service-endpoint/enable-servicepoint.html#getting-started)
* Da nur die private Verbindung unterstützt wird, müssen Sie keine Firewall- oder SNAT-Regeln in vCenter Server für die Netzkonnektivität von vCenter Server zum Endpunkt der KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz konfigurieren.

Weitere Informationen finden Sie unter [KMIP for VMware on IBM Cloud - Lösungsarchitektur](/docs/services/vmwaresolutions/archiref/kmip/overview.html).

## Hinweise zur Löschung von KMIP for VMware on IBM Cloud-Instanzen

Alle Daten, die vom Service "KMIP for VMware on IBM Cloud" geschützt sind, einschließlich verschlüsselter Sicherungen, können nicht entschlüsselt werden, nachdem Sie den Service entfernt haben.

### Zugehörige Links

* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen bestellen](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html)
* [Zertifikate für KMIP for VMware on IBM Cloud-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen anzeigen](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen löschen](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions/vmonic/at-events.html)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
