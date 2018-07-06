---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-21"

---

# Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation

Puoi ordinare servizi per le tue istanze VMware Cloud Foundation, ad esempio una soluzione di ripristino di emergenza. Quando non hai più bisogno di questi servizi, puoi rimuoverli dalle tue istanze.

## Servizi disponibili per le istanze Cloud Foundation

La seguente tabella mostra i servizi disponibili per le istanze Cloud Foundation.

Tabella 1. Servizi disponibili per le istanze Cloud Foundation

| Nome servizio | Disponibilità | Supporto istanza |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)                                 | Sì | V1.9 e successive |
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)       | Sì | V1.8 e successive |
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html) | Sì | V2.0 e successive |
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)              | Sì | V2.3 e successive |
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)              | Sì | V2.3 e successive |
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)         | Sì | V2.2 e successive |
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)                  | Sì | V2.2 e successive |
| [Veeam on IBM Cloud](../services/veeam_considerations.html)                          | Sì | V1.8 e successive |
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                         | No | Non applicabile |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                 | Sì | V1.2 e successive |

## Aggiunta di servizi alle istanze Cloud Foundation

Per aggiungere un servizio alla tua istanza Cloud Foundation, fai clic sul link del servizio appropriato nella tabella precedente per esaminare le considerazioni relative al servizio e controllare i componenti distribuiti. Quindi, segui le istruzioni nell'argomento su come ordinare i servizi per aggiungere il servizio alla tua istanza.

### Risultati dell'installazione del servizio

Una volta completata correttamente l'installazione del servizio, riceverai una notifica via e-mail e il servizio verrà visualizzato nella pagina **Servizi** dell'istanza con lo stato **Installato**.

## Visualizzazione dei servizi per le istanze Cloud Foundation

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza per la quale vuoi visualizzare i servizi.
3. Fai clic su **Servizi** nel riquadro di navigazione a sinistra.
4. Nella pagina **Servizi**, fai clic su un servizio per esaminare le relative informazioni, come lo stato del servizio e altri dettagli.
5. A seconda del servizio visualizzato, puoi accedere alle relative console utilizzando le credenziali fornite nei dettagli del servizio e gestire quindi il servizio da qui.

## Rimozione dei servizi per le istanze Cloud Foundation

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza per la quale vuoi rimuovere i servizi.
3. Fai clic su **Servizi** nel riquadro di navigazione a sinistra.
4. Nella pagina **Servizi**, individua l'istanza del servizio che vuoi rimuovere e fai clic sull'icona **Elimina**.
5. Nella pagina **Elimina servizio**, esamina le eventuali considerazioni o avvertenze. Seleziona **Accetto** e fai clic su **Elimina**.

### Risultati della rimozione del servizio

Dopo che la tua richiesta di rimozione del servizio viene accettata, lo stato del servizio viene modificato in  **In fase di rimozione**.

Una volta completata correttamente la rimozione del servizio, riceverai una notifica via e-mail e il servizio verrà rimosso dalla pagina **Servizi** dell'istanza.

**Attenzione**: per i servizi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}.

## Link correlati

* [Domande frequenti](../vmonic/faq.html)
