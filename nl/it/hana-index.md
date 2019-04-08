---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Esercitazione introduttiva
{: #getting-started}

{{site.data.keyword.IBM_notm}} e SAP hanno collaborato per più di 45 anni in molte aree inclusi hardware, software, cloud, servizi e finanza. Ora stanno collaborando per ottimizzare i prodotti dell'infrastruttura {{site.data.keyword.cloud}} per includere il supporto per la soluzione SAP HANA in più di 60 data center {{site.data.keyword.cloud_notm}} nel mondo.
{: shortdesc}

Questo contenuto ti fornisce i consigli per il provisioning e l'installazione dell'infrastruttura SAP HANA e la sottoscrizione a {{site.data.keyword.cloud_notm}}. Non sostituisce la documentazione SAP HANA e non è pensato per fornire una descrizione completa del processo di installazione. Il suo scopo è di aiutarti nel provisioning e nella pianificazione della tua infrastruttura in modo che puoi avviare la tua installazione di SAP. L'installazione di SAP (inclusa l'installazione del database) non è diversa dall'installazione degli ambienti in loco. I consigli e le linee guida sono forniti per aiutarti ad utilizzare il tuo sistema SAP nell'ambiente {{site.data.keyword.cloud_notm}} correlato all'infrastruttura fornita, ad esempio, la configurazione della rete o l'archiviazione del backup. L'operatività del sistema SAP HANA non è diversa da quella di qualsiasi altro data center dopo che l'infrastruttura è in funzione.

La tabella 1 contiene la procedura per aiutarti a creare la tua infrastruttura {{site.data.keyword.cloud_notm}} velocemente.
<table>
   <CAPTION>Tabella 1. Procedura d'avvio rapida</CAPTION>
   <THEAD>
   <TR>
   <th>Attività</th>
   <th>Dettagli</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Leggi il contenuto IBM Cloud e SAP correlato alla tua implementazione</td>
   <td>Se la tua organizzazione è nuova su IBM Cloud, le seguenti informazioni possono essere utili e dovrebbero essere lette prima della fase di pianificazione.
   <li><a href="https://ibm.com/cloud-computing/">What is IBM Cloud</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Getting started with IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">SAP Certified Infrastructure on IBM Cloud</a></li>

   Puoi trovare utile anche la seguente documentazione SAP:     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA Installation Guide</a>; scarica la guida di installazione</li>
  <li><a href="https://www.youtube.com/watch?v=4wICiRTP8u0/">Come creare un ID S-user SAP</a>. Tieni presente che solo gli amministratori con privilegi avanzati o S-user con l'autorizzazione richiesta possono creare ID S-user. </li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA Administration Guide</a></li>
   <li><a href="https://support.sap.com">SAP Notes</a>; richiede un ID utente SAP S</li>
   <tr>
   <td>2. Registrati con IBM Cloud</td>
   <td>Consulta <a href="https://cloud.ibm.com/docs/account?topic=account-signup#signing-up-for-ibm-cloud">Signing up for IBM Cloud</a> per la procedura su come configurare il tuo account IBM Cloud.</td>
 <tr>
   <td>3. Accedi al portale del cliente dell'infrastruttura IBM Cloud</td>
   <td>Il <a href="https://control.softlayer.com">portale del cliente dell'infrastruttura IBM Cloud</a> è il tuo gateway grafico di tutti i tuoi componenti dell'infrastruttura-calcolo, connettività, archiviazione, rete e data center. Hai bisogno di <a href="https://console.bluemix.net/docs/customer-portal?topic=customer-portal-getting-started#getting-started">un ID IBM e una password</a> per accedere al portale del cliente.</td>
   <tr>
   <td>4. Pianifica il tuo scenario di sistema</td>
   <td>Utilizza le informazioni in <a href="sap-hana?topic=sap-hana-planning-your-system-landscape#planning-your-system-landscape">Pianificazione del tuo scenario di sistema</a> per progettare, dimensionare e fornire il tuo ambiente IBM Cloud per supportare il tuo carico di lavoro SAP HANA.</td>  
 <tr>
   <td>5. Esegui il provisioning del tuo sistema</td>
   <td>Utilizza la procedura e le informazioni in <a href="sap-hana?topic=sap-hana-provision_environment#provision_environment">Provisioning del tuo ambiente SAP HANA</a> per configurare la tua infrastruttura IBM Cloud.</td>
   <tr>
   <td>6. Installa lo scenario SAP</td>
   <td>Installa il tuo scenario SAP sulla tua infrastruttura IBM Cloud come se i server fossero in loco. Per ulteriori informazioni, consulta <a href="sap-hana?topic=sap-hana-install_sap#install_sap">Scaricamento e installazione delle applicazioni e del software SAP</a>.</td>
   </td>
   </tr>
   </TBODY>
   </table>
