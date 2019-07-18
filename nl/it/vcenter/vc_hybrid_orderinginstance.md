---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server Hybridity order instance, order vCenter Server Hybridity, order Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance}

Per distribuire una piattaforma virtualizzata VMware flessibile e personalizzabile che soddisfi al meglio le tue esigenze del carico di lavoro, ordina un'istanza VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Il tuo ordine dell'istanza vCenter Server with Hybridity Bundle include la licenza di VMware Hybrid Cloud Extension (HCX) e ti dà diritto al servizio VMware HCX on {{site.data.keyword.cloud_notm}}. Puoi anche aggiungere dei servizi, come [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) per il ripristino di emergenza.

## Requisiti per ordinare le istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-req}

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Hai esaminato le informazioni in [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning).
* Hai esaminato il formato del nome di istanza e di dominio. Il nome del dominio e l'etichetta del dominio secondario vengono utilizzati per generare il nome utente e i nomi server dell'istanza.

| Nome        | Formato del valore      |
|:------------- |:------------- |
| Nome dominio | `<root_domain>` |  
| Nome utente di accesso vCenter Server | `<user_id>@<root_domain>` (Microsoft Active Directory user) o `administrator@vsphere.local` |
| Dome di dominio completo vCenter Server (con PSC integrato) | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. La lunghezza massima è di 50 caratteri. |
| Nome del sito SSO (Single Sign-On) | `<subdomain_label>` |
| Nome completo server ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove `<n>` è la sequenza del server ESXi. La lunghezza massima è di 50 caratteri. |
{: caption="Tabella 1. Formato del valore per i nomi di istanza e di dominio" caption-side="top"}

Non modificare alcun valore impostato durante l'ordine o la distribuzione dell'istanza. La modifica può rendere inutilizzabile la tua istanza. Ad esempio, se la rete pubblica si interrompe, se i server e le VSI (Virtual Server Instance) vanno dietro una fornitura media di Vyatta o se la VSI di IBM CloudBuilder si arresta o viene eliminata.
{:important}

## Impostazioni di sistema
{: #vc_hybrid_orderinginstance-sys-settings}

Quando ordini un'istanza vCenter Server with Hybridity Bundle, devi specificare le seguenti impostazioni di sistema.

### Nome istanza
{: #vc_hybrid_orderinginstance-inst-name}

Il nome dell'istanza deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome dell'istanza deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* La lunghezza massima del nome dell'istanza è di 10 caratteri.
* Il nome dell'istanza deve essere univoco all'interno del tuo account.

### Licenze VMware vSphere
{: #vc_hybrid_orderinginstance-vsphere-license}

Seleziona se ordinare vSphere Enterprise Plus 6.7u1 o vSphere Enterprise Plus 6.5u2.

vSphere Enterprise Plus 6.7u1 è disponibile solo per {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Broadwell e Skylake.
{:note}

### Primaria o secondaria
{: #vc_hybrid_orderinginstance-primary-secondary}

Scegli se ordinare un nuova istanza primaria o un'istanza secondaria per un'istanza primaria esistente.

## Impostazioni di licenza
{: #vc_hybrid_orderinginstance-licensing-settings}

Con il tuo ordine dell'istanza vCenter Server with Hybridity Bundle sono incluse le seguenti licenze VMware. Devi specificare l'edizione per le licenze NSX e vSAN.

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 o 6.7
* NSX Service Providers 6.4 (Edizione Advanced o Enterprise)
* vSAN 6.6 (Edizione Advanced o Enterprise)

### Attenzione
{: #vc_hybrid_orderinginstance-attention}

* Le istanze vCenter Server with Hybridity Bundle non supportano l'opzione BYOL (Bring Your Own License).
* Le edizioni minime della licenza sono indicate sull'interfaccia utente. Se sono supportate edizioni diverse per i componenti, puoi selezionare l'edizione che vuoi.

## Impostazioni di Bare Metal Server
{: #vc_hybrid_orderinginstance-bare-metal-settings}

Le impostazioni di Bare Metal sono basate sulla tua selezione del {{site.data.keyword.CloudDataCent_notm}} e sulla configurazione del server bare metal.

Per le configurazioni vSAN, sono richiesti quattro server ESXi per i cluster iniziali e di post-distribuzione. Tutti i server ESXi condividono la stessa configurazione. Nella post distribuzione, puoi aggiungere altri quattro cluster.

### Ubicazione data center
{: #vc_hybrid_orderinginstance-dc-location}

Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui deve essere ospitata l'istanza.

### Skylake
{: #vc_hybrid_orderinginstance-skylake}

Se selezioni **Skylake**, puoi scegliere la combinazione di CPU e RAM del Bare Metal Server in base alle tue esigenze.

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabella 2. Opzioni per Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Broadwell
{: #vc_hybrid_orderinginstance-broadwell}

Se selezioni **Broadwell**, puoi scegliere la combinazione di CPU e RAM del Bare Metal Server in base alle tue esigenze.

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 core totali, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 core totali, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabella 3. Opzioni per Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Numero di server Bare Metal
{: #vc_hybrid_orderinginstance-bare-metal-number}

* Tutti i server che ordini hanno la stessa configurazione.
* Puoi ordinare da 4 a 20 server.

## Impostazioni di archiviazione
{: #vc_hybrid_orderinginstance-storage-settings}

VMware vSAN 6.6 è incluso con il tuo ordine dell'istanza vCenter Server with Hybridity Bundle. Specifica le seguenti opzioni vSAN:
* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona un'opzione per i dischi di capacità di cui hai bisogno.
* **Numero di dischi vSAN**: specifica il numero di dischi di capacità che vuoi aggiungere.
* Se vuoi aggiungere dischi di capacità oltre il limite di 10, seleziona la casella **Alte prestazioni con Intel Optane**. Questa opzione fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 12 dischi di capacità ed è utile per i carichi di lavoro che richiedono meno latenza e una maggiore velocità IOPS.

  L'opzione **Alte prestazioni con Intel Optane** è disponibile solo per i modelli di CPU Skylake.
  {:note}

* Riesamina i valori di **Tipo di disco per i dischi cache vSAN** e **Numero di dischi cache vSAN**. Questi valori dipendono dalla selezione della casella **Alte prestazioni con Intel Optane**.

## Impostazioni dell'interfaccia di rete
{: #vc_hybrid_orderinginstance-network-interface-settings}

Quando ordini un'istanza vCenter Server with Hybridity Bundle, devi specificare le seguenti impostazioni dell'interfaccia di rete.

### Prefisso nome host
{: #vc_hybrid_orderinginstance-host-name-prefix}

  Il prefisso del nome host deve rispettare i seguenti requisiti:
  *  Sono consentiti solo caratteri alfanumerici e trattini (-).
  *  Il prefisso del nome host deve iniziare e terminare con un carattere alfanumerico.
  *  La lunghezza massima del prefisso del nome host è di 10 caratteri.

### Etichetta dominio secondario
{: #vc_hybrid_orderinginstance-subdomain-label}

L'etichetta del dominio secondario deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* L'etichetta del dominio secondario deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* La lunghezza massima dell'etichetta del dominio secondario è di 10 caratteri.
* L'etichetta del dominio secondario deve essere univoca all'interno di tutte le istanze nella tua configurazione multisito.

### Nome dominio
{: #vc_hybrid_orderinginstance-domain-name}

Il nome del dominio root deve rispettare i seguenti requisiti:
* Il nome del dominio deve essere composto da due o più stringhe separate da un punto (.)
* La prima stringa deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* Tutte le stringhe, tranne l'ultima, possono contenere solo caratteri alfanumerici e trattini (-).
* L'ultima stringa può contenere solo caratteri alfabetici.
* La lunghezza dell'ultima stringa deve essere compresa tra 2 e 24 caratteri.

La lunghezza massima del nome di dominio completo (o FQDN, Fully Qualified Domain Name) per gli host e le VM (Virtual Machine) è di 50 caratteri. I nomi di dominio devono essere adattati a questa lunghezza massima.
{:note}

### Rete pubblica o privata
{: #vc_hybrid_orderinginstance-public-private-network}

Le impostazioni di abilitazione della scheda di interfaccia di rete (NIC) si basano sulla tua selezione di **Rete pubblica e privata** o **Solo rete privata**.

Se selezioni l'opzione **Solo rete privata**:
* Non viene eseguito il provisioning dei Gateway dei servizi edge (ESG) VMware NSX (né degli ESG del servizio di gestione né di quelli gestiti dal cliente).
* I seguenti servizi aggiuntivi, che richiedono NIC pubbliche, non sono disponibili:
  * F5 on {{site.data.keyword.cloud_notm}}
  * Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
  * Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Ordina nuove VLAN
{: #vc_hybrid_orderinginstance-new-vlans}

Seleziona **Ordina nuove VLAN** per ordinare una nuova VLAN pubblica e due nuove VLAN private.

Per l'ordine della tua istanza sono richieste una VLAN pubblica e due VLAN private. Le due VLAN private sono collegate a ogni Bare Metal Server.

### Seleziona VLAN esistenti
{: #vc_hybrid_orderinginstance-existing-vlans}

A seconda del {{site.data.keyword.CloudDataCent_notm}} che hai selezionato, potrebbero essere disponibili VLAN pubbliche e private esistenti.

Per l'ordine della tua istanza sono richieste una VLAN pubblica e due VLAN private. Le due VLAN private sono collegate a ogni Bare Metal Server.

Seleziona **Seleziona VLAN esistenti** per riutilizzare VLAN pubbliche e private esistenti e scegliere tra le VLAN e sottoreti disponibili.

* Assicurati che la configurazione del firewall sulle VLAN selezionate non blocchi il traffico dei dati di gestione.
* Assicurati che tutte le VLAN che selezioni si trovino nello stesso pod, poiché i server ESXi non possono essere forniti su VLAN di pod misti.
{:important}

### Configurazione DNS
{: #vc_hybrid_orderinginstance-dns-config}

Seleziona la configurazione DNS (Domain Name System) per la tua istanza:

* **Singola VSI Windows pubblica per Active Directory/DNS**: viene distribuita una singola VSI di Microsoft Windows Server per Microsoft Active Directory (AD) consultabile, che funziona come DNS per l'istanza in cui sono registrati gli host e le VM.
* **Due VM di Windows Server dedicate e altamente disponibili sul cluster di gestione**: vengono distribuite due VM di Microsoft Windows, che aiutano a migliorare la sicurezza e la solidità.

Se configuri la tua istanza per utilizzare le due VM di Microsoft Windows, devi fornire due licenze Microsoft Windows Server 2016 Standard Edition.
{:important}

Ogni licenza può essere assegnata solo a un singolo server fisico e comprende fino a due processori fisici. Una licenza Standard Edition è in grado di eseguire due VM di Microsoft Windows virtualizzate per ogni server con 2 processori. Pertanto, sono necessarie due licenze poiché due VM di Microsoft Windows vengono distribuite in due host diversi.

Hai 30 giorni per attivare le VM.

Per ulteriori informazioni su come ordinare le licenze Windows Server 2016, vedi [Get started with Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:external}.

## Impostazioni dei servizi
{: #vc_hybrid_orderinginstance-addon-services}

Quando ordini un'istanza vCenter Server with Hybridity Bundle, puoi anche ordinare servizi aggiuntivi. Per ulteriori informazioni sui servizi, vedi [Servizi disponibili per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Riepilogo ordine
{: #vc_hybrid_orderinginstance-order-summary}

In base alla configurazione che hai selezionato per l'istanza e i servizi aggiuntivi, il costo stimato viene generato e visualizzato istantaneamente nel riquadro di destra **Riepilogo ordine**. Fai clic su **Dettagli sui prezzi** per generare un documento PDF con il riepilogo del costo per le risorse {{site.data.keyword.vmwaresolutions_short}}.

Puoi anche aggiungere le risorse di cui è stato eseguito il provisioning allo strumento di stima {{site.data.keyword.cloud_notm}} facendo clic su **Aggiungi alla stima**. Ciò è utile se desideri stimare il costo delle risorse {{site.data.keyword.vmwaresolutions_short}} selezionate insieme ad altre risorse {{site.data.keyword.cloud_notm}} di cui potresti prendere in considerazione l'acquisto.

## Procedura per ordinare le istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic sull'icona **VMware** nel riquadro di navigazione a sinistra e quindi sulla scheda **VMware vCenter Server on IBM Cloud** nella sezione **VMware Virtual Data Centers**.
2. Nella pagina **VMware vCenter Server on IBM Cloud**, fai clic sulla scheda **vCenter Server with Hybridity Bundle** e quindi su **Crea**.
3. Nella pagina **vCenter Server**, immetti il nome dell'istanza.
5. Seleziona la versione di vSphere.
4. Seleziona il tipo di istanza:
   * Fai clic su **Istanza primaria** per distribuire una singola istanza nell'ambiente o per distribuire la prima istanza in una topologia multisito.
   * Fai clic su **Istanza secondaria** per connettere l'istanza a un'istanza esistente (primaria) nell'ambiente per l'alta disponibilità e completa quindi la seguente procedura:
     1. Seleziona l'istanza primaria a cui desideri collegare l'istanza secondaria.
     2. Per le istanze primarie della V2.8 o successive, immetti la password dell'amministratore vCenter Server per l'istanza primaria.
     3. Per le istanze primarie della V2.7 o precedenti, immetti la password dell'amministratore PSC per l'istanza primaria.
6. Seleziona l'edizione della licenza NSX e l'edizione della licenza vSAN.
7. Completa le impostazioni di Bare Metal Server.
  1. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.
  2. Seleziona il modello CPU **Skylake** o **Broadwell** e la quantità di **RAM**.
8. Completa la configurazione di archiviazione. Specifica i tipi di disco per i dischi di capacità e cache e il numero di dischi. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
9. Completa la configurazione dell'interfaccia di rete.
  1. Immetti il prefisso del nome host per l'istanza di cui viene eseguito il provisioning, l'etichetta del dominio secondario e il nome del dominio root.
  2. Seleziona l'impostazione di rete **Rete pubblica e privata** o **Solo rete privata**.
  3. Seleziona la configurazione della VLAN.
     *  Se vuoi ordinare nuove VLAN pubbliche e private, fai clic su **Ordina nuove VLAN**.
     *  Se vuoi riutilizzare le VLAN pubbliche e private esistenti quando sono disponibili, fai clic su **Seleziona VLAN esistenti** e quindi seleziona la VLAN pubblica, la sottorete primaria, la VLAN privata, la sottorete primaria privata e la VLAN privata secondaria.
  4. Seleziona la configurazione DNS.
10. Completa la configurazione per il servizio HCX on {{site.data.keyword.cloud_notm}} incluso. Per ulteriori informazioni su come fornire le impostazioni per il servizio, vedi la sezione _Configurazione di VMware HCX on IBM Cloud_ in [Ordine di VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering#vmware-hcx-on-ibm-cloud-configuration).
11. Seleziona i servizi aggiuntivi da distribuire nell'istanza facendo clic sulla scheda del servizio corrispondente. Se un servizio richiede la configurazione, completa le impostazioni specifiche del servizio e fai clic su **Aggiungi servizio** sulla scheda.  
Per ulteriori informazioni su come fornire le impostazioni per un servizio, vedi l'argomento relativo all'ordine del servizio corrispondente.

12. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
   1. Esamina le impostazioni per l'istanza.
   2. Esamina il costo stimato dell'istanza. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di ordinare l'istanza.
   4. Fai clic su **Fornitura**.

## Risultati dopo l'ordine di istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-results}

* La distribuzione dell'istanza inizia automaticamente e ricevi una conferma che ti indica che l'ordine è in fase di elaborazione. Puoi verificare lo stato della distribuzione, inclusi gli eventuali problemi che potrebbero richiedere la tua attenzione, visualizzando la sezione **Cronologia distribuzione** dei dettagli dell'istanza.
* Una volta che l'istanza è stata distribuita correttamente, i componenti descritti in [Specifiche tecniche per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs) vengono installati sulla tua piattaforma virtuale VMware. I server ESXi che hai ordinato vengono raggruppati come **cluster1** per impostazione predefinita. Se hai ordinato servizi aggiuntivi, la distribuzione dei servizi inizia dopo che il tuo ordine è stato completato.
* Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e riceverai una notifica via e-mail.
* Se ordini un'istanza secondaria, il client web VMware vSphere per l'istanza primaria (collegata a quella secondaria) potrebbe essere riavviato una volta completato l'ordine della tua istanza secondaria.

## Operazioni successive
{: #vc_hybrid_orderinginstance-next}

Visualizza e gestisci l'istanza vCenter Server with Hybridity Bundle che hai ordinato.

Devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console.
Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.
{:important}

**ATTENZIONE:** la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}} (installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza) dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante l'aggiunta o la rimozione di server ESXi
*  Spegnimento dei componenti
*  Riavvio dei servizi

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

## Link correlati
{: #vc_hybrid_orderinginstance-related}

* [Registrazione per un account {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [Visualizzazione delle istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Configurazione multisito per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_multisite)
* [Aggiunta e visualizzazione di cluster per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Eliminazione di istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
