---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade delle licenze NSX per le istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_upgrade-lic}

Puoi eseguire l'upgrade della licenza VMware NSX per la tua istanza a un'edizione successiva. I downgrade dell'edizione della licenza non sono supportati.

## Procedura per eseguire l'upgrade della tua licenza NSX
{: #vc_hybrid_upgrade-lic-nsx}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale eseguire l'upgrade della licenza NSX.
3. Nella pagina **Riepilogo**, verifica che tutti i dettagli dell'istanza siano visualizzati correttamente. Quindi, fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra per verificare i dettagli nella pagina **Infrastruttura**.

   Se i dettagli non vengono visualizzati, ciò potrebbe indicare un problema di connettività con la VSI (Virtual Server Instance) IBM CloudDriver, a causa di una regola del firewall o di un problema di rete. Risolvi il problema prima di continuare con il passo successivo, altrimenti l'upgrade potrebbe non riuscire.

4. Fai clic su **Aggiorna e applica patch** nel riquadro di navigazione a sinistra e quindi fai clic su **Esegui upgrade**. Nella finestra **Aggiorna edizione licenza NSX**, seleziona l'edizione a cui vuoi aggiornare e fai clic su **Aggiorna**.

   L'aggiornamento della licenza sostituisce tutte le licenze NSX esistenti sull'istanza. Se esegui l'aggiornamento nel mezzo di un ciclo di fatturazione, potrebbero essere applicati dei costi aggiuntivi derivanti da una sovrapposizione di vecchie e nuove licenze. Per evitare costi aggiuntivi, si consiglia di aggiornare la licenza alla fine del ciclo di fatturazione.
   {:note}

## Link correlati
{: #vc_hybrid_upgrade-lic-related}

* [Panoramica di vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
