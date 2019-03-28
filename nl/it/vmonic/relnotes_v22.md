---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Note sulla release per la V2.2
{: #relnotes_v22}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown
{: #relnotes_v22-spectre}

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Aggiornamento della VM (Virtual Machine) IBM CloudDriver
{: #relnotes_v22-cloud-driver}

Durante il processo di aggiornamento alla V2.2, la VM (Virtual Machine) IBM CloudDriver viene ridistribuita con la release di CentOS Linux 7.4.1708. Inoltre, tutte le nuove istanze fornite includono la release di CentOS Linux 7.4.1708 su IBM CloudDriver.

**Importante:**

* Se utilizzi una soluzione di backup che fa riferimento alla VM (Virtual Machine) IBM CloudDriver, dopo l'aggiornamento alla V2.2, assicurati che la soluzione di backup faccia riferimento alla nuova VM (Virtual Machine) IBM CloudDriver.
* Prima di eseguire l'aggiornamento alla V2.2, assicurati di sostituire la VSI Veeam legacy con il servizio Veeam on {{site.data.keyword.cloud_notm}}. Veeam legacy non è più supportato nella V2.2 e release future, pertanto i backup dei componenti di gestione associati a Veeam legacy non sono disponibili per un ripristino.

Per ulteriori informazioni sull'utilizzo del servizio Veeam on {{site.data.keyword.cloud_notm}}, vedi i seguenti argomenti:
* [Componenti e considerazioni per Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Impostazioni di configurazione avanzate sui server ESXi
{: #relnotes_v22-config-esxi}

Per le release della V2.2 o successive, le nuove istanze vengono ordinate con una nuova serie di impostazioni di configurazione avanzate per i server ESXi.
Per le istanze che vengono aggiornate da una release precedente alla V2.2 o release successive, alcune impostazioni richiedono il riavvio dei server ESXi. Pertanto, solo un sottoinsieme delle impostazioni di configurazione viene applicato automaticamente.

Si consiglia di modificare le restanti impostazioni di configurazione nei nuovi valori per garantire coerenza tra tutte le istanze e per consentire il supporto adeguato per l'espansione dell'archiviazione. IBM prevede di eseguire test solo con queste nuove impostazioni per tutte le release future di {{site.data.keyword.cloud_notm}} for VMware Solutions.

Per ulteriori informazioni, vedi _Impostazioni di configurazione avanzate per i server ESXi_ in [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers).

## Supporto per un massimo di 51 server ESXi per un cluster iniziale e un massimo di 59 server ESXi per i cluster aggiuntivi
{: #relnotes_v22-esxi-cluster}

Per le release della V2.2 e successive, puoi ora aumentare il numero di server ESXi a un massimo di 51 per un cluster iniziale e a un massimo di 59 per i cluster aggiuntivi.

Per le istanze distribuite nelle release della V2.1 o precedenti, devi abilitare il supporto vSAN necessario per aumentare la dimensione del cluster a più di 32. Per ulteriori informazioni sulle procedure per aumentare il numero di server ESXi, vedi _Quanti server ESXi posso aggiungere a un cluster?_ in [Domande frequenti sui server ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-).
{:important}

## Altre opzioni di configurazione di rete per le istanze vCenter Server e Cloud Foundation
{: #relnotes_v22-network-config}

Per gli ordini delle istanze vCenter Server e Cloud Foundation, puoi ora riutilizzare le VLAN pubbliche e private esistenti per la tua configurazione di rete. Se non sono disponibili VLAN esistenti, puoi ordinare una nuova VLAN pubblica e due nuove VLAN private.

Per importanti considerazioni prima di selezionare le VLAN esistenti, vedi le sezioni *Impostazioni dell'interfaccia di rete* in [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v22-vcs}

### Aggiornamenti delle impostazioni di configurazione del componente NSX e del gruppo di porte
{: #relnotes_v22-nsx}

La release corrente applica l'aggiornamento del componente VMware NSX per vSphere 6.3.5. Per ulteriori informazioni sui componenti, vedi [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Per le istanze VMware vCenter Server distribuite nelle release della V2.2 o successive, le impostazioni di configurazione di NSX e del gruppo di porte sono state modificate. Per ulteriori informazioni, vedi la sezione *Impostazioni di configurazione di NSX e del gruppo di porte* in  [Distinta base del software vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings).

### Nuova opzione per la configurazione DNS
{: #relnotes_v22-dns}

Puoi ora selezionare la distribuzione di una singola VSI (Virtual Server Instance) di Microsoft Windows Server per Microsoft Active Directory (AD) o due VM (Virtual Machine) Microsoft Windows ad alta disponibilità nel cluster di gestione. Per le release precedenti alla V2.2, la singola VSI di Microsoft Windows per Microsoft AD veniva distribuita automaticamente per impostazione predefinita. La nuova opzione per selezionare due VM (Virtual Machine) Microsoft Windows offre maggiore privacy e la possibilità di eseguire il backup e il ripristino delle VM (Virtual Machine) che utilizzano il servizio Veeam.

Se configuri la tua istanza per utilizzare le due VM (Virtual Machine) di Microsoft Windows, devi fornire 2 licenze Microsoft Windows Server 2012 R2. Utilizza la licenza di Microsoft Windows Server 2012 R2 Standard Edition e/o la licenza di Microsoft Windows Server 2012 R2 Datacenter Edition. Hai 30 giorni per attivare le VM (Virtual Machine).
{:note}

Per ulteriori informazioni, vedi la sezione *Impostazioni di sistema* in [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings).

### Aumento del numero di cluster per istanza
{: #relnotes_v22-clusters-per-inst}

Puoi ora aggiungere fino a 10 cluster alle istanze VMware vCenter Server distribuite o aggiornate alle release della V2.2 e successive. Per ulteriori informazioni, vedi [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances).

## Aggiornamenti per i cluster VMware vSphere
{: #relnotes_v22-vss}

### Bundle di licenze dei componenti disponibili per i clienti Business Partner
{: #relnotes_v22-license-bundles}

Gli utenti Business Partner possono ora scegliere tra quattro bundle di licenze per i componenti quando ordinano un nuovo cluster vSphere. Scegli tra Standard con gestione, Avanzata, Avanzata con rete o Avanzata con rete e gestione. Puoi anche includere ulteriori componenti VMware al tuo ordine. Tuttavia, l'opzione BYOL (Bring Your Own License) non è disponibile.

Per ulteriori informazioni, vedi la sezione *Impostazioni di licenza* in [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Aggiornamenti per le istanze NetApp ONTAP Select
{: #relnotes_v22-netapp}

La release corrente applica l'aggiornamento di NetApp ONTAP Select 9.3.

### Aumento del numero di unità SATA per i server bare metal IBM Cloud ad alta disponibilità
{: #relnotes_v22-sata-drives}

Sono ora disponibili trentaquattro unità SATA per i {{site.data.keyword.baremetal_short}} ad alta disponibilità di NetApp ONTAP Select. Per ulteriori informazioni, vedi [Specifiche tecniche per le istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs).

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v22-services}

### Opzione per l'aumento della larghezza di banda per F5 on IBM Cloud
{: #relnotes_v22-bandwidth}

Puoi ora selezionare una larghezza di banda massima di 10 Gbps quando installi il servizio F5 on {{site.data.keyword.cloud_notm}} per le istanze Cloud Foundation e vCenter Server. Per ulteriori informazioni, vedi [Considerazioni su F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations).

### KMIP for VMware on IBM Cloud
{: #relnotes_v22-kmip}

Puoi ora ordinare un'istanza Cloud Foundation o vCenter Server con il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} incluso o aggiungere il servizio a un'istanza Cloud Foundation o vCenter Server esistente dopo la distribuzione iniziale.

Questo servizio fornisce un servizio altamente disponibile 24x7 per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Questo servizio offre funzionalità di runtime per consentire ai clienti di creare, recuperare, attivare, revocare ed eliminare le chiavi di crittografia. Inoltre, questo servizio fornisce funzionalità di gestione per mantenere le associazioni tra le credenziali del client e tali chiavi di crittografia.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v22-spp}

Il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze che sono distribuite o aggiornate alle release della V2.2 o successive.

Questo servizio fornisce una soluzione efficiente e scalabile per la protezione dei dati, il riutilizzo dei dati e il recupero dei dati per gli ambienti virtuali. Puoi implementarlo come soluzione autonoma o integrarlo con il tuo ambiente IBM Spectrum Protect&trade; Plus per scaricare copie per la governance di dati e archiviazione a lungo termine.

Il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fornisce la protezione dei dati solo per le VM del carico di lavoro.

Per ulteriori informazioni, vedi [Gestione di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp).

### Servizi gestiti
{: #relnotes_v22-managed-services}

I servizi gestiti per Veeam on {{site.data.keyword.cloud_notm}} e per Zerto on {{site.data.keyword.cloud_notm}} sono ora disponibili per le istanze VMware vCenter Server e VMware Cloud Foundation. Richiedi questi servizi gestiti se non vuoi gestire la complessità della tua propria soluzione e del tuo ambiente.

Il servizio Veeam on {{site.data.keyword.cloud_notm}} si integra perfettamente con i tuoi hypervisor VMware per aiutare la tua azienda a raggiungere l'alta disponibilità (HA). È possibile distribuire un ambiente di backup completamente gestito utilizzando sia il software di backup Veeam sia IBM Resiliency Backup as a Service.

Il servizio Zerto on {{site.data.keyword.cloud_notm}} fornisce funzionalità di replica e ripristino di emergenza, che è possibile integrare nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}. È possibile distribuire un ambiente di ripristino di emergenza (DR) completamente gestito utilizzando il software DR Zerto e IBM Resiliency Services.

Puoi richiedere i servizi gestiti per le tue istanze attraverso la pagina **Introduzione**, effettuando un nuovo ordine di istanza o aggiungendo il servizio a un'istanza esistente.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Richiesta di servizi per Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Richiesta di servizi per Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

## Documentazione nuova e aggiornata
{: #relnotes_v22-new-docs}

* Nella documentazione è ora disponibile una tabella di confronto con le funzioni supportate per le istanze Cloud Foundation e vCenter Server, così come per i cluster VMware vSphere. Puoi vedere, a colpo d'occhio, le differenze tra le funzioni fornite da ciascun tipo di istanza. Per ulteriori informazioni, vedi [Tabella di confronto delle offerte](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

* Nella documentazione viene ora fornita la Distinta base di VLAN e software per i cluster Cloud Foundation, vCenter Server e VMware vSphere.

  Per ulteriori informazioni, consulta i seguenti argomenti:

  * [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [Distinta base di VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v22-ui}

Sono stati apportati miglioramenti in tutta l'interfaccia utente:

* Quando ordini un'istanza, tutte le opzioni hardware vengono ora filtrate in base all'ubicazione e le opzioni non disponibili vengono visualizzate nello stato disabilitato.
* Quando ordini un cluster, la configurazione di **{{site.data.keyword.baremetal_short}}** viene ora popolata automaticamente in base alle configurazioni esistenti. Puoi aggiornare la configurazione in base ai tuoi requisiti.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.
