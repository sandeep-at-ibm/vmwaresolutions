---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Aggiornamento delle tue istanze dalle release precedenti alla V1.4

## Problema

La topologia di rete dell'istanza nelle release della V1.4 e successive è diversa da quella delle release precedenti alla V1.4. A causa di questa modifica, le istanze che sono state distribuite nelle release precedenti alla V1.4 non possono essere utilizzate nel loro stato nella release corrente.

## Risoluzione

Nelle release della V1.4 e successive, sono disponibili numerosi miglioramenti della topologia di rete per le tue istanze:
* (Si applica a tutte le istanze): configurazione di rete ottimizzata. Poiché l'account {{site.data.keyword.cloud}} che stai utilizzando deve essere un account VRF (Virtual Routing and Forwarding) o deve avere lo spanning della VLAN abilitato se si tratta di un account classico (non VRF), non è necessario un secondo indirizzo IP portatile. Per la distribuzione è richiesto solo l'indirizzo IP primario portatile dell'infrastruttura {{site.data.keyword.cloud_notm}}.
* (Si applica solo alle istanze Cloud Foundation): funzionalità di distribuzione multisito con i server Microsoft Windows AD SSO (Active Directory Single Sign-On) e Domain Name System (DNS).

Se non hai migrato o eliminato le tue istanze dalle release precedenti alla V1.4, potrebbero essere ancora visibili sulla console {{site.data.keyword.vmwaresolutions_short}} in modalità di sola visualizzazione. Queste istanze sono contrassegnate nell'interfaccia utente come **Obsolete** con un'icona del simbolo di avvertenza.

**Nota:** le informazioni visualizzate nelle proprietà dell'istanza riflettono i dati a partire dalla data di rilascio della V1.4 e non vengono più aggiornate.

Sulle istanze precedenti alla V1.4 sono disponibili le seguenti azioni:
*  Visualizzare le informazioni nella pagina dei dettagli dell'istanza.
*  Visualizzare le informazioni di backup dell'istanza.
*  Aprire il client web vSphere e utilizzare l'istanza in vCenter.
*  Richiedere il ripristino dell'istanza aprendo un ticket di supporto {{site.data.keyword.cloud_notm}}.
*  Eliminare l'istanza.

Tutte le altre azioni sulle istanze precedenti alla V1.4 non sono più disponibili.

Se hai istanze precedenti alla V1.4 e intendi continuare a utilizzarle, puoi aggiornarle creando nuove istanze e spostando le tue configurazioni esistenti in queste nuove istanze.

Per spostare le tue istanze precedenti alla V1.4 in nuove istanze, completa la seguente procedura nel client web vSphere:
1. Dalla tua istanza precedente alla V1.4, esporta tutte le VM (macchine virtuali).
2. Crea un'istanza nella release corrente.
3. Importa tutte le VM esportate dal **Passo 1**.
4. Utilizza la tua nuova istanza.

Per ulteriori informazioni sull'esportazione e importazione delle VM, consulta la tua documentazione di VMware vSphere.

Se hai bisogno di assistenza con {{site.data.keyword.vmwaresolutions_short}}, [contatta il supporto IBM](trbl_support.html) attraverso uno dei canali di supporto.
