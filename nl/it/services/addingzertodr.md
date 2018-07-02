---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di Zerto on IBM Cloud

Il servizio Zerto on {{site.data.keyword.cloud}} fornisce funzionalità di replica e ripristino di emergenza, che è possibile integrare nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}.

## Componenti del servizio Zerto on IBM Cloud

Nel servizio Zerto on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

* Una sottorete portatile privata dall'infrastruttura {{site.data.keyword.cloud_notm}} che verrà utilizzata dai dispositivi Zerto Virtual Replication Appliance
* Un'istanza di servizio virtuale (o VSI, Virtual Service Instance) di Microsoft Windows su cui è installato Zerto Virtual Replication
* Dispositivi Zerto Virtual Replication Appliance da distribuire e configurare in tutti i server ESXi

**Nota**: i componenti Zerto Virtual Manager (ZVM) saranno distribuiti solo nel cluster predefinito.


## Link correlati

* [Informazioni su {{site.data.keyword.vmwaresolutions_short}}](../vmonic/prod_overview.html)
* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Richiesta di servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
