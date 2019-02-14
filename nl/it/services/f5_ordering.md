---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di F5 on IBM Cloud

Puoi ordinare il servizio F5 on {{site.data.keyword.cloud}} quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di F5 on IBM Cloud per una nuova istanza

Puoi ordinare una nuova istanza con F5 on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **F5 on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **F5 on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di F5 on IBM Cloud per un'istanza esistente

Puoi aggiungere il servizio F5 on {{site.data.keyword.cloud_notm}} in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **F5 on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

## Configurazione del servizio F5 on IBM Cloud

Quando ordini il servizio, fornisci le seguenti impostazioni.

### Connessione attivazione licenza F5

Seleziona **Rete pubblica** o **Rete privata** per l'attivazione della licenza. Se il cluster di destinazione è configurato con interfacce di rete solo private, è disponibile solo l'opzione **Rete privata**. Questa selezione determina il modo in cui i server virtuali F5 contatteranno il server di licenza F5 e non influirà sul piano dati del carico di lavoro.

Se selezioni **Rete privata**, specifica le seguenti impostazioni:
* **Indirizzo IP proxy**: l'indirizzo IPv4 del server proxy.
* **Numero porta proxy**: il numero di porta del server proxy, di solito 8080 o 3128.

Il proxy autenticato non è supportato.
{:note}

### Nome

Immetti il nome del servizio.

### Larghezza di banda massima

Specifica la velocità effettiva massima del dispositivo F5 BIG–IP.

### Modello di licenza

Il modello di licenza per il servizio F5 on {{site.data.keyword.cloud_notm}} offre le seguenti opzioni:
<dl class="dl">
        <dt class="dt dlterm">Buono</dt>
        <dd class="dd">Questa offerta utilizza il BIG-IP Local Traffic Manager™ (LTM) VE, che funge da architettura a proxy completo, per fornire una gestione intelligente del traffico locale, la completa visibilità del traffico SSL e l'analisi e il monitoraggio dell'integrità per garantire che i server delle applicazioni siano sempre disponibili per i tuoi utenti.</dd>
        <dt class="dt dlterm">Migliore</dt>
        <dd class="dd">Questa offerta è basata sui vantaggi dell'opzione **Buono**, con l'aggiunta dei moduli BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM) e BIG-IP Application Acceleration Manager™ (AAM). Fornisce servizi globali di gestione del traffico, ottimizzazione delle prestazioni delle applicazioni e funzionalità avanzate di mitigazione DDoS (Distributed Denial of Service) e firewall di rete.</dd>
        <dt class="dt dlterm">Massimo</dt>
        <dd class="dd">Oltre alle offerte **Buono** e **Migliore**, BIG-IP Application Security Manager™ (ASM) fornisce una protezione completa delle applicazioni contro le 10 principali minacce e vulnerabilità delle applicazioni comuni OWASP (Open Web Application Security Project), DDos L7. BIG-IP Access Policy Manager™ (APM) offre agli utenti un accesso sicuro e semplificato alle applicazioni situate ovunque all'interno di un ambiente multi-cloud, incorporando funzioni come SSO (Single Sign-On) e MFA (Multi-Factor Authentication).</dd>
</dl>

Non puoi modificare il modello di licenza dopo l'installazione del servizio. Per modificare il modello di licenza, devi rimuovere il servizio esistente e reinstallare il servizio scegliendo un modello di licenza diverso.
{:important}

### Link correlati

* [Panoramica di F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_considerations.html)
* [Gestione di F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managing_f5.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_addingremovingservices.html)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Guide di distribuzione F5](https://f5.com/solutions/deployment-guides){:new_window}
