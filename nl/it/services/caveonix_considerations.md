---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations}

Il servizio Caveonix RiskForesight on {{site.data.keyword.cloud}} può aiutare a gestire i rischi informatici e di conformità con un monitoraggio proattivo e dei controlli di difesa automatizzati per proteggere da minacce e soddisfare le normative del settore e quelle governative.

Questo servizio è disponibile solo per le istanze VMware vCenter Server on {{site.data.keyword.cloud_notm}} distribuite nella V2.9 e nelle release successive.
{:note}

## Specifiche tecniche per Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-specs}

Nel servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

### Risorse vCenter
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* Disco: 80 GB

### Rete
{: #caveonix_considerations-tech-specs-network}

Viene ordinata una sottorete privata dedicata con 64 indirizzi IP.

### Licenze e tariffe
{: #caveonix_considerations-tech-specs-license-fee}

Una chiave di licenza Caveonix RiskForesight viene ordinata per ogni istanza del servizio.

## Considerazioni quando installi Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-install}

Prima di installare il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, assicurati che CPU e memoria nel cluster predefinito della tua istanza del servizio siano sufficienti per la VM Caveonix RiskForesight.

## Considerazioni sulla rimozione di Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-remove}

Esamina le seguenti considerazioni prima di rimuovere il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}:
* La rimozione del servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} non annulla la licenza Caveonix RiskForesight. Devi eliminare la licenza Caveonix RiskForesight dalla tabella **Licenze Caveonix RiskForesight** nella pagina **Risorse** nella console {{site.data.keyword.vmwaresolutions_short}}.
* Quando rimuovi il servizio, l'automazione {{site.data.keyword.vmwaresolutions_short}} elimina solo la singola VM Caveonix "tutto-in-uno" che era stata distribuita e la sottorete privata dedicata che era stata ordinata per essa. Pertanto:
   * Se avevi ridimensionato la VM Caveonix VM in più VM, queste VM aggiuntive non vengono rimosse.
   * Se avevi utilizzato gli indirizzi IP della sottorete privata dedicata sulle VM aggiuntive, a tali VM devono essere assegnati dei nuovi indirizzi IP perché continuino a funzionare.
   * Se elimini l'istanza A di vCenter Server con il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} installato, e avevi usato gli indirizzi IP sulla sottorete privata dedicata che era stata ordinata per il servizio nell'istanza B di vCenter Server, la sottorete privata dedicata viene annullata quando viene eseguita l'eliminazione dell'istanza A di vCenter Server.

## Link correlati
{: #caveonix_considerations-related}

* [Ordine di Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Gestione di Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
