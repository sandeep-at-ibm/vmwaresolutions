---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Processo di rimozione per Zerto on IBM Cloud

Il processo di rimozione del servizio Zerto on {{site.data.keyword.cloud}} è automatizzato. Per la corretta rimozione del servizio Zerto on {{site.data.keyword.cloud_notm}}, viene completata la seguente procedura.

## Come rimuovere Zerto on IBM Cloud

1. Fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra e seleziona l'istanza da cui vuoi rimuovere il servizio.
2. Fai clic sulla scheda **Servizi**.
3. Nella scheda **Servizi installati**, fai clic sull'icona del menu di overflow nella parte superiore destra della scheda del servizio e quindi su **Rimuovi servizio**.
4. Nella finestra **Rimuovi servizio**, rivedi le possibili considerazioni o avvertenze. Fai clic su **Accetto**.
5. Dopo che la tua richiesta di rimozione del servizio viene accettata, lo stato del servizio viene modificato in **In fase di rimozione** e vengono completati i seguenti passi di rimozione:   
   1. Rimuovi i dispositivi Zerto Virtual Replication Appliance che erano stati distribuiti a tutti i server ESXi.
   2. Disinstalla Zerto Virtual Replication.
   3. Elimina l'istanza di servizio virtuale (o VSI, Virtual Service Instance) di Windows su cui era installato Zerto Virtual Replication.
   4. Restituisci la sottorete portatile privata che era stata ordinata per le comunicazioni di Zerto Virtual Replication all'infrastruttura {{site.data.keyword.cloud_notm}}.   
   5. Rimuovi i costi del servizio di ripristino di emergenza Zerto dall'estratto conto di {{site.data.keyword.cloud_notm}}.

      Per il servizio di ripristino di emergenza Zerto rimosso ti vengono addebitati costi fino alla fine del ciclo di fatturazione.
      {:note}

## Risultati

Una volta completata correttamente la rimozione del servizio, riceverai una notifica via e-mail e la voce del servizio verrà eliminata dalla scheda **Servizi installati**.

### Link correlati

* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Istanze vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
