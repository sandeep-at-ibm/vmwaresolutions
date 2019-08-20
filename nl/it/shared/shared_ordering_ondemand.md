---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordinazione di Shared On-demand
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared viene fornito come un'offerta sperimentale.
{:note}

Per On-demand, vCPU e RAM del data center virtuale vengono assegnati quando necessario e possono variare nella quantità di tempo necessaria all'assegnazione a seconda dell'utilizzo globale di consumo di vCPU e RAM del data center virtuale.
* I limiti stabiliti per la quantità di vCPU e RAM sono i valori massimi che possono essere utilizzati in qualsiasi momento.
* Le risorse di vCPU e RAM possono essere aumentate o diminuite successivamente se necessario.
* Il costo viene calcolato su base oraria e si basa sull'utilizzo di risorse nel data center virtuale.
* Non esistono limiti alla quantità di archiviazione che può essere assegnata e utilizzata nel data center virtuale. Le tariffe sono su base oraria e in base ai GB di archiviazione assegnata.
* Non esistono limiti alla quantità di reti pubbliche in entrata e in uscita. La larghezza di banda pubblica viene addebitata per GB. 

## Requisiti per IBM Cloud for VMware Solutions Shared
{: #shared_ordering_ondemand-req}

### Account dell'infrastruttura IBM Cloud
{: #shared_ordering_ondemand-account-req}

Per utilizzare {{site.data.keyword.vmwaresolutions_short}} per ordinare IBM Cloud for VMware Solutions Shared, devi avere un account **Pagamento a consumo** o **Sottoscrizione** {{site.data.keyword.cloud_notm}}. Il costo delle risorse ordinate viene fatturato su tale account {{site.data.keyword.cloud_notm}}.

### Requisiti del nome del data center virtuale
{: #shared_ordering_ondemand-vdc-name-req}

Il nome del data center virtuale *deve* soddisfare i seguenti requisiti. I requisiti di denominazione saranno applicati in futuro.
* Sono consentiti solo caratteri alfabetici minuscoli, numerici e trattini (-).
* Il nome deve iniziare con un carattere alfabetico minuscolo.
* Il nome deve terminare con un carattere alfabetico minuscolo o un carattere numerico.
* La lunghezza massima del nome del data center virtuale è di 10 caratteri.
* Il nome del data center virtuale deve essere univoco all'interno del tuo account.

## Procedura per ordinare Shared On-demand
{: #shared_ordering_ondemand-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic sull'icona **VMware** nel riquadro di navigazione a sinistra e quindi sulla scheda **IBM Cloud for VMware Solutions Shared** nella sezione **VMware Virtual Data Centers**.
2. Nella pagina **IBM Cloud for VMware Solutions Shared**, fai clic sulla scheda **On-demand** e su **Create**.
3. Nella pagina **IBM Cloud for VMware Solutions Shared - On-demand**, immetti il nome del data center virtuale. Il {{site.data.keyword.CloudDataCent_notm}} in cui è disponibile l'offerta è preselezionato.
4. Seleziona i limiti di vCPU e RAM in base ai tuoi requisiti.
5. Nel riquadro **Riepilogo ordine**, verifica la configurazione e i costi stimati prima di effettuare l'ordine.
6. Fai clic su **Fornitura**.

## Risultati dopo l'ordine di Shared On-demand
{: #shared_ordering_ondemand-results}

* La distribuzione delle risorse inizia automaticamente e ricevi una conferma che ti indica che l'ordine è in fase di elaborazione. Puoi verificare lo stato della distribuzione, inclusi gli eventuali problemi che potrebbero richiedere la tua attenzione, visualizzando **Virtual Data Center Status**.
* Una volta che le risorse sono state distribuite correttamente, i componenti descritti in [Specifiche tecniche per {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) vengono installati sulla tua piattaforma virtuale VMware.
* Quando le risorse sono pronte per l'utilizzo, lo stato viene modificato con **Ready to Use**.

## Link correlati
{: #shared_ordering_ondemand-related}

* [Panoramica di {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Ordinazione di Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Gestione di {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
