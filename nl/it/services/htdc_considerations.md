---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di HyTrust DataControl on IBM Cloud

Il servizio HyTrust DataControl on {{site.data.keyword.cloud}} offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio può fornire la crittografia sia a livello di sistema operativo che a livello di dati, il che significa che è possibile crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.

**Disponibilità:** questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive.

## Componenti di HyTrust DataControl on IBM Cloud

Una coppia di dispositivi HyTrust DataControl (HTDC) ad alta disponibilità (HA) viene distribuita sul cluster predefinito in modalità attiva-attiva. I dispositivi HTDC sono concessi in licenza per fornire la funzionalità HyTrust KeyControl ai tuoi carichi di lavoro.

Ogni coppia di dispositivi HTDC viene distribuita sulla stessa sottorete portatile specificata per le macchine virtuali (VM) di gestione, come il gestore NSX, i dispositivi vCenter Server Appliance e Platform Services Controller. I dispositivi vengono instradati tramite i BCR (backend customer router) {{site.data.keyword.cloud_notm}} e vengono assegnati al gateway associato alla sottorete delle VM di gestione. Inoltre, i dispositivi vengono posizionati nell'archiviazione predefinita del cluster predefinito.

## Considerazioni sulla rimozione di HyTrust DataControl on IBM Cloud

Prima di rimuovere il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}}, assicurati di aver crittografato o eseguito il backup di tutti i dischi da DataControl. Dopo aver rimosso il servizio, le chiavi potrebbero essere eliminate e potresti essere bloccato dalle tue VM.

## Link correlati

* [Ordine di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestione di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web HyTrust](https://www.hytrust.com/)
