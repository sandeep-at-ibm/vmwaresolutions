---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Domande frequenti sui server ESXi
{: #faq_esxi}

Trova le risposte alle domande frequenti sui server ESXi gestiti nella console {{site.data.keyword.vmwaresolutions_full}}.

## Quanti server ESXi posso aggiungere alla mia istanza?
{: #faq_esxi-instance}
{: faq}

* Per le istanze vCenter Server, puoi espandere il cluster predefinito per avere fino a 51 server ESXi. Ciascuno dei cluster non predefiniti può essere espanso per avere fino a 59 server ESXi. Dal momento che puoi aggiungere fino a 10 cluster a un'istanza, ciascuna istanza distribuita può avere un massimo di 51 + 9x59 = 582 server ESXi tra tutti i cluster.
* Per le istanze Cloud Foundation, la configurazione standard ha quattro server ESXi. Puoi aggiungere un massimo di 28 server (per un totale di 32 server). Per le istanze Cloud Foundation in una configurazione multisito, puoi avere un massimo di 128 server ESXi tra tutte le istanze.

  Se la tua configurazione di Cloud Foundation richiede una distribuzione multisito con più di 128 server ESXi, [contatta il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) per richiedere assistenza.
  {:note}

## Quanti server ESXi posso aggiungere a un cluster?
{: #faq_esxi-cluster}
{: faq}

Per le istanze distribuite nella V2.2 e successive, puoi aggiungere un massimo di 51 server ESXi a un cluster iniziale e un massimo di 59 server ESXi ai cluster aggiunti.

Per le istanze distribuite nella V2.1 o precedenti, devi abilitare il supporto vSAN necessario per aumentare la dimensione del cluster a più di 32. Completa la seguente procedura per abilitare il supporto vSAN necessario:

1. Su ciascun server ESXi distribuito, immetti i seguenti comandi:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Riavvia ogni server ESXi. Per ulteriori informazioni, vedi [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Potresti dover aumentare le dimensioni di vCenter Server per ospitare le VM (Virtual Machine) e i server ESXi aggiunti.
4. Apri un ticket di supporto IBM per indicare che hai applicato manualmente le modifiche vSAN completando i passi da 1 a 3. Nel ticket, richiedi che la tua istanza aggiornata sia abilitata per avere più di 32 server ESXi.

## Posso modificare i nomi e gli indirizzi IP del server ESXi?
{: #faq_esxi-change-name-ip}
{: faq}

I nomi e gli indirizzi IP del server ESXi non possono essere modificati perché sono registrati per la risoluzione DNS di Windows. Le modifiche potrebbero comportare un errore durante la distribuzione o un errore delle funzioni di vCenter Server.

Non utilizzare la funzione **Rinomina dispositivo** sull'interfaccia utente di {{site.data.keyword.cloud_notm}} per modificare i nomi dei server ESXi. Questa funzione modifica il nome di dominio completo del server ESXi, ma le registrazioni degli host di vCenter Server e della VSI di Windows configurate non saranno corrette e potrebbero causare errori.
{:note}

## Posso disabilitare l'accesso root sui miei server ESXi?
{: #faq_esxi-disable-root}
{: faq}

Si consiglia di mantenere l'accesso root abilitato sui server ESXi, altrimenti si potrebbe verificare un errore nelle funzioni di {{site.data.keyword.vmwaresolutions_short}}.

Se necessario, puoi disabilitare l'accesso root dopo che i server ESXi passano allo stato **Pronto per l'utilizzo** sulla console {{site.data.keyword.vmwaresolutions_short}}.

Devi riabilitare l'accesso root per le successive operazioni di automazione, ad esempio, quando aggiungi o rimuovi le condivisioni file o quando installi servizi aggiuntivi, come Zerto on {{site.data.keyword.cloud_notm}}.

## Posso aggiungere rotte statiche sui miei server ESXi per montare l'archiviazione da altre ubicazioni?
{: #faq_esxi-static-routes}
{: faq}

Puoi aggiungere rotte statiche per l'archiviazione, ma dovrai farlo con estrema cautela. Altrimenti, le condivisioni esistenti potrebbero essere smontate.

L'aggiunta di rotte statiche per vMotion non è supportata. Le modifiche nella configurazione della sottorete di vMotion potrebbe causare un errore nelle funzioni di {{site.data.keyword.vmwaresolutions_short}}.
{:note}

## Link correlati
{: #faq_esxi-related}

* [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
