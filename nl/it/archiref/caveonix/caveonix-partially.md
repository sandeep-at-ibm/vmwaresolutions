---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Parzialmente distribuito
{: #caveonix-partially}

Dopo il completamento della distribuzione automatizzata, puoi eseguire il ridimensionamento incrementale in modo manuale aumentando la RAM e il disco nella macchina virtuale (VM, Virtual Machine) iniziale e aggiungere tre VM di ridimensionamento incrementale. Lo script di configurazione di Riskforesight può essere eseguito per abilitare e configurare i componenti dell'applicazione su tutte e quattro le VM.

È previsto che questo modello di distribuzione serva fino a 500 asset con un massimo di 30 giorni di indicizzazione di dati.

Seleziona i successivi indirizzi IP disponibili dalla subnet portatile privata {{site.data.keyword.cloud}}. Configura i nomi FQDN in ADDNS.

Il dimensionamento delle VM è il seguente:

Tabella 1. Parametri di base

|Parametro	|Valore|
|---|---|
|Tipo	|Base|
|Quantità VM	|1|
|vCPU	|16|
|RAM	|64 GB|
|Disco	|1000 GB|
|SO	|CentOS 7|
|Componenti dell'applicazione installati	|IU, applicazione, plugin, raccoglitore centrale, archivio dati indice, archivio dati di messaggistica, archivio dati relazionale, raccoglitore remoto|

I dettagli delle VM di ridimensionamento incrementale sono i seguenti:

Tabella 2. Parametri di ridimensionamento incrementale

| Parametro	| Valore |
|---|---|
| Tipo	| Ridimensionamento incrementale |
| Quantità VM	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| Disco	| 4 TB |
| SO	| CentOS 7 |
| Componenti dell'applicazione installati	| Nodi di dati (ridimensionamento incrementale) |

I dettagli della VM del raccoglitore remoto sono visualizzati nella seguente tabella.

Tabella 3. Parametri del raccoglitore remoto

|Parametro	|Valore|
|---|---|
|Quantità VM	|Come richiesto|
|vCPU	|8|
|RAM	|8 GB|
|Disco	|1 TB|
|SO	|CentOS 7|
|Componenti dell'applicazione installati	|Raccoglitore remoto|

## Link correlati
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
