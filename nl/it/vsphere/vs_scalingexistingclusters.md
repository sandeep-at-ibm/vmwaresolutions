---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-08"

---

# Ridimensionamento di cluster vSphere esistenti

Puoi ridimensionare un cluster VMware vSphere esistente che hai ordinato o salvato nella console {{site.data.keyword.vmwaresolutions_full}} aggiungendo i server ESXi oppure ordinando una coppia di FortiGate 300 Series Security Appliance HA per il cluster.

## Requisiti

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](../vmonic/useraccount.html).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per i cluster vSphere](vs_planning.html).

## Procedura

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e quindi su **VMware vSphere** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.  
3. Fai clic su **Incrementa esistente** e seleziona il cluster che vuoi ridimensionare dall'elenco **Configurazioni cluster**.
4. Rivedi le impostazioni del cluster che vengono compilate automaticamente.
5. Nella sezione **{{site.data.keyword.baremetal_short}}**, specifica il numero di {{site.data.keyword.baremetal_short}} che vuoi aggiungere al cluster.
6. Se il cluster non include la coppia HA di dispositivi FortiGate Security Appliance della serie 300 sulla sua VLAN pubblica, ne puoi ordinare una selezionando **Includi con l'acquisto** in **Coppia FortiGate Physical Appliance 300 Series HA**.
7. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza e il costo stimato.
   * Per salvare la configurazione come template senza effettuare un ordine, fai clic su **Salva configurazione**.
   * Per effettuare l'ordine, assicurati che l'account da addebitare sia corretto, esamina e accetta i termini e infine fai clic su **Fornitura**.

## Risultati

La distribuzione del ridimensionamento del cluster inizia automaticamente e riceverai un'e-mail di conferma che ti indica che l'ordine è in fase di elaborazione. Quando il cluster è pronto per l'uso, ti viene inviata una notifica via e-mail.

**Nota:** i cluster vSphere, a differenza delle istanze vCenter Server e Cloud Foundation, non vengono visualizzati nella pagina **Istanze distribuite**.

## Link correlati

* [Ordine di nuovi cluster vSphere](vs_orderinginstances.html)
* [Ordine di cluster vSphere in base alle configurazioni esistenti](vs_orderingbasedonexistingconfig.html)
* [Ridimensionamento di cluster creati all'esterno della console](vs_orderingforclustersoutside.html)
