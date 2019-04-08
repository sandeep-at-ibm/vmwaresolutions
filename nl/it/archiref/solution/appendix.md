---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Tabella di confronto per le edizioni dei componenti VMware
{: #solution-appendix}

## Confronto delle edizioni di VMware NSX
{: #solution-appendix-nsx-editions}

In questa progettazione, ci sono più componenti che necessitano di licenze. Queste informazioni mostrano le licenze minime che sono necessarie all'ambiente per funzionare correttamente.

Tabella 1. Requisiti di licenza

Componente | Scopo | Licenza
----------|---------|-------------
**vSphere** |Virtualizzazione di calcolo| vSphere 6.7 Enterprise Plus
**vCenter Server** | Gestione infrastruttura | vCenter Server 6.7 Standard
**NSX** |Virtualizzazione di rete| NSX Base for Service Providers 6.4
**vSAN** |Virtualizzazione di archiviazione| vSAN 6.6 Advanced  

NSX Base for Service Providers edition è l'unica disponibile per i provider di servizi tramite VMware vCloud Air Network (vCAN). Le funzioni in questa edizione possono essere trovate nella seguente tabella.
{:note}

Tabella 2. Tabella di confronto per le edizioni di VMware NSX

| Funzione NSX                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| Commutazione e instradamento distribuiti             | •    | •        | •          |
| Firewall edge NSX                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| Bilanciamento del carico edge NSX                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| Automazione basata su API                         | •    | •        | •          |
| Integrazione con vRealize e OpenStack\*     | •    | •        | •          |
| Automazione di politiche di sicurezza con vRealize |      | •        | •          |
| Bridging SW L2 all'ambiente fisico        |      | •        | •          |
| Instradamento dinamico con ECMP (attivo-attivo)     |      | •        | •          |
| Firewall distribuito                       |      | •        | •          |
| Integrazione con Active Directory             |      | •        | •          |
| Monitoraggio dell'attività del server                    |      | •        | •          |
| Inserimento dei servizi (integrazione di terze parti)     |      | •        | •          |
| Bilanciamento del carico distribuito                    |      |          | •          |
| Cross vCenter NSX                             |      |          | •          |
| Ottimizzazioni di NSX su più siti                  |      |          | •          |
| Gateway remoto                                |      |          | •          |
| Integrazione con VTEP hardware                     |      |          | •          |
\*Integrazione solo con L2, L3 ed edge NSX. Nessun consumo di gruppi di sicurezza

## Confronto delle edizioni di VMware vSAN
{: #solution-appendix-vsan-editions}

La seguente tabella elenca le funzioni disponibili per le edizioni **Advanced** ed **Enterprise** di VMware vSAN supportate dalla soluzione.

Tabella 3. Tabella di confronto per le edizioni di VMware vSAN

| Funzione vSAN                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| Gestione basata sulla politica di archiviazione                 | •        | •          |
| Memorizzazione nella cache di lettura/scrittura Flash                        | •        | •          |
| RAID distribuito                                | •        | •          |
| Switch distribuito virtuale                      | •        | •          |
| Rilevazione rack                                  | •        | •          |
| Replica vSphere                             | •        | •          |
| Checksum software                               | •        | •          |
| Hardware all-flash                              | •        | •          |
| Servizio di destinazione iSCSI                            | •        | •          |
| Limite IOPS                                      | •        | •          |
| Deduplicazione e compressione                   | •        | •          |
| Codifica di cancellazione RAID-5/6                         | •        | •          |
| Crittografia per dati inattivi                         |          | •          |
| Cluster esteso con protezione dagli errori locali |          | •          |

## Link correlati
{: #solution-appendix-related}

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Panoramica della progettazione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Backup dei componenti](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
