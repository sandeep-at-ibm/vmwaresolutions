---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-22"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Considerazioni sulla post-distribuzione per la tua istanza VMware
{: #solution_considerations}

Le offerte di {{site.data.keyword.vmwaresolutions_full}} non sono servizi gestiti. Sei responsabile della configurazione, della sicurezza, della gestione e del monitoraggio di tutti i componenti software. Con l'accesso amministrativo completo alla soluzione, hai una grande potenza e flessibilità che richiede competenze tecniche, amministrative e operative significative in vari domini. La gestione di un'istanza VMware in {{site.data.keyword.cloud_notm}} richiede la stessa pianificazione e competenza della pianificazione di un'istanza installata in loco. Le tecnologie definite dal software come VMware NSX e VMware vSAN semplificano notevolmente alcuni aspetti della gestione delle istanze, ma potrebbero richiedere nuove competenze e nuovi strumenti affinché siano correttamente gestite e realizzate. La combinazione della potenza, della velocità e dell'affidabilità della distribuzione VMware automatizzata da {{site.data.keyword.cloud_notm}} con la pianificazione e i test operativi appropriati garantisce una navigazione rapida e corretta verso il cloud ibrido.

Esamina le seguenti considerazioni per comprendere le tue responsabilità per la gestione e il funzionamento dell'istanza prima e dopo la sua distribuzione.

Il seguente elenco non è completo. Per ulteriori informazioni, vedi [Servizi gestiti IBM](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_imi).
{:note}

## Accesso all'account IBM Cloud
{: #solution_considerations-acct-access}

Per gestire l'accesso al tuo account {{site.data.keyword.cloud_notm}}, consenti ad altri membri del tuo team di accedere alla tua istanza nella console {{site.data.keyword.vmwaresolutions_short}}. Per ulteriori informazioni, vedi [Come invitare gli utenti ad accedere a servizi e risorse](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite).

## Limitazioni
{: #solution_considerations-limitations}

Familiarizza con le seguenti limitazioni relative alla tua istanza:

- [Impatti della modifica delle risorse vCenter](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact)
- [Considerazioni e limitazioni di rete](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_networkingonvcenterserver)
- [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

## Progettazione e connettività della rete
{: #solution_considerations-net-design}

Completa la seguente procedura per gestire l'accesso alla tua rete {{site.data.keyword.cloud_notm}} e ai tuoi componenti di gestione VMware e per pianificare la topologia di rete {{site.data.keyword.cloud_notm}}.

- Accedi agli endpoint di gestione delle istanze utilizzando la [VPN {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/vpn-access) o la tua [connessione Direct Link {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/direct-link).
- Definisci una strategia per la connettività di rete pubblica dall'interno della tua istanza. Le opzioni includono: il gateway dei servizi edge (ESG) VMware NSX del cliente di esempio, dispositivi gateway come Vyatta e FortiGate e i server proxy distribuiti nella rete {{site.data.keyword.cloud_notm}} o nella tua propria rete a cui si accede tramite Direct Link.
- Pianifica se distribuire il tuo carico di lavoro sulle VLAN {{site.data.keyword.cloud_notm}} con [indirizzi IP portatili di {{site.data.keyword.cloud_notm}}](/docs/infrastructure/subnets?topic=subnets-getting-started) o [su switch logici NSX (VXLAN) utilizzando i tuoi propri indirizzi IP](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview). Nota che l'utilizzo della SDN (software-defined networking) NSX ti fornisce la massima flessibilità per gestire e proteggere la tua rete del carico di lavoro in {{site.data.keyword.cloud_notm}}.
- Utilizza ESG NSX, [IBM Cloud Vyatta](https://cloud.ibm.com/catalog/infrastructure/virtual-router-appliance) e peering Direct Link per pianificare la connettività ai carichi di lavoro (Network Address Translation, Virtual Private Network, instradamento).
- Se si implementa Cross-vCenter NSX, assicurati che gli intervalli di ID del segmento locale non si sovrappongano prima di distribuire i carichi di lavoro locali.

## Pianificazione e protezione della sicurezza
{: #solution_considerations-sec-planning}

Sei responsabile della protezione, della crittografia e del monitoraggio della tua istanza e dei tuoi carichi di lavoro VMware per soddisfare gli standard aziendali, di settore e normativi. Completa la seguente procedura per garantire una sicurezza adeguata.

- Modifica tutte le password visualizzate nella console {{site.data.keyword.vmwaresolutions_short}} e utilizza il tuo proprio sistema di gestione delle password. Nota che IBM conserva ID utente distinti necessari per l'automazione e il supporto continui.
- Esamina le politiche delle password, come la complessità e il periodo di scadenza, per tutti i componenti.
- Esamina le impostazioni di crittografia su tutti i componenti.
- Pianifica e implementa soluzioni di firewall fisico o virtuale appropriate, come ad esempio DFW (Distributed Firewall) NSX, ESG NSX, [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) e [IBM Cloud Vyatta](https://cloud.ibm.com/catalog/infrastructure/virtual-router-appliance).
- Pianifica e implementa soluzioni di sicurezza e bilanciamento del carico dell'applicazione appropriate, come ad esempio [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations).
- Pianifica e implementa soluzioni SIEM (security information and event management) appropriate, come ad esempio [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence).
- Pianifica e implementa una scansione delle vulnerabilità appropriata.
- Pianifica e implementa la gestione delle modifiche, l'approvazione, la verifica e il controllo degli accessi appropriati per la tua istanza, utilizzando soluzioni come [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations).

## Personalizzazione
{: #solution_considerations-custom}

Completa la seguente procedura per personalizzare l'installazione dell'istanza VMware di base in modo da soddisfare i tuoi requisiti.

- Utilizza la tua autorità di certificazione (CA) per generare certificati per componenti come vCenter (con PSC integrato) e NSX Manager.
- Configura i servizi distribuiti. Ad esempio:
  - Per HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, configura l'integrazione AD, il controllo degli accessi, le impostazioni SMTP (Simple Mail Transfer Protocol) e le politiche di conformità.
  - Per Zerto on {{site.data.keyword.cloud_notm}}, pianifica l'indirizzamento e l'instradamento di IP delle comunicazioni del dispositivo Zerto Virtual Replication Appliance (VRA) poiché l'attraversamento NAT (Network Address Translator) non è supportato. Prendi in considerazione il tunneling o la ridistribuzione dei tuoi VRA per l'indirizzamento e l'instradamento appropriati.
  - Per i servizi di backup come Veeam on {{site.data.keyword.cloud_notm}} e IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}, configura il tuo lavoro di backup, configura facoltativamente ulteriore spazio di archiviazione e configura gli avvisi di monitoraggio.
  - Per i servizi di rete e di sicurezza come F5 on {{site.data.keyword.cloud_notm}} e FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, configura le interfacce di rete, i certificati, la configurazione HA (high availability) e le regole in base alla tua topologia di rete e ad altri requisiti.

## Active Directory
{: #solution_considerations-ad}

Completa la seguente procedura per garantire una corretta configurazione e gestione di SSO (Single Sign-On).

- Configura la pianificazione di aggiornamento e riavvio del server AD (Active Directory).
- Se hai scelto l'opzione di distribuire i server AD nel cluster vSphere, fornisci licenze e attivazione di Microsoft Windows per i server per garantire la conformità e la disponibilità.
- Stabilisci la fiducia reciproca tra l'istanza e il tuo server AD in loco.
- Integra la VPN NSX, se applicabile, con AD SSO.
- Integra gli host ESXi con AD SSO.

## Pianificazione della manutenzione
{: #solution_considerations-maint-planning}

Completa la seguente procedura per garantire una corretta pianificazione per la manutenzione del software.

- [Configura VMware Update Manager (VUM)](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro) tramite un proxy per ottenere gli aggiornamenti di VMware.
- Se applicabile, configura vSAN tramite un proxy per mantenere il database HCL (Hardware Compatibility List) vSAN.
- Pianifica la manutenzione regolare dei componenti VMware non supportati da VUM. Ad esempio, VMware vCenter, PSC e NSX.
- Esamina la configurazione di EVC (Enhanced vMotion Compatibility) vSphere. Il tuo cluster potrebbe non essere configurato con EVC abilitato se la versione corrente di vSphere non supporta EVC per il tuo livello hardware.
- Pianifica la manutenzione regolare dei servizi aggiuntivi come Veeam on {{site.data.keyword.cloud_notm}}, Zerto on {{site.data.keyword.cloud_notm}} e F5 on {{site.data.keyword.cloud_notm}}.

## Monitoraggio
{: #solution_considerations-monitoring}

Assicurati di pianificare e implementare le seguenti soluzioni per il monitoraggio della tua istanza e dei componenti dell'istanza.

- Un server di registrazione che include l'inoltro o la raccolta dei log per tutti i componenti dell'istanza e una conservazione dei log adeguata.
- Un'infrastruttura di avviso, inclusa la configurazione del server SMTP e del gateway SMS (Short Message Service), secondo necessità.
- Monitoraggio proattivo di host, unità, software di gestione e rete.
- Monitoraggio vSAN, se applicabile.
- Monitoraggio e pianificazione della capacità. Puoi [aggiungere e rimuovere cluster](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters) e [aggiungere e rimuovere host](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers) nella tua istanza dalla console {{site.data.keyword.vmwaresolutions_short}}.
- Monitoraggio dell'infrastruttura di backup e dei lavori di backup.

## Disponibilità e continuità delle operazioni di business
{: #solution_considerations-business-cont}

La tua istanza VMware è in esecuzione sui server Bare Metal in {{site.data.keyword.cloud_notm}}. Completa la seguente procedura per assicurarti di fare piani adeguati per l'alta disponibilità e la continuità delle operazioni di business.

- Esamina la configurazione di vSphere HA e vSphere Distributed Resource Scheduler (DRS) in base ai tuoi requisiti.
- Esamina la configurazione del controllo I/O di rete e di archiviazione in base ai tuoi requisiti.
- Configura l'ordine di avvio della VM (Virtual Machine) in base ai tuoi requisiti.
- Configura i pool di risorse, secondo necessità, per la gestione e il carico di lavoro.
- Pianifica, implementa e monitora una soluzione di backup per i [componenti di gestione dell'istanza](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup) e per il carico di lavoro.
- Pianifica l'alta disponibilità della gestione dell'istanza, inclusa la possibilità di più istanze, più cluster, vCenter HA e PSC HA.
- Pianifica la continuità delle operazioni di business per i tuoi carichi di lavoro utilizzando soluzioni come [Zerto Disaster Recovery](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr), [Veeam backup and replication](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) e [IBM Spectrum Protect Plus](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations).

## Pianificazione dell'archiviazione
{: #solution_considerations-storage}

Oltre alla pianificazione della capacità, completa quanto segue per garantire che la configurazione di archiviazione soddisfi i tuoi requisiti di prestazioni e disponibilità.

- Le prestazioni dell'archiviazione dipendono da vari fattori, tra cui la configurazione RAID e segmentazione dei dati su disco, la configurazione di rete, la dimensione del blocco; l'IOPS (input/output operations per second) configurato per l'archiviazione collegata alla rete, la configurazione hardware della VM e il metodo di collegamento dell'archiviazione, i metodi di clustering e di replica e l'utilizzo di politiche di archiviazione come crittografia, deduplicazione e compressione. Pianifica il tempo per testare e ottimizzare la configurazione per soddisfare le tue esigenze di prestazioni dell'archiviazione.
- Esamina la tua politica di archiviazione vSAN
  - RAID-1 offre prestazioni migliori e finestre più piccole di suscettibilità all'errore sequenziale, come un tempo di ricostruzione più breve, rispetto a RAID-5. Tuttavia, RAID-5 ha meno costi di archiviazione.
  - RAID-6 fornisce protezione contro i doppi errori, ma richiede un minimo di sei host rispetto ai quattro host richiesti per RAID-5.
- Per aggiungere più archiviazione al cluster vSAN, devi aggiungere nuovi host al cluster o aggiungere l'archiviazione NFS Endurance {{site.data.keyword.cloud_notm}}. L'aggiunta di dischi agli host esistenti non è attualmente supportata.
- Se monti un'ulteriore archiviazione NFS Endurance {{site.data.keyword.cloud_notm}} nel tuo cluster, assicurati di seguire le indicazioni dell'architettura e di configurare le rotte host all'archiviazione utilizzando gli indirizzi del gruppo di porte `SDDC-DPortGroup-NFS`. Devi autorizzare questi indirizzi, anziché gli host stessi, all'archiviazione. Per ulteriori informazioni, vedi [Gestione dell'infrastruttura di archiviazione collegata](/docs/services/vmwaresolutions/archiref/attached-storage?topic=vmware-solutions-storage-infra-mgmt#vsphere-host-static-routing).

Consulta anche l'indicazione di developerWorks che mostra come [aggiungere più archiviazione endurance al tuo cluster VMware](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/) utilizzando IBM Spectrum Protect Plus come esempio.

## Link correlati
{: #solution_considerations-related}

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Panoramica della progettazione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Ridimensionamento della capacità](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)
