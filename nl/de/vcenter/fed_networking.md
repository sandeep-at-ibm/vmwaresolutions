---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-28"

---

# Hinweise zum Netzbetrieb für VMware Federal-Instanzen

Die Informationen in diesem Abschnitt enthalten Hinweise und Voraussetzungen für den Netzbetrieb Ihrer VMware Federal-Instanzen. Stellen Sie sicher, dass die Voraussetzungen erfüllt sind, damit Ihre Instanzen ordnungsgemäß arbeiten.

## Netzkomponenten für VMware Federal-Instanzen

Informationen zu den Komponenten für den Netzbetrieb, die in Ihrer VMware Federal-Instanz enthalten sind, finden Sie unter [Technische Spezifikationen für VMware Federal on {{site.data.keyword.cloud}}-Instanzen](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances).

## Hinweise zur Firewall

Wenn Sie Firewalls verwenden, müssen Sie Regeln für die gesamte Kommunikation aus der IBM CloudDriver-VSI (VSI – virtuelle Serverinstanz) und den SDDC Manager-VMs konfigurieren. Diese Regeln müssen es zulassen, dass alle Protokolle an den IP-Adressen `10.0.0.0/8` und `161.26.0.0/16` kommunizieren können. Beispiele für solche Firewalls sind NSX Distributed Firewalls (DFW) oder Vyatta-Firewalls.

## NSX mit virtuellen Maschinen verwenden

Während der Bereitstellung der VMware Federal-Instanz wird in Ihrer Instanz VMware NSX bestellt, installiert, lizenziert und konfiguriert. Auch der NSX-Manager, die NSX-Controller und die NSX-Transportzone werden eingerichtet und jeder ESXi-Server wird mit den NSX-Komponenten konfiguriert.

Zur Verwendung durch die Workload-VMs wird außerdem ein NSX Edge Services Gateway bereitgestellt. Weitere Informationen finden Sie unter [Netz zur Verwendung des vom Kunden verwalteten NSX ESG mit eigenen virtuellen Maschinen konfigurieren](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Hinweise zum Ändern von Kennwörtern für NSX-Komponenten

Prüfen Sie vor dem Ändern der Kennwörter für den NSX-Manager, die NSX-Controller und NSX-Edges die folgenden Hinweise:
* Ändern Sie nicht das Kennwort für den NSX-Manager, das auf der Seite **Zusammenfassung** der Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole zu finden ist.
* Sie können Kennwörter für NSX-Controller ändern. Anweisungen zum Ändern der Kennwörter für NSX-Controller finden Sie unter [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Sie können das Kennwort und die SSH-Einstellungen für das vom Kunden verwaltete VMware NSX Edge Services Gateway (ESG) ändern. Ändern Sie nicht das Kennwort vom VMware NSX Edge Services Gateway (ESG) für das Management und vom zugehörigen verteilten logischen Router (Distributed Logical Router, DLR).

### Zugehörige Links

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
