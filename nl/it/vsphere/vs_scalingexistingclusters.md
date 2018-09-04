---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-11"

---

# Ridimensionamento di cluster vSphere esistenti

Puoi ridimensionare un cluster VMware vSphere che hai ordinato o salvato nella console {{site.data.keyword.vmwaresolutions_full}}. Per farlo, aggiungi i server ESXi oppure ordina una coppia HA di dispositivi FortiGate Security Appliance della serie 300 per il cluster.

## Requisiti

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](../vmonic/useraccount.html).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per i cluster vSphere](vs_planning.html).

## Procedura

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e poi su **VMware vSphere** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.  
3. Fai clic sulla scheda **Scala esistente** e seleziona il cluster che vuoi ridimensionare dall'elenco **Configurazioni cluster**.
4. Esamina le impostazioni del cluster che vengono completate automaticamente.
5. Nella sezione **{{site.data.keyword.baremetal_short}}**, specifica il numero di {{site.data.keyword.baremetal_short}} che vuoi aggiungere al cluster.
6. Se il cluster non include la coppia HA di dispositivi FortiGate Security Appliance della serie 300 sulla sua VLAN pubblica, ne puoi ordinare una selezionando **Includi con l'acquisto** in **Coppia FortiGate Physical Appliance 300 Series HA**.
7. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza e il costo stimato.
   * Per salvare la configurazione come template senza effettuare un ordine, fai clic su **Salva configurazione**.
   * Per effettuare l'ordine, assicurati che l'account da addebitare sia corretto, esamina e accetta i termini e infine fai clic su **Fornitura**.

### Risultati

Il ridimensionamento del cluster inizia automaticamente. Riceverai un'e-mail di conferma che ti indica che l'ordine è in fase di elaborazione. Quando il cluster è pronto per l'uso, ti viene inviata una notifica via e-mail.

**Nota:** i cluster vSphere, a differenza delle istanze vCenter Server e Cloud Foundation, non vengono visualizzati nella pagina **Istanze distribuite**.

### Link correlati

* [Ordine di nuovi cluster vSphere](vs_orderinginstances.html)
* [Ordine di cluster vSphere in base alle configurazioni esistenti](vs_orderingbasedonexistingconfig.html)
* [Ridimensionamento di cluster creati all'esterno della console](vs_orderingforclustersoutside.html)
