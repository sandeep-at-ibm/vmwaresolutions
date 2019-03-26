---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

# Angebotsvergleichsdiagramm
{: #inst_comp_chart}

Das folgende Diagramm gibt Aufschluss über die Unterschiede bei der Funktionsunterstützung für VMware vCenter Server-Instanzen, VMware vCenter Server with Hybridity Bundle-Instanzen und VMware vSphere-Clustern. 

Tabelle 1. Unterstützte Funktionen für vCenter Server, vCenter Server with Hybridity Bundle und vSphere-Cluster

| Funktion | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Basiert auf erweiterter Automatisierung von {{site.data.keyword.IBM}} <sup>1</sup> | Ja | Ja | Nein. Muss selbst erstellt und konfiguriert werden. |
| Speicheroptionen | vSAN oder NFS (gemeinsam genutzter Speicher auf Dateiebene) | vSAN oder NFS <sup>2</sup> | vSAN oder NFS |
| Anzahl der ESXi-Server im ersten Cluster | 4 bei vSAN und mindestens 2 ( empf. Wert: 3) bei NFS | 4 | 1 zur Skalierung eines vorhandenen Clusters, 4 für neue vSAN-Cluster und mindestens 3 für neue Cluster mit NFS |
| Maximale Anzahl von ESXi-Servern <sup>3</sup> | 59 pro Cluster | 59 pro Cluster | 60 pro Cluster |
| Cloudautomatisierte Bereitstellung mit mehreren Standorten |Unterstützt bei neuen, in V2.0 oder höher bereitgestellten Instanzen | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| ESXi-Server hinzufügen | Unterstützt | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| ESXi-Server entfernen | Unterstützt | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| Unterstützung mehrerer Cluster | Maximale Anzahl von Richtlinien zur VMware-Dimensionierung abhängig | Maximale Anzahl von Richtlinien zur VMware-Dimensionierung abhängig | Unterstützt; automatisierte Konfiguration nicht enthalten |
| Vom Kunden verwaltete Updates und Patches für VMware-Stack | Vom Kunden verwaltete Aktualisierungen:<br/>Native VMware-Tools (VMware Update Manager) | Vom Kunden verwaltete Aktualisierungen:<br/>Native VMware-Tools (VMware Update Manager) | Vom Kunden verwaltete Aktualisierungen:<br/>Native VMware-Tools (VMware Update Manager) |
| Sicherung und Wiederherstellung | Manuell mit IBM Spectrum Protect Plus oder Veeam | Manuell mit IBM Spectrum Protect Plus oder Veeam | Sicherungs- und Wiederherstellungslösung nicht enthalten |
| Software-Defined Networking | NSX Base, Advanced oder Enterprise | NSX Advanced oder Enterprise | NSX Standard, Base oder Enterprise; automatisierte Konfiguration nicht enthalten |
| BYOL für vSphere und vSAN | Vollständig unterstützt pro Cluster | Nicht unterstützt | Unterstützt |
| BYOL für vCenter und NSX | Vollständig unterstützt pro Instanz | Nicht unterstützt | Unterstützt |
| Optionen für Aktualisierung der NSX-Lizenz | Upgrade verfügbar von NSX Base auf Advanced oder Enterprise und von NSX Advanced auf Enterprise. Upgrade verfügbar auf vCenter Server with Hybridity Bundle. | Upgrade verfügbar von NSX Advanced auf Enterprise  | Keine |
| vSAN-Lizenzeditionen | vSAN Advanced oder Enterprise | vSAN Advanced oder Enterprise | vSAN Advanced oder Enterprise  |
| Add-on-Services | Unterstützt, ohne HCX on {{site.data.keyword.cloud_notm}}. Upgrade verfügbar auf vCenter Server with Hybridity Bundle. | Unterstützt, mit HCX on {{site.data.keyword.cloud_notm}}. | Von der Automatisierung dieser Lösung nicht unterstützt, jedoch können Sie eigene Software installieren und verwenden. |

## Hinweise
{: #inst_comp_chart-notes}

<sup>1</sup> Entsprechend einem geprüften Design und mit Verifizierung während der Bereitstellung.

<sup>2</sup> vSAN nur für neue vCenter Server with Hybridity-Instanzen und Cluster. Nach der Bereitstellung können Sie NFS-Speicher hinzufügen. 

<sup>3</sup> Sie können die Anzahl der ESXi-Server in einem vSAN-Cluster auf maximal 64 erhöhen. Weitere Informationen finden Sie unter _Wie viele ESXi-Server kann ich zu einem Cluster hinzufügen?_ im Abschnitt [Häufig gestellte Fragen zu ESXi-Servern](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi).

## Zugehörige Links
{: #inst_comp_chart-related}

* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Übersicht über vCenter Server Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Übersicht über VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [VMware vSphere-Teileliste](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
