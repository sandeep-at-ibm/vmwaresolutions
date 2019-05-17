---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-23"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Trasformazione di Stock Trader da WebSphere Application Server in Stock Trader nei contenitori
{: #vcscontent-stocktrmod}

Il passo successivo nel percorso di modernizzazione di Stock Trader consiste nel trasformare il carico di lavoro dall'esecuzione nelle VM (Virtual Machine) all'esecuzione nei contenitori.

Per continuare, Todd e Jane eseguono Transformation Advisor per analizzare il carico di lavoro di Stock Trader, identificare qualsiasi complessità di migrazione e consigliare delle modifiche. Quando sono pronti, utilizzano Transformation Advisor per distribuire Stock Trader nei contenitori Liberty eseguiti in {{site.data.keyword.icpfull_notm}}.

## Prepara IBM Cloud Private
{: #vcscontent-stocktrmod-prep-icp}

Todd deve innanzitutto installare {{site.data.keyword.icpfull_notm}}. Dal momento che Todd ha il suo proprio ambiente VMware on {{site.data.keyword.cloud_notm}}, decide di utilizzare l'offerta {{site.data.keyword.cloud_notm}} Private Hosted che gli fornisce un'istanza {{site.data.keyword.icpfull_notm}} completa che viene eseguita sulle VM VMware in {{site.data.keyword.cloud_notm}}.

Il dashboard predefinito fornisce un'interfaccia utente completa per gestire il cluster, la sicurezza, l'archiviazione e la distribuzione di Kubernetes dal catalogo.

### Prepara l'archiviazione
{: #vcscontent-stocktrmod-prep-storage}

{{site.data.keyword.cloud_notm}} Private Hosted è configurato per impostazione predefinita con GlusterFS e fornisce l'archiviazione file sulle VM come nodi GlusterFS dedicati. Il valore di GlusterFS è che abilita il provisioning dinamico. Se Todd lo desidera, può configurare VM aggiuntive come server NFS.

Poiché Todd voleva un server NFS a sua disposizione, ha identificato una VM chiamata ‘toddnfs’ e ha eseguito questi
[passi](https://help.ubuntu.com/community/SettingUpNFSHowTo).

Todd esegue i seguenti comandi per creare un nuovo server NFS:

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

Successivamente, Todd aggiunge la seguente riga:

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

Todd esegue quindi il seguente comando su ogni VM per installare NFS su ogni VM di lavoro {{site.data.keyword.icpfull_notm}}:

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd esegue il seguente comando per confermare la versione installata:

`apt-cache policy nfs-common`

Ogni volta che è necessario un nuovo volume NFS, Todd esegue il seguente comando per crearne uno nuovo secondo necessità:

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### Prepara la sicurezza delle immagini
{: #vcscontent-stocktrmod-prep-img-sec}

In {{site.data.keyword.icpfull_notm}} V3.1, la sicurezza viene migliorata richiedendo di applicare una politica di immagine prima che una qualsiasi immagine venga trasferita in un'istanza {{site.data.keyword.icpfull_notm}}. Il miglioramento richiede l'aggiunta di una politica di immagine per il luogo in cui risiedono le immagini IBM, *dockerhub/ibmcom* e nell'archivio docker.

La politica ibmcloud-default-cluster-image-policy viene fornita per impostazione predefinita e copre tutte le immagini IBM in docker.io/ibmcom/\*, ma poiché Db2 e altri contenuti IBM si trovano nell'archivio Docker, è necessaria un'altra politica per l'archivio docker, *docker.io/store/ibmcorp/*.

Inoltre, alcuni contenuti richiedono una serie di politiche di sicurezza pod per consentire l'accesso specifico per il pod. Ad esempio, Db2 richiede una politica per i client che vogliono eseguire Db2 in uno spazio dei nomi diverso da quello di 'default’.

Scopri di più in [IBM Knowledge
Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html).

## Distribuisci Transformation Advisor e Microclimate
{: #vcscontent-stocktrmod-deploy-tam}

Una volta che Todd ha eseguito {{site.data.keyword.icpfull_notm}}, installa Transformation Advisor insieme a Microclimate. Todd apre il [catalogo](https://www.ibm.com/cloud/private/architecture) e visualizza tutti i contenuti disponibili.

Todd cerca Transformation Advisor e Microclimate e li installa utilizzando le istruzioni del file readme fornite quando fa clic sul grafico Helm.

### Esegui Transformation Advisor
{: #vcscontent-stocktrmod-run-trans-advisor}

Per eseguire Transformation Advisor, Jane ha aggiunto il raccoglitore di dati nella VM in cui è in esecuzione Stock Trader in WebSphere e apre l'interfaccia utente di [Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) per visualizzare i risultati.

Jane ha fatto clic su Stock Trader e visualizza il consiglio di eseguire ogni file war in Liberty e che la maggior parte della migrazione sarebbe semplice con una migrazione moderata. Jane fa clic su Migration Details e vede che Transformation Advisor fornisce i file di distribuzione che può utilizzare per completare la migrazione. Dopo che Jane carica i file binari in Transformation Advisor, utilizza le API fornite da Microclimate per distribuire i contenitori Liberty.

Alla fine, le opzioni di layout di Stock Trader risultanti sono:
* Singolo contenitore Liberty - se Jane distribuisce un runtime Liberty e ha aggiunto la sua applicazione Stock Trader in quel singolo contenitore.
* Più contenitori Liberty - uno per ogni file .war come consigliato da Transformation Advisor per Stock Trader.

Todd non ha modificato l'origine dati durante la fase di trasformazione. Transformation Advisor prende la configurazione dell'origine dati di WebSphere Application Server Network Deployment e la aggiunge al file server.xml del contenitore Liberty.
{:important}

## Link correlati
{: #vcscontent-stocktrmod-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
