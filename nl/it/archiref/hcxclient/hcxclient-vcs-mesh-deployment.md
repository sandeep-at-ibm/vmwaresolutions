---

copyright:

  years:  2019, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Rete di servizi in loco HCX
{: #hcxclient-vcs-mesh-deployment}

Esamina la seguente procedura per configurare l'istanza del client HCX.

## Accoppiamento di siti per l'ambiente IBM Cloud for VMware Solutions
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. Accedi al client web VMware vSphere.
2. Dal menu **Home**, seleziona l'opzione **HCX**.
3. Sotto **Infrastructure**, **InterConnect**, fai clic su **Add Site Pairing**.
  1. Imposta l'URL del sito sull'URL di HCX Cloud Manager, ad esempio `https://x.x.x.x.x`.
  2. Imposta il nome utente e la password sui dettagli dell'amministratore di HCX Manager: admin / password.

    I dettagli precedenti possono essere ottenuti dalla console IBM Cloud from VMware Solutions, sotto **Services**, **HCX on IBM Cloud** per l'istanza vCenter Server.

4. Fai clic su **Connect**.

### Risultati
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

L'accoppiamento di siti viene registrato e visualizzato sull'IU.

## Creazione di profili in loco HCX
{: #hcxclient-vcs-mesh-deployment-profiles}

### Creazione di profili di rete delle reti di servizi in loco
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. Accedi al client web vSphere.
2. Dal menu **Home**, seleziona l'opzione **HCX**.
3. In **Infrastructure**, fai clic su **InterConnect**.
4. In **Multi-Site Service Mesh**, fai clic su **Network Profiles**.
5. Da **Create Network Profile**:
   1. Seleziona il gruppo di porte distribuito, ad esempio quello esterno.
   2. Fornisci intervalli di indirizzi IP per **External IPs**, **External Subnet Prefix Length**, **External Gateway** e **DNS Details**.
   3. Imposta MTU su 1500.
   4. Fai clic su **Create**.
6. Ripeti la procedura sopra indicata per le reti di gestione e vMotion.
   Nota: imposta il valore MTU su 9000.

#### Risultati
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| Nome della rete | MTU |
| -----| ----|
| Esterno | 1500|
| Gestione | 9000|
| vMotion | 9000|

### Creazione di profili di calcolo delle reti di servizi in loco
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. Accedi al client web vSphere.
2. Dal menu **Home**, seleziona l'opzione **HCX**.
3. In **Infrastructure**, fai clic su **InterConnect**.
4. In **Multi-Site Service Mesh**, fai clic su **Compute Profiles**.
5. Da **Create Compute Profile**:
   1. Fornisci il nome del profilo di calcolo.
   2. Seleziona tutti i servizi da abilitare e fai clic su **Continue**.
   3. Seleziona il cluster e fai clic su **Continue**.
   4. Seleziona l'archivio dati e fai clic su **Continue**.
   5. Seleziona il profilo di rete per la gestione e fai clic su **Continue**.
   6. Seleziona **Network Profile for External/Uplink** e fai clic su **Continue**.
   7. Seleziona il profilo di rete per vMotion e fai clic su **Continue**.
   8. Seleziona il profilo di rete per la replica vSphere (gestione) e fai clic su **Continue**.
   9. Seleziona lo switch distribuito per l'estensione, ad esempio Private-Switch e fai clic su **Finish**.

#### Risultati
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

Viene creato un profilo per la combinazione di cluster e archiviazione ed è disponibile con la creazione della rete di servizi.

## Rete di servizi in loco HCX
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## Creazione delle reti di servizi in loco
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. Accedi al client web vSphere.
2. Dal menu **Home**, seleziona l'opzione **HCX**.
3. In **Infrastructure**, fai clic su **InterConnect**.
4. In **Multi-Site Service Mesh**, fai clic su **Service Mesh**.
5. Da **Create Service Mesh**:
   1. Seleziona i siti: in loco e organizzazione vCloud e fai clic su **Continue**.
   2. Seleziona il profilo di calcolo di origine.
   3. Seleziona il profilo di calcolo remoto. Ad esempio, CloudCompute.
   4. Seleziona tutti i servizi e fai clic su **Continue**.
   5. Fai clic su **Continue**, nella pagina Advanced Configuration - Override Uplink Network profiles (Optional)
   6. Fai clic su **Continue**.
   7. Fai clic su **Continue**, lascia i valori predefiniti nella pagina Advanced Configuration - Configure WAN Optimization Service Bandwidth Limit.
   8. Fornisci il nome servizio e fai clic su **Finish**.
6. Guarda l'elenco di attività per la creazione delle reti di servizi. Dopo un corretto completamento, l'ubicazione in loco ha tre dispositivi HCX e l'ubicazione cloud ha tre dispositivi HCX.

### Risultati
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

Una rete di servizi HCX è la configurazione dei servizi HCX effettiva per un sito di origine e uno di destinazione. Una rete di servizi può essere aggiunta a una coppia di siti connessi con un profilo di calcolo valido creato su entrambi i siti.

L'aggiunta di una rete di servizi avvia la distribuzione dei dispositivi virtuali di interconnessione HCX su entrambi i siti. Una rete di servizi di interconnessione viene sempre creata nel sito di origine.

## Estensione di rete
{: #hcxclient-vcs-mesh-deployment-network-stretching}

### Procedura per estendere una rete
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

Per estendere una rete (VLAN o VXLAN) con HCX, completa la seguente procedura dall'IU web vCenter lato client.
1. Accedi al client web vSphere.
2. Dal menu **Home**, seleziona l'opzione **HCX**.
3. Nel menu di sinistra, sotto **Services**, fai clic su **Network Extension**.
4. Fai clic su **Extend Network**:
   1. Seleziona la rete da estendere.
   2. Immetti il gateway predefinito e la maschera di sottorete correnti in formato CIDR.
   3. Fai clic su **Stretch** nella parte inferiore dello schermo per avviare il flusso di lavoro di estensione della rete.

Lo stato di avanzamento della rete viene monitorato nel riquadro delle attività client di vCenter.

## Concetti e prassi ottimali per l'estensione di rete
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

La rete lato client è collegata alla VXLAN lato cloud da una sofisticata VPN multitunnel che consiste in tecnologia HCX proprietaria. Non è basata su NSX ma funziona con NSX e ne estende la capacità. Questo processo è controllato dall'interfaccia utente web vCenter lato client e automatizza la distribuzione e l'avvio di entrambi gli endpoint sul lato client e cloud. La selezione della rete da estendere viene eseguito singolarmente o in batch.

Inoltre, come parte del flusso di lavoro di estensione di rete, NSX sul lato cloud è autorizzato a creare una VXLAN. La VXLAN viene quindi connessa a un'interfaccia creata sul dispositivo L3 lato cloud specificato (DLR o ESG lasciato in uno stato di non connesso) e il dispositivo di estensione di rete (Network Extension) lato cloud.

Di norma, quando migri una specifica applicazione, tutte le reti utilizzate dalle VM (Virtual Machine) applicabili devono essere estese in tutta l'istanza {{site.data.keyword.cloud}}.

Perché di norma e non sempre? Può essere vantaggioso disconnettere del traffico specifico dal lato client dopo la migrazione della VM. Un esempio sono i client di backup guest VM, che possono causare un elevato utilizzo della larghezza di banda quando sono spostati al cloud. Il client di backup in-guest non è necessario quando la VM viene migrata e viene selezionato automaticamente da un backup a livello di blocco più moderno sul lato cloud.

Non è possibile accedere all'adattatore di rete di backup del client poiché questo significherebbe accedere a ogni VM per disattivare la pianificazione di backup del client in-guest. Pertanto, se viene utilizzata una rete di backup, il backup potrebbe avere esito negativo. Questa è una situazione temporanea finché non sarà possibile raggiungere tutte le VM post-migrazione per disabilitare il client di backup in-guest.

La larghezza di banda di una singola estensione di rete è teoricamente 4 Gbps. Tuttavia, questo può essere il limite per tutte le reti estese in una singola coppia di estensione di rete e non può essere raggiunto da una singola rete estesa. Una singola rete estesa può raggiungere ~1 Gbps, a condizione che la larghezza di banda sottostante assegnata sia sufficiente e che la latenza sia bassa (<~10 ms).

### Opzione Proximity Routing (Instradamento di prossimità)
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

Senza alcun tipo di ottimizzazione dell'instradamento, le reti estese eseguono l'instradamento nuovamente verso il lato client per qualsiasi accesso L3. Questo effetto, detto "tromboning", introduce un pattern di traffico inefficiente poiché i pacchetti devono muoversi avanti e indietro tra il client (origine) e il cloud. Questo è vero anche per i casi in cui sia la VM di origine che di destinazione siano nel cloud. La funzione Proximity Routing di HCX è stata progettata per risolvere questo problema e l'uscita di dati di traffico locale.

## Link correlati
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
