---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Progettazione KMIP for VMware

KMIP for VMware on {{site.data.keyword.cloud}} fornisce un servizio di gestione delle chiavi compatibile con le crittografie VMware vSAN e VMware vSphere, utilizzando [IBM Key Protect](/docs/services/key-protect/index.html) per fornire l'archiviazione della chiave di dati e della chiave root.

**Nota**: in questa release, KMIP for VMware on {{site.data.keyword.cloud_notm}} è limitato solo alla crittografia vSphere.

## Opzioni di crittografia dell'archiviazione

KMIP for VMware è compatibile con le crittografie VMware vSAN e vSphere. Entrambe queste soluzioni sono implementate nel livello hypervisor ma forniscono funzioni leggermente diverse. Valuta le loro funzioni in base ai tuoi requisiti.

### Crittografia VMware vSAN

La crittografia VMware vSAN è applicabile solo ai datastore vSAN. Con questa soluzione, VMware vCenter e i tuoi host VMware ESXi si connettono a un server di gestione delle chiavi come ad esempio KMIP for VMware per ottenere delle chiavi di crittografia. Queste chiavi vengono utilizzate per proteggere delle unità disco individuali utilizzate per il tuo datastore vSAN, inclusi i dischi di capacità e cache. La crittografia vSAN viene implementata in un modo che preserva i vantaggi della deduplicazione e della compressione vSAN.

Poiché la crittografia vSAN funziona al livello del datastore, il suo obiettivo principale è di evitare l'esposizione dei dati se si verifica una perdita delle unità disco fisiche. Inoltre, la crittografia vSAN è completamente compatibile con tutte le tecnologie di backup e replica della macchina virtuale, come ad esempio la replica vSphere, il vMotion tra vCenter, VMware HCX, Zerto, Veeam e IBM Spectrum Protect Plus.

La crittografia vSAN non crittografa le comunicazioni della replica vSAN da host a host all'interno del tuo cluster. La crittografia vSAN non è applicabile ad altre soluzioni di archiviazione come ad esempio l'archiviazione blocchi e file {{site.data.keyword.cloud_notm}} Endurance. La crittografia vSAN richiede la licenza vSAN Enterprise.
{:note}

### Crittografia vSphere

La crittografia VMware vSphere si applica a tutti i tipi di archiviazione VMware, incluse l'archiviazione vSAN e l'archiviazione blocchi e file {{site.data.keyword.cloud_notm}} Endurance.

Con questa soluzione, il vCenter Server e i tuoi host ESXi si connettono a un server di gestione delle chiavi come ad esempio KMIP for VMware per ottenere delle chiavi di crittografia. Queste chiavi vengono utilizzate per proteggere i dischi della macchina virtuale (VM) individuali, in base alle tue politiche di archiviazione della VM.

La crittografia vSphere funziona al livello del disco della macchina virtuale e può pertanto evitare l'esposizione dei dati se si verifica la perdita delle unità disco fisiche o dei dischi della VM. Molte tecnologie di backup e di replica non possono eseguire il backup o la replica in modo efficace perché i dati forniti sono crittografati.

Pertanto, la crittografia vSphere non è compatibile con la replica vSphere, il vMotion tra vCenter, VMware HCX, Zerto o IBM Spectrum Protect Plus. Tuttavia, quando è configurata correttamente, Veeam Backup and Replication è compatibile con la crittografia vSphere.

### Ulteriori considerazioni

Quando entrambi i tipi di crittografia sono abilitati nel tuo cluster vSphere, VMware crea un'ulteriore chiave per crittografare i tuoi core dump ESXi, poiché tali dump potrebbero contenere dati sensibili come ad esempio le credenziali di gestione delle chiavi, le chiavi di crittografia o i dati decrittografati. Dovresti prendere familiarità con [vSphere Virtual Machine Encryption and Core Dumps](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-63728E8B-810D-418B-B1AA-6A0A2F92AABE.html).

Quando KMIP for VMware viene utilizzato con la crittografia vSAN o vSphere, sono presenti diversi livelli di protezione della chiave.

Se intendi ruotare le chiavi, rivedi le seguenti informazioni sui livelli a cui possono essere ruotate le chiavi:
* La tua chiave root del cliente (CRK) protegge tutte le chiavi VMware. Le chiavi possono essere ruotate nell'istanza IBM Key Protect associata alla tua istanza KMIP for VMware.
* KMIP for VMware utilizza la tua CRK per proteggere le chiavi che genera e distribuisce a VMware. VMware le considera come una "chiave di crittografia delle chiavi" (KEK, key encryption key).
  * Se stai utilizzando la crittografia vSphere, puoi ruotare le chiavi utilizzando il comando **Set-VMEncryptionKey** PowerShell.
  * Se stai utilizzando la crittografia vSAN, puoi ruotare le chiavi sull'interfaccia utente vSAN.
* VMware utilizza queste KEK per proteggere le chiavi reali che utilizza per crittografare le unità disco e i dischi della VM. Puoi ruotare queste chiavi utilizzando una cosa nota a VMware come una reimpostazione delle chiavi "approfondita". Questa operazione riesegue la crittografia di tutti tuoi dati crittografati per cui può richiedere molto tempo.
  * Se stai utilizzando la crittografia vSphere, puoi eseguire una reimpostazione delle chiavi approfondita utilizzando il comando **Set-VMEncryptionKey** PowerShell.
  * Se stai utilizzando la crittografia vSAN, puoi eseguire una reimpostazione delle chiavi approfondita utilizzando l'interfaccia utente vSAN.

## KMIP for VMware

Le crittografie VMware vSAN e vSphere sono compatibili con molti server di gestione delle chiavi. KMIP for VMware fornisce un servizio di gestione delle chiavi gestito da IBM che utilizza IBM Key Protect per darti il controllo completo sulle tue chiavi. Anche altri servizi {{site.data.keyword.cloud_notm}} come Cloud Object Storage sono integrati con Key Protect, rendendolo il tuo punto di controllo centrale per la gestione delle chiavi in {{site.data.keyword.cloud_notm}}.

### Chiavi all'interno di chiavi

I sistemi di gestione delle chiavi normalmente utilizzano una tecnica nota come *crittografia envelope* per impacchettare o proteggere le chiavi con altre chiavi. Queste chiavi sono denominate *chiavi root* o *chiavi di crittografia delle chiavi* (KEK, key encryption key). Per accedere a una chiave, devi decrittografare o spacchettare la chiave utilizzando la chiave root corrispondente. L'eliminazione permanente della chiave root è un modo efficace per annullare la validità di tutte le chiavi che ha protetto. Queste chiavi non devono necessariamente essere archiviate accanto alla chiave root. Il controllo dell'accesso alla chiave root è importante.

{{site.data.keyword.cloud_notm}} Key Protect fornisce questo servizio utilizzando una *chiave root del cliente* (CRK). Key Protect archivia le CRK esclusivamente nell'hardware {{site.data.keyword.cloud_notm}} CloudHSM da cui non possono essere estratte. Queste CRK vengono poi utilizzate per impacchettare ulteriori chiavi di crittografia come ad esempio quelle generate da KMIP for VMware per la tua istanza VMware.

VMware implementa questo stesso concetto per le proprie chiavi. KMIP for VMware fornisce una chiave a VMware su richiesta e VMware a sua volta utilizza questa chiave come una KEK per impacchettare o crittografare le chiavi finali utilizzate per crittografare i tuoi dischi della macchina virtuale o le unità disco vSAN. Queste chiavi finali sono denominate chiavi di crittografia dei dati (DEK, data encryption key).

Terminiamo con la seguente catena di crittografia:
* Chiave root del cliente (CRK) archiviata permanentemente in IBM Key Protect.
* Chiave di crittografia della chiave (KEK, key encrypting key) generata da KMIP for VMware e fornita a VMware vCenter e ESXi nella tua istanza.
* Chiave di crittografia dei dati (DEK, data encrypting key) generata da VMware e archiviata insieme al disco vSAN o al disco della macchina virtuale.

KMIP for VMware archivia il formato impacchettato delle KEK in IBM Key Protect. Sebbene le KEK siano protette in modo crittografico dalla CRK e non è necessario che vengano archiviate all'interno di un HSM, se le archivi in IBM Key Protect, puoi visualizzarle ed eliminarle se devi revocare delle singole chiavi.

### Autenticazione ed autorizzazione

La tua soluzione di crittografia dell'archiviazione è formata da tre componenti: il tuo cluster VMware, la tua istanza KMIP for VMware e la tua istanza Key Protect.

VMware vCenter e ESXi eseguono l'autenticazione con la tua istanza KMIP for VMware utilizzando i certificati che installi o generi in VMware vCenter quando crei una connessione del server di gestione delle chiavi (KMS). Installa il certificato pubblico in KMIP for VMware per identificare il client o i client vCenter che possono connettersi. Ogni client viene autorizzato per tutte le chiavi archiviate in tale istanza KMIP for VMware.

La tua istanza KMIP for VMware viene autorizzata per la tua istanza Key Protect utilizzando un ID del servizio {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) a cui è stato concesso l'accesso alla tua istanza Key Protect. L'ID del servizio deve almeno l'accesso da visualizzatore per la piattaforma e di gestore per il servizio alla tua istanza Key Protect. KMIP for VMware utilizza la chiave root del cliente (CRK) di tua scelta nell'istanza Key Protect e archivia tutte le KEK generate per conto di VMware, nel formato impacchettato, nell'istanza Key Protect.

### Topologia

Figura 1. Componenti di KMIP for VMware on {{site.data.keyword.cloud_notm}}
![Componenti di KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip-key-protect.svg "La soluzione abilita la crittografia VMware vSphere e vSAN utilizzando le chiavi root archiviate in IBM Key Protect.")

KMIP for VMware è disponibile in diverse regioni multizona (MZR) IBM Cloud. Per un elenco completo, consulta [Ordine di KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html).

All'interno di ogni MZR, KMIP for VMware fornisce due endpoint del servizio sulla rete IBM Cloud Private per l'alta disponibilità. Configura entrambi questi endpoint nella tua configurazione del server di gestione delle chiavi (KMS) vCenter come un cluster KMS. Per un elenco degli endpoint in ogni MZR e delle firme del certificato del server KMIP, consulta la [Documentazione del servizio KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html).

KMIP for VMware si connette anche a IBM Cloud Key Protect utilizzando la rete IBM Cloud Private invece di internet pubblico.

Per accedere a KMIP for VMware sulla rete privata, il tuo account dell'infrastruttura IBM Cloud deve essere abilitato per VRF (Virtual Routing and Forwarding) e le rotte dell'endpoint del servizio IBM Cloud devono venire aggiunte alle rotte VRF del tuo account. Per ulteriori informazioni, vedi [abilitazione del tuo account per gli endpoint del servizio](/docs/services/service-endpoint/enable-servicepoint.html#cs_cli_install_steps).

### Link correlati

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/kmip/overview.html)
* [Implementazione e gestione](/docs/services/vmwaresolutions/archiref/kmip/implementation.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
