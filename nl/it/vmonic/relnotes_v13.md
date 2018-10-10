---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# Note sulla release per la V1.3

Questa release include nuove funzioni, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Archiviazione a livello di file condivisa per le istanze vCenter Server

Puoi ora aggiungere il NAS (Network Attached Storage) condiviso alle istanze vCenter Server. L'aggiunta di questa funzione ti consente di eseguire carichi di lavoro di produzione su vCenter Server e di impedire la perdita di dati in caso di errori del nodo. Il File Storage NFS (Network File System) viene fornito come opzione nel processo di ordine per le istanze vCenter Server. Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html).

## Rimozione del ripristino di emergenza Zerto

Sia che tu abbia ordinato il ripristino di emergenza Zerto come parte della tua istanza o l'abbia aggiunto a un'istanza esistente, puoi ora rimuovere questo servizio quando non ne hai più bisogno. Dopo aver richiesto di rimuovere il servizio dalla console, verrai guidato dal supporto IBM per completare il processo di rimozione.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Rimozione del ripristino di emergenza](../services/removingzertodr.html)
* [Visualizzazione delle istanze Cloud Foundation](../sddc/sd_viewinginstances.html)
* [Visualizzazione delle istanze vCenter Server](../vcenter/vc_viewinginstances.html)

## Edge NSX VMware per le istanze Cloud Foundation

Edge NSX è ora incluso come parte delle nuove istanze Cloud Foundation che stai ordinando. Edge NSX fornisce i servizi gateway e di sicurezza edge della rete per isolare una rete virtualizzata.

Durante la distribuzione dell'istanza, un gateway dei servizi edge (ESG) NSX di gestione viene distribuito da IBM. Questo ESG viene utilizzato dalle macchine virtuali di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. L'ESG è distribuito per includere due interfacce: un'interfaccia è connessa alla VLAN privata di {{site.data.keyword.cloud_notm}} e l'altra è connessa alla VLAN pubblica di {{site.data.keyword.cloud_notm}}.

Per garantire la sicurezza, vengono implementate regole del firewall per consentire solo le comunicazioni HTTPS in uscita avviate dalle macchine virtuali di
gestione. Questo ESG viene distribuito in una configurazione di tipo Large e solo il supporto IBM può modificare la configurazione.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Specifiche tecniche per le istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentazione di VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Processo di ordine dell'istanza

Il processo di ordine è stato migliorato sia per le istanze Cloud Foundation che per le istanze vCenter Server:

* Nella pagina di riepilogo vengono visualizzati tutti i termini e le condizioni applicabili per tutti i componenti e i servizi ordinati, per un facile accesso alla revisione e all'accettazione di questi termini prima di effettuare l'ordine.
* Puoi salvare e stampare il riepilogo dell'ordine per l'istanza prima di effettuare l'ordine. Con questa nuova funzione, puoi rivedere le impostazioni e il costo dell'istanza, modificare i componenti ordinati laddove necessario, ottenere l'approvazione e quindi tornare al tuo ordine.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)

## Gestione dell'istanza

Il processo di gestione dell'istanza include nuove funzioni e miglioramenti:

* Sia per le istanze Cloud Foundation che per le istanze vCenter Server, puoi visualizzare ed esaminare il costo stimato dei tuoi server ESXi prima di decidere di aggiungerli all'istanza. Dopo aver specificato quanti server vuoi aggiungere, il costo stimato per server, al mese, viene visualizzato sulla console. Per ulteriori informazioni, vedi [Espansione e contrazione della capacità per le istanze Cloud Foundation](../sddc/sd_addingremovingservers.html) e [Espansione e contrazione della capacità per le istanze vCenter Server](../vcenter/vc_addingremovingservers.html).
* Sia per le istanze Cloud Foundation che per le istanze vCenter Server, il numero totale di istanze è visualizzato nella parte superiore della pagina di riepilogo. Dalle pagine di riepilogo dell'istanza puoi anche ordinare un'istanza con un clic. Inoltre, nella pagina di riepilogo puoi visualizzare lo stato dell'ordine dettagliato durante il provisioning. Quando passi con il mouse sullo stato che viene visualizzato, puoi visualizzare ulteriori dettagli sul passo corrente o sull'eventuale errore.
* Per le istanze Cloud Foundation, la pagina dei dettagli dell'istanza visualizza la cronologia di distribuzione dell'istanza, con le informazioni sullo stato di distribuzione passo dopo passo. Per ulteriori informazioni, vedi [Visualizzazione delle istanze Cloud Foundation](../sddc/sd_viewinginstances.html).
* Per le istanze Cloud Foundation, l'usabilità del processo di aggiornamento e patch è stata migliorata fornendo ulteriori dettagli sull'aggiornamento nella pagina **Aggiorna e applica patch**, come: il tempo di inattività necessario per una patch, il tempo per cui è stato programmato l'aggiornamento e l'indicazione visiva di quando è necessario applicare una patch richiesta prima di quella corrente. Per ulteriori informazioni, vedi [Applicazione di aggiornamenti e patch alle istanze Cloud Foundation](../sddc/sd_applyingupdates.html).

## Notifiche e-mail

Ora ricevi una notifica via e-mail quando viene effettuato un nuovo ordine per la distribuzione dell'istanza e quando un servizio viene aggiunto, distribuito o rimosso dalla tua istanza. Le impostazioni di notifica sono abilitate per impostazione predefinita. In base alle tue preferenze, puoi impostare le notifiche che desideri ricevere nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](useraccount.html).
