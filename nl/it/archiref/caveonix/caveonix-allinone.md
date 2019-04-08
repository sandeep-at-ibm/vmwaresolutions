---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Distribuzione tutto-in-uno
{: #caveonix-allinone}

Una distribuzione e una configurazione automatizzate di una singola VM (Virtual Machine) che ospita tutti i componenti dell'applicazione RiskForesight. Questo modello di distribuzione è adatto per le piccole distribuzioni, fino a 100 asset con 7-30 giorni di indicizzazione. I dettagli della VM “tutto-in-uno” sono visualizzati nella seguente tabella:

Tabella 1. Parametri tutto-in-uno

|Parametro	|Valore|
|---|---|
|Tipo	|Base|
|Quantità VM	|1|
|vCPU	|16|
|RAM	|32 GB|
|Disco	|80 GB|
|SO	|CentOS 7|
|Componenti dell'applicazione installati|	IU, applicazione, plugin, raccoglitore centrale, archivio dati indice, archivio dati di messaggistica, archivio dati relazionale, archivio dati indice, raccoglitore remoto|

I dettagli della VM del raccoglitore remoto aggiuntivi sono visualizzati nella seguente tabella:

Tabella 2. Raccoglitore remoto

|Parametro	|Valore|
|---|---|
|Quantità VM	|Come richiesto|
|vCPU	|8|
|RAM	|8 GB|
|Disco	|1 TB|
|SO	|CentOS 7|
|Componenti dell'applicazione installati	|Raccoglitore remoto|

## Link correlati
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
