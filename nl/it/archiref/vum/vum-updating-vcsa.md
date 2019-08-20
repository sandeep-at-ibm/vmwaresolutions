---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Aggiornamento di VCSA e vCenter collegati a SSO
{: #vum-updating-vcsa}

## Aggiornamento PSC e VCSA
{: #vum-updating-vcsa-psc-vcsa-update}

Questa sezione è correlata a vCentre Server Appliance (VCSA) e PSC (Platform Services Controller). Entrambi i dispositivi sono dispositivi VCSA ma con ruoli diversi. Quando esegui l'upgrade di vSphere con un PSC esterno, aggiorna prima il PSC, poi il VCSA, quindi gli host ESXi ed infine le versioni hardware e i VMware Tools nelle VM (Virtual Machine).

VUM non aggiorna il PSC/VCSA. Le seguenti informazioni descrivono il processo di aggiornamento di questi dispositivi. Il PSC/VCSA distribuito in un'istanza VMware vCenter Server on {{site.data.keyword.cloud}} non ha accesso a Internet, quindi il bundle di aggiornamento deve essere prima scaricato su un server jump.

Il PSC/VCSA viene aggiornato mediante la console di gestione del dispositivo, non con il client web vSphere. È possibile accedere alla console di gestione del dispositivo PSC/VCSA utilizzando un browser, l'indirizzo IP PSC/VCSA e la porta 5480.

Prima di eseguire l'aggiornamento, devi avviare un'istantanea del dispositivo o un backup di PSC/VCSA. Assicurati che tutto funzioni come previsto, quindi rimuovi l'istantanea entro pochi giorni per evitare una riduzione delle prestazioni. Inoltre, esamina le note sulla release VMware prima di tentare qualsiasi upgrade per comprendere tutte le istruzioni specifiche per la release specificata.

Per aggiornare il PSC/VCSA, completa la seguente procedura:
1. Puoi scaricare gli aggiornamenti andando alla pagina di [VMware Patch Download Center](https://www.vmware.com/patchmgr/findPatchByReleaseName.portal), effettuando l'accesso e scegliendo VC dal menu **Search by Product**. Seleziona la patch appropriata e fai clic su **Download**.
2. Utilizzando il client web vSphere, carica il file ISO nel repository dell'archivio chiavi di vCenter.
3. Monta il file ISO di aggiornamento in vCenter Server.
4. Fai un'istantanea del tuo vCenter Server.
5. Accedi alla console di gestione del dispositivo vCenter all'indirizzo: `https://pscip:5480` (per il PSC) o `https://vcenterip:5480` (per il VCSA)
6. Vai alla sezione **Update**, seleziona **Check Updates** e quindi **Check CDROM**. Viene elencato l'aggiornamento.
7. Seleziona **Install Updates** e fai clic su **Accept** per accettare l'EULA. L'aggiornamento viene installato.
8. Al termine dell'aggiornamento, devi tornare alla console di gestione del dispositivo e riavviare la console.
9. Accedi di nuovo al client web vSphere e verifica eventuali errori. Completa una scansione manuale di VUM, fai clic su **Home** > **Hosts and Cluster**, quindi seleziona un data center o un cluster e seleziona la scheda **Update Manager** e poi fai clic su **Scan for Updates**. Se la scansione manuale produce un errore, consulta [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Dopo il test, se devi annullare le modifiche, ripristina l'istantanea o ripristina il vCenter con un backup precedente.

## Istanze vCenter Server collegate SSO
{: #vum-updating-vcsa-sso-vcenter}

Se hai istanze vCenter Server primarie e secondarie, i tuoi VCSA vengono configurati in un singolo dominio SSO (Single Sign-On) di vCenter. Ogni VCSA ha un'istanza VUM distribuita. Le proprietà di configurazione che modifichi vengono applicate solo all'istanza VUM specificata e non vengono propagate alle altre istanze nel gruppo.

Puoi specificare un'istanza VUM selezionando il nome del VCSA con il quale è registrata l'istanza VUM dalla barra di navigazione. Puoi inoltre gestire le baseline, i gruppi di baseline, eseguire scansioni e correggere solo gli oggetti di inventario gestiti dal VCSA con cui è registrata l'istanza VUM.

## Link correlati
{: #vum-updating-vcsa-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (dimostrazioni)
