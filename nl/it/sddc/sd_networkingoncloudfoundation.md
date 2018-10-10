---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-04"

---

# Considerazioni sulla rete per le istanze Cloud Foundation

Rivedi le seguenti informazioni per i dettagli sulle considerazioni e sui requisiti di rete per le tue istanze Cloud Foundation. Assicurati di soddisfare i requisiti affinché l'istanza funzioni correttamente.

## Componenti di rete per le istanze Cloud Foundation

Per esaminare i componenti di rete inclusi nella tua istanza Cloud Foundation, vedi [Specifiche tecniche per le istanze Cloud Foundation](sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Considerazioni su firewall

Se utilizzi i firewall, devi configurare le regole per tutte le comunicazioni dalla VSI (Virtual Server Instance) {{site.data.keyword.IBM}} CloudDriver e dalle VM (virtual machine) di SDDC Manager. Queste regole devono consentire a tutti i protocolli di comunicare sugli indirizzi IP `10.0.0.0/8` e `161.26.0.0/16`. Esempi di questi firewall sono i DFW (Distributed Firewall) NSX o i firewall Vyatta.

## Utilizzo di VMware NSX con le tue VM

Durante la distribuzione dell'istanza Cloud Foundation, VMware NSX viene ordinato, installato, concesso in licenza e configurato nella tua istanza. Inoltre, vengono configurati NSX Manager, i controller NSX e NSX Transport Zone e ciascun server ESXi viene configurato con i componenti NSX.

Tuttavia, se le tue VM del carico di lavoro devono comunicare tra loro e accedere a Internet, è tua responsabilità configurare NSX per l'utilizzo da parte delle tue VM.

Per ulteriori informazioni su come configurare NSX, vedi i seguenti argomenti:
* Per un'istanza primaria (singola) di Cloud Foundation, vedi [Setting up NSX for workload VMs on VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Per un'istanza Cloud Foundation multisito, vedi Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Considerazioni sulla modifica delle password per i componenti NSX

Esamina le seguenti considerazioni prima di modificare le password per NSX Manager, i controller NSX e l'edge NSX:
* Non modificare la password per NSX Manager. Puoi trovare questa password nella pagina **Riepilogo** dell'istanza nella console {{site.data.keyword.vmwaresolutions_short}}.
* Puoi modificare le password per i controller NSX. Per istruzioni su come modificare le password per i controller NSX, vedi [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Non modificare la password per il gateway dei servizi edge (ESG) VMware NSX di gestione.

### Link correlati

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [Gateway dei servizi edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
