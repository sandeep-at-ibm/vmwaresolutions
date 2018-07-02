---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Hinweise zum Netzbetrieb für Cloud Foundation-Instanzen

Die Informationen in diesem Abschnitt enthalten Hinweise und Voraussetzungen für den Netzbetrieb Ihrer Cloud Foundation-Instanzen. Stellen Sie sicher, dass die Voraussetzungen erfüllt sind, damit Ihre Instanzen ordnungsgemäß arbeiten.

## Netzkomponenten für Cloud Foundation-Instanzen

Informationen zu den Komponenten für den Netzbetrieb, die in Ihrer Cloud Foundation-Instanz enthalten sind, finden Sie unter [Komponenten der Cloud Foundation-Instanz](sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

## Hinweise zur Firewall

Wenn Sie NSX Distributed Firewalls (DFW) verwenden, überprüfen Sie die folgenden Voraussetzungen:
* Sie müssen Regeln für die gesamte Kommunikation aus den virtuellen Maschinen für {{site.data.keyword.IBM}} CloudDriver und SDDC Manager konfigurieren, damit alle Protokolle an den IP-Adressen `10.0.0.0/8` und `161.26.0.0/16` kommunizieren können.
* Sie müssen eine DFW-Regel erstellen, die den HTTPS-Datenverkehr aus der VM für IBM CloudDriver an ein beliebiges Ziel zulässt.
* Die DFW-Regel muss vor allen anderen Regeln angegeben sein, die den Datenverkehr zu oder aus diesen VMs blockieren.

## VMware NSX mit virtuellen Maschinen verwenden

Während der Bereitstellung der Cloud Foundation-Instanz wird in Ihrer Instanz VMware NSX bestellt, installiert, lizenziert und konfiguriert. Auch der NSX-Manager, die NSX-Controller und die NSX-Transportzone werden eingerichtet und jeder ESXi-Server wird mit den NSX-Komponenten konfiguriert.

Wenn Ihre Workload-VMs jedoch miteinander kommunizieren und auf das Internet zugreifen müssen, liegt es in Ihrer Verantwortung, NSX für die Verwendung durch Ihre VMs zu konfigurieren.

Informationsquellen für die Konfiguration von NSX:
* Lesen Sie bezüglich einer primären (einzelnen) Cloud Foundation-Instanz den Abschnitt [Setting up NSX for workload VMs on VMware Cloud Foundation on IBM Cloud](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Lesen Sie im Zusammenhang mit einer Cloud Foundation-Instanz in einer Konfiguration mit mehreren Standorten den Artikel [Securely connect your private VMware workloads in the IBM Cloud](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Hinweise zum Ändern von Kennwörtern für NSX-Komponenten

Prüfen Sie vor dem Ändern der Kennwörter für den NSX-Manager, die NSX-Controller und die NSX-Edge die folgenden Hinweise:
* Ändern Sie nicht das Kennwort für den NSX-Manager. Dieses Kennwort finden Sie auf der Seite **Zusammenfassung** der Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
* Sie können Kennwörter für NSX-Controller ändern. Anweisungen zum Ändern der Kennwörter für NSX-Controller finden Sie unter [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Das Kennwort vom VMware NSX Edge Services Gateway (ESG) für das Management kann nicht geändert werden.

## Zugehörige Links

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway]( https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
