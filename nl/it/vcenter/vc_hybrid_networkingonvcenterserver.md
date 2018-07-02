---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Considerazioni sulla rete per le istanze vCenter Server with Hybridity Bundle

Rivedi le seguenti informazioni per i dettagli sulle considerazioni e sui requisiti di rete per le tue istanze VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Assicurati di soddisfare i requisiti affinché l'istanza funzioni correttamente.

## Componenti di rete per le istanze vCenter Server with Hybridity Bundle

Per esaminare i componenti di rete inclusi nella tua istanza vCenter Server with Hybridity Bundle, vedi la sezione _Specifiche tecniche per vCenter Server with Hybridity Bundle_ in [Panoramica di vCenter Server with Hybridity Bundle](vc_hybrid_overview.html).

## Considerazioni sul firewall NSX

Se utilizzi i DFW (Distributed Firewall) NSX, esamina i seguenti requisiti:
* Devi configurare regole per tutte le comunicazioni dalla macchina virtuale di {{site.data.keyword.IBM}} CloudDriver per consentire a tutti i protocolli di comunicare sugli indirizzi IP `10.0.0.0/8` e `161.26.0.0/16`.
* Devi creare una regola DFW che consenta il traffico HTTPS dalla VM IBM CloudDriver a qualsiasi destinazione.
* La regola DFW deve precedere qualsiasi altra regola che blocchi il traffico da o verso queste VM.

## Utilizzo di NSX con le tue macchine virtuali

Durante la distribuzione dell'istanza vCenter Server, VMware NSX viene ordinato, installato, concesso in licenza e configurato nella tua istanza. Inoltre, vengono configurati il gestore NSX, i controller NSX e NSX Transport Zone e ciascun server ESXi viene configurato con i componenti NSX.

Viene distribuito anche un gateway dei servizi edge NSX per essere utilizzato con le tue VM del carico di lavoro. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG NSX gestito dal cliente con le tue VM](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Considerazioni sulla modifica delle password per i componenti NSX

Esamina le seguenti considerazioni prima di modificare le password per il gestore NSX, i controller NSX e gli edge NSX:
* Non modificare la password del gestore NSX che puoi trovare nella pagina **Riepilogo** dell'istanza nella console {{site.data.keyword.vmwaresolutions_short}}.
* Puoi modificare le password per i controller NSX. Per istruzioni su come modificare le password per i controller NSX, vedi [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Puoi modificare la password e le impostazioni SSH per il gateway dei servizi edge (ESG) VMware NSX gestito dal cliente. Non modificare la password per il gateway dei servizi edge (ESG) VMware NSX di gestione e il relativo DLR (Distributed Logical Router).

## Link correlati

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [Gateway dei servizi edge NSX](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
* [Panoramica di VMware HCX on IBM Cloud](../services/hcx_considerations.html)
