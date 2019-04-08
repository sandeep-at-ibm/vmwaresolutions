---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Completamente distribuito
{: #caveonix-fully}

VM di base e VM di ridimensionamento incrementale aggiuntive vengono aggiunte in base al numero di asset e ai requisiti di conservazione dei dati.

Tabella 1. Base - interfaccia utente

|Parametro	|Valore|
|---|---|
|Tipo	|Base|
|Quantità VM	|2|
|vCPU	|2|
|RAM	|6 GB|
|Disco	|60 GB|
|SO	|CentOS 7|
|Componenti dell'applicazione installati	|IU|

Tabella 2. Base - applicazioni e plug-in

|Parametro	|Valore|
|---|---|
|Tipo	|Base|
|Quantità VM	|2|
|vCPU	|8|
|RAM	|16 GB|
|Disco	|500 GB|
|SO	|CentOS 7|
|Componenti dell'applicazione installati	|Applicazione, plugin|

Tabella 3. Base - raccoglitore centrale

|Parametro	|Valore |
|---|---|
|Tipo	|Base |
|Quantità VM	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|500 GB |
|SO	|CentOS 7 |
|Componenti dell'applicazione installati	|Raccoglitore centrale (cluster) |

Tabella 4. Base - database relazionale

|Parametro	|Valore |
|---|---|
|Tipo	|Base |
|Quantità VM	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|1 TB |
|SO|CentOS 7 |
|Componenti dell'applicazione installati	|Archivio dati relazionale (primario/secondario) |

Tabella 5. Base - archivio dati di messaggistica

|Parametro	|Valore |
|---|---|
|Tipo	|Base |
|Quantità VM	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|1 TB |
|SO	|CentOS 7 |
|Componenti dell'applicazione installati	|Archivio dati di messaggistica (cluster) |

Tabella 6. Base - archivio dati indice (nodi master)

|Parametro	|Valore |
|---|---|
|Tipo	|Base |
|Quantità VM	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|1 TB |
|SO	|CentOS 7 |
|Componenti dell'applicazione installati	|Archivio dati indice (nodi master) |

Tabella 7. Database - archivio dati indice (nodi di dati)

|Parametro	|Valore |
|---|---|
|Tipo	|Base |
|Quantità VM	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|4 TB |
|SO	|CentOS 7 |
|Componenti dell'applicazione installati	|Archivio dati indice (nodi di dati) |

I dettagli della VM di ridimensionamento incrementale sono descritti nella seguente tabella.

Tabella 8. Ridimensionamento incrementale - nodi di dati

|Parametro	|Valore |
|---|---|
|Tipo	|ridimensionamento incrementale |
|Quantità VM	28 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|4 TB |
|SO	|CentOS 7 |
|Componenti dell'applicazione installati	|Nodi di dati (ridimensionamento incrementale) |

I dettagli della VM del raccoglitore remoto sono visualizzati nella seguente tabella.

Tabella 9. Raccoglitore remoto

|Parametro	|Valore |
|---|---|
|Quantità VM	|Come richiesto |
|vCPU	|8 |
|RAM	|8 GB |
|Disco	|1 TB |
|SO	|CentOS 7 |
|Componenti dell'applicazione installati	|Raccoglitore remoto |

## Link correlati
{: #caveonix-fully-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
