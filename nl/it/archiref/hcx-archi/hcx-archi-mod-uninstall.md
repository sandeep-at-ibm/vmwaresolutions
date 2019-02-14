---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modifica o disinstallazione dell'HCX

È possibile eseguire l'upgrade delle installazioni esistenti o può essere rimossa una parte o tutta una distribuzione Hybrid Cloud Services.

##  Annullamento dell'estensione di una rete di livello 2

L'annullamento dell'estensione di una rete di livello 2 è necessario prima di poter rimuovere l'applicazione virtuale del servizio del concentratore di livello 2 associato o prima di disinstallare Hybrid Cloud Services.

1. Controlla le reti estese.
2. Dalla pagina del plugin di Hybrid Cloud Services, visualizza la scheda Hybrid Services e controlla la sezione Network Extension Service. Se sono in corso dei lavori attivi o pianificati, attendi finché non vengono completati o arrestali prima di continuare.
3. Per rimuovere la rete, fai clic sull'icona Delete (la X rossa) sulla destra.
4. Fare clic su **OK** per confermare.

## Disinstallazione di applicazioni virtuali HCX

Un'applicazione del servizio può essere disinstallata per preparare la disinstallazione dell'Hybrid Cloud Services o a causa di una modifica nell'architettura di installazione. Utilizza Hybrid Cloud Services per gestire le applicazioni, come descritto nella seguente procedura.

### Prerequisiti per la disinstallazione delle applicazioni virtuali HCX

* Annulla o reimposta il tempo di esecuzione di tutte le migrazioni che possono verificarsi durante l'attività di disinstallazione.
* Controlla la console delle attività del client web vSphere per tutte le migrazioni in esecuzione e attendi finché non vengono completate.
* Assicurati che non ci sia alcun tipo di attività Hybrid Cloud Services attivo.

Non eliminare mai le applicazioni virtuali dall'inventario vSphere. Utilizza sempre il portale di gestione per interagire con le applicazioni virtuali del servizio.
{:note}

### Procedura per disinstallare le applicazioni virtuali HCX

1. Nell'interfaccia client web vSphere, seleziona il plugin Hybrid Cloud Services dal pannello di sinistra.
2. Nel pannello centrale, fai clic sulla scheda **Hybrid Services**.
3. Individua l'applicazione Hybrid Cloud Gateway e fai clic sulla voce per visualizzare i dettagli.
4. In basso a destra, fai clic sull'icona Delete per rimuovere l'applicazione.
5. Se una rete estesa non condivide un indirizzo IP con Hybrid Cloud Gateway, devi rimuoverlo separatamente. Espandi i dettagli del servizio delle estensioni di rete e fai clic sull'icona Delete per rimuovere il concentratore di livello 2.

L'Hybrid Cloud Gateway e tutte le applicazioni virtuali del servizio ibride che utilizzano l'Hybrid Cloud Gateway vengono rimossi sia dal vCenter che dal cloud VCF/VCS Hybrid Cloud Services.

## Disinstallazione dell'HCX Manager

L'applicazione HCX Manager dovrebbe essere disinstallata prima di rimuovere la soluzione HCX dal data center in loco. Segui questa procedura per disinstallare la macchina virtuale Hybrid Cloud Services.

1. Annulla l'estensione di tutte le reti di livello 2.
2. Rimuovi le applicazioni virtuali del servizio ibride.
3. Nel vCenter in loco, spegni la macchina virtuale Hybrid Cloud Services.
4. Elimina la macchina virtuale Hybrid Cloud Services.

Tutte le applicazioni del servizio virtuali vengono rimosse. Potrebbero rimanere i seguenti elementi:
* Log
* VM migrate

### Operazioni successive

I log e le VM migrate possono essere eliminati o ne può venire eseguito il backup manualmente.

## Accesso al portale di gestione HCX

La distribuzione di Hybrid Cloud Services può essere gestita dal portale di gestione utilizzando un'interfaccia utente basata sul browser.

1. In un browser web, immetti l'indirizzo IP assegnato all'Hybrid Cloud Services e specifica il numero di porta 9443. Ad esempio, `https://HCXip:9443`.
2. L'interfaccia utente di Hybrid Cloud Services viene aperta in una finestra del browser web utilizzando SSL. Se necessario, accetta il certificato di sicurezza. Si apre la schermata di accesso VMware Hybridity and Networking.
3. Immetti il nome utente e la password. Per impostazione predefinita, il nome utente è Admin. La password è il valore che è stato fornito quando è stata installata l'applicazione virtuale Hybrid Cloud Services.

### Link correlati

* [Risoluzione dei problemi di HCX on IBM Cloud](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-trbl.html)
