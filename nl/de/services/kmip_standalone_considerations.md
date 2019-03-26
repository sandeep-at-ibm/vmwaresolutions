---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

Der Service "KMIP for VMware on {{site.data.keyword.cloud}}" stellt täglich rund um die Uhr einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können. Außerdem stellt er Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit.

Der Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" ist als eigenständiger Service verfügbar, ohne einer VMware-Instanz zugeordnet zu sein. Jede Instanz des Service kann eine oder mehrere Cloud Foundation-Instanzen, vCenter-Serverinstanzen oder vSphere-Cluster bedienen.

## Technische Spezifikationen für KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

Die folgenden Spezifikationen werden mit dem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" einbezogen:

* Ein VMware-kompatibles Key Management Interoperability Protocol (KMIP)
* Ein verwalteter Service
* Verfügbar in mehreren geografischen Regionen weltweit
* Zwei in jeder Region bereitgestellte KMIP-Netzserviceendpunkte für hohe Verfügbarkeit

## Hinweise zur Installation von KMIP for VMware on IBM Cloud-Instanzen
{: #kmip_standalone_considerations-install}

Lesen Sie die folgenden Hinweise, bevor Sie eine KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz installieren:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} verwendet den Service "IBM Key Protect for {{site.data.keyword.cloud_notm}}", um Verschlüsselungsschlüssel zu erstellen, zu verschlüsseln und zu entschlüsseln. Daher müssen Sie vor der Installation von KMIP for VMware on {{site.data.keyword.cloud_notm}} Folgendes sicherstellen:
   * Sie haben einen verwendbaren Key Protect-Service in der {{site.data.keyword.cloud_notm}}-Region bestellt, in der Ihre KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz gehostet werden soll. Weitere Informationen finden Sie unter [Service bereitstellen](/docs/services/key-protect?topic=key-protect-provision).
   * Es wurde eine {{site.data.keyword.cloud_notm}}-Service-ID unter Beachtung der Schritte in [Service-ID erstellen](/docs/iam?topic=iam-serviceids) erstellt. Diese Service-ID wird verwendet, um auf die von Ihnen erstellte Instanz des Key Protect-Service zuzugreifen.
   * Sie haben die folgenden Zugriffsebenen für die Service-ID erteilt:
      * Auf Plattformzugriffsebene: Anzeigeberechtigung für Ihre Instanz von IBM Key Protect.
      * Auf Servicezugriffsebene: Verwaltungsberechtigung für Ihre Instanz von IBM Key Protect.
   * Sie verfügen über einen API-Schlüssel für die erstellte Service-ID. Der Schlüssel ist zum Bestellen des Service erforderlich.
   * Sie haben mindestens einen Stammschlüssel für Kunden (Customer Root Key, CRK) in der Key Protect-Benutzerschnittstelle erstellt. Dazu haben Sie die entsprechenden Schritte wie in [Stammschlüssel erstellen](/docs/services/keymgmt/keyprotect_create_root.html) beschrieben ausgeführt oder Sie haben die REST-API in [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect) verwendet.

     **Wichtig:** Der Service kann nicht ohne Stammschlüssel für Kunden (Customer Root Key, CRK) bestellt werden. Es wird dringend empfohlen, das Verfahren für die Erstellung eines Stammschlüssels für Kunden unter Verwendung vorhandener Schlüsselinformationen zu verwenden und die erstellten Schlüsselinformationen zu sichern. Dadurch stellen Sie sicher, dass Sie Ihre Schlüssel im Falle eines Ausfalls des Rechenzentrums, in dem IBM Key Protect Ihre Stammschlüssel für Kunden speichert, wiederherstellen können.
* Stellen Sie sicher, dass Ihr {{site.data.keyword.cloud_notm}}-Infrastrukturkonto für Virtual Routing and Forwarding (VRF) und für die Verbindung zu Serviceendpunkten aktiviert ist. Weitere Informationen finden Sie in den folgenden Abschnitten:
   * [Virtual Routing and Forwarding (VRF) on IBM Cloud - Übersicht](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Konto für die Verwendung von Serviceendpunkten unter Verwendung der IBM Cloud-CLI aktivieren](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* Da nur die private Verbindung unterstützt wird, müssen Sie keine Firewall- oder SNAT-Regeln in vCenter Server für die Netzkonnektivität von vCenter Server zum Endpunkt der KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz konfigurieren.

Weitere Informationen finden Sie unter [KMIP for VMware on IBM Cloud - Lösungsarchitektur](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview).

## Hinweise zur Löschung von KMIP for VMware on IBM Cloud-Instanzen
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

Alle Daten, die vom Service "KMIP for VMware on IBM Cloud" geschützt sind, einschließlich verschlüsselter Sicherungen, können nicht entschlüsselt werden, nachdem Sie den Service entfernt haben.

## Zugehörige Links
{: #kmip_standalone_considerations-related}

* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Zertifikate für KMIP for VMware on IBM Cloud-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen anzeigen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanzen löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
