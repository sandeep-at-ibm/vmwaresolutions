---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: single-node trial, data protection DR, order data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine, visualizzazione ed eliminazione delle istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_orderinginstance}

Controlla i requisiti di pianificazione prima di ordinare un'istanza Single-node Trial for Data Protection and Disaster Recovery.

Questa versione di prova viene eliminata automaticamente dopo 90 giorni. Nella pagina dei dettagli dell'istanza viene visualizzato un conto alla rovescia di scadenza per l'istanza Single-node Trial for Data Protection and Disaster Recovery.
{:important}

## Requisiti e pianificazione per l'ordinazione delle istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_orderinginstance-req}

Assicurati di confermare i seguenti requisiti e di completare le seguenti attività.

### Prerequisiti per le istanze HCX in loco
{: #dr_backup_bundle_orderinginstance-hcx-req}

* Richiede VMware vSphere e vCenter 5.5 o superiore.
* L'ambiente vSphere deve disporre di switch distribuiti per le VM che verranno migrate a {{site.data.keyword.cloud_notm}}.
* Il dispositivo virtuale HCX Manager deve poter essere distribuito su una rete privata nell'ambiente in loco e deve essere autorizzato ad accedere a Internet pubblico.

### Account dell'infrastruttura IBM Cloud
{: #dr_backup_bundle_orderinginstance-account-req}

* Per utilizzare {{site.data.keyword.vmwaresolutions_short}} per effettuare l'ordine di istanze, devi disporre di un account dell'infrastruttura {{site.data.keyword.cloud_notm}}. Il costo dei componenti ordinati nelle tue istanze viene addebitato su tale account {{site.data.keyword.cloud_notm}}.
*  Configura le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Impostazioni** dal riquadro di navigazione a sinistra.

### Requisiti del nome dell'istanza
{: #dr_backup_bundle_orderinginstance-inst-name-req}

Controlla i requisiti del nome dell'istanza:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome dell'istanza deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* La lunghezza massima del nome dell'istanza è di 10 caratteri.
* Il nome dell'istanza deve essere univoco all'interno del tuo account.

## Procedura per ordinare istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_orderinginstance-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic sull'icona **VMware** nel riquadro di navigazione a sinistra e quindi sulla scheda **Single-node Trial for Data Protection and Disaster Recovery** nella sezione **VMware Virtual Data Centers**.
2. Nella pagina **Single-node Trial for Data Protection and Disaster Recovery**, fai clic su **Continua**.
3. Completa la procedura per richiedere un account dell'infrastruttura {{site.data.keyword.cloud_notm}} o fornisci i tuoi **Nome utente** e **Chiave API** esistenti e fai clic su **Recupera**.

 Questa sezione è nascosta se la chiave API esiste.
 {:note}
4. Immetti il nome dell'istanza.
5. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.  

 Per impostazione predefinita, il {{site.data.keyword.CloudDataCent_notm}} DAL09 è preselezionato. Seleziona un'ubicazione {{site.data.keyword.CloudDataCent_notm}} diversa, se necessario.
 {:note}
6. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
   1. Esamina le impostazioni per l'istanza.
   2. Esamina il costo stimato dell'istanza. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo
del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di ordinare l'istanza.
   4. Fai clic su **Fornitura**.

### Risultati dopo l'ordinazione delle istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_orderinginstance-results}

* La distribuzione dell'istanza inizia automaticamente e viene ordinata la chiave di attivazione del servizio HCX on {{site.data.keyword.cloud_notm}}.
* Puoi verificare lo stato della distribuzione, inclusi gli eventuali problemi che potrebbero richiedere la tua attenzione, visualizzando la sezione **Cronologia distribuzione** dei dettagli dell'istanza.
* Quando l'istanza viene distribuita correttamente, vengono installati i componenti descritti in [Specifiche tecniche per le istanze Single-node Trial for Data Protection and Disaster Recovery](/docs/services/vmwaresolutions/services?topic=vmware-solutions-dr_backup_bundle_overview#dr_backup_bundle_overview-tech-specs).
* Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e riceverai una notifica via e-mail.

#### Processo di distribuzione per HCX on IBM Cloud
{: #dr_backup_bundle_orderinginstance-hcx-deploy-process}

La distribuzione di HCX on {{site.data.keyword.cloud_notm}} è automatizzata. Le seguenti istruzioni vengono completate dal processo automatico di {{site.data.keyword.vmwaresolutions_short}}:
1. Dall'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate tre sottoreti per HCX:
   * Due sottoreti portatili private per la gestione HCX.
   * Una sottorete portatile pubblica per l'attivazione e la manutenzione con VMware. Questa sottorete viene utilizzata anche per le interconnessioni HCX.

   Gli indirizzi IP nelle sottoreti ordinate per HCX devono essere gestiti dall'automazione di VMware on {{site.data.keyword.cloud_notm}}. Questi indirizzi IP non possono essere assegnati alle risorse VMware, come VM ed Edge NSX, create da te. Se hai bisogno di più indirizzi IP per le tue risorse VMware, devi ordinare le tue proprie sottoreti da {{site.data.keyword.cloud_notm}}.
   {:important}
3. Vengono creati tre pool di risorse e cartelle VM per HCX, necessari per interconnessioni HCX, componenti HCX locali e componenti HCX remoti.
4. Viene distribuita e configurata una coppia di gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HCX:
   * Le interfacce di uplink pubblico e privato vengono configurate utilizzando le sottoreti ordinate.
   * Gli ESG vengono configurati come una coppia di dispositivi edge di grandi dimensioni con l'alta disponibilità (HA) abilitata.
   * Le regole del firewall e le regole NAT (Network Address Translation) vengono configurate per consentire il traffico HTTPS in entrata e in uscita da e verso HCX Manager.
   * Vengono configurate le regole di bilanciamento del carico e i pool di risorse. Tali regole e pool di risorse sono utilizzati per inoltrare il traffico in entrata correlato a HCX ai dispositivi virtuali appropriati di HCX Manager e vCenter Server (con Platform Services Controller integrato).
   * Viene applicato un certificato SSL per crittografare il traffico HTTPS in entrata correlato a HCX che arriva tramite gli ESG.

   L'edge di gestione HCX è dedicato al traffico di gestione HCX tra i componenti HCX in loco e i componenti HCX lato cloud. Non modificare l'edge di gestione HCX o utilizzarlo per le estensioni di rete HCX. Crea, invece, edge separati per le estensioni di rete. Inoltre, l'utilizzo di un firewall o la disabilitazione delle comunicazioni dell'edge di gestione HCX ai componenti di gestione IBM privati o all'Internet pubblico potrebbero influire negativamente sulla funzionalità di HCX.
   {:important}

5. HCX Manager on {{site.data.keyword.cloud_notm}} viene distribuito, attivato, e configurato:
   * HCX Manager viene registrato con vCenter Server.
   * Vengono configurati HCX Manager, vCenter Server (con Platform Services Controller integrato) e NSX Manager.
   * Viene configurata la flotta HCX.
   * Vengono configurati i contenitori di distribuzione HCX locali e remoti.
6. Il nome host e l'indirizzo IP di HCX Manager vengono registrati con il server DNS di VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualizzazione dei dettagli dell'istanza
{: #dr_backup_bundle_orderinginstance-view-inst-details}

Puoi controllare lo stato della distribuzione visualizzando i dettagli dell'istanza. Fai clic su **Risorse** nel riquadro di navigazione a sinistra e individua la tabella **Istanze vCenter Server** o **Istanze HCX on-premise** per visualizzare informazioni sulle istanze che hai ordinato.

Una volta che l'istanza è stata distribuita correttamente, i componenti descritti nelle sezioni delle *Specifiche tecniche* di questo argomento vengono installati sulla tua piattaforma virtuale VMware e la chiave di attivazione del servizio HCX on {{site.data.keyword.cloud_notm}} in loco viene elencata nella tabella **Istanze HCX on-premise**.

Lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e ricevi una notifica per email.

### Operazioni successive
{: #dr_backup_bundle_orderinginstance-next}

Installa HCX Enterprise Manager in loco e configura la connessione alla tua istanza HCX on {{site.data.keyword.cloud_notm}}.

1. Individua la chiave di attivazione in loco nella pagina **Risorse**.
  1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
  2. Nella tabella **Istanze vCenter Server**, controlla la colonna **Tipo** per individuare l'istanza Single-node Trial for Migration and App Modernization e prendi nota del nome dell'istanza.
  3. Scorri fino alla tabella **Istanze HCX on-premise** e controlla la colonna **Nome** per individuare l'istanza che ha lo stesso nome dell'istanza a singolo nodo che hai ordinato con il suffisso *-OnPrem*.
  4. Prendi nota della chiave nel campo **Chiave di attivazione**.
2. Ottieni il HCX Enterprise Manager Open Virtual Appliance (OVA) dalla console HCX on {{site.data.keyword.cloud_notm}} HCX Manager.
  1. Collegati alla console HCX Cloud.
    1. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza Single-node Trial for Migration and App Modernization per visualizzarne i dettagli.
    2. In **Informazioni di accesso**, individua e prendi nota delle credenziali vCenter.
    3. Fai clic su **Servizi** dal riquadro di navigazione a sinistra.
    4. Nella pagina **Servizi**, fai clic su **Servizi installati**.
    5. Nella pagina dei dettagli **HCX on IBM Cloud**, individua e prendi nota dell'**IP cloud HCX**.
    6. Assicurati di essere collegato alla VPN per accedere alla tua rete privata {{site.data.keyword.cloud_notm}}.
    7. Fai clic su **Visualizza console cloud HCX**.
  2. Nella **Console cloud HCX**, completa la seguente procedura:
      1. Fai clic sulla scheda **Amministrazione**.
      2. Nella scheda **Aggiornamenti di sistema**, fai clic su **RICHIEDI LINK DI DOWNLOAD**.
      3. Fai clic su **COPIA LINK** e utilizza quindi questo link per scaricare HCX Enterprise Client in un ambiente in loco con accesso al tuo ambiente vSphere in loco.
3. Nel client web VMware vSphere, distribuisci HCX Enterprise Client come dispositivo virtuale HCX Manager nel tuo ambiente in loco. Attieniti alle istruzioni contenute nel manuale [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

    Devi distribuire l'HCX Manager in loco su una rete privata e consentirgli l'accesso alla rete pubblica. Puoi utilizzare un gateway Edge NSX, Vyatta o simile per consentire l'accesso a internet all'HCX Manager in loco. Se i gateway utilizzati per l'accesso alla rete privata e l'accesso alla rete pubblica sono diversi, si consiglia di utilizzare il gateway predefinito per consentire l'accesso alla rete pubblica e la **Console di gestione HCX Manager** per creare una rotta statica per l'accesso alla rete privata.  
    {:note}
4. Utilizza la chiave di attivazione in loco annotata nel passo 1 per attivare la tua VM HCX Enterprise Manager.
  1. Accedi alla tua VM HCX Enterprise Manager in loco utilizzando le credenziali specificate durante la distribuzione di OVA.
  2. Immetti la chiave di attivazione quando richiesto.

  Attieniti alle istruzioni contenute nel manuale [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

5. Un certificato SSL autofirmato è stato generato dal servizio HCX on {{site.data.keyword.cloud_notm}}. Devi importare il certificato nell'HCX Manager in loco completando le seguenti istruzioni:
    1. Nella **Console di gestione HCX Manager** in loco, fai clic sulla scheda **Amministrazione**.
    2. Dal riquadro di navigazione a sinistra, fai clic su **Certificato CA attendibile** e quindi su **IMPORTA** sulla destra.
    3. Fai clic su **URL** e immetti quindi l'URL del certificato che vuoi applicare. Si tratta dell'**IP cloud HCX** (``https://<cloud-side public IP>``) che puoi trovare nella pagina dei dettagli del servizio HCX on {{site.data.keyword.cloud_notm}} nella console {{site.data.keyword.vmwaresolutions_short}}.
    4. Fai clic su **APPLICA**.
6. Continua la configurazione iniziale e crea l'interconnessione. Attieniti alle istruzioni contenute nel manuale [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.
7. Estendi le reti in VMware HCX dal locale a {{site.data.keyword.cloud_notm}}. Attieniti alle istruzioni contenute nel manuale [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.
8. Migra le VM tra i locale e {{site.data.keyword.cloud_notm}}. Attieniti alle istruzioni contenute nel manuale [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

Devi gestire i componenti dell'infrastruttura {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console.
Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console e il tuo ambiente potrebbe diventare instabile.
{:important}

## Procedura per eliminare istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_orderinginstance-deleting-procedure}

Quando elimini un'istanza Single-node Trial for Disaster Recovery, i seguenti componenti vengono rilasciati in modo sequenziale:

1. Tutti i servizi distribuiti
3. Licenze del prodotto VMware
4. Server ESXi
5. Sottoreti
6. VLAN

A causa delle dipendenze delle risorse, i componenti della tua istanza non vengono rilasciati immediatamente quando elimini l'istanza. Ad esempio, le sottoreti e le VLAN non possono essere eliminate finché i server ESXi non vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}}, cosa che avviene alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}. Alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni, le sottoreti e le VLAN vengono eliminate e l'eliminazione dell'istanza viene completata.

Per l'istanza eliminata ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
{:note}

Completa la seguente procedura per eliminare un'istanza Single-node Trial for Data Protection and Disaster Recovery:

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, trova l'istanza da eliminare.
3. Nella colonna **Azioni**, fai clic sull'icona Elimina.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Nella colonna **Azioni**, fai di nuovo clic sull'icona Elimina.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Link correlati
{: #dr_backup_bundle_orderinginstance-related}

* [Guida di vCenter Server e IBM Cloud Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Apri un ticket per IBM Cloud privato](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [Risorse VMware HCX](https://hcx.vmware.com/#/docs){:external}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Annullamento dei server virtuali](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
