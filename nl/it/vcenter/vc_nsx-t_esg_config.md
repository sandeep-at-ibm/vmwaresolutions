---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configurazione della rete per utilizzare l'ESG NSX-T gestito dal cliente con le tue VM
{: #vc_nsx-t_esg_config}

Configura la rete per le tue VM (Virtual Machine) in modo da poter usufruire del gateway dei servizi edge (ESG, Edge Services Gateway) VMware NSX-T che viene distribuito nelle tue istanze VMware vCenter Server. Per ulteriori informazioni sulle misure di sicurezza implementate per ridurre al minimo il rischio di sicurezza, vedi [L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T è una piattaforma di virtualizzazione di rete che consente la virtualizzazione di reti isolate e fornisce numerosi servizi
di rete come switch, instradamento e firewall. Per ulteriori informazioni su NSX, vedi [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Come parte del processo di ordine per la tua istanza di vCenter Server with NSX-T, le seguenti azioni vengono completate per tuo conto:
* Una sottorete del cliente privata viene ordinata per essere utilizzata dalle tue VM (Virtual Machine) per accedere alla rete privata dell'infrastruttura {{site.data.keyword.cloud}}.
* Una sottorete del cliente pubblica viene ordinata per consentire alla tue VM di accedere a Internet.
* NSX-T viene distribuito e configurato nella tua istanza vCenter Server with NSX-T.
* Uno switch logico NSX-T di esempio viene distribuito per essere utilizzato dalle VM del carico di lavoro del cliente.
* Un router NSX-T Tier 1 di esempio viene distribuito per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2).
* Un dispositivo Edge NSX-T viene distribuito e configurato per eseguire la conversione degli indirizzi di rete (NAT) dall'intervallo di indirizzi IP
dello switch logico del carico di lavoro a un indirizzo IP pubblico sulle regole NAT.

  L'edge NSX-T non viene distribuito per le istanze che sono solo private.
  {:note}

## Procedura per configurare le impostazioni di rete per le tue VM
{: #vc_nsx-t_esg_config-procedure-config-networking}

Per usufruire di NSX-T per le tue VM del carico di lavoro, devi configurare una serie di impostazioni completando le seguenti operazioni quando crei le VM:

1. Imposta l'adattatore di rete della VM sullo switch logico del carico di lavoro:
   1. Nella casella di dialogo **Nuova VM (Virtual Machine)**, fai clic sulla scheda **Personalizza hardware**.
   2. Nel menu **nuovo dispositivo**, seleziona **Rete** e fai clic su **Aggiungi**.
   3. Sull'adattatore di rete appena aggiunto, seleziona lo switch logico di sovrapposizione del carico di lavoro dal menu. Il nome dell'esempio dello switch è **overlay-ls**.

   Assicurati di non selezionare lo switch **Workload Transit**.
   {:important}

2. Identifica un indirizzo IP disponibile per la VM:
   *  L'indirizzo IP deve essere compreso nell'intervallo `192.168.10.0/24`. Nota che l'indirizzo IP `192.168.10.1` è riservato (vedi il **Passo 3**).
   *  Quando configuri la rete del sistema operativo che viene eseguito sulla VM, utilizza l'indirizzo IP selezionato e la maschera di rete
   `255.255.255.0`.

   Sei responsabile della gestione dell'intervallo di indirizzi IP a cui hai assegnato le tue VM.
   {:note}

3. Assegna il gateway predefinito della VM come `192.168.10.1`. Questo è l'indirizzo IP della porta del router di downlink sul router logico Tier 1 ed è collegato allo stesso switch logico di sovrapposizione delle VM del carico di lavoro.

## Abilitazione della regola SNAT
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

NSX-T abilita la regola SNAT per impostazione predefinita. Per informazioni sulla modifica di regole esistenti, vedi [Configure Source and Destination NAT on a Tier-0 Logical Router](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}.

## Procedura per identificare i dettagli delle sottoreti del cliente
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

I router logici **Customer-T1-LR** e **Customer-T0-LR** così come gli edge **cust-nsx-edge0** e **cust-nsx-edge1** sono destinati al tuo utilizzo personale, quindi puoi modificarli per definire più regole NAT per il traffico in entrata o in uscita. Queste regole devono utilizzare solo gli indirizzi IP sulle sottoreti del cliente pubbliche o private ordinate a tuo nome.

Per identificare i dettagli per le sottoreti del cliente in modo da poter utilizzare gli indirizzi IP ordinati, completa la seguente procedura nel client web NSX-T:

1. Fai clic sulla scheda **Advanced Networking & Security**.
2. Sul pannello di sinistra, fai clic su **Fabric**, poi sull'elenco a discesa e seleziona **Nodes**.
3. Sulla scheda, seleziona **Edge Transport Nodes**.
4. Fai clic su uno degli edge del cliente. Ad esempio, **cust-nsx-edge0**. Le sottoreti del cliente pubblica e privata vengono visualizzate nel campo **Description**.

Inoltre, puoi trovare ulteriori dettagli sulle sottoreti del cliente completando la seguente procedura nel 	{{site.data.keyword.slportal}}:

1. Fai clic su **Networking > IP Management > Subnets**.
2. Fai clic sul menu del filtro e, nel campo **Sottorete**, immetti l'identificativo come mostrato nella descrizione di **customer-nsx-edge0** nel client web NSX-T.
3. Riesamina le note che vengono visualizzate per gli indirizzi IP. Queste note identificano quali sottoreti e indirizzi IP vengono ordinati e utilizzati durante la configurazione iniziale.

   Non utilizzare gli indirizzi IP che vengono ordinati e utilizzati durante la configurazione iniziale. Puoi comunque utilizzare altri indirizzi IP
   su queste sottoreti in base ai tuoi requisiti. Per configurare ulteriori regole NAT (network address translation), vedi [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Link correlati
{: #vc_nsx-t_esg_config-related}

* [Considerazioni sulla modifica delle risorse vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Gateway dei servizi edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
