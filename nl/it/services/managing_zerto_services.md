---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Richiesta di servizi gestiti per Zerto on IBM Cloud
{: #managing_zerto_services}

Il servizio Zerto on {{site.data.keyword.cloud}} fornisce funzionalità di replica e di ripristino di emergenza. Queste funzionalità possono essere integrate nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}.

Se richiedi i servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}, può essere distribuito un ambiente di ripristino di emergenza (DR) completamente gestito utilizzando il software DR Zerto e IBM Resiliency Services.

Per Zerto on {{site.data.keyword.cloud_notm}} sono disponibili i seguenti modelli di servizi gestiti.

## Servizi gestiti orchestrati da IBM per Zerto
{: #managing_zerto_services-orchestrated}

Questo modello è adatto se stai utilizzando l'offerta Zerto on {{site.data.keyword.cloud_notm}}.

In questo modello, viene eseguito il provisioning del servizio {{site.data.keyword.cloud_notm}} Resiliency Orchestration per Zerto on {{site.data.keyword.cloud_notm}}. Questo modello può proteggere continuamente le macchine virtuali, i sistemi operativi e i dati su {{site.data.keyword.cloud_notm}}, con test DR ininterrotto, visibilità RTO/RPO (obiettivo del tempo di ripristino/obiettivo del punto di ripristino) e funzionalità di failover e failback.

Tutte le funzioni sono gestite tramite il dashboard {{site.data.keyword.cloud_notm}} Resiliency Orchestration dall'IBM Resiliency Services Global Command Center.

Per ulteriori informazioni, vedi [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration).

## Servizi gestiti IBM per Zerto (senza orchestrazione)
{: #managing_zerto_services-without-orchestrated}

In questo modello, viene eseguito il provisioning di una soluzione DR completamente gestita per Zerto on {{site.data.keyword.cloud_notm}}. Questo modello è adatto se vuoi solo un servizio gestito per Zerto Virtual Replication, senza il servizio {{site.data.keyword.cloud_notm}} Resiliency Orchestration su {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, vedi [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top).

## Procedura per richiedere i servizi gestiti per Zerto on IBM Cloud
{: #managing_zerto_services-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Introduzione** nel riquadro di navigazione a sinistra.
2. Scorri la pagina verso il basso e sotto **Ordina servizi gestiti aggiuntivi** fai clic sulla scheda **Servizi gestiti per Zerto on IBM Cloud**.
3. Nella pagina **Zerto on IBM Cloud**, controlla la descrizione e le specifiche tecniche per Zerto on {{site.data.keyword.cloud_notm}} come servizio gestito e fai clic su **Crea**.
4. Specifica le impostazioni di configurazione in base ai tuoi requisiti o accetta i valori predefiniti.
5. Fai clic su **vCenter Server** o **Cloud Foundation** per aggiungere il servizio a una delle tue istanze.
6. Per aggiungere il servizio mentre ordini una nuova istanza, fai clic su **Aggiungi alla nuova istanza** e procedi quindi con l'ordine di una nuova istanza [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance), [vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance) o [Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance).
7. Per aggiungere il servizio a un'istanza esistente, fai clic su **Aggiungi all'istanza esistente**, seleziona l'istanza desiderata dall'elenco, quindi conferma di voler procedere con l'ordine facendo clic su **Fornitura**.

## Link correlati
{: #managing_zerto_services-related}

* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
