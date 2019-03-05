---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Entfernen von HCX
{: #vcshcx-removal}

Für die Entfernung von HCX wird davon ausgegangen, dass keine erweiterten Netze mehr in Gebrauch sind. Gehen Sie wie folgt vor, um HCX zu entfernen.

1. Machen Sie die Ausdehnung aller erweiterten Netzwerke rückgängig.
2. Löschen Sie in der Clientbenutzerschnittstelle alle L2C-Appliances. Warten Sie, bis die L2C-Appliances von der Webbenutzerschnittstelle entfernt wurden.
3. Löschen Sie das Cloud-Gateway (CGW). Damit wird auch das WAN-Optimierungsprogramm entfernt. Warten Sie, bis die Appliances des CGW und des WAN-Optimierungsprogramms gelöscht wurden.
4. Beenden und löschen Sie die virtuellen Maschinen (VMs) der HCX-Manager-Appliance auf Client- und auf Cloud-Seite.
5. Entfernen Sie das ESG von HCX von der NSX-Cloudseite.
6. Verwenden Sie den vCenter-Mob-Browser, um das HCX-Snap-in zu entfernen.

## Zugehörige Links
{: #vcshcx-removal-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
