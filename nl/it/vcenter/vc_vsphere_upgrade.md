---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-07"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade del software vCenter Server vSphere da VMware vSphere 6.5 a 6.7
{: #vc_vsphere_upgrade}

L'offerta vCenter Server on {{site.data.keyword.cloud}} è una soluzione di distribuzione automatizzata completa per lo stack VMware vSphere SDDC inclusi vSphere, NSX e facoltativamente i prodotti vSAN. Sebbene vCenter Server automatizzi le parti più impegnative della distribuzione, dell'espansione e della contrazione di un'infrastruttura basata su VMware SDDC, non è un servizio gestito. Poiché vCenter Server ha una politica di supporto dell'automazione delle versioni del software VMware SDDC all'interno dell'intervallo N-1, devi eseguire l'upgrade delle istanze esistenti di vCenter Server se vuoi continuare a trarre vantaggio dall'automazione {{site.data.keyword.vmwaresolutions_short}}.

Le versioni vCenter Server all'esterno dei livelli necessari per il supporto dell'automazione continuano ad essere supportate come richiesto dalla politica del supporto VMware, ma non funzionano più con l'automazione {{site.data.keyword.vmwaresolutions_short}}. Devi eseguire l'applicazione della patch e l'upgrade periodici del software VMware durante il ciclo di vita di un'istanza vCenter Server. Ciò include l'upgrade del software VMware SDDC a una versione supportata dall'automazione {{site.data.keyword.vmwaresolutions_short}} in base alle necessità.

La seguente procedura fornisce i passi necessari per convertire un'istanza basata su vCenter Server VMware vSphere 6.5 in un'istanza basata su vCenter Server VMware vSphere 6.7. Questi passi forniscono l'upgrade iniziale al livello 6.7 più recente di vSphere, NSX e vSAN. A seguito di questo upgrade, potresti dover utilizzare la normale funzionalità di vSphere per eseguire l'upgrade degli strumenti e dei livelli hardware della VM (virtual machine).

vCenter Server è progettato per consentire un aggiornamento “dinamico”. Ovvero, i carichi di lavoro della VM al momento in funzione continuano a funzionare senza interruzione se completi la seguente procedura. Le aziende devono coinvolgere le loro politiche di gestione per consentire un upgrade e un piano strutturati e comunicati per eventuali imprevisti. Tuttavia, durante il processo di upgrade di determinate funzioni di gestione, ad esempio il gestore vCenter e NSX, possono venire coinvolte interruzioni temporanee delle funzioni di gestione, modifiche di configurazione e lo spegnimento e l'accensione delle VM.
{:note}

## Prima di iniziare
{: #vc_vsphere_upgrade-prereq}

Il tempo stimato per eseguire l'upgrade è sconosciuto. È possibile che impieghi diverse finestre di manutenzione per eseguire l'upgrade completo di un ambiente. L'esecuzione di versioni di livello superiore o inferiore del software SDDC è supportata da VMware durante il processo di upgrade. Tuttavia, alcune funzioni come vMotion, potrebbero essere limitate durante questo processo.

Completa i seguenti requisiti prima di iniziare l'upgrade:  
* È tua responsabilità eseguire l'upgrade delle estensioni o degli snap-in all'interno dell'ambiente vCenter Server. Esamina la seguente documentazione prima di pianificare il tuo upgrade:
  * [VMware vCenter Server 6.7 Update 1b Release Notes](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:new_window}
  * [About VMware ESXi Upgrade](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:new_window}
* Configura vSphere Update Manager (VUM) all'interno della tua istanza vCenter Server per scaricare gli aggiornamenti più recenti da VMware vSphere. Per ulteriori informazioni, vedi [Introduzione a VMware Update Manager](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro).
*	Apri un ticket di supporto con il team {{site.data.keyword.vmwaresolutions_short}} per notificare loro che stai per eseguire un upgrade. Il ticket rimane aperto fino a quando l'istanza non viene registrata al livello di upgrade eseguito nella console {{site.data.keyword.vmwaresolutions_short}}.
* Conferma se l'istanza vCenter Server di cui stai eseguendo l'upgrade è collegata o meno a un'altra istanza vCenter Server come primaria o secondaria nella console {{site.data.keyword.vmwaresolutions_short}}. È necessario che i PCS (Platform Services Controllers) di tutte le istanze collegate siano stati sottoposti ad upgrade come parte di una particolare upgrade del sito.
* Conferma quanto segue per le istanze basate su vSAN:
  * Assicurati che lo strumento di integrità di vSAN sia abilitato e non riporti errori critici. Se sono presenti errori critici, contatta il team di supporto IBM con l'ID ticket di supporto dell'upgrade.
  * Assicurati che sia presente spazio su ciascun nodo per gestire la ridondanza di ricostruzione degli oggetti vSAN che dovesse verificarsi nel caso in cui un host ESXi non riesca a tornare attivo durante l'upgrade. Potresti dover ridurre l'utilizzo del disco o aggiungere un host ESXi aggiuntivo prima dell'upgrade.  
  * Verifica se l'utilizzo del volume vSAN complessivo supera o meno il 70 percento. Potresti dover ridurre l'utilizzo del disco o aggiungere un host ESXi aggiuntivo prima dell'upgrade.
* Se la tua istanza vCenter Server è stata avviata come un {{site.data.keyword.vmwaresolutions_short}} V2.5 o successiva, devi contattare il supporto IBM per l'ID utente e la password **root** per PSC e vCenter poiché solo un account di servizi con accesso **customerroot** è visibile sul portale. Se l'ID utente PSC e vCenter **root** è visibile con la sua password, questo passo non è necessario.
* Conferma che hai un ID utente https://my.vmware.com per il quale scaricare i file binari di upgrade necessari. Se non ce l'hai, contatta il supporto IBM con l'ID ticket di supporto dell'upgrade.
* Conferma che VUM è configurato per raggiungere l'indirizzo https://www.vmware.com per scaricare le patch. Se non può essere configurato a causa di politiche di sicurezza, devi scaricare manualmente le serie di patch più recenti e caricarle nel VUM. Per ulteriori informazioni, vedi [Introduzione a VMware Update Manager](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro).

### Preparazione del tuo jumpbox
{: #vc_vsphere_upgrade-prereq-jumpbox}

Poiché la VPN di accesso del client {{site.data.keyword.cloud_notm}} è limitata a 512 Kbps, ti consigliamo di eseguire il provisioning di una VSI (Virtual Server Instance) del server {{site.data.keyword.cloud_notm}} Windows 2012-2016 o di configurare una VM Windows simile in un ambiente vSphere vCenter Server separato all'interno dello stesso {{site.data.keyword.CloudDataCent_notm}}. Viene utilizzato come un jumpbox nell'istanza vCenter Server per eseguire l'upgrade e consente di scaricare velocemente i file binari dall'indirizzo https://my.vmware.com. Anche se è possibile collocare questa VM nell'istanza vCenter Server di cui viene eseguito l'upgrade, non te lo consigliamo.

Completa i seguenti passi per ordinare un jumpbox VSI.

Ignora il primo passo se hai già un jumpbox VSI nel tuo ambiente.
{:note}

1. Ordina una VSI oraria o mensile dal [portale del cliente dell'infrastruttura IBM Cloud](https://control.softlayer.com/). Ordina i seguenti attributi:
  * Windows 2012 o 2016 Server Standard
  * 2 CPU
  * 16 GB di memoria
  * 100 G di disco
  * Uplink pubblici e privati da 1 Gbps
2. Quando viene eseguito il provisioning della VSI, configura {{site.data.keyword.cloud_notm}} Access Control Lists (ACLs) all'interno del pannello di controllo per consentire tutte le entrate e le uscite dai link privati e solo le uscite da quelli pubblici. Devi utilizzare la VPN di accesso del client {{site.data.keyword.cloud_notm}} per le sessioni RDP (Remote Desktop Protocol) nella VSI Windows.
3. RDP nella VSI Windows. Modifica le sue impostazioni DNS (Domain Name System) sull'adattatore della rete privata in modo che punti solo al server AD Windows all'interno dell'istanza vCenter Server di cui eseguire l'upgrade.
4. Scarica e installa il browser Google Chrome. Puoi utilizzare Mozilla Firefox, ma si verifica un problema di cache quando utilizzi le schermate VUM all'interno dell'interfaccia utente vCenter.
5. Scarica il tuo software preferito per il terminale SSH. Ad esempio, Putty.
6. Utilizza Google Chrome per accedere all'istanza vCenter Server di cui eseguire l'upgrade. Utilizza **administrator@vsphere.local** e assicurati di poter visualizzare l'interfaccia utente.  
7. Controlla l'ambiente vSphere alla ricerca di errori e problemi come discusso nella sezione precedente.
8. Utilizza il tuo software del terminale SSH per accedere a PSC e a vCenter con le password fornite dal supporto o dal portale per **root**.
9. Facoltativamente, utilizza l'ID utente e la password **root** annotati nel pannello di controllo SL per accedere a ogni host ESXi per verificare la password **root**.

#### Download dei file binari
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Utilizza il tuo jumpbox VSI di Windows e accedi al tuo account https://my.vmware.com per scaricare i seguenti file binari:

*	Immagine VMware vSphere 6.7u1 Hypervisor (ESXi ISO) (Include gli strumenti VMware)
* ISO del dispositivo vCenter 6.7u1b. Non il bundle di aggiornamento.
*	NSX for vSphere 6.4.4 Upgrade Bundle

Per le unità Intel Optane, scarica il seguente file per utilizzarlo come parte del processo di applicazione della patch post-upgrade che utilizza VMware Update Manager.

Individua il file ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` per il driver Intel NVMe per Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) all'indirizzo https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742.

#### Backup dei componenti

Prima di iniziare l'upgrade, esegui il backup di ciascun componente.

* Per informazioni sul backup di vCenter Server e PSC, vedi [Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}.
* Per ulteriori considerazioni e informazioni sul backup di vCenter Server e PSC, vedi [Backup basato su file di vCenter](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter).
*	Per informazioni sul backup di NSX, vedi [Backing Up NSX Manager Data](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}.

Ti consigliamo di utilizzare il backup basato su file. Il backup basato sulle immagini (utilizzando vSphere Data Protection) non è supportato in VMware vSphere 6.7.
{:note}

## Procedura per eseguire l'upgrade del software IBM vCenter Server vSphere da 6.5 a 6.7
{: #vc_vsphere_upgrade-procedure}

Se riscontri un problema in qualsiasi momento durante il processo di upgrade, utilizza il ticket di upgrade di {{site.data.keyword.vmwaresolutions_short}} che hai aperto all'inizio del processo per contattare il supporto IBM. Il supporto IBM apre ticket con il supporto VMware come richiesto.

**Importante**:

* Devi utilizzare questo percorso per assicurarti che {{site.data.keyword.vmwaresolutions_short}} fornisca al supporto VMware tutte le informazioni necessarie sulla progettazione e la configurazione di vCenter Server e le informazioni {{site.data.keyword.cloud_notm}}. Seguendo questo processo per garantire che le informazioni accurate vengano condivise con il supporto VMware, si riduce l'esperienza di supporto. Una volta che il supporto IBM fornisce le informazioni necessarie al supporto VMware, puoi interagire direttamente con il supporto VMware in base alle esigenze.
* Assicurati di tenere traccia di tutte le nuove password e credenziali che crei come parte di questo processo di upgrade. Il supporto IBM richiede queste credenziali alla fine del processo di upgrade per aggiornare il suo database interno.

### Upgrade di VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

L'upgrade di VMware NSX può richiedere un po' di tempo in quanto il processo di upgrade aggiorna i bundle di installazione vSphere sugli host ESXi e richiede un riavvio di ciascun host. Pianifica di conseguenza la tua finestra di manutenzione.

#### Prima di eseguire l'upgrade di VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* Se hai Zerto for {{site.data.keyword.cloud_notm}} installato nel tuo ambiente, utilizza l'interfaccia utente di Zerto per arrestare le VM zVRA su ciascun host. Seleziona **Allow Zerto to always enter hosts into maintenance mode during remediation** all'interno delle impostazioni del sito Zerto, nella sezione delle politiche nell'interfaccia utente Zerto. In caso contrario, Zerto avvia zVRA e non permette di proseguire l'upgrade impedendo all'host ESXi di cui si sta eseguendo l'upgrade di andare in modalità di manutenzione.
* Per le VM che non hanno gli strumenti VMware installati, esegui l'arresto manualmente o forza lo spegnimento prima dell'installazione del modulo host NSX ESXi. Queste VM impediscono all'host ESXi di destinazione di andare in modalità di manutenzione.

#### Procedura per eseguire l'upgrade di VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

Fai riferimento a [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window} per dettagli relativi alla seguente procedura.

1. Leggi le note sulla release per NSX 6.4.4 per assicurarti della compatibilità con la tua configurazione dell'ambiente specifica. Per ulteriori informazioni, vedi [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}.
2. Esegui innanzitutto l'upgrade del gestore NSX. Se hai più ambienti NSX che utilizzano la modalità collegata tra vCenter, esegui l'upgrade di tutti i gestori NSX prima di eseguire l'upgrade dei componenti nell'interfaccia utente NSX **Upgrade Coordinator**.
3.	Utilizza **Upgrade Coordinator** nell'interfaccia utente NSX all'interno dell'interfaccia utente vCenter per eseguire l'upgrade dei componenti NSX.
4. Continua a esaminare e monitorare l'interfaccia utente di upgrade NSX all'interno dell'interfaccia utente vCenter man mano che vengono risolti possibili problemi per assicurarti che l'upgrade stia procedendo fino a quando tale processo non viene eseguito per tutti i componenti.

### Upgrade di PSC (Platform Services Controller)
{: #vc_vsphere_upgrade-procedure-psc}

Se hai istanze collegate vCenter Server, devi eseguire l'upgrade di tutte le istanze PSC nei siti primari e secondari vCenter Server. Poiché le istanze vCenter Server collegate creano un hub e hanno comunicato la topologia di replica PSC con l'istanza vCenter Server primaria come hub, ti consigliamo di iniziare eseguendo l'upgrade del PSC dell'istanza vCenter Server primaria e poi di eseguire l'upgrade di ogni PSC del sito secondario.

#### Prima di eseguire l'upgrade di PSC (Platform Services Controller)
{: #vc_vsphere_upgrade-procedure-psc-before}

* Per la seguente procedura, devi avere disponibili le tue password root vCenter e PSC. Utilizza la console {{site.data.keyword.vmwaresolutions_short}} per notare se è stato eseguito o meno l'upgrade della tua versione dell'istanza vCenter Server dalla V2.4 o precedenti alla V2.7 o successive.
* Nella console {{site.data.keyword.vmwaresolutions_short}}, viene visualizzata una singola password per root sia per PSC che per vCenter. Tuttavia, si tratta unicamente della password di vCenter. Devi contattare il supporto per la password root di PSC.
* Per evitare conflitti, utilizza l'IP nella parte superiore della stessa sottorete che viene al momento utilizzata da vCenter e PSC. Devi utilizzare un IP temporaneo per la distribuzione del nuovo dispositivo.

#### Procedura per eseguire l'upgrade di PSC (Platform Services Controller)
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Accedi alle interfacce utente di gestione del dispositivo di PSC, ``https://<psc-fqdn>:5480`` e di vCenter per confermare se la password root è scaduta o meno. Se la data di scadenza della password è **1970**, è scaduta e devi abilitare SSH e la shell bash nell'interfaccia utente di gestione del dispositivo PSC.
    1. Esegui SSH in PSC con l'ID e la password root. Anche se la password è scaduta, ti consente di eseguire l'accesso.
    2. Utilizza il comando shell **passwd** per impostare una nuova password root sia per PSC che per vCenter.
    3. Salva le password visualizzate nella console {{site.data.keyword.vmwaresolutions_short}} o che ti sono state fornite dal supporto IBM. Queste password vengono riutilizzate in un secondo momento quando esegui l'upgrade dei dispositivi.
2. Utilizza la funzione di montaggio ISO Windows integrata per montare l'ISO di vCenter 6.7u1b nel tuo jumpbox.
3. Segui le istruzioni VMware per eseguire innanzitutto l'upgrade di tutti i PSC. Per ulteriori informazioni, vedi [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html).

Il requisito **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade** specificato si applica a qualsiasi sottorete all'interno del tuo {{site.data.keyword.cloud_notm}} nel tuo account.
{:note}

Ti consigliamo di utilizzare vCenter come tua origine e destinazione per l'upgrade.

### Upgrade di vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

Per le istanze collegate vCenter Server, sebbene ti consigliamo di eseguire l'upgrade di tutte le istanze vCenter nei siti primari e secondari vCenter Server, non è obbligatorio.

#### Prima di eseguire l'upgrade di vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Per la seguente procedura, devi avere disponibili le tue password root vCenter e PSC. Utilizza la console {{site.data.keyword.vmwaresolutions_short}} per notare se è stato eseguito o meno l'upgrade della tua versione dell'istanza vCenter Server dalla V2.4 o precedenti alla V2.7 o successive.
* Per evitare conflitti, utilizza l'IP nella parte superiore della stessa sottorete che viene al momento utilizzata da vCenter e PSC. Devi utilizzare un IP temporaneo per la distribuzione del nuovo dispositivo.

#### Procedura per eseguire l'upgrade di vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Accedi alle interfacce utente di gestione del dispositivo di PSC, ``https://<psc-fqdn>:5480`` e di vCenter per confermare se la password root è scaduta o meno. Se la data di scadenza della password è **1970**, è scaduta e devi abilitare SSH e la shell bash nell'interfaccia utente di gestione del dispositivo PSC.
    1. Esegui SSH in PSC con l'ID e la password root. Anche se la password è scaduta, ti consente di eseguire l'accesso.
    2. Utilizza il comando shell **passwd** per impostare una nuova password root sia per PSC che per vCenter.
    3. Salva le password visualizzate nella console {{site.data.keyword.vmwaresolutions_short}} o che ti sono state fornite dal supporto IBM. Queste password vengono riutilizzate in un secondo momento quando esegui l'upgrade dei dispositivi.
2. Utilizza la funzione di montaggio ISO Windows integrata per montare l'ISO di vCenter 6.7u1b nel tuo jumpbox.
3. Segui le istruzioni VMware per eseguire l'upgrade di vCenter. Per ulteriori informazioni, vedi [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html). Le istruzioni VMware sono simili al processo di upgrade di PSC. Tuttavia, invece di puntare al PSC, punti all'FQDN/IP vCenter per il processo di upgrade.

**Note**:
* Il requisito **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade** specificato si applica a qualsiasi sottorete all'interno del tuo {{site.data.keyword.cloud_notm}} nel tuo account.
* Ti consigliamo di utilizzare vCenter come tua origine e destinazione per l'upgrade.

#### Consolidamento della funzione PSC in vCenter

1. Dopo aver completato correttamente l'upgrade di PSC e vCenter, accedi all'interfaccia utente basata su vCenter FLEX e controlla l'integrità di tutti i servizi correlati a vCenter e a PSC nella sezione **System Configuration**.  
2. Esegui il backup del tuo PSC.  Ti consigliamo di utilizzare il backup basato su file. Per ulteriori informazioni, vedi il documento relativo al [backup basato su file in vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:new_window}.
3. Passa alla directory ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge``.
4. Copia il file ``converge.json`` in un'unità locale nella tua VM jump.
  * Se questo è il primo PSC che stai consolidando, devi rimuovere la sezione **replication** dal file ``json``.
  * Se questo è un PSC collegato successivo, devi riempire gli attributi richiesti nella sezione **replication** del file ``json``.
5. Passa alla directory ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission``.
6. Copia il file ``decommission_psc.json`` in un'unità locale nella tua VM jump.
7. Modifica i file ``converge.json`` e ``decommission_psc.json``. Le istruzioni per i campi da modificare si trovano all'interno dei file ``json``. Ti consigliamo di utilizzare l'host ESXi che contiene il PSC invece di quello del vCenter nella sezione **managing_esxi_or_vc**.
8. Passa alla directory ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` in una finestra comandi.
9. Esegui ``vcsa-util.exe`` con lo switch **converge** e il percorso al file ``converge.json`` modificato in precedenza. Ad esempio, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Immetti **Y** per confermare che è stato eseguito il backup di PSC per procedere.
   2. Una volta completato il processo, immetti **Y** per confermare il riavvio di vCenter.

   Se il processo di convergenza non riesce con il messaggio ``ERROR converge Failed to get vecs users and permissions``, vedi [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:new_window} per la procedura per risolvere l'errore.
   {:note}

10. Una volta riavviato vCenter, verifica il normale funzionamento accedendo all'interfaccia utente vCenter.
11. Passa alla directory ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` in una finestra comandi.
12. Esegui ``vcsa-util.exe`` con lo switch **decommission** e il percorso al file ``decommission_psc.json`` modificato in precedenza. Ad esempio, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	Una volta completato correttamente il comando, accedi all'interfaccia utente vCenter flex e verifica che il dispositivo vCenter sia l'unico elencato negli ambienti non collegati e che tutti i servizi siano integri.
14. Elimina i vecchi PSC e vCenter e le VM PSC consolidate non utilizzate.
15. Ridenomina il vCenter Server all'interno dell'interfaccia utente vCenter in **<instancename>_vc_separate**. Ad esempio, se il tuo nome istanza vCenter Server è **production**, il nome dell'interfaccia utente vCenter è **production_vc_separate**. Ciò è necessario perché così l'automazione può riprendere la sua funzione per questa istanza vCenter Server.  

### Upgrade degli host ESXi
{: #vc_vsphere_upgrade-procedure-esxi}

La funzione VMware Update Manager all'interno di vCenter viene utilizzata per eseguire l'upgrade e l'applicazione della patch degli host ESXi al livello 6.7u1. Analogamente alla sezione di upgrade di NSX di questo documento, qualsiasi VM che può non essere vMotion per un altro host deve essere arrestata senza problemi, altrimenti può causare uno stallo del processo di upgrade.
{:note}

#### Caricamento dell'ISO ESXi in VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Assicurati di aver configurato VUM per scaricare le patch dall'indirizzo https://www.vmware.com. Per ulteriori informazioni, vedi [Introduzione a VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction).
2. Utilizza Flex o HTML per aprire l'interfaccia utente vCenter e passa a **VUM Admin View**.
3. Da **VUM Admin View**, seleziona la scheda **ESXi Images** e seleziona **Import ESXi Images**.
4. Cerca l'immagine **ESXi 6.7u1iso** che è stata scaricata da VMware e importala nel repository VUM.

#### Procedura per eseguire l'upgrade degli host ESXi
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. Dall'interfaccia utente vCenter, passa al cluster che contiene gli host ESXi di cui eseguire l'upgrade.
2. Fai clic sulla scheda **updates** nel riquadro di navigazione. Vai a host updates e fai clic su **Attach**.
3. Seleziona la linea di base (immagine ISO per l'upgrade ESXi) che hai caricato in VUM e fai clic su **Remediate**.
4. Accetta l'accordo di licenza con l'utente finale e fai clic su **OK**.
5. Esamina gli host da correggere e conferma i risultati del controllo che precede la correzione.

   Devi scollegare gli eventuali CD e DVD collegati alle VM altrimenti all'host che contiene tali VM non è consentito passare alla modalità di manutenzione.
   {:note}

6. Dopo la corretta esecuzione del controllo che precede la correzione, fai clic su **Remediate**. Monitora il processo di upgrade con l'attività di correzione dell'entità.
7. Una volta completato l'upgrade, esamina la sezione di riepilogo dell'host per confermare che sia visualizzato ``VMware ESXi, 6.7.0``.

Se il processo di upgrade ha subito esito negativo e visualizza il messaggio di errore **host cannot enter maintenance mode**, arresta gli ZVA Zerto e riprova. Le VM ZVRA si avviano automaticamente man mano che ogni server esce dal processo di correzione. Per informazioni su come continuare la replica Zerto durante il processo di upgrade, vedi [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:new_window}.
{:note}

#### Aggiunta della patch del driver Intel NVME al repository VUM
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

Come descritto nella sezione dei download dei file binari, devi importare il contenuto del file ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` nel repository. Viene poi applicato nella sezione successiva come un'estensione host ESXi non critica.

1. Estrai il file ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` in un'unità locale nella tua VM jump.
2. Utilizza Flex o HTML per aprire l'interfaccia utente vCenter e passa a **VUM Admin View**.
3. Da **VUM Admin View**, seleziona la scheda **Patch Repository** e seleziona **Import Patches**.
4. Cerca il contenuto estratto della directory ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` e seleziona il file ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip``. Il file viene importato immediatamente nel repository VUM.

Individua l'immagine nel repository di patch come un'estensione host **importante**.

#### Applicazione della patch agli host ESXi
{: #vc_vsphere_upgrade-procedure-esxi-patch}

Dopo l'upgrade, ti consigliamo di applicare tutte le patch host ESXi critiche e non critiche.

1. Dall'interfaccia utente vCenter, seleziona il cluster che contiene gli host a cui si devono applicare le patch.
2. Fai clic sulla scheda **updates** nel pannello di navigazione e seleziona la scheda **Host Updates**. Seleziona **Critical Host Patches (Predefined)**. Ripetere la procedura per eseguire l'upgrade degli host ESXi.
3. Fai clic sulla scheda **updates** nel pannello di navigazione e seleziona la scheda **Host Updates**. Seleziona **Non-Critical Host Patches (Predefined)**. Ripetere la procedura per eseguire l'upgrade degli host ESXi.

Potresti dover arrestare di nuovo le VM Zerto zVRA come parte di questo processo.
{:note}

### Upgrade di altri elementi
{: #vc_vsphere_upgrade-procedure-addtl}

#### Upgrade di vSAN nell'upgrade della versione del formato su disco
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Esegui l'upgrade della versione del formato del disco vSAN alla versione 7.

1. Passa al cluster che contiene il vSAN di cui eseguire l'upgrade nell'interfaccia utente vCenter.
2. Dall'oggetto cluster, seleziona **Configuration > vSAN > General**.
3. Fai clic su **Pre-check Upgrade** per controllare la compatibilità dell'upgrade e i possibili problemi. Aspetta che il controllo restituisca **Ready to upgrade..**.
4. Fai clic su **Upgrade**. Poiché l'upgrade elabora un gruppo di dischi alla volta, il completamento può richiedere un po' di tempo a seconda della dimensione del cluster. Facoltativamente, seleziona **reduced redundancy** durante il processo. Mentre questo può ridurre in modo significativo il tempo impiegato per l'upgrade, può generare una perdita di dati se si verifica un errore del disco durante il processo di upgrade.

#### Upgrade dello Switch distribuito virtuale
{: #vc_vsphere_upgrade-procedure-addtl-vds}

L'upgrade dello Switch distribuito virtuale (VDS) alla v6.6.0 esegue anche l'upgrade del controllo I/O di rete e aggiunge il supporto migliorato Link Aggregation Control Protocol (LACP).

1.	Se hai HCX distribuito, devi annullare la distribuzione della parte Gateway cloud di HCX prima di eseguire l'upgrade del VDS in cui risiede. Assicurati che HCX sia aggiornato alla versione più recente prima di ridistribuire il Gateway cloud.
2.	Dall'interfaccia utente vCenter, passa alla scheda **Network**.
3.	Fai clic con il tasto destro del mouse sullo switch distribuito di cui eseguire l'upgrade (**SDDC-Dswitch-Private** o **SDDC-Dswitch-Public**) e seleziona **Upgrade Distributed Switch**.

#### Upgrade delle estensioni e dei plug-in dell'interfaccia utente vCenter
{: #vc_vsphere_upgrade-procedure-addtl-extension}

È tua responsabilità eseguire l'upgrade delle estensioni o degli snap-in all'interno dell'ambiente vCenter Server. Dall'interfaccia utente vCenter, fai clic su **Home > Administration > Solutions** per visualizzare lo stato e abilitare o disabilitare le estensioni e i plug-in di vCenter.

#### Upgrade degli strumenti VMware
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Utilizza l'interfaccia utente vCenter per eseguire gli upgrade degli strumenti guest VMware. Alcuni strumenti VMware possono essere necessari su alcune delle VM più vecchie che sono state migrate nell'ambiente vCenter Server.  

#### Upgrade del livello hardware della VM (virtual machine)
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

Analogamente agli strumenti guest VMware, un upgrade dell'ambiente vCenter Server può far sì che le VM più vecchie si trovino in uno stato non supportato nel loro livello di hardware corrente. Utilizza l'interfaccia utente vCenter per trovare e aggiornare queste VM come necessario.  

#### Impostazione della modalità Enhanced vMotion Compatibility su Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

Puoi impostare gli host con la generazione Intel Skylake per un cluster in modalità EVC (Enhanced vMotion Compatibility) Skylake dopo l'upgrade. Attieniti alla seguente procedura per aggiornare la modalità EVC:

1. Dal cluster che contiene gli host, fai clic su **configure**.
2. Da **VMware EVC**, fai clic su **Edit** e modifica la modalità EVC in **Intel "Skylake" Generation**.

Per ulteriori informazioni, vedi [Enhanced vMotion Compatibility (EVC) processor support (1003212)](https://kb.vmware.com/s/article/1003212){:new_window}.

#### Riconfigurazione di NSX Manager e HCX Manager per puntare al PSC

1. Da un browser web, vai all'interfaccia utente del dispositivo NSX Manager all'indirizzo ``https://<nsx-manager-ip>`` o ``https://<nsx-manager-hostname>``. Accedi con le credenziali.
2. Dalla home page, fai clic su **Manage vCenter Registration**.
3. Modifica **Lookup Service URL** per puntare all'IP vCenter. Utilizza il PSC **PSC doesn’t exist anymore** integrato in modo autonomo.

## Risultati dopo l'upgrade del software vCenter Server vSphere
{: #vc_vsphere_upgrade-results}

L'esecuzione del controllo di integrità vSAN una volta che hai completato l'upgrade, potrebbe presentare avvertenze firmware per i controller di rete e RAID forniti da IBM Cloud. Una volta che hai stabilito gli host che necessitano di aggiornamenti firmware, apri un ticket con il supporto IBM per ottenere il firmware aggiornato alle versioni consigliate.

1. Dall'interfaccia utente vCenter, seleziona il cluster che contiene il vSAN con l'integrità da controllare.
2. Seleziona la scheda **Monitor** e quindi seleziona la scheda **vSAN**.
3. Seleziona **Health** e prendi nota delle avvertenze visualizzate.
4. Se viene visualizzata un'avvertenza **Hardware compatibility**, espandi l'avvertenza e fai clic sul messaggio **Controller Firmware is VMware certified** se è in uno stato di avvertenza.
5. Prendi nota degli host elencati con i suggerimenti di aggiornamento firmware.
6. Apri un ticket con il supporto IBM per pianificare quando escludere dal servizio ciascun host per consentire gli aggiornamenti firmware.

Una volta completato il tuo upgrade, aggiorna il tuo ticket di supporto con il supporto IBM. Fornisci le nuove password che hai creato come parte di questo processo di upgrade. Ad esempio, fornisci le password per distribuire i servizi di gestione del dispositivo -PSC e vCenter nel ticket di supporto. Il supporto IBM aggiorna quindi la console {{site.data.keyword.vmwaresolutions_short}} e il database interno per riprendere l'automazione {{site.data.keyword.vmwaresolutions_short}} a un livello 6.7. Ciò include l'aggiunta e la rimozione, i servizi, gli host, il cluster e le istanze vCenter Server secondarie.

## Link correlati
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}
* [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
