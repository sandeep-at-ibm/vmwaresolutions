---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Protezione di istanze VMware Federal

Completa la seguente procedura per proteggere la tua istanza VMware Federal distribuita, ossia, per rimuovere la connessione di gestione aperta per l'accesso in corso all'istanza.

## Prima di iniziare

Consulta le seguenti informazioni per comprendere i risultati della protezione della tua istanza VMware Federal distribuita:

* Prima di completare questa procedura, registra e salva le credenziali necessarie per il tuo ambiente. Tutte le credenziali relative al tuo ambiente vengono cancellate dal database {{site.data.keyword.vmwaresolutions_full}} e non possono essere recuperate dopo il richiamo dell'azione di protezione.
* Ad eccezione dell'eliminazione completa dell'istanza, tutte le funzioni di gestione vengono disabilitate dopo il richiamo dell'azione di protezione.
* Il gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HTTPS in uscita e la macchina virtuale IBM CloudDriver vengono eliminati come parte dell'azione per proteggere l'istanza VMware Federal distribuita.

## Procedura

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da proteggere.
3. Fai clic sull'icona del menu di overflow a destra di **Console vCenter**.
4. Fai clic su **Proteggi istanza**.
5. Fai clic su **OK** per confermare che vuoi disconnettere l'istanza dall'automazione.

   **Nota**: prima di completare questo passo, assicurati di aver esaminato le informazioni nella sezione **Prima di iniziare**.

## Risultati

Lo stato dell'istanza viene modificato in **In fase di modifica**.

Una volta che l'istanza è protetta, il suo stato viene modificato in **Protetto** e saranno disponibili solo le proprietà e la cronologia di distribuzione dell'istanza.

### Link correlati

* [Panoramica di VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Ordine di istanze VMware Federal](vc_fed_orderinginstance.html)
* [Visualizzazione delle istanze VMware Federal](vc_fed_viewinginstance.html)
* [Eliminazione di istanze VMware Federal](vc_fed_deletinginstance.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
