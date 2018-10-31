---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Angebotsvergleichsdiagramm

Das folgende Diagramm gibt Aufschluss über die Unterschiede bei der Funktionsunterstützung für VMware Cloud Foundation-Instanzen, VMware vCenter Server-Instanzen, VMware vCenter Server with Hybridity Bundle-Instanzen und VMware vSphere-Cluster.

Tabelle 1. Unterstützte Funktionen für Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle und vSphere-Cluster

| Funktion                          | Cloud Foundation    | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Basiert auf erweiterter Automatisierung von {{site.data.keyword.IBM}} <sup>1</sup> | Ja | Ja | Ja | Nein. Muss selbst erstellt und konfiguriert werden. |
| Speicheroptionen        | vSAN                | vSAN oder gemeinsam genutzter Speicher auf Dateiebene (NFS) | vSAN | vSAN oder gemeinsam genutzter Speicher auf Dateiebene (NFS) |
| Anzahl der ESXi-Server im ersten Cluster | 4 | 4 bei vSAN und mindestens 2 ( empf. Wert: 3) bei NFS | 4 | 1 zur Skalierung eines vorhandenen Clusters, 4 für neue vSAN-Cluster und mindestens 3 für neue Cluster mit NFS |
| Maximale Anzahl von ESXi-Servern <sup>2</sup> | 32 pro Cluster      | 59 pro Cluster     | 59 pro Cluster | 60 pro Cluster     |
| Cloud-automatisierte Bereitstellung mit mehreren Standorten | Unterstützt bei neuen, in V2.0 oder höher bereitgestellten Instanzen | Unterstützt bei neuen, in V2.0 oder höher bereitgestellten Instanzen | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| ESXi-Server hinzufügen              | Unterstützt           | Unterstützt | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| ESXi-Server entfernen           | Unterstützt           | Unterstützt | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| Unterstützung mehrerer Cluster         | 5 Cluster | 10 Cluster | 10 Cluster | Unterstützt; automatisierte Konfiguration nicht enthalten |
| Vom Kunden verwaltete Updates und Patches für VMware-Stack | VMware-Updates | Nicht enthalten | Nicht enthalten | Nicht enthalten |
| Sicherung und Wiederherstellung            | Manuell mit IBM Spectrum Protect Plus oder Veeam | Manuell mit IBM Spectrum Protect Plus oder Veeam | Manuell mit IBM Spectrum Protect Plus oder Veeam | Sicherungs- und Wiederherstellungslösung nicht enthalten |
| Software-Defined Networking   | NSX Enterprise   | NSX Base, Advanced oder Enterprise | NSX Advanced oder Enterprise | NSX Standard, Base oder Enterprise; automatisierte Konfiguration nicht enthalten |
| BYOL für vSphere und vSAN | Vollständig unterstützt pro Cluster   | Vollständig unterstützt pro Cluster     | Nicht unterstützt | Unterstützt |
| BYOL für vCenter und NSX | Vollständig unterstützt pro Instanz   | Vollständig unterstützt pro Instanz     | Nicht unterstützt | Unterstützt |
| Optionen für Aktualisierung der NSX-Lizenz           | Keine   | Upgrade verfügbar von NSX Base auf Advanced oder Enterprise und von NSX Advanced auf Enterprise. Upgrade verfügbar auf vCenter Server with Hybridity Bundle. | Upgrade verfügbar von NSX Advanced auf Enterprise  | Keine |
| vSAN-Lizenzeditionen         | vSAN Advanced oder Enterprise  | vSAN Advanced oder Enterprise  | vSAN Advanced oder Enterprise | vSAN Advanced oder Enterprise  |
| Add-on-Services               | Unterstützt, ohne HCX on {{site.data.keyword.cloud_notm}}.  | Unterstützt, ohne HCX on {{site.data.keyword.cloud_notm}}. Upgrade verfügbar auf vCenter Server with Hybridity Bundle. | Unterstützt, mit HCX on {{site.data.keyword.cloud_notm}}. | Von der Automatisierung dieser Lösung nicht unterstützt, jedoch können Sie eigene Software installieren und verwenden. |

**Hinweise:**

<sup>1</sup> Entsprechend einem geprüften Design und mit Verifizierung während der Bereitstellung.

<sup>2</sup> Sie können die Anzahl von ESXi-Servern in einem vSAN-Cluster auf maximal 64 erhöhen. Weitere Informationen finden Sie unter _Wie viele ESXi-Server kann ich zu einem Cluster hinzufügen?_ im Abschnitt [Häufig gestellte Fragen zu ESXi-Servern](faq_esxi.html).

### Zugehörige Links

* [Häufig gestellte Fragen](faq.html)
* [Übersicht über Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Übersicht über vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Übersicht über vCenter Server Hybridity](../vcenter/vc_hybrid_overview.html)
* [Übersicht über VMware vSphere](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation-Teileliste](../sddc/sd_bom.html)
* [vCenter Server-Teileliste](../vcenter/vc_bom.html)
* [VMware vSphere-Teileliste](../vsphere/vs_bom.html)
