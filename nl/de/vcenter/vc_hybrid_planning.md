---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-01"

---

# Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_planning}

Überprüfen Sie die nachstehenden Voraussetzungen, bevor Sie Ihre VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanzen bestellen. Legen Sie der Planung für Ihre Instanz den Standort von {{site.data.keyword.CloudDataCent_notm}} sowie Ihre Anforderungen an die Workloadkapazität und Ihren Bedarf an zusätzlichen Services zugrunde.

## Voraussetzungen für IBM Cloud-Konto
{: #vc_hybrid_planning-account-req}

Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Konto](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Verfügbarkeit des IBM Cloud-Rechenzentrums
{: #vc_hybrid_planning-dc-availability}

Die vCenter Server with Hybridity Bundle-Bereitstellung stellt strenge Anforderungen an die physische Infrastruktur. Sie können Instanzen daher nur in {{site.data.keyword.CloudDataCents_notm}} bereitstellen, die diese Anforderungen erfüllen. Die folgenden {{site.data.keyword.CloudDataCents_notm}} stehen für die Bereitstellung von vCenter Server with Hybridity Bundle zur Verfügung:

Tabelle 1. Verfügbare {{site.data.keyword.CloudDataCents_notm}} für vCenter Server with Hybridity Bundle-Instanzen

| {{site.data.keyword.CloudDataCent_notm}} | Standort | Region |
|:----------------------|:---------|:---------------|
| AMS03 | Amsterdam | Europa |
| CHE01 | Chennai | Asien/Pazifik |
| DAL09 | Dallas | NA Süd |
| DAL10 | Dallas | NA Süd |
| DAL12 | Dallas | NA Süd |
| DAL13 | Dallas | NA Süd |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| HKG02 | Hongkong | Asien/Pazifik |
| LON02 | London | Europa |
| LON04 | London | Europa |
| LON06 | London | Europa |
| MEL01 | Melbourne | Asien/Pazifik |
| MEX01 | Queretaro | NA Süd |
| MIL01 | Mailand | Europa |
| MON01 | Montreal | NA Ost |
| OSL01 | Oslo | Europa |
| PAR01 | Paris | Europa |
| SAO01 | Sao Paulo | Südamerika |
| SEO01 | Seoul | Asien/Pazifik |
| SJC03 | San Jose | NA West |
| SJC04 | San Jose | NA West |
| SNG01 | Singapur | Asien/Pazifik |
| SYD01 | Sydney | Asien/Pazifik |
| SYD04 | Sydney | Asien/Pazifik |
| TOK02 | Tokio | Asien/Pazifik |
| TOK04 | Tokio | Asien/Pazifik |
| TOR01 | Toronto | NA Ost |
| WDC04 | Washington, DC | NA Ost |
| WDC06 | Washington, DC | NA Ost |
| WDC07 | Washington, DC | NA Ost |

Je nach Verfügbarkeit und Bestandsangebot ist für {{site.data.keyword.CloudDataCents_notm}} möglicherweise ein Statusanzeiger in der {{site.data.keyword.vmwaresolutions_short}}-Konsole dargestellt, der Ihnen bei der Planung Ihrer Bereitstellungen hilft.

Tabelle 2. Statusanzeiger für {{site.data.keyword.CloudDataCents_notm}} bei der Bestellung von vCenter Server with Hybridity Bundle-Instanzen

| Status | Statusdetails |
|:------------------------------|:--------------------------------------------------|
| Demnächst verfügbar                   | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Vorübergehend ohne Bestand  | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Eingeschränkter Bestand             | Das {{site.data.keyword.CloudDataCent_notm}} bietet eine begrenzte Verfügbarkeit und die Bestellung kann möglicherweise nicht ausgeführt werden. |

## Sicherung von Managementkomponenten
{: #vc_hybrid_planning-backup-mgmt-components}

Sie sind für die Erhaltung und Sicherstellung der Verfügbarkeit aller Instanzkomponenten verantwortlich. Es wird dringend empfohlen, die Sicherung oder Hochverfügbarkeit aller Managementkomponenten zu planen. Weitere Informationen finden Sie unter [Komponenten sichern](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services für vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_planning-addon-services}

Die vCenter Server with Hybridity Bundle-Instanz beinhaltet die Lizenzierung von VMware Hybrid Cloud Extension (HCX) und berechtigt Sie zur Verwendung des Service "VMware HCX on {{site.data.keyword.cloud_notm}}". Dieser Service kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist.

Geben Sie beim Bereitstellen dieses Service die folgenden Einstellungen an:
* Geben Sie den **HCX-Verbindungstyp** durch Auswählen einer der folgenden Optionen an:
  * **Öffentliches Netz**: HCX stellt eine verschlüsselte Verbindung zwischen Standorten im öffentlichen Netz her.
  * **Privates Netz**: HCX stellt eine verschlüsselte Verbindung zwischen Standorten im privaten Netz her.
* Geben Sie den **Zertifikatstyp für den öffentlichen Endpunkt** an. Bei Auswahl von **CA-Zertifikat** konfigurieren Sie die folgenden Einstellungen:
  * **Zertifikatsinhalt**: Geben Sie den Inhalt des CA-Zertifikats ein.
  * **Privater Schlüssel**: Geben Sie den privaten Schlüssel des CA-Zertifikats ein.
  * (Optional) **Kennwort**: Geben Sie das Kennwort für den privaten Schlüssel ein, wenn er verschlüsselt ist.
  * (Optional) **Kennwort erneut eingeben**: Geben Sie das Kennwort für den privaten Schlüssel erneut ein.
  * (Optional) **Hostname**: Geben Sie den Hostnamen ein, der dem allgemeinen Namen (Common Name, CN) des CA-Zertifikats zugeordnet werden soll. HCX on {{site.data.keyword.cloud_notm}} setzt voraus, dass das CA-Zertifikat in einem Format vorliegt, das von NSX Edge akzeptiert wird. Weitere Informationen zu den Zertifikatsformaten von NSX Edge finden Sie unter [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

Sie können für Ihre Instanz auf der Basis Ihrer Anforderungen weitere Add-on-Services bestellen, zum Beispiel für die Disaster-Recovery. Weitere Informationen finden Sie unter [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices).

## Kapazitätsaspekte
{: #vc_hybrid_planning-capacity-considerations}

Weitere Informationen zu Kapazitätsaspekten finden Sie unter [Skalierungskapazität](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Zugehörige Links
{: #vc_hybrid_planning-related}

* [Übersicht über vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
