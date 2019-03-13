---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Installazione e configurazione dei servizi ibridi
{: #hcx-archi-install-cfg-hybrid}

Il programma di installazione esegue il provisioning e configura una macchina virtuale per ogni applicazione virtuale del servizio. Le macchine virtuali del servizio vengono distribuite sia in loco che nel cloud.

## Prerequisiti
{: #hcx-archi-install-cfg-hybrid-prereq}

* L'HCX Manager deve essere installato in loco e registrato con un endpoint cloud abilitato VCF/VCS HCX.
* Il data center virtuale di destinazione deve disporre di sufficienti risorse.

## Panoramica sulla configurazione
{: #hcx-archi-install-cfg-hybrid-config-ovw}

La procedura di configurazione presuppone che saranno configurate tutte le applicazioni virtuali del servizio. Tuttavia, non sono tutte necessarie.
* L'Hybrid Cloud Gateway è obbligatorio.
* L'installazione dell'ottimizzazione della WAN viene eseguita selezionando la casella WAN Optimization Service durante l'installazione. Non è necessaria ulteriore configurazione.
* Per configurare il servizio Network Extension, consulta la sezione _Configurazione del servizio Network Extension_. La distribuzione dell'applicazione facoltativa può essere rinviata ritornando alla pagina Hybrid Services e installando l'applicazione successivamente.

## Avvio dell'installazione e della configurazione dell'applicazione virtuale del servizio ibrida
{: #hcx-archi-install-cfg-hybrid-start-hsva}

L'interfaccia web semplice viene utilizzata per installare le applicazioni virtuali del servizio e per configurare ulteriori concentratori di livello 2.

L'HCX Manager deve essere installato e registrato con l'endpoint cloud abilitato VCF/VCS HCX.

### Procedura per installare e configurare l'applicazione virtuale del servizio ibrida
{: #hcx-archi-install-cfg-hybrid-proc-install}

1. Accedi al client web vSphere.
2. Sulla scheda **Home**, fai clic sull'icona **Hybrid Cloud Services**.
3. Fai clic sulla scheda **Hybrid Services**.
4. Fai clic su **Install Service**.
5. Sulla pagina **Choose Hybrid Services**, seleziona i servizi che devono essere installati e fai clic su **Next**.

### Operazioni successive
{: #hcx-archi-install-cfg-hybrid-start-hsva-next}

1. Il passo successivo è quello di configurare l'Hybrid Cloud Gateway se necessario.
2. Un concentratore di livello 2 può essere aggiunto a un'installazione esistente in qualsiasi momento se sono disponibili risorse sufficienti per supportare l'estensione.

## Configurazione dell'Hybrid Cloud Gateway
{: #hcx-archi-install-cfg-hybrid-config-hcg}

Configura l'applicazione virtuale del servizio Hybrid Cloud Gateway. Prima di cominciare, segui la procedura in _Avvio dell'installazione e della configurazione dell'applicazione virtuale del servizio ibrida_ e seleziona Hybrid Cloud Gateway.

### Procedura per configurare l'Hybrid Cloud Gateway
{: #hcx-archi-install-cfg-hybrid-proc-config-hcg}

Sulla pagina **Hybrid Cloud Gateway**, fornisci i seguenti valori e fai clic su **Next**:
* **Network** - Lo switch che connette l'interfaccia di gestione Hybrid Cloud Gateway. Nei casi di utilizzo 1 e 2, può essere uno switch virtuale standard o uno distribuito virtuale. Per tutte le configurazioni che utilizzano l'estensione di livello 2, deve essere uno switch distribuito virtuale.
* **Cluster/Host** - Seleziona il cluster o l'host in cui il gateway cloud deve essere distribuito.
* **Datastore** - Seleziona il datastore in cui distribuire il gateway cloud.
* **VM/Hostname** - Questo valore è facoltativo.
* Fornisci l'indirizzo IP/CIDR, il gateway predefinito e il server DNS da utilizzare con l'interfaccia di gestione del gateway cloud.
* Per immettere più indirizzi per il server DNS, separali con delle virgole.
* In **Extended (optional)**, scegli la rete vMotion se applicabile e imposta le password **admin** e **root**. Queste password sono specifiche per l'applicazione Hybrid Cloud Gateway. Il nome utente e la password non devono corrispondere a quelli configurati per l'applicazione Hybrid Cloud Services.

## Configurazione del servizio Network Extension
{: #hcx-archi-install-cfg-hybrid-config-nes}

Configura un servizio Network Extension per una distribuzione a singolo percorso o per un'estensione di rete autonoma su un percorso alternativo. Prima di cominciare, seleziona il servizio Network Extension. Se è installata la configurazione a singolo percorso, **Network Extension** è la tua unica scelta.

### Procedura per configurare il servizio Network Extension
{: #hcx-archi-install-cfg-hybrid-proc-config-nes}

1. Sulla pagina **Network Extension Service**, seleziona uno switch distribuito virtuale dal menu **Distributed Switch**. Quando installi un concentratore di livello 2, sarà disponibile la casella di spunta **Route stretched networks via Hybrid Cloud Gateway**. Non è presente per il L2C ad elevata velocità effettiva.
2. Se **Route stretched networks via Hybrid Cloud Gateway** è selezionata, il programma di installazione determina una posizione ragionevole per il concentratore di livello 2 (basato sullo switch) e popola le informazioni di posizionamento. Altrimenti, le informazioni di posizionamento devono essere immesse manualmente nel prossimo passo.
3. Imposta l'instradamento per il posizionamento del concentratore L2. Se **Route stretched networks via Hybrid Cloud Gateway** è stata selezionata, questi valori non possono essere modificati.
  * **Network** - La rete di distribuzione per l'interfaccia di gestione del concentratore di livello 2.
  * **Compute** - Il cluster o l'host di distribuzione per il concentratore di livello 2.
  * **Datastore** - Il datastore di distribuzione per il concentratore di livello 2.
  * **VM/Hostname** - Questo valore è facoltativo.
4. Specifica i parametri di rete per il concentratore di livello 2 locale.
  * Se questa opzione è disabilitata, utilizza i parametri predefiniti forniti dal programma di installazione.
  * Se il gruppo di porte selezionato nel menu **Network** dalla pagina Hybrid Cloud Gateway non fa parte dello switch distribuito, seleziona **Specify the Network Parameters for the local Layer 2 Concentrator** e modifica le caselle di testo **Extended Configurations**.
5. (Facoltativo) **Extended Configurations** - Imposta le password **admin** e **root** per questo concentratore di livello 2 specifico.
6. Fai clic su **Avanti**. Sulla pagina **Ready to complete**, controlla le informazioni e fai clic su **Finish**.

## Monitoraggio della distribuzione dell'applicazione del servizio
{: #hcx-archi-install-cfg-hybrid-monitor}

La console delle attività può essere utilizzata per monitorare l'avanzamento della distribuzione per una macchina virtuale del servizio.

### Procedura per monitorare la distribuzione dell'applicazione del servizio
{: #hcx-archi-install-cfg-hybrid-monitor-proc}

1. Accedi al client web vSphere. Sulla scheda **Home**, fai clic sull'icona **Hybrid Cloud Services**.
2. Sul pannello **Hybrid Cloud Services**, fai clic sulla scheda **Hybrid Services**. La distribuzione dell'applicazione virtuale può essere monitorata dalla console delle attività.
3. Vai al pannello **Recent Tasks** e visualizza **All Users’ Tasks**.
4. Fai clic su **More Tasks** per aprire la console delle attività.
5. Nella console delle attività, controlla le attività di distribuzione.
6. Quando tutte le attività sono state completate, vai all'elenco dell'inventario e fai clic su **Hybrid Cloud Services**.
7. Nel pannello centrale, fai clic sulla scheda **Hybrid Services**.
8. Controlla il riepilogo della configurazione per le applicazioni virtuali del servizio ibride.

## Visualizzazione dello stato del tunnel
{: #hcx-archi-install-cfg-hybrid-view-tunnel}

Visualizza lo stato del tunnel del gateway cloud. Il servizio Network Extension deve essere attivo prima di poter estendere una rete.

### Procedura per visualizzare lo stato del tunnel
{: #hcx-archi-install-cfg-hybrid-proc-view-tunnel}

1. Per controllare lo stato del tunnel dal client web, seleziona **Hybrid Cloud Services** nell'inventario e fai clic sulla scheda **Hybrid Services**.
2. Per confermare che un tunnel Hybrid Cloud Gateway sia corretto, controlla che lo stato di CGW (l'acronimo per Hybrid Cloud Gateway) sia **Active** e all'estrema destra, che il tunnel sia codificato con il colore verde.

## Estensione di una rete di livello 2 a IBM Cloud

Estendi una rete di livello 2 dal data center in loco al cloud abilitato VCF/VCS HCX.
{: #hcx-archi-install-cfg-hybrid-stretch-layer-2}

### Prerequisiti per l'estensione di una rete di livello 2 a IBM Cloud
{: #hcx-archi-install-cfg-hybrid-prereq-stretch-layer-2}

* Solo i gruppi di porte contrassegnati con la VLAN (diversi rispetto a quelli del tipo di VLAN None o di ID VLAN 0) possono essere estesi. Le VXLAN possono essere considerate VLAN.
* Questa procedura utilizza la procedura guidata **Extend Network**. Questa procedura guidata deve essere eseguita dalla vista dell'inventario di rete del client web vSphere®. Sebbene la procedura guidata sia visibile da altre viste, deve essere eseguita dal contesto dell'inventario per ottenere le informazioni corrette.

### Procedura per estendere una rete di livello 2 a IBM Cloud
{: #hcx-archi-install-cfg-hybrid-proc-stretch-layer-2}

1. Accedi al client web vSphere. Sulla scheda **Home** nel pannello centrale, fai clic sull'icona **Networking** nell'elenco **Inventories**.
2. Nella gerarchia **Networking**, identifica il gruppo di porte per la rete che deve essere estesa.
3. Fai clic con il tasto destro sul gruppo di porte e dal menu seleziona **Hybridity Actions** e **Extend Network**.
4. Sulla pagina **Select source port groups**, conferma le informazioni sul gruppo di porte e immetti l'indirizzo IP del gateway (**Gateway IP address**) e il prefisso per la rete. Fai clic su **Avanti**.
5. Sulla pagina **Select destination gateway**, completa la seguente procedura:
  1. Seleziona l'organizzazione cloud VCF/VCS Hybrid Cloud Services dal menu **Organization**.
  2. Seleziona il data center virtuale cloud VCF/VCS Hybrid Cloud Services dal menu.
  3. Lascia **Proximity Routing** disabilitato per forzare una VM all'interno del cloud abilitato VCF/VCS Hybrid Cloud Services ad utilizzare sempre il gateway in loco per accedere a internet. Per impostazione predefinita, il traffico originato da una VM nel cloud abilitato VCF/VCS Hybrid Cloud Services attraversa il percorso di dati di livello 2, ritorna al data center in loco e arriva al gateway predefinito. Se **Proximity Routing** è selezionato, una VM all'interno del cloud abilitato VCF/VCS Hybrid Cloud Services può accedere a internet senza attraversare il percorso di dati di livello 2 di vSphere.
  4. Seleziona il gateway di destinazione remoto dall'elenco dei gateway facendo clic sulla relativa riga. Fai clic su **Avanti**.
6. Sulla pagina **Ready to complete**, controlla tutti i valori forniti. Fai clic su **Finish**.
7. Per tenere traccia dell'avanzamento dell'estensione di rete, vai alla finestra **Recent Tasks**, fai clic sulla scheda **All** e visualizza **All Users’ Tasks**.
8. Per aprire la console delle attività, fai clic su **More Tasks**. L'estensione di rete viene eseguita quando lo stato dell'attività **Extend Network** è **Completed**.

## Link correlati
{: #hcx-archi-install-cfg-hybrid-related}

* [Modifica o disinstallazione dell'HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
