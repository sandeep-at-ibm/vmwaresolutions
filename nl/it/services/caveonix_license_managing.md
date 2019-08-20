---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione delle licenze Caveonix RiskForesight
{: #caveonix_license_managing}

Puoi visualizzare, modificare le note o eliminare le licenze Caveonix RiskForesight che hai ordinato per l'utilizzo autonomo.

## Procedura per visualizzare le licenze Caveonix RiskForesight
{: #caveonix_license_managing_procedure-view}

1. Fai clic su **Risorse** dal riquadro di navigazione a sinistra e scorri in basso alla tabella **Licenze Caveonix RiskForesight**.

   | Elemento | Descrizione |
   |:-----|:------------|
   | Nome | Il nome della licenza. |
   | Data/ora di creazione | La data e l'ora in cui è stata creata la licenza. |
   | Stato | Lo stato della licenza: <br>In fase di modifica: la licenza è in fase di modifica.<br>Installata: la licenza è pronta per l'utilizzo.<br>In fase di rimozione: la licenza è in fase di eliminazione. |
   {: caption="Tabella 1. Descrizione degli elementi di licenza Caveonix RiskForesight" caption-side="top"}

2. Per visualizzare i dettagli di una specifica licenza, fai clic sulla licenza.

## Procedura per modificare le note delle licenze Caveonix RiskForesight
{: #caveonix_license_managing_procedure-edit}

1. Fai clic su **Risorse** nel riquadro di navigazione a sinistra.
2. Scorri verso il basso alla tabella **Caveonix RiskForesight Licenses** e fai clic sulla licenza per cui desideri modificare le note.
3. Nella pagina dei dettagli della licenza, modifica le note della licenza e fai quindi clic su **Confirm**.

## Problemi noti relativi alla visualizzazione della data della licenza
{: #caveonix_license_considerations-date}

Se stai utilizzando Mozilla Firefox come tuo browser, le date di inizio e fine della licenza potrebbero essere visualizzate senza alcun valore nella console di Caveonix RiskForesight. Per risolvere il problema, visualizza le informazioni sulla licenza in un altro browser, come ad esempio Google Chrome.

Se stai riscontrando questo problema e il solo browser che puoi utilizzare è Firefox, contatta il [supporto di Caveonix](https://www.caveonix.com/support/){:external} per assistenza.
{:note}

## Procedura per eliminare le licenze Caveonix RiskForesight
{: #caveonix_license_managing_procedure-delete}

L'eliminazione di una licenza Caveonix RiskForesight non rimuove il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} installato su un'istanza vCenter Server. Per rimuovere il servizio, devi farlo nella console {{site.data.keyword.vmwaresolutions_short}}. Per ulteriori informazioni, vedi [Procedura per rimuovere i servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).
{:note:}

1. Fai clic su **Risorse** nel riquadro di navigazione a sinistra.
2. Scorri alla tabella **Licenze Caveonix RiskForesight** e trova la licenza da eliminare.
3. Nella colonna **Azioni**, fai clic sull'icona di eliminazione.
4. Nella finestra **Elimina licenza**, fai clic su **OK**.
   Lo stato della licenza viene modificato in **In fase di rimozione**. Una volta completata la sua eliminazione, la licenza non è più disponibile nella tabella **Licenze Caveonix RiskForesight**.

## Link correlati
{: #caveonix_license_managing-related}

* [Panoramica di Caveonix RiskForesight]()
* [Ordine di licenze Caveonix RiskForesight](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
