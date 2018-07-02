---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di HyTrust CloudControl on IBM Cloud

Il servizio HyTrust CloudControl on {{site.data.keyword.cloud}} applica e controlla la conformità rispetto agli standard di sicurezza e fornisce funzionalità dettagliate di controllo degli accessi in base al ruolo (RBAC), approvazione e verifica. Se combinato con HyTrust DataControl, il servizio può garantire che le macchine virtuali e i dati del carico di lavoro non lascino una particolare regione, cluster o server ESXi all'interno del {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilità:** questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive.

## Componenti di HyTrust CloudControl on IBM Cloud

Una coppia di dispositivi HyTrust CloudControl (HTCC) ad alta disponibilità (HA) viene distribuita sul cluster predefinito in modalità attiva-passiva.

Ogni coppia di dispositivi HTCC viene distribuita sulla stessa sottorete portatile privata specificata per le macchine virtuali (VM) di gestione, come il gestore NSX, i dispositivi vCenter Server Appliance e Platform Services Controller. La coppia di dispositivi funge da proxy per gli host vSphere, il dispositivo vCenter Server e il gestore NSX di un'istanza. Pertanto, gli utenti accedono agli host vSphere, al dispositivo vCenter Server e al gestore NSX tramite un indirizzo IP pubblicato (PIP) assegnato dall'amministratore anziché l'indirizzo IP reale (RIP) assegnato da IBM Cloud.

I dispositivi HTCC si integrano con Microsoft Active Directory per applicare il controllo degli accessi basato sui ruoli.

## Considerazioni sulla rimozione di HyTrust CloudControl on IBM Cloud

Prima di rimuovere il servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, assicurati di disabilitare l'**Archiviazione della password root**, se configurata, e di eliminare tutti gli host protetti da CloudControl.

## Link correlati

* [Ordine di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestione di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web HyTrust](https://www.hytrust.com/)
