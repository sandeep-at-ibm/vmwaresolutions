---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: FortiGate VA, FortiGate configuration, order FortiGate

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering}

Puoi ordinare il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud}} quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per una nuova istanza
{: #fortinetvm_ordering-new}

Puoi ordinare una nuova istanza con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **FortiGate Virtual Appliance on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **FortiGate Virtual Appliance on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per un'istanza esistente
{: #fortinetvm_ordering-existing}

Puoi aggiungere il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **FortiGate Virtual Appliance on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per le istanze private
{: #fortinetvm_ordering-private}

Quando ordini FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} per le istanze che non sono configurate con interfacce pubbliche, devi fornire un server proxy per completare l'installazione. Il server proxy HTTP deve essere configurato e disponibile mediante VRF (Virtual Routing and Forwarding) prima che possa essere avviata l'installazione di Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}.

Per garantire un funzionamento ininterrotto, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} deve avere un accesso persistente al server di licenze Fortigate via internet.

## Configurazione del servizio FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-config}

Quando ordini il servizio, fornisci le seguenti impostazioni.

### Connessione di rete FortiGuard
{: #fortinetvm_ordering-config-network-connect}

Seleziona **Rete pubblica** o **Rete privata** per FortiGuard. Se il cluster di destinazione è configurato con interfacce di rete solo private, è disponibile solo l'opzione **Rete privata**. Questa selezione determina come FortiGuard contatterà il server di licenza Fortinet per attivare la licenza e per scaricare le patch di sicurezza e non influirà sul piano dati del carico di lavoro.

Se selezioni **Rete privata**, specifica le seguenti impostazioni:
* **Indirizzo IP proxy**: l'indirizzo IPv4 del server proxy.
* **Numero porta proxy**: il numero di porta del server proxy, di solito 8080 o 3128.
* **Nome utente proxy**: se hai bisogno dell'autenticazione proxy, immetti il nome utente del server proxy.
* **Password proxy**: se hai bisogno dell'autenticazione proxy, immetti la password del server proxy.

### Nome
{: #fortinetvm_ordering-config-name}

Immetti il nome del servizio.

### Dimensione distribuzione
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}} fornisce le seguenti opzioni di dimensioni della distribuzione:
* Small (2 vCPU / 4 GB di RAM)
* Medium (4 vCPU / 6 GB di RAM)
* Large (8 vCPU / 12 GB di RAM)

### Modello di licenza
{: #fortinetvm_ordering-config-license}

Il modello di licenza per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} offre le seguenti opzioni:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Questo bundle include Filtraggio stateful dei pacchetti, Protezione VLAN e registrazione avanzata, Regole firewall in entrata e in uscita, Terminazione VPN SSL/IPSec e supporto e supporto 24 x 7.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Questo bundle include tutti i servizi firewall standard in aggiunta al servizio AMP (Advanced Malware Protection). Include Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service e Content Disarm & Reconstruct. Include inoltre i servizi Web Filtering, IPS, Antispam, Application Control e FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Questo bundle include tutti i servizi firewall standard e i servizi UTM oltre ai seguenti servizi:<ul><li>Cloud Access Security Broker (CASB) - Questo servizio fornisce visibilità, conformità, sicurezza dei dati e protezione dalle minacce per i servizi basati su cloud.</li><li>Industrial Security - Questo servizio fornisce firme per i protocolli ICS/SCADA comuni.</li><li>Security Rating - Questo servizio fornisce funzionalità di controllo per identificare vulnerabilità critiche e debolezze di configurazione e per implementare i suggerimenti delle procedure consigliate.</li></ul></dd>
</dl>

Nel terzo quadrimestre del 2018, Fortinet ha aggiunto tre nuovi servizi (CASB, Industrial Security, e Security Rating) al proprio bundle aziendale. Questi servizi sono disponibili solo su FortiGate 6.0.
{:note}

Non puoi modificare il modello di licenza dopo l'installazione del servizio. Per modificare il modello di licenza, devi rimuovere il servizio esistente e reinstallare il servizio selezionando un'opzione di licenza diversa.
{:important}

## Link correlati
{: #fortinetvm_ordering-related}

* [Panoramica di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:new_window}
