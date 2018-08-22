---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Panoramica di HyTrust CloudControl on IBM Cloud

Il servizio HyTrust CloudControl on {{site.data.keyword.cloud}} applica e controlla la conformità rispetto agli standard di sicurezza e fornisce funzionalità dettagliate di controllo degli accessi in base al ruolo (RBAC), approvazione e verifica. Se combinato con HyTrust DataControl, il servizio può garantire che le macchine virtuali e i dati del carico di lavoro non lascino una particolare regione, cluster o server ESXi all'interno del {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilità:** questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive.

## Specifiche tecniche per HyTrust CloudControl on IBM Cloud

Nel servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Dispositivo HyTrust CloudControl

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: 70 GB VMDK residente su vSAN in cluster convergente
* Rete: posizionata su rete trasferibile privata supportata dalla VLAN specificata per la gestione

### Alta disponibilità (HA)

Vengono distribuiti due dispositivi CloudControl in una configurazione attiva-passiva.

### Licenze e tariffe

Licenza per host: viene ordinata una licenza HyTrust CloudControl per ciascun host nell'ambiente.

## Considerazioni sulla rimozione di HyTrust CloudControl on IBM Cloud

Prima di rimuovere il servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, assicurati di disabilitare l'**Archiviazione della password root**, se configurata, e di eliminare tutti gli host protetti da HyTrust CloudControl.

### Link correlati

* [Ordine di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestione di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web HyTrust](https://www.hytrust.com/)
