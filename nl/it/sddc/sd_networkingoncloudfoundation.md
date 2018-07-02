---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Considerazioni sulla rete per le istanze Cloud Foundation

Rivedi le seguenti informazioni per i dettagli sulle considerazioni e sui requisiti di rete per le tue istanze Cloud Foundation. Assicurati di soddisfare i requisiti affinché l'istanza funzioni correttamente.

## Componenti di rete per le istanze Cloud Foundation

Per esaminare i componenti di rete inclusi nella tua istanza Cloud Foundation, vedi [Componenti dell'istanza Cloud Foundation](sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

## Considerazioni su firewall

Se utilizzi i DFW (Distributed Firewall) NSX, esamina i seguenti requisiti:
* Devi configurare regole per tutte le comunicazioni dalle macchine virtuali (VM) di {{site.data.keyword.IBM}} CloudDriver e SDDC Manager per consentire a tutti i protocolli di comunicare sugli indirizzi IP `10.0.0.0/8` e `161.26.0.0/16`.
* Devi creare una regola DFW che consenta il traffico HTTPS dalla VM IBM CloudDriver a qualsiasi destinazione.
* La regola DFW deve precedere qualsiasi altra regola che blocchi il traffico da o verso queste VM.

## Utilizzo di VMware NSX con le tue VM

Durante la distribuzione dell'istanza Cloud Foundation, VMware NSX viene ordinato, installato, concesso in licenza e configurato nella tua istanza. Inoltre, vengono configurati il gestore NSX, i controller NSX e NSX Transport Zone e ciascun server ESXi viene configurato con i componenti NSX.

Tuttavia, se le tue macchine virtuali del carico di lavoro devono comunicare tra loro e accedere a Internet, è tua responsabilità configurare NSX per l'utilizzo da parte delle macchine virtuali.

Per informazioni su come configurare NSX:
* Per un'istanza primaria (singola) di Cloud Foundation, vedi [Setting up NSX for workload VMs on VMware Cloud Foundation on IBM Cloud](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Per un'istanza Cloud Foundation multisito, vedi [Securely connect your private VMware workloads in the IBM Cloud](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Considerazioni sulla modifica delle password per i componenti NSX

Esamina le seguenti considerazioni prima di modificare le password per il gestore NSX, i controller NSX e l'edge NSX:
* Non modificare le password per il gestore NSX. Puoi trovare questa password nella pagina **Riepilogo** dell'istanza nella console {{site.data.keyword.vmwaresolutions_short}}.
* Puoi modificare le password per i controller NSX. Per istruzioni su come modificare le password per i controller NSX, vedi [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Non modificare la password per il gateway dei servizi edge (ESG) VMware NSX di gestione.

## Link correlati

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [Gateway dei servizi edge NSX]( https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
