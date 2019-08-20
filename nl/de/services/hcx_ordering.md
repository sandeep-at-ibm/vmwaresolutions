---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX deployment, HCX configuration, order HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud bestellen
{: #hcx_ordering}

Sie können den VMware HCX on {{site.data.keyword.cloud}}-Service durch Bestellen einer neuen VMware vCenter Server-Instanz mit enthaltenem Service oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

Für die Bestellung des VMware HCX on {{site.data.keyword.cloud_notm}}-Service ist eine Verpflichtung über 12 Monate erforderlich. Wenn Sie einen Host oder Cluster vor dem Ende des 12-monatigen Verpflichtungszeitraums löschen, wird Ihr Konto weiterhin für die HCX-Komponenten belastet.
{:important}

Wählen Sie zum Bestellen einer neuen Instanz von VMware vCenter Server mit VMware HCX on {{site.data.keyword.cloud_notm}} im Abschnitt **Services** die Option **HCX on IBM Cloud 3.5** aus, sofern Sie die Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen.


## VMware HCX on IBM Cloud für eine vorhandene Instanz bestellen
{: #hcx_ordering-existing}

Zum Hinzufügen des VMware HCX on {{site.data.keyword.cloud_notm}}-Service zu einer vorhandenen VMware vCenter Server-Instanz zeigen Sie die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und dann auf **Hinzufügen**.

## VMware HCX on IBM Cloud - Konfiguration
{: #hcx_ordering-config}

Geben Sie zum Installieren von HCX on {{site.data.keyword.cloud_notm}} die folgenden Einstellungen an:
1. Wählen Sie die entsprechenden Kontrollkästchen aus, um zu bestätigen, dass Sie mit den Bedingungen einverstanden sind, die mit der Bestellung des HCX on {{site.data.keyword.cloud_notm}}-Service verbunden sind.

   Nach Ablauf des 12-monatigen Verpflichtungszeitraums werden diese Kontrollkästchen nicht mehr angezeigt.
   {:note}

2. Geben Sie **HCX-Netzverbindung** an, indem Sie eine der folgenden Optionen auswählen:
  * **Öffentliches Netz:** HCX stellt eine verschlüsselte Verbindung zwischen Standorten im öffentlichen Netz her. Die Lizenzregistrierung und -messung erfolgt über das öffentliche Netz.
  * **Private Verbindung:** HCX stellt über das private Netz eine verschlüsselte Verbindung zwischen Standorten her. Die Lizenzregistrierung und -messung erfolgt über das öffentliche Netz.
  * **Privates Netz:** HCX stellt über das private Netz eine verschlüsselte Verbindung zwischen Standorten her. Die Lizenzregistrierung und -messung erfolgt im privaten Netz über den HTTP-Proxy.
3. Bei Auswahl von **Privates Netz** müssen Sie folgende Felder ausfüllen:
  * **Proxy-Adresse:** Die IPv4-Adresse des Proxy-Servers.
  * **Proxy-Port:** Der Port des Proxy-Servers. Die Portnummer ist in der Regel 8080 oder 3128.
  * **Benutzername:** Der Benutzername, falls eine Proxy-Authentifizierung erforderlich ist.
  * **Kennwort:** Das Kennwort, falls eine Proxy-Authentifizierung erforderlich ist.
  * **Kennwort erneut eingeben:** Geben Sie zur Überprüfung der Proxy-Authentifizierung erneut das Kennwort ein.
2. Geben Sie den **Zertifikatstyp für den öffentlichen Endpunkt** an. Bei Auswahl von **CA-Zertifikat** konfigurieren Sie die folgenden Einstellungen:
  * **Zertifikatsinhalt:** Geben Sie den Inhalt des CA-Zertifikats ein.
  * **Privater Schlüssel:** Geben Sie den privaten Schlüssel des CA-Zertifikats ein.
  * (Optional) **Kennwort:** Geben Sie das Kennwort für den privaten Schlüssel ein, wenn er verschlüsselt ist.
  * (Optional) **Kennwort erneut eingeben:** Geben Sie das Kennwort für den privaten Schlüssel erneut ein.
  * (Optional) **Hostname:** Geben Sie den Hostname ein, der dem allgemeinen Namen (Common Name, CN) des CA-Zertifikats zugeordnet werden soll. HCX on {{site.data.keyword.cloud_notm}} erfordert, dass das Format des CA-Zertifikats von NSX Edge akzeptiert wird. Weitere Informationen zu den Zertifikatsformaten von NSX Edge finden Sie unter [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Bereitstellungsprozess für HCX on IBM Cloud
{: #hcx_ordering-deploy}

Die Bereitstellung von HCX on {{site.data.keyword.cloud_notm}} ist automatisiert. Unabhängig davon, ob Sie die vCenter Server-Instanz mit enthaltenem Service bestellen oder den Service später in Ihrer Instanz bereitstellen, werden vom {{site.data.keyword.vmwaresolutions_short}}-Automatisierungsprozess die folgenden Schritte ausgeführt:
1. Über die {{site.data.keyword.cloud_notm}}-Infrastruktur werden drei Teilnetze für HCX bestellt:
   * Ein privates portierbares Teilnetz für das HCX-Management.
   * Ein privates portierbares Teilnetz für HCX-Verbindungen. Dieses Teilnetz wird bei Auswahl der Option **Privates Netz** für den **HCX-Verbindungstyp** verwendet.
   * Ein öffentliches portierbares Teilnetz für die Aktivierung und Wartung mit VMware. Bei Auswahl der Option **Öffentliches Netz** für den **HCX-Verbindungstyp** wird dieses Teilnetz auch für HCX-Verbindungen verwendet.

   Die IP-Adresse in den für HCX bestellten Teilnetzen sollten durch die Automatisierung von VMware on {{site.data.keyword.cloud_notm}} verwaltet werden. Diese IP-Adressen können nicht zu VMware-Ressourcen wie VMs und NSX-Edges zugeordnet werden, die von Ihnen erstellt worden sind. Wenn Sie zusätzliche IP-Adressen für Ihre VMware-Artefakte benötigen, müssen Sie Ihre eigenen Teilnetze aus {{site.data.keyword.cloud_notm}} bestellen.
   {:important}
2. Wenn für **HCX-Netzverbindung** die Option **Privates Netz** ausgewählt wurde, wird auf dem privaten verteilten virtuellen Switch (Distributed Virtual Switch, DVS) eine Portgruppe namens **SDDC-DPortGroup-HCX-Private** erstellt.
3. Es wird ein HCX-Aktivierungsschlüssel von VMware bestellt.
4. Es werden drei Ressourcenpools und VM-Ordner für HCX erstellt. Diese werden für die HCX-Verbindungen, die lokalen HCX-Komponenten sowie die fernen HCX-Komponenten benötigt.
5. Ein Paar von VMware NSX Edge Services Gateways (ESGs) für den HCX-Managementdatenverkehr wird bereitgestellt und konfiguriert:
   * Öffentliche und private Uplink-Schnittstellen werden unter Verwendung der bestellten Teilnetze konfiguriert.
   * Die ESGs werden als ein Paar sehr großer Edge-Appliances mit aktivierter Hochverfügbarkeit konfiguriert.
   * Die Firewallregeln und die Regeln für die Netzadressumsetzung (NAT-Regeln) werden konfiguriert, damit eingehender und abgehender HTTPS-Datenverkehr an den und vom HCX-Manager zulässig ist.
   * Die Regeln für den Lastausgleich und Ressourcenpools werden konfiguriert. Diese Regeln und Ressourcenpools werden verwendet, um den HCX-bezogenen eingehenden Datenverkehr an die entsprechenden virtuellen Appliances von HCX Manager und vCenter Server (mit Embedded Platform Services Controller) weiterzuleiten.
   * Ein SSL-Zertifikat zum Verschlüsseln des HCX-bezogenen eingehenden HTTPS-Datenverkehrs, der über die ESGs eintrifft, wird angewendet.

   Die HCX-Management-Edge ist für den HCX-Managementdatenverkehr zwischen den lokalen HCX-Komponenten und den cloudseitigen HCX-Komponenten dediziert. Das HCX-Management-Edge darf weder geändert noch für HCX-Netzerweiterungen verwendet werden. Erstellen Sie für Netzerweiterungen stattdessen separate Edges. Außerdem kann die Verwendung einer Firewall oder die Inaktivierung der HCX-Edge-Kommunikation mit den privaten IBM Managementkomponenten oder dem öffentlichen Internet die HCX-Funktionalität beeinträchtigen.
   {:important}

6. Der HCX-Manager on {{site.data.keyword.cloud_notm}} wird bereitgestellt, aktiviert und konfiguriert:
   * Der HCX-Manager wird bei vCenter Server registriert.
   * Der HCX-Manager, vCenter Server (mit integriertem Platform Services Controller) und NSX-Manager sind konfiguriert.
   * Das HCX-Produktpaket wird konfiguriert.
   * Lokale und ferne HCX-Bereitstellungscontainer werden konfiguriert.
7. Der Hostname und die IP-Adresse des HCX-Managers werden beim DNS-Server von VMware vCenter Server on {{site.data.keyword.cloud_notm}} registriert.

## Zugehörige Links
{: #hcx_ordering-related}

* [HCX on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [HCX on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Glossar der HCX-Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Überblick über VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Dokumentation zu VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
