---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di cluster vSphere in base alle configurazioni esistenti
{: #vs_orderingbasedonexistingconfig}

Puoi ordinare un cluster VMware vSphere in base a un template di configurazione che hai salvato. Utilizza questa procedura per definire la configurazione di un nuovo cluster basata su una configurazione cluster esistente.

## Requisiti
{: #vs_orderingbasedonexistingconfig-req}

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per i cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).
*  Hai creato un template di configurazione da riutilizzare.

## Procedura per ordinare i cluster vSphere in base alle configurazioni esistenti
{: #vs_orderingbasedonexistingconfig-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e poi su **VMware vSphere** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.  
3. Fai clic sulla scheda **Crea nuovo** e seleziona un template di configurazione dell'elenco **Configurazioni cluster**.
4. Immetti il nome del nuovo cluster.
5. Esamina le impostazioni del cluster che vengono completate automaticamente e aggiorna le impostazioni in base alle tue esigenze. Per ulteriori informazioni sulle impostazioni, vedi [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).
6. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza e il costo stimato.
   * Per salvare la configurazione come template senza effettuare un ordine, fai clic su **Salva configurazione**.
   * Per effettuare l'ordine, assicurati che l'account da addebitare sia corretto, esamina e accetta i termini e infine fai clic su **Fornitura**.

   Vengono installati solo i {{site.data.keyword.baremetal_short}}. Sei responsabile dell'installazione e della configurazione dei vari componenti dopo la distribuzione del cluster, come VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

## Risultati
{: #vs_orderingbasedonexistingconfig-results}

Se hai salvato la configurazione del cluster come template, ricevi una notifica dalla console che indica che la configurazione è stata salvata. Potrai quindi trovare il template nell'elenco **Configurazioni cluster**.

Se hai effettuato un ordine, la distribuzione del cluster inizia automaticamente. Riceverai un'e-mail di conferma che ti indica che l'ordine è in fase di elaborazione. Quando il cluster è pronto per l'uso, ti viene inviata un'altra notifica e-mail.

I cluster vSphere, a differenza delle istanze vCenter Server e Cloud Foundation, non vengono visualizzati nella pagina **Risorse**.
{:note}

## Link correlati
{: #vs_orderingbasedonexistingconfig-related}

* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ridimensionamento di cluster vSphere esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Ridimensionamento di cluster creati all'esterno della console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
