---

copyright:

  years: 2016, 2019

lastupdated: "2019-02-21"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Introduzione a IBM Cloud for VMware Solutions
{: #getting-started}

In questa esercitazione introduttiva, ti guidiamo attraverso il processo di ordine di un'istanza e di alcuni servizi aggiuntivi per tale istanza.
{:shortdesc}

## Prima di iniziare
{: #getting-started-prereqs}

Prima di iniziare a lavorare con {{site.data.keyword.vmwaresolutions_full}}, esamina le seguenti informazioni importanti sui requisiti del browser, gli account utente, le opzioni di distribuzione e i servizi aggiuntivi.

### Requisiti del browser
{: #getting-started-browser-req}

Sono supportati i seguenti browser:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer non è supportato.
{:note}

Per una visualizzazione e un funzionamento ottimali della console {{site.data.keyword.vmwaresolutions_short}}, imposta la risoluzione dello schermo su almeno 1024 pixel di larghezza per 500 pixel di altezza.

### Account utente
{: #getting-started-user-accts}

Devi avere un account {{site.data.keyword.cloud_notm}} e un account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer). Questi account devono soddisfare determinati requisiti.

   Tabella 1. Account utente richiesti
   <table>
   <tr>
      <th>Account</th>
      <th>Descrizione</th>
   </tr>
   <tr>
      <td>ID IBM</td>
      <td>Utilizzando l'**ID IBM**, puoi avere un unico nome utente di accesso per tutti i prodotti e servizi IBM che utilizzi, incluso {{site.data.keyword.cloud_notm}}. {{site.data.keyword.vmwaresolutions_short}} viene fornito come soluzione dell'infrastruttura nel catalogo {{site.data.keyword.cloud_notm}}. Per accedere alla console {{site.data.keyword.vmwaresolutions_short}}, devi avere un **ID IBM**.<br><br>Per utilizzare il tuo **ID IBM** per accedere alla console {{site.data.keyword.vmwaresolutions_short}}, devi associare l'**ID IBM** a un account {{site.data.keyword.cloud_notm}}. Quando accedi alla console per la prima volta, ti verranno fornite le indicazioni per associare il tuo **ID IBM** esistente a un account {{site.data.keyword.cloud_notm}} o per registrare un nuovo account {{site.data.keyword.cloud_notm}}. Il nuovo account {{site.data.keyword.cloud_notm}} viene associato automaticamente al tuo **ID IBM**. Devi seguire questa procedura solo una volta.<br><br>Se hai dei problemi durante l'associazione del tuo **ID IBM** a un account {{site.data.keyword.cloud_notm}}, vedi [Risoluzione dei problemi relativi all'accesso a {{site.data.keyword.cloud_notm}}](https://console.cloud.ibm.com/docs/account/ts_accessing.html).</td>
   </tr>
   <tr>
      <td>Account IBM Cloud</td>
      <td>Per ordinare e utilizzare i servizi {{site.data.keyword.cloud_notm}}, è richiesto un account {{site.data.keyword.cloud_notm}}. Le informazioni di fatturazione sono associate all'account {{site.data.keyword.cloud_notm}}. Il costo dell'infrastruttura fisica e virtuale e delle licenze risultanti viene addebitato sul tuo account {{site.data.keyword.cloud_notm}}.</td>
   </tr>
   <tr>
      <td>Account dell'infrastruttura IBM Cloud (SoftLayer)</td>
      <td>L'account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) era precedentemente noto come account IBM SoftLayer.  Per ulteriori informazioni sui requisiti che l'account deve soddisfare, vedi [Requisiti per l'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).<br><br>Puoi collegare gli account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) agli account {{site.data.keyword.cloud_notm}} per utilizzare le risorse combinate IaaS (Infrastructure as a Service) e PaaS (Platform as a Service). Quindi, puoi accedere alle risorse IaaS e alle risorse PaaS effettuando un singolo accesso. Il collegamento dei tuoi account ti fornisce anche una singola fattura per tutte le risorse PaaS e IaaS che utilizzi.<ul><li>Se non disponi di un account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer), richiedine uno seguendo la procedura in [Registrazione di un account dell'infrastruttura IBM Cloud (SoftLayer)](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account) e quindi collega il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) al tuo account {{site.data.keyword.cloud_notm}} seguendo la procedura in [Collegamento degli account ID IBM](https://console.cloud.ibm.com/docs/account/softlayerlink.html).</li><li>Se hai un account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer), puoi collegarlo al tuo account {{site.data.keyword.cloud_notm}} seguendo la procedura descritta in [Collegamento degli account ID IBM](https://console.cloud.ibm.com/docs/account/softlayerlink.html).</li></ul></td>
   </tr>
   </table>

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Registrazione degli account richiesti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [Requisiti per l'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement)

### Offerte di distribuzione
{: #getting-started-depl-offerings}

Esamina e scegli la tua offerta di distribuzione.

  Tabella 2. Offerte di distribuzione
  <table>
    <tr>
       <th>Offerta di distribuzione</th>
       <th>Descrizione</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)</td>
       <td>Con l'offerta vCenter Server, puoi distribuire un ambiente virtuale VMware utilizzando risorse di calcolo, archiviazione e rete personalizzate per soddisfare al meglio le tue esigenze aziendali.</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)</td>
       <td>L'offerta vCenter Server with Hybridity è un cloud privato ospitato che consente di estendere in modo semplice e rapido la tua infrastruttura in loco nel cloud. L'ambiente VMware è basato sulle licenze Software Defined Data Center VMware fornite da IBM e comprende VMware Hybrid Cloud Extension (HCX). Utilizzando HCX, puoi connettere in modo sicuro un ambiente vSphere 5.0+ in loco con i siti {{site.data.keyword.cloud_notm}} per un'ibridità dell'infrastruttura senza interruzioni e una reale mobilità dell'applicazione.</td>
    </tr>
    <tr>
       <td>[VMware Cloud Foundation on IBM Cloud](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)</td>
       <td>L'offerta Cloud Foundation fornisce un ambiente virtuale VMware unificato utilizzando le risorse di calcolo, archiviazione e rete standard di {{site.data.keyword.cloud_notm}}, dedicate alla distribuzione di ciascun utente.</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)</td>
       <td>L'offerta vSphere on {{site.data.keyword.cloud_notm}} fornisce un servizio di virtualizzazione personalizzabile che combina {{site.data.keyword.baremetal_short}}, componenti hardware e licenze compatibili con VMware per creare il tuo proprio ambiente VMware ospitato su IBM.</td>
    </tr>
    <tr>
       <td>[NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)</td>
       <td>L'offerta NetApp ONTAP Select ti consente di distribuire un cluster di archiviazione definita dal software che risponda alle tue esigenze di un'applicazione di archiviazione dedicata e altamente disponibile basata su NetApp ONTAP Select.</td>
    </tr>
  </table>

### Servizi aggiuntivi
{: #getting-started-add-on-services}

Esamina e scegli i servizi aggiuntivi per la tua offerta di distribuzione.

  Tabella 3. Servizi aggiuntivi disponibili per le offerte di distribuzione
  <table>
    <tr>
       <th>Nome servizio</th>
       <th>Descrizione</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)</td>
       <td>Il servizio F5 on {{site.data.keyword.cloud_notm}} (F5 BIG-IP® Virtual Edition) fornisce servizi intelligenti di bilanciamento del carico L4-L7 e di gestione del traffico su scala locale e globale, una solida protezione firewall per reti e applicazioni web e accesso sicuro e federato alle applicazioni.</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)</td>
       <td>Il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} distribuisce una coppia di dispositivi FortiGate Security Appliance (FSA) della serie 300 in una modalità altamente disponibile per fornire servizi di firewall, instradamento, NAT e VPN per proteggere ogni server e macchina virtuale sulla VLAN pubblica delle tue istanze.</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)</td>
       <td>Il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} distribuisce una coppia di dispositivi FortiGate Virtual Appliance al tuo ambiente, che può aiutarti a ridurre i rischi implementando controlli di sicurezza critici all'interno della tua infrastruttura virtuale.</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)</td>
       <td>Il servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} applica e controlla la conformità rispetto agli standard di sicurezza e fornisce funzionalità dettagliate di controllo degli accessi in base al ruolo (RBAC), approvazione e verifica. Se combinato con HyTrust DataControl, il servizio può garantire che le macchine virtuali e i dati del carico di lavoro non lascino una particolare regione, cluster o server ESXi all'interno del {{site.data.keyword.CloudDataCent_notm}}.</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)</td>
       <td>Il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}} offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio può fornire la crittografia sia a livello di sistema operativo che a livello di dati, il che significa che è possibile crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hytrust-keycontrol-on-ibm-cloud-overview)</td>
       <td>Il servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} semplifica la gestione dei carichi di lavoro crittografati automatizzando e semplificando il ciclo di vita delle chiavi di crittografia. Il servizio può facilmente gestire le chiavi di crittografia in scala utilizzando la crittografia conforme a FIPS 140-2.</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)</td>
       <td>Il servizio {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} porta il potere dei microservizi e dei contenitori nel tuo ambiente VMware su {{site.data.keyword.cloud_notm}}. Con questo servizio, puoi estendere lo stesso modello operativo e gli stessi strumenti VMware e {{site.data.keyword.cloud_notm}} Privato con cui hai dimestichezza da una situazione in loco a {{site.data.keyword.cloud_notm}}.</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)</td>
       <td>Il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} fornisce una soluzione efficiente e scalabile per la protezione dei dati, il riutilizzo dei dati e il recupero dei dati per gli ambienti virtuali. Puoi implementare il servizio come soluzione autonoma o integrarlo con il tuo ambiente IBM Spectrum Protect per scaricare copie per la governance di dati e archiviazione a lungo termine.</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)</td>
       <td>Il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} fornisce un servizio altamente disponibile per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Questo servizio offre funzionalità di runtime per consentire ai clienti di creare, recuperare, attivare, revocare e distruggere le chiavi di crittografia. Fornisce inoltre funzionalità di gestione per mantenere le associazioni tra le credenziali del client e le chiavi di crittografia.</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)</td>
       <td>Il servizio Veeam on {{site.data.keyword.cloud_notm}} si integra perfettamente con i tuoi hypervisor VMware per aiutare la tua azienda a raggiungere l'alta disponibilità. Questo servizio può fornire obiettivi di tempo e punti di ripristino per le tue applicazioni e i tuoi dati. Gli obiettivi di tempo e punti di ripristino possono essere forniti in meno di 15 minuti dopo il completamento della configurazione. Utilizzando questo servizio, puoi controllare direttamente sia il backup che il ripristino di tutte le macchine virtuali per la tua infrastruttura dalla console Veeam.</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-overview)</td>
       <td>Il servizio HCX on {{site.data.keyword.cloud_notm}} può estendere senza problemi le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione delle macchine virtuali (VM) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)</td>
       <td>Il servizio Zerto on {{site.data.keyword.cloud_notm}} fornisce funzionalità di replica e ripristino di emergenza, che è possibile integrare nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}.</td>
    </tr>
   </table>

## Passo 1: accesso alla console IBM Cloud for VMware Solutions
{: #getting-started-step1}

La console {{site.data.keyword.vmwaresolutions_short}} è l'interfaccia in cui ordini e gestisci le tue distribuzioni. Nella console, ogni distribuzione è gestita come un'istanza. La console è un'interfaccia utente autonoma separata dal portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}}.

Per accedere alla console {{site.data.keyword.vmwaresolutions_short}}:
1. Vai al sito https://console.cloud.ibm.com/infrastructure/vmware-solutions/console.
2. Accedi alla console con il tuo **ID IBM**.

## Passo 2: configurazione dell'account utente e delle impostazioni
{: #getting-started-step2}

Prima di ordinare un'istanza, devi immettere il nome utente e la chiave API del tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) nella pagina **Impostazioni** della console.

Per informazioni su come configurare il tuo account utente e le impostazioni, vedi [Gestione di account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Passo 3: ordine di un'istanza
{: #getting-started-step3}

Dopo aver scelto un'offerta di distribuzione, che viene gestita come istanza nella console, inizia il processo di ordine.

Per informazioni su come ordinare un'istanza, vedi i seguenti argomenti in base alla tua selezione dell'offerta di distribuzione:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Ordine di istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ordine di istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Passo 4: visualizzazione dell'istanza
{: #getting-started-step4}

Dopo aver effettuato un ordine di istanza nel **Passo 3**, la distribuzione dell'istanza inizia automaticamente. Puoi tenere traccia dello stato della distribuzione visualizzando i dettagli dell'istanza. Una volta completata la distribuzione dell'istanza, puoi visualizzare il riepilogo e le informazioni dettagliate dell'istanza e dei relativi servizi aggiuntivi nella pagina dei dettagli dell'istanza.

Per informazioni su come visualizzare l'istanza che hai ordinato, vedi i seguenti argomenti:
* [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Visualizzazione delle istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Visualizzazione delle istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Visualizzazione delle istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)

## Passo 5: gestione dei servizi aggiuntivi per l'istanza
{: #getting-started-step5}

Se hai ordinato servizi aggiuntivi per la tua istanza, puoi gestire anche tali servizi:

Per informazioni su come gestire i servizi, vedi i seguenti argomenti:
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)

## Passo successivo
{: #getting-started-next}

Gestisci la tua istanza dalla console {{site.data.keyword.vmwaresolutions_short}} o dal client web VMware vSphere.
