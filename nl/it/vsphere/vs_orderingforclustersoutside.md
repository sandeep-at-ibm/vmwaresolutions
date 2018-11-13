---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ridimensionamento di cluster creati all'esterno della console

Puoi utilizzare l'offerta VMware vSphere per ridimensionare i cluster vSphere esistenti creati all'esterno della console {{site.data.keyword.vmwaresolutions_full}}. Per ridimensionare un cluster vSphere creato al di fuori della console, ricrea il cluster con le stesse impostazioni mediante la console e quindi ridimensionalo.

## Requisiti

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](../vmonic/useraccount.html).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_planning.html).

## Procedura per ridimensionare i cluster creati all'esterno della console

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e poi su **VMware vSphere** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.  
   Assicurati di essere nella scheda **Crea nuovo** e che **Nuovo cluster** sia visualizzato nell'elenco **Configurazioni cluster**.
3. Crea un cluster con le stesse impostazioni del cluster esistente creato al di fuori della console {{site.data.keyword.vmwaresolutions_short}}. Per ulteriori informazioni, vedi [Ordine di nuovi cluster vSphere](vs_orderinginstances.html).  
   Per l'interfaccia di rete, per ridimensionare un cluster creato all'esterno della console {{site.data.keyword.vmwaresolutions_short}}, devi selezionare le VLAN esistenti per il cluster.
   {:note}
4. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster e fai quindi clic su **Salva configurazione**.   
5. Nella pagina **Introduzione**, fai clic sulla scheda **VMware vSphere on IBM Cloud**.
6. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.
7. Fai clic sulla scheda **Scala esistente**. Dall'elenco **Configurazioni cluster**, seleziona il cluster che hai creato di recente.
8. Nella sezione **{{site.data.keyword.baremetal_short}}**, specifica il numero di {{site.data.keyword.baremetal_short}} che vuoi aggiungere al cluster.
9. Se il cluster non include la coppia HA di dispositivi FortiGate Security Appliance della serie 300 sulla sua VLAN pubblica, ne puoi ordinare una selezionando **Includi con l'acquisto** in **Coppia FortiGate Physical Appliance 300 Series HA**.
10. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza e il costo stimato, assicurati che l'account da addebitare sia corretto, esamina e accetta i termini e infine fai clic su **Fornitura**.

## Risultati

La distribuzione del cluster inizia automaticamente e ricevi un'e-mail di conferma che ti indica che l'ordine è in fase di elaborazione. Quando il cluster è pronto per l'uso, ti viene inviata una notifica via e-mail.

I cluster vSphere non vengono visualizzati nella pagina **Istanze distribuite** insieme alle istanze vCenter Server e Cloud Foundation.
{:note}

### Link correlati

* [Ordine di nuovi cluster vSphere](vs_orderinginstances.html)
* [Ordine di cluster vSphere in base alle configurazioni esistenti](vs_orderingbasedonexistingconfig.html)
* [Ridimensionamento di cluster vSphere esistenti](vs_scalingexistingclusters.html)
