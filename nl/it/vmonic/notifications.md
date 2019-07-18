---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# Gestione delle notifiche di sistema
{: #notifications}

Puoi controllare le notifiche per verificare lo stato delle operazioni di sistema o dell'utente. Puoi anche utilizzare le informazioni per analizzare i problemi che potrebbero verificarsi.

## Visualizzazione delle notifiche
{: #notifications-view}

1. Dalla console {{site.data.keyword.vmwaresolutions_full}}, fai clic su **Notifiche** nel riquadro di navigazione a sinistra.
2. Visualizza il riepilogo su tutte le notifiche.

| Colonna | Descrizione |
|:------ |:----------- |
| Severità | La severità dell'evento segnalato dalla notifica.<br>**Critico**: un evento critico potrebbe influire sull'intero sistema o servizio.<br>**Errore**: durante un'operazione si verifica un evento di errore che potrebbe richiedere l'intervento dell'amministratore o dell'utente.<br>**Avvertenza**: un componente produce errori o non funziona correttamente. Tuttavia, l'errore non interrompere il processo in corso del
componente.<br>**Informativo**: è stata completata un'operazione di sistema o dell'utente. In genere, i seguenti eventi segnalano notifiche informative:<br>Un servizio è stato installato.<br>Un servizio è stato aggiornato.<br>Un servizio è stato rimosso.<br>Tutti i servizi sono stati riconfigurati per i server ESXi aggiunti.<br>Tutti i servizi sono stati riconfigurati per i server ESXi rimossi. |
| Tipo | Il tipo di componente a cui è correlato l'evento segnalato: istanze vCenter Server, servizi, sistema |
| Risorsa | Il nome dell'istanza o del servizio che invia la notifica. |
| Descrizione | Una breve descrizione della notifica. |
| Data | La data e ora in cui la notifica è stata inviata. |
{: caption="Tabella 1. Cronologia delle notifiche" caption-side="top"}

3. Fai clic su una riga di notifica per visualizzarne i dettagli.

## Filtraggio delle notifiche
{: #notifications-filter}

Per impostazione predefinita, vengono visualizzate tutte le notifiche non lette. Puoi filtrare le notifiche per stato, severità e tipo. Per filtrare le notifiche, seleziona le caselle di spunta solo per gli elementi che vuoi visualizzare negli elenchi **Stato**, **Severità** o **Tipo**.

## Link correlati
{: #notifications-related}

* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
