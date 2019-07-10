---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade delle licenze per le istanze vCenter Server
{: #vc_upgrade-lic}

Puoi eseguire l'upgrade delle tue istanze VMware vCenter Server in vCenter Server with Hybridity Bundle solo se la versione della tua istanza è V2.3 o successive.

Gli utenti IBM Business Partner non hanno l'opzione per eseguire l'upgrade a Hybridity Bundle.
{:note}

## Prima di eseguire l'upgrade della tua licenza a Hybridity Bundle
{: #vc_upgrade-lic-upgrade-prereq}

Esamina le seguenti azioni che vengono eseguite quando esegui l'upgrade a Hybridity Bundle:

* Se la tua istanza vCenter Server ha l'edizione VMware NSX Base installata, verrà eseguito automaticamente l'upgrade della tua licenza NSX all'edizione NSX Advanced.
* Se la tua istanza vCenter Server ha l'archiviazione NFS, non ti verranno addebitati costi per l'archiviazione VMware vSAN. Tuttavia, ti verrà addebitato il costo per la licenza vSAN inclusa con Hybridity Bundle.

## Procedura per eseguire l'upgrade a Hybridity Bundle (istanze V2.3 o successive)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per eseguire l'upgrade a Hybridity Bundle.
3. Nella pagina **Riepilogo**, verifica che tutti i dettagli dell'istanza siano visualizzati correttamente. Quindi, fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra per verificare i dettagli nella pagina **Infrastruttura**.

   Se i dettagli non vengono visualizzati, ciò potrebbe indicare un problema di connettività con la VSI IBM CloudDriver, a causa di una regola del firewall o di altri problemi di rete. Risolvi il problema prima di continuare con il passo successivo, altrimenti l'upgrade potrebbe non riuscire.

4. Fai clic su **Aggiorna e applica patch** nel riquadro di navigazione a sinistra.
5. Per applicare l'upgrade della licenza Hybridity Bundle, nella tabella **Aggiornamenti della licenza**, fai clic su **Esegui upgrade** nella colonna **Azioni**. Esamina il costo stimato e fai clic su **Esegui upgrade**.
6. Facoltativamente, puoi distribuire il servizio VMware HCX on {{site.data.keyword.cloud_notm}}. Quando Hybridity Bundle è abilitato nella tabella **Aggiornamenti della licenza**, completa i seguenti passi:
  1. Nella tabella **Aggiornamenti della licenza**, fai clic su **Distribuisci HCX on {{site.data.keyword.cloud_notm}}** nella colonna **Azione**.
  2. Scorri fino alla scheda **HCX on {{site.data.keyword.cloud_notm}}** e fai clic su **Seleziona servizio**.
  3. Scorri verso il basso e specifica le impostazioni richieste per il servizio e fai clic su **Avanti**.
  4. Controlla i termini che si applicano al servizio, esamina il costo stimato e fai clic su **Effettua ordine**.

## Procedura per eseguire l'upgrade della tua licenza NSX (istanze V2.1 o successive)
{: #vc_upgrade-lic-nsx}

Questa procedura si applica alle istanze distribuite nella V2.1 o successive. Per le istanze distribuite nella V2.0 e precedenti, devi eseguire manualmente l'upgrade della licenza NSX.

Puoi eseguire l'upgrade della licenza NSX per la tua istanza a un'edizione successiva. I downgrade dell'edizione della licenza non sono supportati.

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale eseguire l'upgrade della licenza NSX.
3. Nella pagina **Riepilogo**, verifica che tutti i dettagli dell'istanza siano visualizzati correttamente. Quindi, fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra per verificare i dettagli nella pagina **Infrastruttura**.

   Se i dettagli non vengono visualizzati, ciò potrebbe indicare un problema di connettività con la VSI (Virtual Server Instance) IBM CloudDriver, a causa di una regola del firewall o di un problema di rete. Risolvi il problema prima di continuare con il passo successivo, altrimenti l'upgrade potrebbe non riuscire.

4. Fai clic su **Aggiorna e applica patch** nel riquadro di navigazione a sinistra e quindi fai clic su **Esegui upgrade**. Nella finestra **Aggiorna edizione licenza NSX**, seleziona l'edizione a cui vuoi aggiornare e fai clic su **Aggiorna**.

   L'aggiornamento della licenza sostituisce tutte le licenze NSX esistenti sull'istanza. Se esegui l'aggiornamento nel mezzo di un ciclo di fatturazione, potrebbero essere applicati dei costi aggiuntivi derivanti da una sovrapposizione di vecchie e nuove licenze. Per evitare costi aggiuntivi, si consiglia di aggiornare la licenza alla fine del ciclo di fatturazione.
   {:note}

## Link correlati
{: #vc_upgrade-lic-related}

* [Panoramica di vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
