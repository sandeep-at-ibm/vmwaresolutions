---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Benutzer-IDs
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} verwaltet eine Gruppe von Benutzern in Ihrem Konto für die Verwendung durch die {{site.data.keyword.cloud_notm}}-Automatisierung, wenn Sie Operationen, wie das Hinzufügen von Hosts, Clustern oder Speicher zu Ihrer VMware-Instanz, ausführen. In den folgenden Abschnitten finden Sie die Benutzer-IDs für die {{site.data.keyword.cloud_notm}}-Automatisierung.

VMware-Instanzoperationen schlagen fehl, wenn die IBM Benutzer-IDs gelöscht oder inaktiviert oder die entsprechenden Kennwörter geändert werden.
{:important}

## Benutzer-IDs für vCenter und Platform Services Controller
{: #audit_user_ids-vcenter-psc}

Ab Version 2.5 verwendet {{site.data.keyword.vmwaresolutions_short}} die folgenden Benutzer-IDs, um eine standardmäßig integrierte Identitätsquelle in vCenter hinzuzufügen.

Tabelle 1. Benutzer-IDs für vCenter und Platform Services Controller

| User     | Benutzer-ID      | Methode | Beschreibung |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Wird für die VMware-Konfiguration verwendet, wie z. B. die Einrichtung von VMware High Availability und die Erstellung verteilter Switches. Wird nach der Bereitstellung verwendet, um primäre und sekundäre vCenter Server-Instanzen zu paaren. |
| Kunde | customerroot | SSH    | Nur für die Verwendung durch den Kunden erstellt. |
| IBM      | automation@``rootdomäne``<br/>(Active Directory-Benutzer) | HTTP | Wird nach der Bereitstellung zum Hinzufügen und Entfernen von Hosts und Clustern und zum Bereitstellen und Konfigurieren virtueller Maschinen für Add-on-Services verwendet. |
| Kunde | Administrator@vsphere.local | HTTP | Nur für die Verwendung durch den Kunden erstellt. |

HTTP wird für die Einrichtung und Konfiguration von vCenter sowie für VMware-Operationen, wie das Hinzufügen von Hosts, Clustern oder Speicher für das Ressorcenmanagement in vCenter, verwendet.
{:note}

## NSX-Manager-Benutzer-IDs
{: #audit_user_ids-nsx-mgr}

Tabelle 2. NSX-Manager-Benutzer-IDs

| User     | Benutzer-ID      | Beschreibung |
|:---------|:-------------|:------------|
| IBM      | automation@``rootdomäne``<br/>(Active Directory-Benutzer) | Wird nach der Bereitstellung zum Verwalten von NSX-VTEP-IP-Adressen, zum Verwalten von Host- und Clusterkonfigurationen beim Hinzufügen und Entfernen von Hosts und Clustern und zum Verwalten der ESG-Konfiguration für Add-on-Services verwendet, für die ein öffentlicher Netzzugriff für die Lizenzierung, Lizenzaktivierung oder für Nutzungsberichte erforderlich ist. |
| Kunde | Administrator        | Nur für die Verwendung durch den Kunden erstellt. |

## Benutzer-IDs für ESXi-Hosts
{: #audit_user_ids-esxi}

Tabelle 3. ESXi-Host-Benutzer-IDs

| User     | Benutzer-ID      | Beschreibung |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Wird nach der Bereitstellung zum Hinzufügen von zusätzlichem NFS-Speicher, zum Konfigurieren von Routen für diesen Speicher sowie zum Ausführen aller Servervalidierungscodes verwendet. |
| Kunde | root         | Nur für die Verwendung durch den Kunden erstellt. |

## Microsoft Active Directory-Benutzer-IDs
{: #audit_user_ids-ad}

Tabelle 4. Active Directory-Benutzer-IDs

| User     | Benutzer-ID       | Beschreibung |
|:---------|:------------- |:------------|
| IBM      | automation    | Dient zum Hinzufügen eines Hosts, zum Hinzufügen einer virtuellen Maschine für den Service und zum Festlegen von Active Directory- und DNS-Einträgen. |
| Kunde | Administrator | Nur für die Verwendung durch den Kunden erstellt. |

## Zugehörige Links
{: #audit_user_ids-related}

* [Hinweise zum Ändern von vCenter Server-Artefakten](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
