---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di Veeam on IBM Cloud

Il servizio Veeam on {{site.data.keyword.cloud}} si integra perfettamente con i tuoi hypervisor VMware per aiutare la tua azienda a raggiungere l'alta disponibilità. Questo servizio può fornire obiettivi di tempo e punti di ripristino per le tue applicazioni e i tuoi dati. Gli obiettivi di tempo e punti di ripristino possono essere forniti in meno di 15 minuti dopo il completamento della configurazione. Utilizzando questo servizio, puoi controllare direttamente sia il backup che il ripristino di tutte le macchine virtuali per la tua infrastruttura dalla console Veeam.

**Disponibilità**: questo servizio è disponibile solo per le istanze distribuite nelle release della V1.8 o successive.

## Componenti di Veeam on IBM Cloud

Nel servizio Veeam on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:
* Una VSI Windows Server 2016 con un indirizzo IP privato primario e un'interfaccia da 1 GbE
* {{site.data.keyword.cloud_notm}}Archiviazione a blocchi Endurance dalle dimensioni e prestazioni selezionate nel momento in cui ordini servizio

## Considerazioni sull'istallazione di Veeam on IBM Cloud

* Il servizio esegue il backup dei seguenti componenti di gestione:
  - VMware vCenter Server
  - PSC (Platform Services Controller)
  - IBM CloudDriver
  - **Solo per le istanze Cloud Foundation**: VMware SDDC Manager
  - **Solo per le istanze vCenter Server con AD/DNS HA**: coppia ad alta disponibilità di server AD/DNS

* Le configurazioni dei server ESXi non vengono sottoposte a backup dal servizio Veeam on {{site.data.keyword.cloud_notm}}.

* Per impostazione predefinita, le configurazioni del controller NSX e dell'edge NSX vengono sottoposte quotidianamente a backup utilizzando il gestore NSX con un massimo di 14 punti di ripristino. Per un ripristino completo delle configurazioni NSX, devi creare un ticket di supporto {{site.data.keyword.cloud_notm}}, perché i backup delle configurazioni NSX vengono salvati nell'archiviazione interna a {{site.data.keyword.vmwaresolutions_full}}. Per ulteriori informazioni sulla gestione dei backup di configurazione NSX utilizzando il gestore NSX, vedi le [istruzioni tecniche di VMware](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html).
* Il repository per l'archiviazione e il server Veeam si trovano nel pod e nel data center originali. Per questo motivo, le prestazioni delle operazioni di backup per i cluster remoti potrebbero ridursi.

## Considerazioni sulla rimozione di Veeam on IBM Cloud

Prima di rimuovere il servizio Veeam on {{site.data.keyword.cloud_notm}}, nota che la rimozione di questo servizio interromperà tutti i backup (incluso il backup delle VM di gestione) ed eliminerà tutti i backup precedenti (l'eliminazione è irreversibile). Se le VM di gestione vengono successivamente danneggiate, non possono essere ripristinate.

## Link correlati

* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Richiesta di servizi gestiti per Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Veeam](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
