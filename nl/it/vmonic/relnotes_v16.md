---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# Note sulla release per la V1.6

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e ulteriori suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Aggiornamenti per le istanze VMware Cloud Foundation

I seguenti componenti sono nuovi o aggiornati:

*  SDDC Manager 2.2.1
*  Componenti di gestione IBM V1.6
*  Nuove specifiche hardware: **Small** o **Standard**, a seconda dei tuoi requisiti.
*  Nuovi data center disponibili per la distribuzione: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seul**, **SNG01 - Singapore** e **SYD04 - Sydney**.

Per l'elenco completo dei componenti, vedi [Panoramica di VMware Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Aggiornamenti per le istanze VMware vCenter Server

### Miglioramenti hardware per le istanze vCenter Server

A partire dalla release della V1.6, sono disponibili numerosi miglioramenti per le tue istanze vCenter Server.

*  Implementazione completa della specifica della V2.0 per l'offerta di vCenter Server. Per ulteriori informazioni, vedi [VMware vCenter Server on {{site.data.keyword.cloud_notm}} solution architecture](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0).
*  Nuove specifiche hardware: **Small**, **Medium** o **Large**, a seconda dei tuoi requisiti.
*  Nuovi data center disponibili per la distribuzione: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seul**, **SNG01 - Singapore** e **SYD04 - Sydney**.
*  Almeno due server ESXi nel tuo ordine dell'istanza, con VMware vSphere DRS (Distributed Resource Scheduler) e VMware HA (High Availability) abilitati per impostazione predefinita.
*  È possibile aggiungere fino a sette condivisioni file NFS quando ordini le istanze. I componenti di gestione (vCenter, PSC, gestore e controller NSX, CloudDriver) vengono ora eseguiti su una condivisione file NFS per l'alta disponibilità.
*  Distribuzione e configurazione automatiche del gateway dei servizi edge VMware NSX gestito dal cliente.

A causa di queste modifiche, non puoi utilizzare così come sono (o aggiornare) le tue istanze vCenter Server esistenti nella release corrente. Le istanze vCenter Server delle release precedenti alla V1.6 sono ancora visibili sulla console {{site.data.keyword.vmwaresolutions_short}} in modalità di sola visualizzazione. Queste istanze sono contrassegnate nell'interfaccia utente come **Obsolete** con un'icona del simbolo di avvertenza.

Sulle istanze vCenter Server precedenti alla V1.6 sono disponibili le seguenti azioni:

*  Visualizzare le informazioni nella pagina dei dettagli dell'istanza. Le informazioni visualizzate nelle proprietà dell'istanza riflettono i dati a partire dalla data di rilascio della V1.6 e non vengono più aggiornate.
*  Aprire il client web VMware vSphere e utilizzare l'istanza in vCenter.
*  Eliminare l'istanza.

Tutte le altre azioni sulle istanze precedenti alla V1.6 non sono più disponibili.

### Miglioramenti della rete per le istanze vCenter Server

*  Una sottorete pubblica con 16 indirizzi IP sulla VLAN pubblica viene ordinata per tuo conto per consentire alle tue VM (macchine virtuali) di accedere a Internet.
*  Una sottorete privata con 64 indirizzi IP sulla VLAN privata viene ordinata per tuo conto per consentire alle tue VM di accedere alla rete interna SoftLayer®.
*  I controller NSX vengono distribuiti con regole di anti-affinità ed eseguiti su server ESXi separati in una configurazione di distribuzione a 3 nodi.
*  Nuovo gateway dei servizi edge VMware NSX per l'utilizzo da parte del cliente.

   Viene distribuito un ulteriore gateway dei servizi edge (ESG) NSX come parte delle nuove istanze vCenter Server che stai ordinando.

   Questo ESG viene fornito per essere utilizzato con le tue VM per le comunicazioni tra le sottoreti private e pubbliche ordinate per tuo
   conto e include due interfacce: un'interfaccia è connessa alle VXLAN virtualizzate associate alle tue VM e
   l'altra è connessa alla VLAN pubblica. Inoltre, sono configurate le seguenti impostazioni:
   *  Regola del firewall per consentire tutto il traffico in uscita dall'intervallo di indirizzi IP della sottorete privata.
   *  Regola SNAT (Source Network Address Translation) (disabilitata per impostazione predefinita) per tradurre tutti gli indirizzi IP dalla sottorete privata in un
   singolo indirizzo IP sulla sottorete pubblica.
   * VMware HA (High Availability) è configurato per utilizzare un nuovo gruppo di porte condiviso tra l'ESG di gestione e l'ESG gestito
   dal cliente.

   Questo ESG viene distribuito per tutti i tipi di hardware dell'istanza e i clienti possono modificare la configurazione. Per ulteriori informazioni, vedi i
   seguenti argomenti:
   *  [Configurazione della rete per utilizzare l'ESG NSX gestito dal cliente con le tue VM](../vcenter/vc_esg_config.html)
   *  [Documentazione di VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Miglioramenti dell'usabilità

Sono stati apportati miglioramenti in tutta l'interfaccia utente:

*  La navigazione principale sulla console è notevolmente migliorata attraverso l'introduzione del riquadro di navigazione a sinistra con accesso a tutte le aree dell'interfaccia utente. Puoi rapidamente ordinare una nuova istanza, visualizzare le tue istanze distribuite, rivedere le notifiche di sistema, modificare le impostazioni e accedere alla documentazione in linea.
*  La nuova pagina **Introduzione** accessibile dal riquadro di navigazione a sinistra ti fornisce dettagli sufficienti direttamente sulla console per aiutarti a prendere una decisione consapevole sui componenti dell'istanza che stai ordinando. Nella pagina **Introduzione**, sei anche guidato passo dopo passo nel processo di ordine di un'istanza, iniziando con soddisfare tutti i prerequisiti per ordinare un'istanza, come gli account utente richiesti, e terminando con effettuare un ordine.
*  I dettagli di riepilogo per le istanze Cloud Foundation e vCenter Server sono consolidati in un'unica pagina, accessibile dal menu **Istanze distribuite** nel riquadro di navigazione a sinistra. Da questa pagina, puoi selezionare la scheda appropriata per filtrare le istanze Cloud Foundation o le istanze vCenter Server.
* Se sulla tua istanza è installato il ripristino di emergenza Zerto, puoi accedere direttamente alla console Zerto dalla pagina dei dettagli del servizio con un solo clic. Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html) e [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html).
