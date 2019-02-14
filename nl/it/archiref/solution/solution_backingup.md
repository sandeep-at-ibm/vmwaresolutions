---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Backup dei componenti

Sei responsabile della configurazione, della gestione e del monitoraggio di tutti i componenti software, incluso del backup e della disponibilità dei carichi di lavoro e dell'infrastruttura di gestione.

Come parte della soluzione, puoi distribuire facoltativamente i servizi aggiuntivi IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}. Veeam e IBM Spectrum Protect Plus possono aiutare a soddisfare i requisiti per il backup dei tuoi componenti di gestione.

Questi servizi aggiuntivi vengono distribuiti insieme all'archiviazione Endurance {{site.data.keyword.cloud_notm}}. I servizi ti aiutano a eseguire il backup dei tuoi carichi di lavoro e dei componenti di gestione. In [Panoramica dell'architettura di IBM Spectrum Protect Plus](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} e [Panoramica dell'architettura di Veeam](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window} vengono fornite indicazioni utili sulla pianificazione e sul dimensionamento della tua distribuzione. Puoi anche richiedere i [servizi gestiti](/docs/services/vmwaresolutions/services/managing_veeam_services.html) per la tua distribuzione Veeam.

I diversi componenti della soluzione richiedono differenti strategie per il backup. Alcuni componenti sono protetti utilizzando il backup a livello di immagine mentre altri componenti sono protetti utilizzando il backup basato su file per la loro configurazione e i dati.

## File server per il backup basato su file

Alcuni componenti, come VMware vCenter Server, PSC (Platform Services Controller) e VMware NSX, richiedono il backup della loro configurazione su un file server.

Per ospitare questi backup, distribuisci un file server Linux nel tuo cluster utilizzando la seguente procedura:

1. Ordina una sottorete portatile privata dall'infrastruttura {{site.data.keyword.cloud_notm}} e posizionala sulla stessa VLAN dei tuoi componenti di sistema. Questa è la VLAN privata su cui risiedono gli indirizzi IP di gestione per i tuoi host.
2. Carica un'immagine del sistema operativo nel tuo archivio dati di gestione VMware, ad esempio Ubuntu Server 18.04 LTS, dal mirror privato di {{site.data.keyword.cloud_notm}}.
3. Distribuisci questa macchina virtuale (VM) nel tuo cluster sul gruppo di porte di gestione utilizzando un indirizzo IP portatile privato ordinato in precedenza. Assicurati che la VM sia configurata per puntare ai tuoi server AD/DNS e, facoltativamente, aggiungi la VM al DNS del tuo dominio secondario.
4. Crea un ID utente di backup non root su questo server e assicurati che tutti i servizi necessari siano configurati e avviati per i trasferimenti di file. Ad esempio, FTP o SSH.
5. Assicurati che questa VM sia inclusa nel tuo lavoro di backup di gestione Veeam o IBM Spectrum Protect Plus.

## Backup basato su file di vCenter

VMware vCenter Server e PSC forniscono un'[interfaccia utente di gestione dispositivi e un'API per esportare il database e la configurazione in un file server](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window} utilizzando vari protocolli. VMware documenta un esempio di come puoi configurare tutto questo in modo che venga [eseguito periodicamente come lavoro cron](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window} direttamente su vCenter Server Appliance e PSC, che puoi adattare per il tuo utilizzo.

Se hai un PSC esterno, devi eseguire il backup sia di vCenter Server Appliance che di PSC separatamente utilizzando questa tecnica. Se hai un PSC integrato, il backup di PSC è incluso nel tuo backup di vCenter. Scopri e pianifica le considerazioni e le limitazioni documentate da VMware. Inoltre, pianifica una rotazione e una scadenza regolari dei backup dei file sul tuo file server.

VMware richiede che l'ubicazione di backup sia una cartella vuota, quindi pianifica la rotazione o l'automazione del backup in modo da lasciare l'ubicazione vuota per ogni successivo lavoro di backup.
{:note}

## Backup basato su file di NSX

Un corretto backup di tutti i componenti NSX è fondamentale per ripristinare il sistema al suo stato operativo in caso di malfunzionamento. La progettazione richiede di configurare il backup NSX tramite la funzione di backup del gestore NSX. A tale scopo, puoi [configurare il gestore NSX per eseguire regolarmente i backup](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window} sul tuo file server. Assicurati che il backup del file server o dei suoi dati sia stato eseguito correttamente e garantisci la rotazione dei vecchi backup NSX.

## Backup basato su immagine delle macchine virtuali di gestione

Dopo aver distribuito la tua istanza e il servizio IBM Spectrum Protect Plus o il servizio di backup Veeam, configura un lavoro di backup per le tue macchine virtuali di gestione. Pianifica il backup delle seguenti VM con almeno 7 giorni di backup giornalieri:

* Se presente, VMware SDDC Manager
* Se presenti, i server Active Directory
* Server di backup dei file

Pianifica l'assegnazione di un numero sufficiente di licenze Veeam o IBM Spectrum Protect Plus per eseguire il backup di queste macchine virtuali e predisponi almeno 2 TB di archiviazione di backup per le VM.

## Servizi aggiuntivi

Se distribuisci componenti aggiuntivi della soluzione nella tua istanza, devi anche pianificare il backup di questi componenti come parte della tua strategia di backup di gestione:

* Zerto Virtual Replication: il sistema Zerto Virtual Manager (ZVM) viene distribuito come VSI (Virtual Server Instance) di {{site.data.keyword.cloud_notm}} e il suo backup non è supportato da Veeam o IBM Spectrum Protect Plus. Se la tua strategia di ripristino di emergenza richiede il ripristino del sistema ZVM senza eseguire un failover del sito, devi utilizzare la tua soluzione di backup Windows preferita per eseguire il backup e il ripristino di ZVM.
* F5 BIG-IP: F5 raccomanda il [backup basato su file della configurazione F5](https://support.f5.com/csp/article/K13132){:new_window}, che puoi indirizzare al tuo file server.
* FortiGate Security Appliance o VM: Fortinet raccomanda il [backup basato su file della configurazione FortiGate](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}, che puoi indirizzare al tuo file server.
* HyTrust Cloud Control e Data Control: HyTrust supporta sia il backup basato su immagine sia quello basato su file dei dispositivi server HyTrust. Per ulteriori informazioni, consulta le guide di amministrazione HyTrust.
* VMware HCX: l'interfaccia di gestione del dispositivo HCX ti consente di creare e scaricare un backup basato su file della configurazione del gestore HCX simile a vCenter Server Appliance.

## Ulteriori considerazioni

Se scegli di distribuire il tuo server AD/DNS come VSI (Virtual Server Instance) di {{site.data.keyword.cloud_notm}}, non puoi eseguirne il backup mediante Veeam o IBM Spectrum Protect Plus. In questo caso, utilizza la tua soluzione di backup Windows preferita per le operazioni di backup e ripristino o pianifica la distribuzione della tua istanza utilizzando le VM AD/DNS all'interno del tuo cluster VMware, che può essere sottoposto a backup da Veeam o IBM Spectrum Protect Plus.

A partire da VMware vCenter 6.5u2, VMware supporta il backup del database vCenter Postgres utilizzando backup basati su immagine, con script di sospensione e ripristino integrati per il database durante la finestra di backup per garantire l'integrità del database. Se aggiorni la tua istanza VMware a vCenter 6.5u2, puoi scegliere di utilizzare Veeam o IBM Spectrum Protect Plus per il backup dei tuoi vCenter Server e PSC invece di utilizzare i backup basati su file. In tal caso, per garantire l'integrità del database devi utilizzare la funzione di sospensione di Veeam o IBM Spectrum Protect Plus.

## Ripristino dal backup

Quando ripristini i backup di gestione, ci sono diverse considerazioni speciali:

* Per vCenter e PSC, VMware fornisce un programma di installazione che può distribuire un nuovo dispositivo virtuale e ripristinare la configurazione dal backup.
* Quando ripristini un dispositivo dal backup, il programma di installazione rileva il tipo di dispositivo (vCenter Server. PSC o vCenter con PSC integrato) in base alle informazioni di backup da te fornite.
* Poiché distribuisci direttamente su uno dei tuoi host, potresti non essere in grado di eseguire la distribuzione su uno switch distribuito o un gruppo di porte. Potresti dover creare uno switch e un gruppo di porte standard temporaneo per la distribuzione dei dispositivi ripristinati e migrare temporaneamente una delle tue vmnic a questo switch per fornire la connettività di rete per le tue VM. Dopo la distribuzione, puoi migrare le VM al gruppo di porte distribuito e restituire la vmnic al dvSwitch.
* Per NSX, potresti dover ridistribuire NSX Manager e i controller prima di ripristinare la configurazione dal backup.
* Assicurati di acquisire familiarità con le considerazioni e le limitazioni di VMware per il backup e il ripristino di vCenter.

## Riepilogo

Con una pianificazione adeguata, puoi garantire che la tua istanza VMware possa sostenere correttamente la perdita e il ripristino dei suoi componenti di gestione. Assicurati di monitorare regolarmente l'esito positivo dei lavori di backup e la disponibilità dei tuoi dati di backup e di verificare regolarmente la tua pianificazione di backup e ripristino, sia per la tua infrastruttura di gestione che per i tuoi carichi di lavoro.

### Link correlati

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
* [Panoramica della progettazione](/docs/services/vmwaresolutions/archiref/solution/design_overview.html)
* [Ridimensionamento della capacità](/docs/services/vmwaresolutions/archiref/solution/solution_scaling.html)
