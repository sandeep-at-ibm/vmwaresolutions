---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Angebotsvergleichsdiagramm

Das folgende Diagramm gibt Aufschluss über die Unterschiede bei der Funktionsunterstützung für VMware Cloud Foundation-Instanzen, VMware vCenter Server-Instanzen, VMware vCenter Server with Hybridity Bundle-Instanzen und VMware vSphere-Cluster.

Tabelle 1. Unterstützte Funktionen für Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle und vSphere-Cluster

| Funktion                          | Cloud Foundation    | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Basiert auf erweiterter Automatisierung von {{site.data.keyword.IBM}} <sup>1</sup> | Ja | Ja | Ja | Nein. Muss selbst erstellt und konfiguriert werden. |
| Speicheroptionen        | vSAN                | vSAN oder gemeinsam genutzter Speicher auf Dateiebene (NFS) | vSAN | vSAN oder gemeinsam genutzter Speicher auf Dateiebene (NFS) |
| Anzahl der ESXi-Server im ersten Cluster | 4 | 4 bei vSAN und mindestens 2 bei NFS (3 werden dringend empfohlen) | 4 | 1 zur Skalierung eines vorhandenen Clusters, 4 für neue vSAN-Cluster und mindestens 3 für neue Cluster mit NFS |
| Maximale Anzahl von ESXi-Servern <sup>2</sup> | 32 pro Cluster      | 59 pro Cluster     | 59 pro Cluster | 60 pro Cluster     |
| Cloud-automatisierte Bereitstellung mit mehreren Standorten | Unterstützt bei neuen, in V2.0 oder höher bereitgestellten Instanzen | Unterstützt bei neuen, in V2.0 oder höher bereitgestellten Instanzen | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| ESXi-Server hinzufügen              | Unterstützt           | Unterstützt | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| ESXi-Server entfernen           | Unterstützt           | Unterstützt | Unterstützt | Unterstützt; automatisierte Konfiguration nicht enthalten |
| Unterstützung mehrerer Cluster         | 5 Cluster | 10 Cluster | 10 Cluster | Unterstützt; automatisierte Konfiguration nicht enthalten |
| Vom Kunden verwaltete Updates und Patches für VMware-Stack | IBM CloudDriver- und VMware-Updates | IBM CloudDriver | IBM CloudDriver |Automatisierte Patches nicht enthalten |
| Sicherung und Wiederherstellung            | Unterstützt | Unterstützt | Unterstützt | Automatisierte Konfiguration der Sicherungslösung nicht enthalten |
| Software-Defined Networking   | NSX Enterprise   | NSX Base, Advanced oder Enterprise | NSX Advanced oder Enterprise | NSX Standard, Base oder Enterprise; automatisierte Konfiguration nicht enthalten |
| BYOL für vSphere und vSAN | Vollständig unterstützt pro Cluster   | Vollständig unterstützt pro Cluster     | Nicht unterstützt | Unterstützt |
| BYOL für vCenter und NSX | Vollständig unterstützt pro Instanz   | Vollständig unterstützt pro Instanz     | Nicht unterstützt | Unterstützt |
| Optionen für Aktualisierung der NSX-Lizenz           | Keine   | Upgrade verfügbar von NSX Base auf Advanced oder Enterprise und von NSX Advanced auf Enterprise. Upgrade verfügbar auf vCenter Server with Hybridity Bundle. | Upgrade verfügbar von NSX Advanced auf Enterprise  | Keine |
| vSAN-Lizenzeditionen         | vSAN Advanced oder Enterprise  | vSAN Advanced oder Enterprise  | vSAN Advanced oder Enterprise | vSAN Advanced oder Enterprise  |
| Add-on-Services               | Unterstützt, ohne HCX on {{site.data.keyword.cloud_notm}}.  | Unterstützt, ohne HCX on {{site.data.keyword.cloud_notm}}. Upgrade verfügbar auf vCenter Server with Hybridity Bundle. | Unterstützt, mit HCX on {{site.data.keyword.cloud_notm}}. | Unterstützt; automatisierte Konfiguration nicht enthalten |

**Hinweise**:

<sup>1</sup> Entsprechend einem geprüften Design und mit Verifizierung während der Bereitstellung.

<sup>2</sup> Sie können die Anzahl von ESXi-Servern in einem vSAN-Cluster auf maximal 64 erhöhen. Weitere Informationen finden Sie unter _Wie viele ESXi-Server kann ich zu einem Cluster hinzufügen?_ im Abschnitt [Häufig gestellte Fragen zu ESXi-Servern](faq_esxi.html).

### Zugehörige Links

* [Häufig gestellte Fragen](faq.html)
* [Überblick zu Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Überblick zu vCenter Server Hybridity](../vcenter/vc_hybrid_overview.html)
* [Überblick zu VMware vSphere](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation-Teileliste](../sddc/sd_bom.html)
* [vCenter Server-Teileliste](../vcenter/vc_bom.html)
* [VMware vSphere-Teileliste](../vsphere/vs_bom.html)
