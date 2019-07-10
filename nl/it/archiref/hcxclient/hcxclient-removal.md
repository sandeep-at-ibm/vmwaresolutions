---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Modifica o disinstallazione dell'HCX
{: #hcxclient-removal-uninstall}

È possibile eseguire l'upgrade delle installazioni esistenti o può essere rimossa una parte o tutta una distribuzione Hybrid Cloud Services.

##  Annullamento dell'estensione di una rete di livello 2
{: #hcxclient-removal-uninstall-unstretch-layer2}

L'annullamento dell'estensione di una rete di livello 2 è necessario prima di poter rimuovere il dispositivo virtuale del servizio del concentratore di livello 2 associato o prima di disinstallare Hybrid Cloud Services.

1. Controlla le reti estese.
2. Dalla pagina del plugin di Hybrid Cloud Services, visualizza la scheda Hybrid Services e controlla la sezione Network Extension Service. Se sono in corso dei lavori attivi o pianificati, attendi finché non vengono completati o arrestali prima di continuare.
3. Per rimuovere la rete, fai clic sull'icona Delete (la X rossa) sulla destra.
4. Fare clic su **OK** per confermare.

## Disinstallazione di dispositivi virtuali HCX
{: #hcxclient-removal-uninstall-uninst-hva}

Un dispositivo del servizio può essere disinstallato per preparare la disinstallazione dell'Hybrid Cloud Services o a causa di una modifica nell'architettura di installazione. Utilizza Hybrid Cloud Services per gestire i dispositivi, come descritto nella seguente procedura.

### Prerequisiti per la disinstallazione dei dispositivi virtuali HCX
{: #hcxclient-removal-uninstall-prereq-uninst-hva}

* Annulla o reimposta il tempo di esecuzione di tutte le migrazioni che possono verificarsi durante l'attività di disinstallazione.
* Controlla la console delle attività del client web vSphere per tutte le migrazioni in esecuzione e attendi finché non vengono completate.
* Assicurati che non ci sia alcun tipo di attività Hybrid Cloud Services attivo.

Non eliminare mai i dispositivi virtuali dall'inventario vSphere. Utilizza sempre il portale di gestione per interagire con i dispositivi virtuali del servizio.
{:note}

### Procedura per disinstallare i dispositivi virtuali HCX
{: #hcxclient-removal-uninstall-proc-uninst-hva}

1. Nell'interfaccia client web vSphere, seleziona il plugin Hybrid Cloud Services dal pannello di sinistra.
2. Nel pannello centrale, fai clic sulla scheda **Hybrid Services**.
3. Individua il dispositivo Hybrid Cloud Gateway e fai clic sulla voce per visualizzare i dettagli.
4. In basso a destra, fai clic sull'icona Delete per rimuovere il dispositivo.
5. Se una rete estesa non condivide un indirizzo IP con Hybrid Cloud Gateway, devi rimuoverlo separatamente. Espandi i dettagli del servizio delle estensioni di rete e fai clic sull'icona Delete per rimuovere il concentratore di livello 2.

L'Hybrid Cloud Gateway e tutti i dispositivi virtuali del servizio ibridi che utilizzano l'Hybrid Cloud Gateway vengono rimossi sia dal vCenter che dal cloud VCS Hybrid Cloud Services.

## Disinstallazione dell'HCX Manager
{: #hcxclient-removal-uninstall-unist-hcxm}

Il dispositivo HCX Manager dovrebbe essere disinstallato prima di rimuovere la soluzione HCX dal data center in loco. Segui questa procedura per disinstallare la VM (Virtual Machine) Hybrid Cloud Services.

1. Annulla l'estensione di tutte le reti di livello 2.
2. Rimuovi i dispositivi virtuali del servizio ibridi.
3. Nel vCenter in loco, spegni la VM (Virtual Machine) Hybrid Cloud Services.
4. Elimina la VM (Virtual Machine) Hybrid Cloud Services.

Tutti i dispositivi del servizio virtuali vengono rimossi. Potrebbero rimanere i seguenti elementi:
* Log
* VM migrate

### Operazioni successive
{: #hcxclient-removal-uninstall-what-next}

I log e le VM migrate possono essere eliminati o ne può venire eseguito il backup manualmente.

## Accesso al portale di gestione HCX
{: #hcxclient-removal-uninstall-log-hcxmp}

La distribuzione di Hybrid Cloud Services può essere gestita dal portale di gestione utilizzando un'interfaccia utente basata sul browser.

1. In un browser web, immetti l'indirizzo IP assegnato all'Hybrid Cloud Services e specifica il numero di porta 9443. Ad esempio, `https://HCXip:9443`.
2. L'interfaccia utente di Hybrid Cloud Services viene aperta in una finestra del browser web utilizzando SSL. Se necessario, accetta il certificato di sicurezza. Si apre la schermata di accesso VMware Hybridity and Networking.
3. Immetti il nome utente e la password. Per impostazione predefinita, il nome utente è Admin. La password è il valore che è stato fornito quando è stato installato il dispositivo virtuale Hybrid Cloud Services.

## Link correlati
{: #hcxclient-removal-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
