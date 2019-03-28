---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-28"

---

{:faq: data-hd-content-type='faq'}

# Considerazioni sulla rete per le istanze vCenter Server with NSX-T
{: #vc_nsx-t_networkingonvcenterserver}

Esamina le seguenti informazioni per i dettagli sulle considerazioni e sui requisiti di rete per le tue istanze vCenter Server on {{site.data.keyword.cloud}} with NSX-T. Assicurati di soddisfare i requisiti affinché l'istanza funzioni correttamente.

## Componenti di rete per le istanze vCenter Server with NSX-T
{: #vc_nsx-t_networkingonvcenterserver-networking-components}
{: faq}

Per esaminare i componenti di rete inclusi nella tua istanza vCenter Server with NSX-T, vedi [Specifiche tecniche per le istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview-specs).

## Considerazioni su firewall
{: #vc_nsx-t_networkingonvcenterserver-firewall-considerations}
{: faq}

Se utilizzi i firewall, devi configurare le regole per tutte le comunicazioni dalla VSI (Virtual Server Instance) {{site.data.keyword.IBM}} CloudDriver e dalle VM (virtual machine) di SDDC Manager. Queste regole devono consentire a tutti i protocolli di comunicare sugli indirizzi IP `10.0.0.0/8` e `161.26.0.0/16`. Esempi di questi firewall sono i DFW (Distributed Firewall) NSX o i firewall Vyatta.

## Utilizzo di NSX con le tue VM (Virtual Machine)
{: #vc_nsx-t_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

Durante la distribuzione dell'istanza vCenter Server with NSX-T, VMware NSX viene ordinato, installato, concesso in licenza e configurato nella tua istanza. Inoltre, vengono configurati NSX Manager, i controller NSX e NSX Transport Zone e ciascun server ESXi viene configurato con i componenti NSX.

Viene distribuito anche un gateway dei servizi edge NSX per essere utilizzato dalla tua VM del carico di lavoro. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG NSX gestito dal cliente con le tue VM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Considerazioni sulla modifica delle password per i componenti NSX
{: #vc_nsx-t_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

Esamina le seguenti considerazioni prima di modificare le password per NSX Manager, i controller NSX e gli edge NSX:
* Non modificare la password di NSX Manager che puoi trovare nella pagina **Riepilogo** dell'istanza nella console {{site.data.keyword.vmwaresolutions_short}}.
* Puoi modificare le password per i controller NSX. Per istruzioni su come modificare le password per i controller NSX, vedi [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Puoi modificare la password e le impostazioni SSH per il gateway dei servizi edge (ESG) VMware NSX gestito dal cliente. Non modificare la password per il gateway dei servizi edge (ESG) VMware NSX di gestione e il relativo DLR (Distributed Logical Router).

## Link correlati
{: #vc_nsx-t_networkingonvcenterserver-related}

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [Gateway dei servizi edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
