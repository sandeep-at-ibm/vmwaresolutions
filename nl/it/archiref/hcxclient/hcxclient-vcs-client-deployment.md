---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Distribuzione del client HCX
{: #hcxclient-vcs-client-deployment}

Un'installazione HCX minima consiste in una singola distribuzione lato cloud e client.

Il lato client HCX
può essere installato su qualsiasi versione di vSphere supportata da HCX, presumendo che ci sia una connettività di rete tra i lati client e cloud.

## Requisiti
{: #hcxclient-vcs-client-deployment-req}

| Componente | Conteggio CPU | Memoria (GB) | Disco (GB) |
|--------|--------|---------|-------|
| HCX Manager | 4 | 12G |  60G |
| HCX Interconnect (HCX-IX) | 4 | 3G |  2G |
| HCX Network Extension (HCX-NE) | 4 | 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) | 8 | 14G |  100G |

## Licenze client
{: #hcxclient-vcs-client-deployment-licensing}

HCX è un servizio. HCX è concesso su licenza per ogni sito e per ogni VM (virtual machine) con gestione eseguita tramite i server di licenze mantenuti da VMware. Le istanze del lato client e di quello cloud HCX richiedono le comunicazioni con il sito di registrazione VMware in tutto il loro ciclo di vita.
- Il traffico su 80 e 443 deve essere consentito a `https://connect.hybridity.vmware.com`
- Una chiave di registrazione monouso viene fornita dalla console {{site.data.keyword.vmwaresolutions_full}} per l'installazione lato client. È richiesta una chiave per ogni installazione HCX lato client.

### Procedura per ordinare le licenze HCX in loco
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Scorri fino alla tabella **Licenze HCX in loco** e fai clic su **Esegui provisioning del nuovo**.
3. Specifica il nome della licenza.
4. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e assicurati di accettare questi termini prima di ordinare la licenza.
5. Fai clic su **Fornitura**.

## Requisiti dell'indirizzo IP
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

Per distribuire l'HCX, deve essere disponibile il numero corretto di indirizzi IP in loco
e nell'IBM Cloud di destinazione.

* Indirizzo vMotion
  Il mantenere una rete separata per il vMotion è una pratica comune nel data center in loco. Il gateway cloud deve avere accesso alla rete vMotion. Se non è così, è necessario un ulteriore indirizzo IP per la comunicazione con la rete vMotion.

* In loco
  * Un indirizzo IP per il dispositivo HCX Manager.
  * Uno per ciascun dispositivo di interconnessione, aggiungine uno se è presente una rete vMotion separata.
  * Uno per ogni estensione di rete standard

* IBM Cloud
  * Due indirizzi IP per il dispositivo HCX Manager connesso a IBM Cloud. Gli indirizzi possono venire utilizzati per il collegamento a internet o a una o più linee Direct Connect.
  * Aggiungine un altro se è presente una rete vMotion separata.

## Download OVA lato client
{: #hcxclient-vcs-client-deployment-client-ova}

HCX lato client è distribuito dall'utente e richiede delle autorizzazioni di livello amministratore al vCenter di origine. Al momento della redazione del presente documento, l'OVA di HCX Manager lato client è di circa 1,7 GB. Quando si utilizza la console {{site.data.keyword.vmwaresolutions_short}} per ordinare HCX, viene fornito un URL con un collegamento per scaricare la versione di HCX per il lato client che corrisponde alla versione di HCX distribuita sul lato cloud. Questo collegamento viene fornito nell'interfaccia utente (IU) di HCX Manager lato cloud.

Viene fornita anche una chiave di registrazione monouso. Per configurare la registrazione di utilizzo, utilizza la seguente procedura.

1. Scarica l'OVA (enterprise) del client HCX dal collegamento fornito nell'IU HCX lato cloud.
    1. Accedi all'IU HCX lato cloud utilizzando l'IU di registrazione HCX fornita da IBM.
    2. Utilizza ID e la password vCenter cloud per accedere all'IU.
    3. Nella scheda **Administration**, seleziona **request download link** per scaricare l'OVA lato client. Utilizza una “jump box” locale per il vCenter di origine dove viene eseguita la distribuzione dell'OVA per completare questo passo.

## Installazione e configurazione dell'HCX sull'origine
{: #hcxclient-vcs-client-deployment-install-cfg-src}

L'installazione in loco implica la distribuzione del dispositivo di gestione HCX e la sua registrazione con l'ambiente vCenter.

### Installazione del dispositivo HCX Manager
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

Installa il dispositivo HCX Manager nel vCenter in loco.
1. Accedi a **My VMware** e scarica il file OVA di Hybrid Cloud Services dalla pagina di scaricamento del prodotto.
2. Apri un browser e accedi al client web vSphere. Visualizza la scheda **Home**.
3. Nell'elenco **Inventories Trees**, fai clic su **Host and Clusters**.
4. Espandi la gerarchia per mostrare i data center.
5. Fai clic con il tasto destro sul data center di destinazione e seleziona **Deploy OVF Template** dal menu. La visualizzazione della voce di menu **Deploy OVF template** potrebbe richiedere alcuni secondi.
6. Scegli **Deploy OVF template**.
  1. Seleziona **Local file** e fai clic su **Browse** per trovare il file OVA scaricato sul computer. Fai clic su **Avanti**.
  2. Sulla pagina **Review details**, seleziona la casella **Accept extra configuration options** e fai clic su **Next**.
  3. Sulla pagina **Accept EULAs**, scorri in basso per controllare l'accordo di licenza utente VMware. Fai clic su **Accept** e **Next**.
  4. Sulla pagina **Select name and folder**, modifica il nome se necessario e seleziona l'ubicazione per Hybrid Cloud Services. Fai clic su **Avanti**.
  5. Sulla pagina **Select a resource**, seleziona l'ubicazione di installazione.
  6. Sulla pagina **Select storage**, seleziona l'archiviazione per Hybrid Cloud Services e fai clic su **Next**. Dall'elenco **Select virtual disk format**, puoi selezionare **thin provisioning** o **thick provisioning**.
  7. Sulla pagina **Setup networks**, associa l'adattatore Hybrid Cloud Services a una rete host scelta dall'elenco **Destination**.
7. Sulla pagina **Customized template**, immetti i valori specifici per l'ambiente:
  * Per le password, il nome utente predefinito per l'interfaccia riga di comando (CLI) e l'interfaccia utente web è **admin**. La password e l'utente **admin** sono obbligatori per accedere all'interfaccia utente web ed è presente inoltre un account utente **root** di cui può essere impostata una password.
  * Immetti e reimmetti la password utente **admin** della CLI.
  * Immetti e reimmetti la password utente **root**. In futuro, se hai bisogno di assistenza da VMware Global Support Services (GSS), questa password potrebbe dover essere condivisa in modo da poter risolvere i problemi del sistema.
  * Per le proprietà di rete, immetti il nome host per la VM HCX Manager. Immetti l'indirizzo IPv4 di rete, il prefisso IPv4 (il CIDR) e il gateway predefinito. La seguente tabella mostra i valori di esempio:

Tabella 1. Valori di esempio per le proprietà di rete

| Campo                    | Valore           |
|--------------------------|-----------------|
| Nome host                 | HCM_1           |
| Indirizzo IPv4 rete 1   | 192.168.200.101 |
| Prefisso IPv4 rete 1    | 24              |
| Gateway IPv4 predefinito     | 192.168.200.1   |
| Indirizzo IPv6 rete 1   |                 |
| Prefisso IPv6 rete 1    |                 |

8. Controlla la pagina di bind vService. Fai clic su **Next** per continuare.
9. Sulla pagina **Ready to complete**, segui questa procedura:
  * Seleziona la casella **Power on after deployment**.
  * Controlla le impostazioni di Hybrid Cloud Services e fai clic su **Finish**. Potrebbero essere necessari diversi minuti per l'accensione del dispositivo Hybrid Cloud Services.
  * Per controllare lo stato, vai alla home page del client web e sulla scheda **Home**, vai a **Inventories** e fai clic su **Hosts and Clusters**. Espandi la gerarchia del data center e fai clic sulla VM (Virtual Machine) del servizio Hybrid Cloud Services per visualizzare un riepilogo nel pannello centrale.
  * Visualizza la scheda **Summary**, la console legge **Powered On** e l'icona **Play** è verde.
10. L'HCX Manager è acceso ed è pronto per essere registrato con il vCenter in loco.

## Configurazione iniziale del dispositivo HCX Manager
{: #hcxclient-vcs-client-deployment-inital-config}

1. Assicurati che il dispositivo virtuale Hybrid Cloud Service abbia l'accesso in uscita a `https://connect.hcx.vmware.com`
2. Accedi all'interfaccia di amministrazione del dispositivo virtuale Hybrid Cloud Services `https://<IP>:9443` con **admin**
3. Fornisci la chiave di licenza raccolta in Prerequisiti lato client.
4. Ubicazione del datacenter cloud HCX
    - Immetti la città più vicina al datacenter dove risiede l'istanza cloud HCX. Se la città non è presente, seleziona la città principale più vicina.
5. Fornisci il nome del sistema

## Importa il certificato server vSphere
{: #hcxclient-vcs-client-deployment-import-cert}

1. Accedi all'interfaccia di amministrazione HCX Manager `https://<IP>:9443`
2. Seleziona la scheda **Amministrazione **, in **Certificato** -> **Certificato CA attendibile**
3. Importa il sito web vSphere Server
   1. Seleziona l'importazione dei certificati dall'URL e inserisci l'URL di registrazione lato cloud HCX.
     * Sao Paulo: `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## Procedura per registrare HCX Manager con vCenter/SSO/NSX
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. Accedi al dispositivo virtuale del servizio Hybrid Cloud Services.
2. Nel pannello **Dashboard**, completa la seguente procedura:
  1. Nel pannello di sinistra, in **Configure Systems**, seleziona vCenter.
  2. Fai clic su **Add vCenter** in alto a destra.
  3. Immetti l'indirizzo IP del vCenter Server nel formato `https://vCenter-host-name` o `https://vCenter-IP-address`. Ad esempio, `https://My-vCenter` o `https://10.108.26.211`
  4. Immetti il nome utente e la password vCenter Server. L'account che viene utilizzato deve avere il ruolo di amministratore di vCenter.
  5. Fai clic su **OK**. Non riavviare quando viene visualizzato il messaggio _You need to restart the app_.
3. Configura il servizio di ricerca / SSO.
  6. Fai clic sulla scheda **Manage**.
  7. Fai clic su **Edit** accanto alla casella di testo **Lookup Service URL**.
  8. Immetti l'endpoint del servizio di rete di ricerca nel seguente formato:
    * Per vCenter Server 6.5 `https://psc/`
  9.  Fornisci i dettagli NSX, se necessario.
  10. Fai clic su **OK**. Non riavviare quando viene visualizzato un messaggio che richiede di riavviare il motore web.
4. Fai clic sulla scheda **Summary** e trova la sezione **Hybridity Management Components**. Arresta e avvia il motore dell'applicazione e il motore web.
5. Per finalizzare la registrazione, disconnettiti dal client web vSphere. Esegui nuovamente l'accesso a vSphere Web Client e verifica che la scheda HCX sia presente.

## Risultati
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

Nota l'icona **Hybrid Cloud** esistente e la voce di menu **Hybrid Cloud Services** sulla sinistra. La registrazione a Hybrid Cloud Services aggiorna queste etichette. Nell'inventario, l'etichetta dell'icona diventa **Hybrid Cloud Services**.

## Link correlati
{: #hcxclient-vcs-client-deployment-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
