---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Ordine di FortiGate Virtual Appliance on IBM Cloud

Puoi ordinare il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud}} quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per una nuova istanza

Puoi ordinare una nuova istanza con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **FortiGate Virtual Appliance on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **FortiGate Virtual Appliance on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per un'istanza esistente

Puoi aggiungere il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **FortiGate Virtual Appliance on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

## Configurazione del servizio FortiGate Virtual Appliance on IBM Cloud

Quando ordini il servizio, fornisci le seguenti impostazioni.

### Nome

Immetti il nome del servizio.

### Dimensione distribuzione

{{site.data.keyword.cloud_notm}} fornisce le seguenti opzioni di dimensioni della distribuzione:
* Small (2 vCPU / 4 GB di RAM)
* Medium (4 vCPU / 6 GB di RAM)
* Large (8 vCPU / 12 GB di RAM)

### Modello di licenza

Il modello di licenza per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} offre le seguenti opzioni:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Questo bundle include Filtraggio stateful dei pacchetti, Protezione VLAN e registrazione avanzata, Regole firewall in entrata e in uscita, Terminazione VPN SSL/IPSec e supporto continuo.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Questo bundle include tutti i servizi Standard Firewall otre a NGFW IPS e filtro web, AntiVirus e AntiSpam, Reputazione IP e dominio e servizi di sicurezza FortiCare di base.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Questo bundle include tutti i servizi Standard Firewall e UTM in aggiunta a FortiSandbox Cloud e Mobile Security.</dd>
</dl>

**Importante:** non puoi modificare il modello di licenza dopo l'installazione del servizio. Per modificare il modello di licenza, devi rimuovere il servizio esistente e reinstallare il servizio selezionando un'opzione di licenza diversa.

### Link correlati

* [Panoramica di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_considerations.html)
* [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
