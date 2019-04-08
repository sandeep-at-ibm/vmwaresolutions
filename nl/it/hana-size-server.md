---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP Quick Sizer, {{site.data.keyword.cloud_notm}}, {{site.data.keyword. baremetal_short}}, deployment

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. Ridimensionamento del server
{: #size_the_server}

Dopo che hai deciso quali soluzioni SAP pensi di utilizzare, il tuo passo successivo è di determinare il numero di {{site.data.keyword.baremetal_long}} di cui hai bisogno per supportare il tuo scenario SAP e per assicurarti che i server siano correttamente dimensionati.
{: shortdesc}

## Informazioni sulla metodologia di dimensionamento SAP
{: #size_method}

SAP HANA viene offerto in configurazioni a singolo nodo {{site.data.keyword.cloud_notm}} con un totale di dimensioni RAM di
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 6144 GB (6 TB)
  * 8192 GB (8 TB)
  * 12288 GB (12 TB)

È un database a colonne che normalmente richiede meno spazio per archiviare i dati in confronto a un Relation Database Management System (RDMS) basato sulle righe tradizionale. I dati possono essere altamente compressi e i rapporti di compressione possono essere compresi tra 3:1 e 10:1 in base ai dati di origine al database.

Devi dimensionare correttamente il tuo server *prima* di acquistarlo, perché il dimensionamento è un fattore determinante per il tuo progetto. I requisiti di memoria o archiviazione dimensionati in modo non corretto possono comportare un upgrade e la migrazione a un server più grande.

## Accesso a SAP Quick Sizer
{: #quick_sizer}

La memoria principale è una delle risorse più importanti da considerare quando si dimensiona un'applicazione certificata SAP HANA. La [*SAP HANA Master Guide* ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf){: new_window} pubblica fornisce un punto di partenza degli argomenti correlati al dimensionamento. Le informazioni su [Sizing SAP HANA ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: new_window} nella guida forniscono le indicazioni su come dimensionare il tuo sistema SAP HANA. Punta a scenari di installazione e migrazione differenti per le nuove installazioni e per i sistemi esistenti. È presente un link alla versione di SAP HANA per lo strumento SAP Quick Sizer (è necessario un ID utente SAP S per accedere allo strumento). La pagina elenca inoltre le note SAP correlate al dimensionamento del tuo server SAP HANA.

## Dimensionamento di un ambiente virtualizzato
{: #size_virtual}

Per ulteriori considerazioni sul dimensionamento quando esegui SAP HANA in un ambiente virtualizzato, consulta [Distribuzioni server VMware ESXi](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server) e [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}.

## Passi successivi

 [5. Determinazione della tua configurazione](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
