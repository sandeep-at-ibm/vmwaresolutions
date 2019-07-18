---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: vCenter Server update, patch vCenter Server, IBM component update

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Applicazione di aggiornamenti del componente di gestione IBM alle istanze vCenter Server
{: #vc_applyingupdates}

La procedura in questa sezione si applica ai componenti di gestione IBM in aggiornamento per le istanze che vengono distribuite nelle release dalla V2.1 alla V2.4.

Per le istanze distribuite o di cui è stato eseguito l'upgrade alla V2.5 o successive, gli aggiornamenti e le patch per i componenti di gestione IBM vengono applicati automaticamente, in base alle esigenze.

Per le istanze distribuite nella V2.0 e precedenti, devi applicare manualmente gli aggiornamenti.

Inoltre, nota il seguente comportamento quando completi determinate operazioni sulla tua istanza:
* Quando ordini nuovi servizi, l'istanza viene aggiornata alla versione più recente.
* Quando aggiungi nuovi cluster, ne viene eseguito il provisioning con i componenti VMware più recenti ma non viene eseguito per i cluster esistenti.
* Quando aggiungi nuovi server ESXi, ne viene eseguito il provisioning con i componenti VMware più recenti ma non viene eseguito per i server ESXi esistenti.

{{site.data.keyword.vmwaresolutions_short}} non offre supporto per applicare gli aggiornamenti e le patch per i componenti VMware. Devi monitorare e applicare autonomamente questi aggiornamenti.
{:important}

## Prima di applicare gli aggiornamenti del componente di gestione IBM
{: #vc_applyingupdates-prereq}

Espandi la voce dell'aggiornamento facendo clic sulla freccia in giù e verifica le seguenti informazioni:
* La versione dell'aggiornamento. Devi applicare gli aggiornamenti in sequenza cronologica, dalla più antica alla più recente. Assicurati di aver applicato tutti gli aggiornamenti precedenti prima di applicare quello più recente. Ad esempio, devi applicare l'aggiornamento alla V2.3 prima di tentare di applicare l'aggiornamento alla V2.4.
* Se è necessario un tempo di inattività.
* Il tempo totale stimato per completare l'aggiornamento.
* L'impatto dell'aggiornamento sull'ambiente virtuale VMware. La tabella 1 mostra come i diversi livelli di impatto degli aggiornamenti sul sistema.
* I dettagli dell'aggiornamento.

| Livello di aggiornamento | Impatto |
|:------------ |:------ |
| Basso | Questo aggiornamento non influisce su alcun sistema. Non devi applicarlo durante i tempi di inattività pianificati. |
| Medium | Questo aggiornamento potrebbe influire su alcuni sistemi. Si consiglia di applicarlo durante i tempi di inattività pianificati. |
| Maggiore | Questo aggiornamento influisce su alcuni o tutti i sistemi. Devi applicarlo durante i tempi di inattività pianificati. |
{: caption="Tabella 1. Livelli di aggiornamento e impatto" caption-side="top"}

## Procedura per applicare gli aggiornamenti del componente di gestione IBM (istanze dalla V2.1 alla V2.4)
{: #vc_applyingupdates-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da aggiornare.
3. Nella pagina **Riepilogo**, verifica che tutti i dettagli dell'istanza siano visualizzati correttamente. Quindi, fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra per verificare i dettagli nella pagina **Infrastruttura**.

   Se i dettagli non vengono visualizzati, ciò potrebbe indicare un problema di connettività con la VSI (Virtual Server Instance) IBM CloudDriver, a causa di una regola del firewall o di un problema di rete. Risolvi il problema prima di continuare con il passo successivo, altrimenti l'aggiornamento potrebbe non riuscire.

4. Fai clic su **Aggiorna e applica patch** nel riquadro di navigazione a sinistra, fai clic sulla freccia in giù per espandere l'aggiornamento di gestione IBM che vuoi applicare e poi completa la seguente procedura:
   * Per avviare immediatamente l'aggiornamento, fai clic sull'icona del menu di overflow nella colonna **Azioni** della voce di aggiornamento, quindi fai clic su **Aggiorna ora**.
   * Per pianificare un aggiornamento futuro, fai clic sull'icona del menu di overflow nella colonna **Azioni** della voce di aggiornamento, quindi fai clic su **Pianifica aggiornamento**. Seleziona la data, l'ora e il fuso orario in cui vuoi avviare l'aggiornamento. Fai clic su **OK**.
5. Se applichi aggiornamenti alle istanze nella configurazione di distribuzione multisito, viene visualizzata una sezione intitolata **Passi necessari per l'aggiornamento**. Questa sezione elenca le operazioni di aggiornamento richieste per tutte le istanze nella distribuzione multisito. Devi completare i passi in sequenza facendo clic su **Applica aggiornamento** per ciascun passo. Devi attendere il completamento del passo precedente prima di iniziare il passo successivo.

## Risultati dopo l'applicazione degli aggiornamenti del componente di gestione IBM
{: #vc_applyingupdates-results}

1. Dopo aver applicato un aggiornamento, viene visualizzato un record nell'elenco di stato degli aggiornamenti software, in cui puoi visualizzare l'avanzamento dettagliato e lo stato dell'aggiornamento. Al termine dell'aggiornamento, viene visualizzato un record nell'elenco degli aggiornamenti software installati.

  Per recuperare lo stato più recente per un lavoro di aggiornamento, fai clic sull'icona di aggiornamento nell'angolo superiore destro della pagina.
  {:tip}

2. Per i dettagli sugli stati di aggiornamento, consulta la seguente tabella.

| Stato | Dettagli |
|:------ |:------- |
| Disponibile | L'aggiornamento è disponibile per l'applicazione. Non puoi selezionare un aggiornamento disponibile finché non vengono applicati tutti gli aggiornamenti precedenti. |
| In corso | Il lavoro di aggiornamento è iniziato ma non è ancora terminato. Non puoi applicare altri aggiornamenti finché non viene completato il lavoro di aggiornamento corrente. |
| Installato | Il lavoro di aggiornamento è completato. Il componente corrispondente della piattaforma VMware è aggiornato. |
| Non riuscito | Il lavoro di aggiornamento non riesce. La console segnala un errore di aggiornamento. Esamina l'errore e correggi il problema segnalato prima
di riapplicare l'aggiornamento. |
| Pianificato | Il lavoro di aggiornamento è pianificato per un secondo momento. Il lavoro di aggiornamento si avvia automaticamente all'ora pianificata. |
| Sconosciuto | Non è possibile ottenere lo stato del lavoro di aggiornamento. Contatta il supporto IBM per assistenza. |
{: caption="Tabella 2. Dettagli degli stati di aggiornamento" caption-side="top"}

3. Se il processo di aggiornamento non riesce in un passo specifico, [contatta il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) per assistenza. Ti verrà comunicato come risolvere il problema e sarai guidato ad applicare gli aggiornamenti e le patch dal passo non riuscito.

## Link correlati
{: #vc_applyingupdates-related}

* [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Upgrade delle licenze per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
