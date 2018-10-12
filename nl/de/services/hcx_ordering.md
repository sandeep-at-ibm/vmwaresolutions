---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-17"

---

# VMware HCX on IBM Cloud bestellen

Sie können den Service "VMware HCX on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz von VMware vCenter Server with Hybridity Bundle, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## VMware HCX on IBM Cloud für eine neue Instanz bestellen

Wählen Sie zum Bestellen einer neuen Instanz von VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle mit VMware HCX on {{site.data.keyword.cloud_notm}} den Service **VMware HCX on IBM Cloud** im Abschnitt **Services** aus, wenn Sie die Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen.


## VMware HCX on IBM Cloud für eine vorhandene Instanz bestellen

Wenn Sie den Service "VMware HCX on {{site.data.keyword.cloud_notm}}" einer vorhandenen Instanz von VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle hinzufügen möchten, zeigen Sie die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.

## VMware HCX on IBM Cloud - Konfiguration

Geben Sie zum Installieren von HCX on {{site.data.keyword.cloud_notm}} die folgenden Einstellungen an:
1. Geben Sie den **HCX-Verbindungstyp** durch Auswählen einer der folgenden Optionen an:
  * **Öffentliches Netz**: HCX stellt eine verschlüsselte Verbindung zwischen Standorten im öffentlichen Netz her. Die Lizenzregistrierung und -messung erfolgt über das öffentliche Netz.
  * **Private Verbindung**: HCX stellt über das private Netz eine verschlüsselte Verbindung zwischen Standorten her. Die Lizenzregistrierung und -messung erfolgt über das öffentliche Netz.
  * **Privates Netz**: HCX stellt eine verschlüsselte Verbindung zwischen Standorten im privaten Netz her. Die Lizenzregistrierung und -messung erfolgt im privaten Netz über den HTTP-Proxy.
3. Bei Auswahl von **Privates Netz** müssen Sie folgende Felder ausfüllen:
  * **Proxy-Adresse**: Die IPv4-Adresse des Proxy-Servers.
  * **Proxy-Port**: Der Port des Proxy-Servers. Die Portnummer ist in der Regel 8080 oder 3128.
  * **Benutzername**: Der Benutzername, falls eine Proxy-Authentifizierung erforderlich ist.
  * **Kennwort**: Das Kennwort, falls eine Proxy-Authentifizierung erforderlich ist.
  * **Kennwort erneut eingeben**: Geben Sie zur Überprüfung der Proxy-Authentifizierung erneut das Kennwort ein.
2. Geben Sie den **Zertifikatstyp für den öffentlichen Endpunkt** an. Bei Auswahl von **CA-Zertifikat** konfigurieren Sie die folgenden Einstellungen:
  * **Zertifikatsinhalt**: Geben Sie den Inhalt des CA-Zertifikats ein.
  * **Privater Schlüssel**: Geben Sie den privaten Schlüssel des CA-Zertifikats ein.
  * (Optional) **Kennwort**: Geben Sie das Kennwort für den privaten Schlüssel ein, wenn er verschlüsselt ist.
  * (Optional) **Kennwort erneut eingeben**: Geben Sie das Kennwort für den privaten Schlüssel erneut ein.
  * (Optional) **Hostname**: Geben Sie den Hostname ein, der dem allgemeinen Namen (Common Name, CN) des CA-Zertifikats zugeordnet werden soll. HCX on {{site.data.keyword.cloud_notm}} erfordert, dass das Format des CA-Zertifikats von NSX Edge akzeptiert wird. Weitere Informationen zu den Zertifikatsformaten von NSX Edge finden Sie unter [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Bereitstellungsprozess für HCX on IBM Cloud

Die Bereitstellung von HCX on {{site.data.keyword.cloud_notm}} ist automatisiert. Unabhängig davon, ob Sie die vCenter Server with Hybridity Bundle-Instanz mit enthaltenem Service bestellen oder den Service später in Ihrer Instanz bereitstellen, werden vom {{site.data.keyword.vmwaresolutions_short}}-Automatisierungsprozess die folgenden Schritte ausgeführt:
1. Über die {{site.data.keyword.cloud_notm}}-Infrastruktur werden drei Teilnetze für HCX bestellt:
   * Ein privates portierbares Teilnetz für das HCX-Management.
   * Ein privates portierbares Teilnetz für HCX-Verbindungen. Dieses Teilnetz wird bei Auswahl der Option **Privates Netz** für den **HCX-Verbindungstyp** verwendet.
   * Ein öffentliches portierbares Teilnetz für die Aktivierung und Wartung mit VMware. Bei Auswahl der Option **Öffentliches Netz** für den **HCX-Verbindungstyp** wird dieses Teilnetz auch für HCX-Verbindungen verwendet.

   **Wichtig:** Die IP-Adresse in den für HCX bestellten Teilnetzen sollten durch die Automatisierung von VMware on {{site.data.keyword.cloud_notm}} verwaltet werden. Diese IP-Adressen können nicht zu VMware-Ressourcen wie VMs und NSX-Edges zugeordnet werden, die von Ihnen erstellt worden sind. Wenn Sie zusätzliche IP-Adressen für Ihre VMware-Artefakte benötigen, müssen Sie Ihre eigenen Teilnetze aus {{site.data.keyword.cloud_notm}} bestellen.
2. Wenn für **HCX-Verbindungstyp** die Option **Privates Netz** ausgewählt wurde, wird auf dem privaten verteilten virtuellen Switch (Distributed Virtual Switch, DVS) eine Portgruppe namens **SDDC-DPortGroup-HCX-Private** erstellt.
3. Es wird ein HCX-Aktivierungsschlüssel von VMware bestellt.
4. Es werden drei Ressourcenpools und VM-Ordner für HCX erstellt. Diese werden für die HCX-Verbindungen, die lokalen HCX-Komponenten sowie die fernen HCX-Komponenten benötigt.
5. Ein Paar von VMware NSX Edge Services Gateways (ESGs) für den HCX-Managementdatenverkehr wird bereitgestellt und konfiguriert:
   * Öffentliche und private Uplink-Schnittstellen werden unter Verwendung der bestellten Teilnetze konfiguriert.
   * Die ESGs werden als ein Paar sehr großer Edge-Appliances mit aktivierter Hochverfügbarkeit konfiguriert.
   * Die Firewallregeln und die Regeln für die Netzadressumsetzung (NAT-Regeln) werden konfiguriert, damit eingehender und abgehender HTTPS-Datenverkehr an den und vom HCX-Manager zulässig ist.
   * Die Regeln für den Lastausgleich und Ressourcenpools werden konfiguriert. Diese Regeln und Ressourcenpools werden für die Weiterleitung des HCX-bezogenen eingehenden Datenverkehrs an die entsprechenden virtuellen Appliances für den HCX-Manager, für vCenter Server und für Platform Services Controller (PSC) verwendet.
   * Ein SSL-Zertifikat zum Verschlüsseln des HCX-bezogenen eingehenden HTTPS-Datenverkehrs, der über die ESGs eintrifft, wird angewendet.

   **Wichtig**: Das HCX-Management-Edge ist für den HCX-Managementdatenverkehr zwischen den lokalen HCX-Komponenten und den cloudseitigen HCX-Komponenten dediziert. Das HCX-Management-Edge darf weder geändert noch für HCX-Netzerweiterungen verwendet werden. Erstellen Sie für Netzerweiterungen stattdessen separate Edges. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der HCX-Edge-Kommunikation mit den privaten IBM Managementkomponenten oder dem öffentlichen Internet die HCX-Funktionalität beeinträchtigen kann.

6. Der HCX-Manager on {{site.data.keyword.cloud_notm}} wird bereitgestellt, aktiviert und konfiguriert:
   * Der HCX-Manager wird bei vCenter Server registriert.
   * Der HCX-Manager, vCenter Server, PSC und der NSX-Manager werden konfiguriert.
   * Das HCX-Produktpaket wird konfiguriert.
   * Lokale und ferne HCX-Bereitstellungscontainer werden konfiguriert.
7. Der Hostname und die IP-Adresse des HCX-Managers werden beim DNS-Server von VMware vCenter Server on {{site.data.keyword.cloud_notm}} registriert.

### Zugehörige Links

* [Übersicht über HCX on {{site.data.keyword.cloud_notm}}](hcx_considerations.html)
* [HCX on {{site.data.keyword.cloud_notm}} verwalten](managinghcx.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_hybrid_addingremovingservices.html)
* [Glossar der HCX-Begriffe](hcx_glossary.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
