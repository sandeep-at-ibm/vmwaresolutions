---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: vCenter Server NSX-T delete instance, delete vCenter Server NSX-T, remove vCenter Server NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Eliminazione di istanze vCenter Server with NSX-T
{: #vc_nsx-t_deletinginstance}

Per rilasciare i componenti che hai ordinato in un'istanza VMware vCenter Server with NSX-T, elimina l'istanza.

Quando elimini un'istanza vCenter Server with NSX-T, i seguenti componenti vengono rilasciati in modo sequenziale:
2. Spese di supporto
3. Licenze del prodotto VMware
4. Server ESXi
5. Sottoreti
6. VLAN

A causa delle dipendenze delle risorse, i componenti della tua istanza non vengono rilasciati immediatamente quando elimini l'istanza. Ad esempio, le sottoreti e le VLAN non possono essere eliminate finché i server ESXi non vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud}}, cosa che avviene alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}. Alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni, le sottoreti e le VLAN vengono eliminate e l'eliminazione dell'istanza viene completata.

Per l'istanza eliminata ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
{:note}

## Procedura per eliminare le istanze dalla pagina Risorse
{: #vc_nsx-t_deletinginstance-procedure1}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, trova l'istanza da eliminare.
3. Nella colonna **Azioni**, fai clic sull'icona Elimina.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Nella colonna **Azioni**, fai di nuovo clic sull'icona Elimina.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Procedura per eliminare le istanze dalla pagina dei dettagli dell'istanza
{: #vc_nsx-t_deletinginstance-procedure2}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da eliminare.
3. Fai clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Fai di nuovo clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Link correlati
{: #vc_nsx-t_deletinginstance-related}

* [Eliminazione di istanze vCenter Server in una configurazione multisito](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance_multi)
* [Ordine di istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Espansione e contrazione della capacità per le istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [Annullamento dei server virtuali](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
