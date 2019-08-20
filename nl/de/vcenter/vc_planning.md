---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Voraussetzungen und Planung für vCenter Server-Instanzen
{: #vc_planning}

Überprüfen Sie die nachstehenden Voraussetzungen, bevor Sie Ihre VMware vCenter Server-Instanzen bestellen. Legen Sie der Planung für Ihre Instanz den Standort von {{site.data.keyword.CloudDataCent}} sowie Ihre Anforderungen an die Workloadkapazität und Ihren Bedarf an Add-on-Services zugrunde.

## Voraussetzungen für IBM Cloud-Konto
{: #vc_planning-account-req}

Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Konto](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## Verfügbarkeit des IBM Cloud-Rechenzentrums
{: #vc_planning-dc-availability}

Die vCenter Server-Bereitstellung stellt strenge Anforderungen an die physische Infrastruktur. Sie können Instanzen daher nur in {{site.data.keyword.CloudDataCents_notm}} bereitstellen, die diese Anforderungen erfüllen. Die folgenden {{site.data.keyword.CloudDataCents_notm}} stehen für die Bereitstellung von vCenter Server zur Verfügung.

Cascade Lake-{{site.data.keyword.baremetal_short}} sind in Mehrzonen-Regionen (MZR)-{{site.data.keyword.CloudDataCents_notm}} verfügbar. Weitere Informationen finden Sie in [Mehrzonen-Region (MZR) - Übersicht
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Standort | Region | Serveroptionen |
|:----------------------|:---------|:-------|:---------------|
| AMS01 | Amsterdam | Europa | Skylake, SAP-zertifiziert, Broadwell |
| AMS03 | Amsterdam | Europa | Skylake, SAP-zertifiziert, Broadwell |
| CHE01 | Chennai | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| DAL09 | Dallas | NA Süd | Skylake, SAP-zertifiziert, Broadwell |
| DAL10 | Dallas | NA Süd | Skylake, SAP-zertifiziert, Broadwell |
| DAL12 | Dallas | NA Süd | Skylake, SAP-zertifiziert, Broadwell |
| DAL13 | Dallas | NA Süd | Skylake, SAP-zertifiziert, Broadwell |
| FRA02 | Frankfurt | Europa | Skylake, SAP-zertifiziert, Broadwell |
| FRA04 | Frankfurt | Europa | Skylake, SAP-zertifiziert, Broadwell |
| FRA05 | Frankfurt | Europa | Skylake, SAP-zertifiziert, Broadwell |
| HKG02 | Hongkong | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| LON02 | London | Europa | Skylake, Broadwell |
| LON04 | London | Europa | Skylake, SAP-zertifiziert, Broadwell |
| LON05 | London | Europa | Skylake, Broadwell |
| LON06 | London | Europa | Skylake, SAP-zertifiziert, Broadwell |
| MEL01 | Melbourne | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| MEX01 | Queretaro | NA Süd | Skylake, SAP-zertifiziert, Broadwell |
| MIL01 | Mailand | Europa | Skylake, SAP-zertifiziert, Broadwell |
| MON01 | Montreal | NA Ost | Skylake, SAP-zertifiziert, Broadwell |
| OSL01 | Oslo | Europa | Skylake, SAP-zertifiziert, Broadwell |
| PAR01 | Paris | Europa | Skylake, SAP-zertifiziert, Broadwell |
| SAO01 | Sao Paulo | Südamerika | Skylake, SAP-zertifiziert, Broadwell |
| SEO01 | Seoul | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapur | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| SYD01 | Sydney | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| SYD04 | Sydney | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| SYD05 | Sydney | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| TOK02 | Tokio | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| TOK04 | Tokio | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| TOK05 | Tokio | Asien/Pazifik | Skylake, SAP-zertifiziert, Broadwell |
| TOR01 | Toronto | NA Ost | Skylake, SAP-zertifiziert, Broadwell |
| WDC04 | Washington, DC | NA Ost | Skylake, SAP-zertifiziert, Broadwell |
| WDC06 | Washington, DC | NA Ost | Skylake, SAP-zertifiziert, Broadwell |
| WDC07 | Washington, DC | NA Ost | Skylake, SAP-zertifiziert, Broadwell |
{: caption="Tabelle 1. Verfügbare {{site.data.keyword.CloudDataCents_notm}} für vCenter Server-Instanzen" caption-side="top"}

Je nach Verfügbarkeit und Bestandsangebot ist für {{site.data.keyword.CloudDataCents_notm}} möglicherweise ein Statusanzeiger in der {{site.data.keyword.vmwaresolutions_short}}-Konsole dargestellt, der Ihnen bei der Planung Ihrer Bereitstellungen hilft.

| Status | Statusdetails |
|:------------------------------|:--------------------------------------------------|
| Demnächst verfügbar                   | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Vorübergehend ohne Bestand  | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Eingeschränkter Bestand             | Das {{site.data.keyword.CloudDataCent_notm}} bietet eine begrenzte Verfügbarkeit und die Bestellung kann möglicherweise nicht ausgeführt werden. |
{: caption="Tabelle 2. Statusanzeiger für {{site.data.keyword.CloudDataCents_notm}} bei der Bestellung von vCenter Server-Instanzen" caption-side="top"}

## Sicherung von Managementkomponenten
{: #vc_planning-backup-mgmt-components}

Sie sind für die Erhaltung und Sicherstellung der Verfügbarkeit aller Instanzkomponenten verantwortlich. Es wird dringend empfohlen, die Sicherung oder Hochverfügbarkeit aller Managementkomponenten zu planen. Weitere Informationen finden Sie unter [Komponenten sichern](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services für vCenter Server-Instanzen
{: #vc_planning-addon-services}

Sie können für Ihre Instanz auf der Basis Ihrer Anforderungen Add-on-Services bestellen, zum Beispiel für die Disaster-Recovery. Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

Services werden für vCenter Server with NSX-T-Instanzen unterstützt.
{:note}

### Planung für VMware HCX on IBM Cloud
{: #vc_planning-addon-services-hcx}

Der VMware HCX on {{site.data.keyword.cloud_notm}}-Service kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist.

Geben Sie beim Bereitstellen dieses Service die folgenden Einstellungen an:
* Geben Sie den **HCX-Verbindungstyp** durch Auswählen einer der folgenden Optionen an:
  * **Öffentliches Netz**: HCX stellt eine verschlüsselte Verbindung zwischen Standorten im öffentlichen Netz her.
  * **Privates Netz**: HCX stellt eine verschlüsselte Verbindung zwischen Standorten im privaten Netz her.
* Geben Sie den **Zertifikatstyp für den öffentlichen Endpunkt** an. Bei Auswahl von **CA-Zertifikat** konfigurieren Sie die folgenden Einstellungen:
  * **Zertifikatsinhalt**: Geben Sie den Inhalt des CA-Zertifikats ein.
  * **Privater Schlüssel**: Geben Sie den privaten Schlüssel des CA-Zertifikats ein.
  * (Optional) **Kennwort**: Geben Sie das Kennwort für den privaten Schlüssel ein, wenn er verschlüsselt ist.
  * (Optional) **Kennwort erneut eingeben**: Geben Sie das Kennwort für den privaten Schlüssel erneut ein.
  * (Optional) **Hostname**: Geben Sie den Hostnamen ein, der dem allgemeinen Namen (Common Name, CN) des CA-Zertifikats zugeordnet werden soll. HCX on {{site.data.keyword.cloud_notm}} setzt voraus, dass das CA-Zertifikat in einem Format vorliegt, das von NSX Edge akzeptiert wird. Weitere Informationen zu den Zertifikatsformaten von NSX Edge finden Sie unter [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.

## Kapazitätsaspekte
{: #vc_planning-capacity-considerations}

Weitere Informationen zu Kapazitätsaspekten finden Sie unter [Skalierungskapazität](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Zugehörige Links
{: #vc_planning-related}

* [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
