---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Migrazione di una macchina virtuale
{: #hcx-archi-migrate-vm}

HCX abilita la migrazione bidirezionale: dal locale al cloud o dal cloud al data center in loco. HCX utilizza la tecnologia di replica durante il processo di migrazione. La tecnologia di replica è integrata nell'applicazione virtuale Hybrid Cloud Gateway. Non è necessaria l'installazione di un ulteriore software di replica.

## Migrazione con basso tempo di inattività

La migrazione con basso tempo di inattività utilizza la replica basata sull'host per spostare una macchina virtuale live da un vCenter a un data center virtuale o nella direzione opposta. Per ridurre il tempo di inattività, la VM di origine rimane online durante la replica e ne viene eseguito il bootstrap sull'host ESX di destinazione dopo il completamento della replica.

1. Una richiesta di migrazione attiva le seguenti azioni:
  * La replica avvia un trasferimento della sincronizzazione completa in un data center virtuale VCF/VCS HCX. Il tempo necessario per la replica dipende dalla dimensione della VM e alla larghezza di banda disponibile.
  * Il consumo della larghezza di banda della replica varia in base a come il carico di lavoro modifica i blocchi sul disco.
2. Quando viene completata una sincronizzazione completa, si verifica una sincronizzazione delta.
3. Quando viene completata la sincronizzazione delta, HCX attiva un cambio. Il cambio può iniziare immediatamente o in modo pianificato in un momento specifico.
4. Dopo il cambio, la VM di origine viene spenta e viene accesa la replica migrata. Se per qualche motivo la VM non può essere accesa, viene spenta la nuova VM (o rimane spenta) e viene accesa quella originale.
5. HCX ridenomina la VM originale spenta per evitare un conflitto di denominazione con la VM migrata e accoda una data/ora binaria al nome della VM originale.
6. Se non è stato specificato di abilitare **Retain MAC**, la VM migrata ottiene un nuovo indirizzo MAC.
7. La migrazione è terminata. Hybrid Cloud Services copia la VM originale nella cartella **Migrated VMs** nella vista vSphere Templates.

## vMotion senza tempo di inattività
{: #hcx-archi-migrate-vm-no-downtime-vm}

vMotion trasferisce una macchina virtuale live da un vSphere vCenter a un cloud VCF/VCS. Questo vMotion richiede una rete estesa. Il trasferimento vMotion acquisisce la memoria attiva della macchina virtuale e i relativi stato di esecuzione, indirizzo IP e indirizzo MAC.

La versione hardware della macchina virtuale deve essere almeno alla 9 o il vMotion tra cloud potrebbe non riuscire.
{:note}

## Migrazione di tipo cold (a freddo)
{: #hcx-archi-migrate-vm-cold-mig}

La migrazione di tipo cold (a freddo) utilizza lo stesso piano di dati del vMotion tra cloud per trasferire una macchina virtuale spenta su una rete estesa. I relativi indirizzi IP e MAC vengono conservati. I requisiti e le limitazioni della macchina virtuale sono gli stessi del vMotion.

### Migrazione delle VM utilizzando la procedura guidata bidirezionale
{: #hcx-archi-migrate-vm-mig-bidir-wiz}

Utilizzando il client web vSphere, è possibile accedere alla procedura guidata bidirezionale dalla scheda Getting Started dell'Hybrid Cloud Services. Questa procedura guidata gestisce tutti i dettagli della migrazione, incluse più macchine virtuali.

Dal client web vSphere, è possibile accedere alla procedura guidata bidirezionale dalla scheda Getting Started dell'Hybrid Cloud Services. Questa procedura guidata gestisce tutti i dettagli della migrazione, incluse più macchine virtuali.
* Da vSphere a VCF/VCS Hybrid Cloud Services
* Da VCF/VCS HCX Cloud a vSphere

### Verifica delle VM prima della migrazione
{: #hcx-archi-migrate-vm-check-vms}

Per migrare una macchina virtuale, deve essere mantenuta una connessione sicura dall'Hybrid Cloud Gateway e la VM deve soddisfare i seguenti requisiti:
* La macchina virtuale deve essere accesa.
* L'architettura sottostante deve essere x86, indipendentemente dal sistema operativo.
* Per utilizzare la migrazione vMotion, la versione hardware deve essere superiore alla 9.
* La versione hardware deve essere inferiore alla 10.
* Le VM con l'associazione al disco non formattato nella modalità di compatibilità possono essere migrate.

Le VM con i seguenti attributi non sono supportate per la migrazione:
* Superiori a 2 TB.
* Che condividono i file VMDK.
* Che hanno un supporto virtuale o ISO allegato.
* Con la versione hardware inferiore alla 9.

### Monitoraggio di una migrazione
{: #hcx-archi-migrate-vm-monitor-mig}

L'avanzamento di una migrazione basata sulla replica può essere monitorato dall'interfaccia utente o dalla riga di comando. Visualizza la console delle attività, come descritto in Monitorare la distribuzione dell'applicazione del servizio e cerca l'attività **Migrate VM**. Quando lo stato è **Completed**, la VM viene migrata e accesa.

Questa procedura utilizza una VM non correlata nello stesso vCenter per tenere traccia dell'avanzamento di una VM migrata.

1. Identifica la VM da migrare e scegli una VM di osservazione che può eseguire il ping della VM in migrazione.
2. Dall'interfaccia utente, avvia la migrazione della VM e monitorala dalla console delle attività.
3. Utilizzando SSH, accedi all'host ESXi che esegue la VM di osservazione.
4. Immetti il seguente comando per ottenere l'ID della VM (il vmid):

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. Immetti i seguenti comandi per monitorare lo stato della replica, dove il vmid è il valore ottenuto nel passo precedente:

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. Ping di ICMP - Monitora il ping continuo avviato precedentemente.

Potrebbe verificarsi un'interruzione nel ping continuo durante il cambio. Tuttavia, il ping di test riprende rapidamente dopo il completamente dell'attività **Migrate VM**, come risulta dalla console delle attività.

### Visualizzazione delle VM migrate
{: #hcx-archi-migrate-vm-view-vms}

Quando Hybrid Cloud Services accende una macchina virtuale migrata correttamente, spegne la VM originale e la archivia in una cartella nel vCenter. Le macchine virtuali archiviate sono conservate finché non vengono eliminate manualmente.

Dopo la migrazione, controlla il vCenter e prendi nota delle cartelle etichettate **VMs migrated from the cloud** e **VMs migrated to the cloud**.
* Come per le repliche, le VM spente hanno il nome originale, con una data/ora binaria accodata.
* Le VM migrate possono essere trattate come qualsiasi altra VM. Ad esempio, possono essere spostate in un'ubicazione diversa e accese.
* Le VM non desiderate all'interno di queste cartelle possono essere eliminate.
* L'eliminazione è definitiva, a meno che non sia in atto una soluzione di backup.

## Link correlati
{: #hcx-archi-migrate-vm-related}

* [Modifica o disinstallazione dell'HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
