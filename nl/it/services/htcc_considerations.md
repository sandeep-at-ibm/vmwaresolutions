---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di HyTrust CloudControl on IBM Cloud
{: #htcc_considerations}

Il servizio HyTrust CloudControl on {{site.data.keyword.cloud}} applica e controlla la conformità rispetto agli standard di sicurezza che includono il controllo degli accessi in base al ruolo (RBAC), l'approvazione e la verifica. Quando viene combinato con HyTrust DataControl, il servizio garantisce che le VM (Virtual Machine) e i dati del carico di lavoro non lascino una regione, un cluster o un server ESXi particolare all'interno del {{site.data.keyword.CloudDataCent_notm}}.

Questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o di cui è stato eseguito l'upgrade alla V2.3 o successive. La versione HyTrust CloudControl corrente installata è la 5.5.
{:note}

## Specifiche tecniche per HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-specs}

Nel servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Dispositivo HyTrust CloudControl
{: #htcc_considerations-appliance}

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: 70 GB VMDK residente su vSAN in cluster convergente
* Rete: posizionata su rete trasferibile privata supportata dalla VLAN specificata per la gestione

### Alta disponibilità (HA)
{: #htcc_considerations-ha}

Vengono distribuiti due dispositivi CloudControl in una configurazione attiva-passiva.

### Licenze e tariffe
{: #htcc_considerations-licenses}

Licenza per host: viene ordinata una licenza HyTrust CloudControl per ciascun host nell'ambiente.

## Considerazioni sulla rimozione di HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-remove}

Prima di rimuovere il servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, assicurati di disabilitare l'**Archiviazione della password root**, se configurata, e di eliminare tutti gli host protetti da HyTrust CloudControl.

## Link correlati
{: #htcc_considerations-related}

* [Ordine di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Gestione di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web HyTrust](https://www.hytrust.com/)
