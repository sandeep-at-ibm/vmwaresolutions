---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Richiesta di IBM Cloud Private Hosted - Obsoleto
{: #managing_icp}

Le informazioni contenute in questo argomento sono obsolete. Per le informazioni più aggiornate su IBM Cloud Private Hosted, vedi [Panoramica su IBM Cloud Private Hosted](icp_overview.html).
{:deprecated}

{{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} distribuisce automaticamente {{site.data.keyword.cloud_notm}} Private Hosted sulle tue istanze di VMware vCenter Server.

{{site.data.keyword.cloud_notm}} Private Hosted porta la potenza dei microservizi e dei contenitori al tuo ambiente VMware su {{site.data.keyword.cloud_notm}}. Con questo servizio, puoi estendere lo stesso modello operativo e gli stessi strumenti VMware e {{site.data.keyword.cloud_notm}} Privato con cui hai dimestichezza da una situazione in loco a {{site.data.keyword.cloud_notm}}.

## Specifiche tecniche per IBM Cloud Private Hosted
{: #managing_icp-specs}

Di seguito sono riportati i requisiti minimi per richiedere il servizio {{site.data.keyword.cloud_notm}} Private Hosted:

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
  **Nota:** VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle non è supportato.
* VMware NSX Advanced o Enterprise edition
* Tre {{site.data.keyword.baremetal_long}}
* Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz
* 384 GB di RAM per server
* Una condivisione file dell'archiviazione NFS condivisa con 8.000 GB a 4 IOPS/GB
* 33 licenze Virtual processor core di IBM Cloud privato
* Per il backup dei dati, si consiglia il servizio Veeam on IBM Cloud.

## Procedura per richiedere IBM Cloud Private Hosted
{: #managing_icp-procedure}

1. Ordina una nuova istanza di vCenter Server attenendoti alla procedura in [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html). Puoi anche richiedere IBM Cloud Private Hosted per un'istanza esistente.
  **Importante:** assicurati che il tuo ambiente soddisfi i requisiti minimi elencati precedentemente.
2. Assicurati di avere le tue autorizzazioni IBM Cloud privato.
3. Dopo che hai ricevuto la conferma che l'istanza di vCenter Server è pronta per l'utilizzo, attieniti alla seguente procedura per richiedere IBM Cloud Private Hosted.
4. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Introduzione** nel riquadro di navigazione a sinistra.
5. Scorri verso il basso la pagina e, in **Ordina servizi aggiuntivi** fai clic sulla scheda **IBM Cloud Private Hosted**.
6. Nella pagina **IBM Cloud Private Hosted on vCenter Server on IBM Cloud**, nella casella **Rivolgersi al team IBM Cloud Private Hosted DevOps**, immetti una descrizione dei tuoi requisiti e fai clic su **Richiesta di una consultazione**.

Un rappresentante di {{site.data.keyword.cloud_notm}} Private Hosted DevOps ti contatterà utilizzando le tue informazioni di contatto {{site.data.keyword.cloud_notm}} per aiutarti a iniziare.
