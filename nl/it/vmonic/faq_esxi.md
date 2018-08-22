---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-17"

---

# Domande frequenti sui server ESXi

Trova le risposte alle domande frequenti sui server ESXi gestiti nella console {{site.data.keyword.vmwaresolutions_full}}.

## Quanti server ESXi posso aggiungere alla mia istanza?

* Per le istanze vCenter Server, puoi espandere il cluster predefinito per avere fino a 51 server ESXi. Ciascuno dei cluster non predefiniti può essere espanso per avere fino a 59 server ESXi. Dal momento che puoi aggiungere fino a 10 cluster a un'istanza, ciascuna istanza distribuita può avere un massimo di 51 + 9x59 = 582 server ESXi tra tutti i cluster.
* Per le istanze Cloud Foundation, la configurazione standard ha quattro server ESXi. Puoi aggiungere un massimo di 28 server (per un totale di 32 server). Per le istanze Cloud Foundation in una configurazione multisito, puoi avere un massimo di 128 server ESXi tra tutte le istanze.

  **Nota**: se la tua configurazione di Cloud Foundation richiede una distribuzione multisito con più di 128 server ESXi, [contatta il supporto IBM](trbl_support.html) per assistenza.

## Quanti server ESXi posso aggiungere a un cluster?

Per le release della V2.2 e successive, puoi aggiungere un massimo di 51 server ESXi a un cluster iniziale e un massimo di 59 server ESXi ai cluster aggiuntivi.

Per le istanze distribuite nelle release della V2.1 o precedenti, devi abilitare il supporto vSAN necessario per aumentare la dimensione del cluster a più di 32. Completa la seguente procedura per abilitare il supporto vSAN necessario:

1. Su ciascun server ESXi distribuito, immetti i seguenti comandi:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Riavvia ogni server ESXi. Per ulteriori informazioni, vedi [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Nota che potresti dover aumentare le dimensioni di vCenter Server per ospitare ulteriori macchine virtuali e server ESXi.
4. Apri un ticket di supporto IBM indicando che hai applicato manualmente le modifiche vSAN completando i passi da 1 a 3 e che vuoi abilitare la tua istanza aggiornata ad avere più di 32 server ESXi aggiuntivi.

## Posso modificare i nomi e gli indirizzi IP del server ESXi?

I nomi e gli indirizzi IP dei server ESXi non possono essere modificati perché sono registrati per la risoluzione DNS di Windows. Le modifiche potrebbero causare errori durante la distribuzione o errori nelle funzioni di vCenter Server.

**Nota**: non utilizzare la funzione **Rinomina dispositivo** sull'interfaccia utente di {{site.data.keyword.cloud_notm}} per modificare i nomi dei server ESXi. Questa funzione modificherà effettivamente il nome di dominio completo del server ESXi, ma le registrazioni degli host della VSI di Windows e vCenter Center configurate non saranno corrette e potrebbero causare errori.

## Posso disabilitare l'accesso root sui miei server ESXi?

Si consiglia di mantenere l'accesso root abilitato sui server ESXi, altrimenti potrebbero verificarsi errori nelle funzionalità di {{site.data.keyword.vmwaresolutions_short}}.

Se assolutamente necessario, puoi disabilitare l'accesso root dopo che i server ESXi passano allo stato **Pronto per l'utilizzo** sulla console {{site.data.keyword.vmwaresolutions_short}}.

Devi riabilitare l'accesso root per le successive operazioni di automazione, ad esempio durante l'aggiunta o rimozione di condivisioni file o durante l'installazione di servizi aggiuntivi, come Zerto on {{site.data.keyword.cloud_notm}}.

## Posso aggiungere rotte statiche sui miei server ESXi per montare l'archiviazione da altre ubicazioni?

È possibile aggiungere le rotte statiche per l'archiviazione, ma le operazioni devono essere eseguite con estrema attenzione. Altrimenti, le condivisioni esistenti potrebbero essere smontate.

**Nota**: l'aggiunta di rotte statiche per vMotion non è supportata. Le modifiche alla configurazione della sottorete di vMotion potrebbero causare errori nelle funzionalità di {{site.data.keyword.vmwaresolutions_short}}.

### Link correlati

* [Espansione e contrazione della capacità per le istanze vCenter Server](../vcenter/vc_addingremovingservers.html)
* [Espansione e contrazione della capacità per le istanze Cloud Foundation](../sddc/sd_addingremovingservers.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze Cloud Foundation](../sddc/sd_addingviewingclusters.html)
* [Come contattare il supporto IBM](trbl_support.html)
