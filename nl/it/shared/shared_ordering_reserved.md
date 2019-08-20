---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resources, order reserved shared, order reserved resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordinazione di Shared Reserved
{: #shared_ordering_reserved}

{{site.data.keyword.vmwaresolutions_full}} Shared viene fornito come un'offerta sperimentale.
{:note}

Per Shared Reserved, le prenotazioni del data center virtuale di vCPU e RAM sono preassegnate e la loro disponibilità è garantita.
* Il costo viene calcolato mensilmente per l'intera prenotazione e si basa sulla dimensione dell'assegnazione del data center virtuale.
* Le risorse di vCPU e RAM possono essere aumentate o diminuite successivamente se necessario.
* Non esistono limiti alla quantità di archiviazione che può essere assegnata e utilizzata nel data center virtuale. Le tariffe sono su base oraria e in base ai GB di archiviazione assegnata.
* Non esistono limiti alla quantità di reti pubbliche in entrata e in uscita. La larghezza di banda pubblica viene addebitata per GB.

## Requisiti per IBM Cloud for VMware Solutions Shared
{: #shared_ordering_reserved-req}

### Account dell'infrastruttura IBM Cloud
{: #shared_ordering_reserved-account-req}

Per utilizzare {{site.data.keyword.vmwaresolutions_short}} per ordinare IBM Cloud for VMware Solutions Shared, devi avere un account **Pagamento a consumo** o **Sottoscrizione** {{site.data.keyword.cloud_notm}}. Il costo delle risorse ordinate viene fatturato su tale account {{site.data.keyword.cloud_notm}}.

### Requisiti del nome del data center virtuale
{: #shared_ordering_reserved-vdc-name-req}

Il nome del data center virtuale *deve* soddisfare i seguenti requisiti. I requisiti di denominazione saranno applicati in futuro.
* Sono consentiti solo caratteri alfabetici minuscoli, numerici e trattini (-).
* Il nome deve iniziare con un carattere alfabetico minuscolo.
* Il nome deve terminare con un carattere alfabetico minuscolo o un carattere numerico.
* La lunghezza massima del nome del data center virtuale è di 10 caratteri.
* Il nome del data center virtuale deve essere univoco all'interno del tuo account.

## Procedura per ordinare Shared Reserved
{: #shared_ordering-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic sull'icona **VMware** nel riquadro di navigazione a sinistra e quindi sulla scheda **IBM Cloud for VMware Solutions Shared** nella sezione **VMware Virtual Data Centers**.
2. Nella pagina **IBM Cloud for VMware Solutions Shared**, fai clic sulla scheda **Reserved** e su **Create**.
3. Nella pagina **IBM Cloud for VMware Solutions Shared - Reserved**, immetti il nome del data center virtuale. 
4. Scegli l'impegno a termine per la prenotazione delle risorse. Il {{site.data.keyword.CloudDataCent_notm}} in cui è disponibile l'offerta è preselezionato.
5. Specifica la prenotazione delle risorse:
    * Quando selezioni **Preconfigurato**, scegli una delle configurazioni preimpostate.
    * Quando selezioni **Personalizzato**, specifica le prenotazioni di vCPU e RAM.
6. Nel riquadro **Riepilogo ordine**, verifica la configurazione e i costi stimati prima di effettuare l'ordine.
7. Fai clic su **Fornitura**.

## Risultati dopo l'ordine di Shared Reserved
{: #shared_ordering_reserved-results}

* La distribuzione delle risorse inizia automaticamente e ricevi una conferma che ti indica che l'ordine è in fase di elaborazione. Puoi verificare lo stato della distribuzione, inclusi gli eventuali problemi che potrebbero richiedere la tua attenzione, visualizzando **Virtual Data Center Status**.
* Una volta che le risorse sono state distribuite correttamente, i componenti descritti in [Specifiche tecniche per {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) vengono installati sulla tua piattaforma virtuale VMware.
* Quando le risorse sono pronte per l'utilizzo, lo stato viene modificato con **Ready to Use**.

## Link correlati
{: #shared_ordering_reserved-related}

* [Panoramica di {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Ordinazione di Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Gestione di {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
