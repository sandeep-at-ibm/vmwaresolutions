---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ridimensionamento di cluster vSphere esistenti
{: #vs_scalingexistingclusters}

Puoi ridimensionare un cluster VMware vSphere che hai ordinato o salvato nella console {{site.data.keyword.vmwaresolutions_full}}. Per farlo, aggiungi i server ESXi oppure ordina una coppia HA di dispositivi FortiGate Security Appliance della serie 300 per il cluster.

## Requisiti
{: #vs_scalingexistingclusters-req}

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per i cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).
*  Hai ricevuto un'e-mail con la conferma che il cluster che vuoi ridimensionare è pronto per l'utilizzo.

## Procedura per ridimensionare i cluster esistenti
{: #vs_scalingexistingclusters-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e poi su **VMware vSphere** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.  
3. Fai clic sulla scheda **Scala esistente** e seleziona il cluster che vuoi ridimensionare dall'elenco **Configurazioni cluster**.
4. Esamina le impostazioni del cluster che vengono completate automaticamente.
5. Nella sezione **{{site.data.keyword.baremetal_short}}**, specifica il numero di {{site.data.keyword.baremetal_short}} che vuoi aggiungere al cluster.
6. Se il cluster non include la coppia HA di FortiGate Security Appliance della serie 300 sulla sua VLAN pubblica, puoi ordinare il dispositivo. Per farlo, seleziona la casella di spunta **Includi con l'acquisto** sotto **Coppia FortiGate Physical Appliance 300 Series HA**.
7. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza e il costo stimato.
   * Per salvare la configurazione come template senza effettuare un ordine, fai clic su **Salva configurazione**.
   * Per effettuare l'ordine, assicurati che l'account da addebitare sia corretto, esamina e accetta i termini e infine fai clic su **Fornitura**.

### Risultati
{: #vs_scalingexistingclusters-results}

Il ridimensionamento del cluster inizia automaticamente. Riceverai un'e-mail di conferma che ti indica che l'ordine è in fase di elaborazione. Quando il cluster è pronto per l'uso, ti viene inviata una notifica via e-mail.

Se il cluster che stai ridimensionando non è pronto per l'utilizzo, potresti ricevere un messaggio di errore.

I cluster vSphere, a differenza delle istanze vCenter Server, non vengono visualizzati nella pagina **Risorse**.
{:note}

## Link correlati
{: #vs_scalingexistingclusters-related}

* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ordine di cluster vSphere in base alle configurazioni esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Ridimensionamento di cluster creati all'esterno della console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
