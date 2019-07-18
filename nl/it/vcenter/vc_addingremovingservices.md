---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-27"

keywords: vCenter Server add service, view service vCenter Server, remove service vCenter Server

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server
{: #vc_addingremovingservices}

Puoi ordinare servizi per le tue istanze VMware vCenter Server, ad esempio una soluzione di ripristino di emergenza. Quando non hai più bisogno di questi servizi, puoi rimuoverli dalle tue istanze.

## Servizi disponibili per le istanze vCenter Server
{: #vc_addingremovingservices-available-services}

La seguente tabella mostra i servizi disponibili per le istanze vCenter Server, insieme alle versioni del servizio installate.

| Nome servizio | Versione servizio corrente | Versione istanza |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2.1 | V2.9 e successive |
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | V1.9 e successive |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) | 300 series | V2.0 e successive |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 e successive |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | 5.5.1 | V2.3 e successive |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)  | 4.3.2 | V2.3 e successive |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | 4.3.2 | V2.5 e successive |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1.2 | V2.5 e successive |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | 10.1.3 | V2.2 e successive |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | 2.0  | N/A  |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | V1.8 e successive |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6.5 aggiornamento a 3 | V1.2 e successive |
{: caption="Tabella 1. Servizi disponibili per le istanze vCenter Server" caption-side="top"}

## Procedura per aggiungere servizi alle istanze vCenter Server
{: #vc_addingremovingservices-adding-procedure}

Per aggiungere un servizio alla tua istanza vCenter Server, fai clic sul link del servizio appropriato nella tabella precedente per esaminare le considerazioni relative al servizio e controllare i componenti distribuiti. Quindi, segui le istruzioni indicate nell'argomento su come ordinare i servizi per aggiungere il servizio alla tua istanza.

### Risultati dell'installazione del servizio
{: #vc_addingremovingservices-adding-results}

Una volta completata correttamente l'installazione del servizio, riceverai una notifica via e-mail e il servizio verrà visualizzato nella pagina **Servizi** dell'istanza con lo stato **Installato**.

## Procedura per visualizzare i servizi per le istanze vCenter Server
{: #vc_addingremovingservices-viewing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi visualizzare i servizi.
3. Fai clic su **Servizi** nel riquadro di navigazione a sinistra.
4. Nella pagina **Servizi**, fai clic su un servizio per esaminare le relative informazioni, come lo stato del servizio e altri dettagli.
5. A seconda del servizio visualizzato, puoi accedere alle relative console utilizzando le credenziali fornite nei dettagli del servizio e puoi gestire il servizio da qui.

## Procedura per rimuovere i servizi per le istanze vCenter Server
{: #vc_addingremovingservices-removing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi rimuovere i servizi.
3. Fai clic su **Servizi** nel riquadro di navigazione a sinistra.
4. Nella pagina **Servizi**, individua l'istanza del servizio che vuoi rimuovere e fai clic sull'icona **Elimina**.
5. Nella pagina **Elimina servizio**, esamina le eventuali considerazioni o avvertenze. Seleziona **Accetto** e fai clic su **Elimina**.

### Risultati della rimozione del servizio
{: #vc_addingremovingservices-removing-results}

Dopo che la tua richiesta di rimozione del servizio viene accettata, lo stato del servizio viene modificato in **In fase di rimozione**.

Una volta completata correttamente la rimozione del servizio, riceverai una notifica via e-mail e il servizio verrà rimosso dalla pagina **Servizi** dell'istanza.

Per i servizi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
{:note}

## Link correlati
{: #vc_addingremovingservices-related}

* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
