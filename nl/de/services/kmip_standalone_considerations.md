---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: KMIP for VMware, KMIP stand-alone, tech specs KMIP

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

Der Service "KMIP for VMware on {{site.data.keyword.cloud}}" stellt täglich rund um die Uhr einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und zerstören können. Außerdem stellt er Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit.

Der Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" ist als eigenständiger Service verfügbar, ohne einer VMware-Instanz zugeordnet zu sein. Jede Instanz des Service kann eine oder mehrere vCenter Server-Instanzen oder vSphere-Cluster bedienen.

## Technische Spezifikationen für KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

Die folgenden Spezifikationen werden mit dem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" einbezogen:

* Ein VMware-kompatibles Key Management Interoperability Protocol (KMIP)
* Zwei verwaltete Services: [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/catalog/services/key-protect) und [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* Verfügbar in mehreren geografischen Regionen weltweit
* Zwei in jeder Region bereitgestellte KMIP-Netzserviceendpunkte für hohe Verfügbarkeit

## Hinweise zur Installation von KMIP for VMware on IBM Cloud-Instanzen
{: #kmip_standalone_considerations-install}

Lesen Sie die folgenden Hinweise, bevor Sie eine KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz installieren:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} verwendet den IBM Key Protect for {{site.data.keyword.cloud_notm}}-Service oder den {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services-Service (HPCS), um Verschlüsselungsschlüssel zu erstellen, zu verschlüsseln und zu entschlüsseln. Daher müssen Sie vor der Installation von KMIP for VMware on {{site.data.keyword.cloud_notm}} Folgendes sicherstellen:
   * Sie haben eine verwendbare Key Protect- oder HPCS-Serviceinstanz in der {{site.data.keyword.cloud_notm}}-Region bestellt, in der Ihre KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz gehostet werden soll:
      * Weitere Informationen zum Erstellen einer Instanz von Key Protect finden Sie im Abschnitt zum [Bereitstellen des Service](/docs/services/key-protect?topic=key-protect-provision).
      * Weitere Informationen zum Erstellen einer Instanz von HPCS finden Sie im Abschnitt zum [Bereitstellen des Service](/docs/services/hs-crypto?topic=hs-crypto-provision#provision). Zusätzlich zur Bereitstellung des HPCS-Service müssen Sie [Ihre Crypto-Instanz auch initialisieren](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm), damit HPCS schlüsselbezogene Funktionen bereitstellen kann.
   * Es wurde eine {{site.data.keyword.cloud_notm}}-Service-ID unter Beachtung der Schritte in [Service-ID erstellen](/docs/iam?topic=iam-serviceids) erstellt. Diese Service-ID wird verwendet, um auf die von Ihnen erstellte Instanz der Key Protect- oder HPCS-Serviceinstanz zuzugreifen.
   * Sie haben die folgenden Zugriffsebenen für die Service-ID erteilt:
      * Auf Plattformzugriffsebene: Anzeigeberechtigung für Ihre Serviceinstanz von Key Protect oder HPCS.
      * Auf Servicezugriffsebene: Verwaltungsberechtigung für Ihre Serviceinstanz von Key Protect oder HPCS.
   * Sie verfügen über einen API-Schlüssel für die erstellte Service-ID. Der Schlüssel ist zum Bestellen des Service erforderlich.
   * Sie haben mindestens einen Stammschlüssel für Kunden (Customer Root Key, CRK) über die GUI oder API von Key Protect oder HPCS erstellt:
      * Weitere Informationen zum Erstellen von Stammschlüsseln mit der Key Protect-GUI oder -API finden Sie im Abschnitt [Stammschlüssel erstellen](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) oder [IBM Key Protect-API](https://cloud.ibm.com/apidocs/key-protect).
      * Weitere Informationen zum Erstellen von Stammschlüsseln mit der HPCS-GUI oder -API finden Sie im Abschnitt [Stammschlüssel erstellen](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys) oder [IBM Cloud Hyper Protect Crypto Services-API](https://cloud.ibm.com/apidocs/hs-crypto).

     **Wichtig:** Der Service kann nicht ohne Stammschlüssel für Kunden (Customer Root Key, CRK) bestellt werden. Es wird dringend empfohlen, das Verfahren für die Erstellung eines Stammschlüssels für Kunden unter Verwendung vorhandener Schlüsselinformationen zu verwenden und die erstellten Schlüsselinformationen zu sichern. Dadurch stellen Sie sicher, dass Sie Ihre Schlüssel im Falle eines Ausfalls des Rechenzentrums, in dem Key Protect oder HPCS Ihre Stammschlüssel für Kunden speichert, wiederherstellen können.
* Stellen Sie sicher, dass Ihr {{site.data.keyword.cloud_notm}}-Infrastrukturkonto für Virtual Routing and Forwarding (VRF) und für die Verbindung zu Serviceendpunkten aktiviert ist. Weitere Informationen finden Sie in den folgenden Abschnitten:
   * [Virtual Routing and Forwarding (VRF) on IBM Cloud - Übersicht](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Konto über die IBM Cloud-CLI für die Verwendung von Serviceendpunkten aktivieren](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)
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
