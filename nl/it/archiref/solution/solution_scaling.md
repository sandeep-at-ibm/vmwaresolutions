---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---

# Ridimensionamento della capacità

Dopo la distribuzione iniziale, puoi ridimensionare la capacità di calcolo dalla console {{site.data.keyword.vmwaresolutions_full}}. La progettazione supporta i seguenti percorsi di ridimensionamento:
* Aggiunta di nuovi siti gestiti da vCenter Server separati
* Aggiunta di nuovi cluster
* Aggiunta di nuovi host a un cluster esistente

## Aggiunta di più siti

{{site.data.keyword.vmwaresolutions_short}} può sfruttare la presenza di data center {{site.data.keyword.cloud_notm}} in tutto il mondo e il backbone di rete integrato per consentire la distribuzione e il funzionamento di vari casi di utilizzo di più aree geografiche in solo una frazione del tempo necessario a costruire da zero un'infrastruttura di questo tipo.

In questa progettazione, la definizione di una distribuzione multisito è composta da quanto segue:
* Una distribuzione VMware iniziale o primaria contenente un nuovo dominio root DNS/AD, dominio secondario, dominio SSO e nome del sito SSO da fornire.
* Siti secondari singoli o multipli che vengono forniti nel dominio SSO dei siti primari che richiedono la seguente configurazione:
   * Nuovo nome del sito SSO
   * Nuovo sito/dominio secondario DNS collegato alla root del dominio primario
   * Configurazione della replica DNS e AD tra le VM AD del sito primario e secondario
   * PSC distribuito e configurato per la sincronizzazione con il PSC del sito primario
   * vCenter configurato con la modalità di collegamento migliorata nel vCenter del sito primario

Inoltre, il gestore NSX nei siti secondari può essere configurato come gestore NSX secondario per il gestore NSX sul sito primario.

## Aggiunta di nuovi cluster

Per ridimensionare la capacità di calcolo puoi anche creare un nuovo cluster dalla console {{site.data.keyword.vmwaresolutions_short}} e ordinare nuovi host che vengono aggiunti automaticamente al nuovo cluster.

Questo metodo ti consente di ottenere i seguenti risultati:
* Creazione di un ulteriore cluster separato nell'ambiente.
* Segregazione dei carichi di lavoro di gestione dai carichi di lavoro dell'applicazione fisicamente e logicamente.
* Segregazione dei carichi di lavoro in base ad altre caratteristiche, ad esempio, il cluster di database Microsoft SQL.
* Distribuzione di applicazioni in topologie altamente disponibili.

**Nota**: quando il cluster iniziale viene convertito in un cluster di sola gestione, la migrazione dei carichi di lavoro esistenti implicherà dei passi manuali che dovranno essere eseguiti dall'utente. Ciò potrebbe comportare il ricollegamento degli archivi dati dal nuovo cluster o, in alternativa, la migrazione dell'archiviazione. Potrebbe essere necessario modificare gli indirizzi IP dei carichi di lavoro se il nuovo cluster risiede in un pod {{site.data.keyword.cloud_notm}} diverso o se gli viene assegnato un ID VLAN differente.

## Aggiunta di host ESXi nei cluster esistenti

Puoi ridimensionare un cluster esistente ordinando gli host dalla console {{site.data.keyword.vmwaresolutions_short}}.  I nuovi host vengono aggiunti automaticamente al cluster. Tieni presente che potresti dover regolare la politica di prenotazione dell'alta disponibilità (HA) per in cluster in base ai tuoi requisiti di prenotazione.

### Link correlati

* [Panoramica della soluzione](solution_overview.html)
* [Panoramica della progettazione](design_overview.html)
* [Backup dei componenti](solution_backingup.html)
