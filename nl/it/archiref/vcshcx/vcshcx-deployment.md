---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

# Distribuzione cloud e client
{: #vcshcx-deployment}

Un'installazione HCX minima consiste in una singola distribuzione lato cloud e client. Il lato client HCX
può essere installato su qualsiasi versione di vSphere supportata da HCX, presumendo che ci sia una connettività di rete tra i lati client e cloud.

## Requisiti
{: #vcshcx-deployment-req}

- HCX Manager – Conteggio CPU 4, Memoria 12G, Disco 60G
- CGW – Conteggio CPU 8, Memoria 3G, Disco 2G
- L2C – Conteggio CPU 8, Memoria 3G, Disco 2G
- Ottimizzazione WAN – Conteggio CPU 8, Memoria 14G, Disco 100G

## Cloud
{: #vcshcx-deployment-cloud}

La distribuzione HCX lato cloud è gestita dall'automazione {{site.data.keyword.vmwaresolutions_full}}. La configurazione predefinita utilizza il gruppo di porte pubblico per configurare qualsiasi connettività di endpoint dei componenti della flotta. I componenti della flotta sul lato cloud vengono distribuiti con le loro interfacce endpoint configurate con gli indirizzi IP
pubblici poiché sono dispositivi con un potenziamento della sicurezza. È possibile distribuirli dietro un firewall. La connessione dei lati client e cloud tra di loro tramite un tunnel VPN esistente non è supportata. Se desideri utilizzare la rete privata per la connettività di endpoint HCX, puoi ordinare il lato cloud HCX per la distribuzione della flotta di rete privata per l'utilizzo su un collegamento dedicato come MPLS.

## Client
{: #vcshcx-deployment-client}

HCX lato client è distribuito dall'utente e richiede delle autorizzazioni di livello amministratore al vCenter di origine. Al momento della redazione del presente documento, l'OVA di HCX Manager lato client è di circa 1,7 GB. Quando si utilizza la console {{site.data.keyword.vmwaresolutions_short}} per ordinare HCX, viene fornito un URL con un collegamento per scaricare la versione di HCX per il lato client che corrisponde alla versione di HCX distribuita sul lato cloud. Questo collegamento viene fornito nell'interfaccia utente (IU) di HCX Manager lato cloud.

Viene fornita anche una chiave di registrazione monouso. Per configurare la registrazione di utilizzo, utilizza la seguente procedura.

1. Scarica l'OVA (enterprise) del client HCX dal collegamento fornito nell'IU HCX lato cloud.
    1. Accedi all'IU HCX lato cloud utilizzando l'IU di registrazione HCX fornita da IBM.
    2. Utilizza ID e la password vCenter cloud per accedere all'IU.
    3. Nella scheda **Administration**, seleziona **request download link** per scaricare l'OVA lato client. Utilizza una “jump box” locale per il vCenter di origine dove viene eseguita la distribuzione dell'OVA per completare questo passo.
2. Accedi al client vSphere C++ (o al client web con uno snap-in di integrazione client funzionante) e importa l'OVA che utilizza la procedura guidata di importazione vCenter.
    1. Assicurati che la rete su cui è configurato HCX Manager abbia accesso sia al vCenter di origine che a internet.  
    2. Immetti la chiave di registrazione quando richiesto. (Utilizza il client web se hai lo snap-in degli strumenti client impostato).  
3. Disconnettiti e accedi nuovamente al client web vCenter. L'icona di selezione del menu **HCX** viene visualizzata sotto al menu della schermata home.
4. Per i certificati autofirmati, seleziona la voce di menu HCX per accedere all'IU dello snap-in HCX. Selezionare la scheda **Administration**.
    1. Seleziona l'importazione dei certificati dall'URL e inserisci l'URL di registrazione lato cloud HCX fornito dalla console {{site.data.keyword.vmwaresolutions_short}} per HCX.
    2. Seleziona **New Site Paring** nel riquadro della finestra **Site Parings** nella scheda **Dashboard**.
    3. Attieniti ai prompt e fornisci l'URL di registrazione del lato cloud HCX e ID e password dell'amministratore di vCenter lato cloud.
    4. Continua a seguire i prompt nella procedura guidata di registrazione del sito nella configurazione dei componenti della flotta, compresi il gateway cloud, L2C (Layer 2 Concentrator) e l'ottimizzatore WAN.  

Per il lato client, utilizza il menu **Tasks** per monitorare la distribuzioni dei componenti della flotta. Per la distribuzione lato cloud, utilizza il menu **Tasks** nell'IU web vCenter per la specifica istanza di vCenter Server.

Se si verifica un errore di distribuzione sull'uno o sull'altro lato, le distribuzioni dei componenti della flotta vengono annullate ed eliminate. Dopo che hai determinato la causa dell'errore, fai clic sulla scheda **Interconnect** nell'IU web HCX vCenter sul lato client e seleziona quindi **Install HCX Components** nella parte superiore dello schermo.

Dopo la corretta distribuzione dei componenti della flotta e dopo diversi minuti, lo stato del tunnel per i componenti CGW e L2C viene visualizzato come **Up** nella scheda **Interconnect**.

## Link correlati
{: #vcshcx-deployment-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro) 
