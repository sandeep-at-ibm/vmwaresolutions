---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# Note sulla release per la V1.4

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Aggiornamenti dei componenti per le istanze Cloud Foundation

I seguenti componenti sono nuovi o aggiornati:

* VC e PSC (vCenter e Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* Una nuova VSI (Virtual Server Instance) di Windows viene ordinata per i servizi Microsoft Active Directory (AD) e DNS (Domain Name System), necessari per il supporto della configurazione multisito in questa release. Questa VSI ha le seguenti specifiche: Windows 2012 R2 (8 GB di RAM / 2 core CPU / disco da 100 GB / Doppi uplink privati da 1 Gbps).

Per ulteriori informazioni, vedi [Panoramica di Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Aggiornamenti dei componenti per le istanze vCenter Server

I seguenti componenti sono nuovi o aggiornati:

### VMware NSX per vSphere 6.2.4

VMware NSX per vSphere 6.2.4 è ora installato per impostazione predefinita su tutte le istanze vCenter Server (in precedenza solo sulle istanze Cloud Foundation).

Come parte dell'installazione di NSX, NSX Manager viene installato e concesso in licenza su tutte le nuove istanze che vengono distribuite. Inoltre, viene creato un edge NSX per la gestione dell'istanza, ma puoi creare i tuoi propri componenti edge NSX secondo necessità. Per ulteriori informazioni sull'edge NSX, vedi la sezione _Edge NSX VMware_ in questa pagina.

**Nota**: il controller NSX non viene installato sulle istanze vCenter Server (così come è installato sulle istanze Cloud Foundation). Se utilizzi VXLAN o DLR (Distributed Logical Router) per le tue istanze vCenter Server, devi installare il controller NSX autonomamente.

Per ulteriori informazioni sui miglioramenti introdotti in VMware NSX for vSphere 6.2.4, i relativi requisiti e i problemi noti, vedi [Note sulla release di NSX per vSphere 6.2.4](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### Edge NSX VMware

Edge NSX è ora incluso come parte delle nuove istanze vCenter Server che stai ordinando. Edge NSX fornisce i servizi gateway e di sicurezza edge della rete per isolare una rete virtualizzata.

Durante la distribuzione dell'istanza, un gateway dei servizi edge (ESG) VMware NSX di gestione viene distribuito da IBM. Questo ESG viene utilizzato dalle macchine virtuali di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. L'ESG è distribuito per includere due interfacce: un'interfaccia è connessa alla VLAN privata di {{site.data.keyword.cloud_notm}} e l'altra è connessa alla VLAN pubblica di {{site.data.keyword.cloud_notm}}.

Per garantire la sicurezza, vengono implementate regole del firewall per consentire solo le comunicazioni HTTPS in uscita avviate dalle macchine virtuali di gestione. Questo ESG viene distribuito in una configurazione di tipo Large e solo il supporto IBM può modificare la configurazione. Per ulteriori informazioni, consulta i seguenti argomenti:

* [Specifiche tecniche per vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentazione di VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### Licenza NSX

Viene ordinata una licenza di VMware NSX Base for Service Providers Edition per ciascun nodo.

### Nuovo blocco di indirizzi della sottorete

Viene ordinato un blocco della sottorete di 16 indirizzi pubblici portatili per ciascun nodo.

## Aggiornamenti del modello di addebito del servizio

Il modello di addebito del servizio è stato semplificato:

* Per le istanze Cloud Foundation, le tariffe per il _servizio delle istanze VMware Cloud Foundation_, il _servizio di archiviazione VMware Cloud Foundation_ e
   l'_Hypervisor di VMware Solutions_ vengono sospese.
* Per le istanze vCenter Server, le tariffe per l'_istanza VMware vCenter Server_ e l'_Hypervisor di VMware Solutions_ vengono sospese.
* Per entrambi i tipi di istanze, viene introdotta una nuova tariffa per _Supporto e servizi_, che è una tariffa mensile applicata a ciascun nodo.

## Aggiornamenti alla topologia di rete dell'istanza

Questa release include i seguenti miglioramenti della topologia per le tue istanze:

* Sia per le istanze Cloud Foundation che per le istanze vCenter Server: configurazione ottimizzata della rete, ovvero, solo gli indirizzi IP pubblici e privati primari assegnati da SoftLayer® vengono collegati ai server ESXi. Gli indirizzi privati portatili non vengono più distribuiti per il traffico di gestione.
* Solo per le istanze Cloud Foundation: server Windows AD SSO (Active Directory Single Sign-On) e Domain Name System (DNS)

**Nota**: a causa di queste modifiche, non puoi utilizzare le tue istanze precedenti alla V1.4 esistenti nella release corrente. Per riutilizzare la configurazione delle tue istanze esistenti, devi aggiornarle alla versione corrente. Per ulteriori informazioni, vedi [Aggiornamento delle istanze dalle release precedenti alla V1.4](movinginstances.html).

## Supporto della configurazione multisito per le istanze Cloud Foundation

Puoi ora distribuire una singola istanza Cloud Foundation, come nelle release precedenti o, in aggiunta, distribuire istanze secondarie che vengono collegate a un'istanza primaria. Il modello di configurazione multisito utilizza una topologia "hub and spoke" con un sito primario e un massimo di sette siti secondari.

Per ulteriori informazioni, vedi [Configurazione multisito per le istanze Cloud Foundation](../sddc/sd_multisite.html).

## Miglioramenti alla distribuzione del ripristino di emergenza Zerto

* Per le istanze Cloud Foundation, la distribuzione del ripristino di emergenza Zerto è automatizzata anziché gestita tramite un ticket di supporto. Tutti i componenti di Zerto, come una sottorete portatile privata, una VSI (Virtual Service Instance) di Windows e i costi di licenza Zerto vengono elencati sotto il costo stimato, quindi puoi esaminarli prima di effettuare l'ordine.
* Per le istanze vCenter Server, la distribuzione del ripristino di emergenza Zerto viene effettuata tramite un ticket di supporto, come nella release precedente. Tuttavia, l'edge NSX e la sottorete portatile pubblica non sono più necessari, poiché sono ora inclusi nella distribuzione di base. Si applicano ancora gli addebiti per una sottorete portatile privata, una VSI (Virtual Service Instance) di Windows e la licenza Zerto.

Per ulteriori informazioni, vedi [Ripristino di emergenza Zerto](../services/addingzertodr.html).

## Processo di ordine dell'istanza

Il processo di ordine dell'istanza è stato notevolmente semplificato:

* Sia per le istanze Cloud Foundation che per le istanze vCenter Server, la pagina delle credenziali di SoftLayer non viene più visualizzata durante il processo di ordine. Le credenziali SoftLayer definite nella pagina delle impostazioni vengono utilizzate per impostazione predefinita e ti viene richiesto di aggiornarle solo se non soddisfano i requisiti.
* Inoltre, per le istanze vCenter Server, sono ora disponibili solo l'opzione **Large** per il tipo di **Hardware** e l'impostazione **10 Gbps Dual** per **Velocità porta uplink**, il che riduce il numero di impostazioni da specificare durante l'ordine.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)

## Gestione dell'istanza

Il processo di gestione dell'istanza include nuove funzioni e miglioramenti:

* Per le istanze Cloud Foundation, puoi visualizzare il nome utente e le password per vari componenti nella pagina dei dettagli dell'istanza. Per ulteriori informazioni, vedi [Visualizzazione delle istanze Cloud Foundation](../sddc/sd_viewinginstances.html).
* Per le istanze vCenter Server, puoi ora installare aggiornamenti e patch di software per i componenti IBM direttamente dalla console. Per ulteriori informazioni, vedi [Applicazione di aggiornamenti e patch alle istanze vCenter Server](../vcenter/vc_applyingupdates.html).

## Notifiche della console

Puoi ora configurare le notifiche della console nella pagina **Impostazioni**. Per impostazione predefinita, l'impostazione è abilitata, il che significa che ricevi una notifica nella console per tutti gli eventi. Puoi anche disabilitare le notifiche per la console nella pagina **Impostazioni**.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Account utente e impostazioni](useraccount.html)
* [Notifiche](notifications.html)
