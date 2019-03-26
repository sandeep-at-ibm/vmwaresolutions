---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:faq: data-hd-content-type='faq'}

# Hinweise zum Netzbetrieb für Cloud Foundation-Instanzen
{: #sd_networkingoncloudfoundation}

Die Informationen in diesem Abschnitt enthalten Hinweise und Voraussetzungen für den Netzbetrieb Ihrer Cloud Foundation-Instanzen. Stellen Sie sicher, dass die Voraussetzungen erfüllt sind, damit Ihre Instanzen ordnungsgemäß arbeiten.

## Netzkomponenten für Cloud Foundation-Instanzen
{: #sd_networkingoncloudfoundation-networking-components}
{: faq}

Informationen zu den Komponenten für den Netzbetrieb, die in Ihrer Cloud Foundation-Instanz enthalten sind, finden Sie unter [Technische Spezifikationen für Cloud Foundation-Instanzen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances).

## Hinweise zur Firewall
{: #sd_networkingoncloudfoundation-firewall-considerations}
{: faq}

Wenn Sie Firewalls verwenden, müssen Sie Regeln für die gesamte Kommunikation aus der {{site.data.keyword.IBM}} CloudDriver-VSI (VSI - virtuelle Serverinstanz) und den SDDC Manager-VMs konfigurieren. Diese Regeln müssen es zulassen, dass alle Protokolle an den IP-Adressen `10.0.0.0/8` und `161.26.0.0/16` kommunizieren können. Beispiele für solche Firewalls sind NSX Distributed Firewalls (DFW) oder Vyatta-Firewalls.

## VMware NSX mit virtuellen Maschinen verwenden
{: #sd_networkingoncloudfoundation-using-nsx-with-vm}
{: faq}

Während der Bereitstellung der Cloud Foundation-Instanz wurde in Ihrer Instanz VMware NSX bestellt, installiert, lizenziert und konfiguriert. Auch der NSX-Manager, die NSX-Controller und die NSX-Transportzone werden eingerichtet und jeder ESXi-Server wird mit den NSX-Komponenten konfiguriert.

Wenn Ihre Workload-VMs jedoch miteinander kommunizieren und auf das internet zugreifen müssen, liegt es in Ihrer Verantwortung, NSX für die Verwendung durch Ihre VMs zu konfigurieren.

Weitere Informationen zur Vorgehensweise beim Einrichten von NSX finden Sie in den folgenden Abschnitten:
* Lesen Sie bezüglich einer primären (einzelnen) Cloud Foundation-Instanz den Abschnitt [Setting up NSX for workload VMs on VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Informationen zu einer Cloud Foundation-Instanz in einer Konfiguration mit mehreren Standorten finden Sie in [Sichere Verbindung für private VMware-Workloads in {{site.data.keyword.cloud_notm}} herstellen](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.

## Hinweise zum Ändern von Kennwörtern für NSX-Komponenten
{: #sd_networkingoncloudfoundation-considerations-when-change-nsx-component-password}
{: faq}

Prüfen Sie vor dem Ändern der Kennwörter für den NSX-Manager, die NSX-Controller und die NSX-Edge die folgenden Hinweise:
* Ändern Sie nicht das Kennwort für den NSX-Manager. Dieses Kennwort finden Sie auf der Seite **Zusammenfassung** der Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
* Sie können Kennwörter für NSX-Controller ändern. Anweisungen zum Ändern der Kennwörter für NSX-Controller finden Sie unter [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Das Kennwort vom VMware NSX Edge Services Gateway (ESG) für das Management kann nicht geändert werden.

## Zugehörige Links
{: #sd_networkingoncloudfoundation-related}

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
