---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Hinweise zum Netzbetrieb für vCenter Server with Hybridity Bundle-Instanzen

Die Informationen in diesem Abschnitt enthalten Hinweise und Voraussetzungen für den Netzbetrieb Ihrer VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanzen. Stellen Sie sicher, dass die Voraussetzungen erfüllt sind, damit Ihre Instanzen ordnungsgemäß arbeiten.

## Netzkomponenten für vCenter Server with Hybridity Bundle-Instanzen

Informationen zu den Komponenten für den Netzbetrieb, die in Ihrer vCenter Server with Hybridity Bundle-Instanz enthalten sind, finden Sie im Abschnitt _Technische Spezifikationen für vCenter Server with Hybridity Bundle_ im [Überblick zu vCenter Server with Hybridity Bundle](vc_hybrid_overview.html).

## Hinweise zur NSX-Firewall

Wenn Sie NSX Distributed Firewalls (DFW) verwenden, überprüfen Sie die folgenden Voraussetzungen:
* Sie müssen Regeln für die gesamte Kommunikation aus der virtuellen Maschine für {{site.data.keyword.IBM}} CloudDriver konfigurieren, damit alle Protokolle an den IP-Adressen `10.0.0.0/8` und `161.26.0.0/16` kommunizieren können.
* Sie müssen eine DFW-Regel erstellen, die den HTTPS-Datenverkehr aus der VM für IBM CloudDriver an ein beliebiges Ziel zulässt.
* Die DFW-Regel muss vor allen anderen Regeln angegeben sein, die den Datenverkehr zu oder aus diesen VMs blockieren.

## NSX mit virtuellen Maschinen verwenden

Während der Bereitstellung der vCenter Server-Instanz wird in Ihrer Instanz VMware NSX bestellt, installiert, lizenziert und konfiguriert. Auch der NSX-Manager, die NSX-Controller und die NSX-Transportzone werden eingerichtet und jeder ESXi-Server wird mit den NSX-Komponenten konfiguriert.

Ebenfalls wird zur Verwendung durch die Workload-VMs ein NSX Edge Services Gateway bereitgestellt. Weitere Informationen finden Sie unter [Netz zur Verwendung des vom Kunden verwalteten NSX ESG mit eigenen virtuellen Maschinen konfigurieren](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Hinweise zum Ändern von Kennwörtern für NSX-Komponenten

Prüfen Sie vor dem Ändern der Kennwörter für den NSX-Manager, die NSX-Controller und NSX-Edges die folgenden Hinweise:
* Ändern Sie nicht das Kennwort für den NSX-Manager, das auf der Seite **Zusammenfassung** der Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole zu finden ist.
* Sie können Kennwörter für NSX-Controller ändern. Anweisungen zum Ändern der Kennwörter für NSX-Controller finden Sie unter [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Sie können das Kennwort und die SSH-Einstellungen für das vom Kunden verwaltete VMware NSX Edge Services Gateway (ESG) ändern. Ändern Sie nicht das Kennwort vom VMware NSX Edge Services Gateway (ESG) für das Management und vom zugehörigen verteilten logischen Router (Distributed Logical Router, DLR).

## Zugehörige Links

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
* [Überblick zu VMware HCX on IBM Cloud](../services/hcx_considerations.html)
