---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Risoluzione dei problemi di HCX
{: #hcxclient-troubleshooting}

Esamina le informazioni di seguito riportate per i problemi comuni di HCX e le correzioni.

## Problemi dell'interfaccia utente client HCX
{: #hcxclient-troubleshooting-hcx-client-issues}

### Timeout del token dell'interfaccia utente HCX
{: #hcxclient-troubleshooting-hcx-ui-issues}

Di norma, se l'IU (interfaccia utente) vCenter viene lasciata aperta per qualche tempo, potresti riscontrare un timeout nell'IU HCX. Ciò è dovuto al fatto che si è verificato un timeout del token di accesso per il server di HCX Manager. Disconnettiti dall'IU web vSphere ed esegui nuovamente l'accesso per aggiornare il token.

### L'IU client HCX visualizza “NaN” per tutte le metriche nella schermata del dashboard
{: #hcxclient-troubleshooting-nan-display}

Questo problema è correlato alle autorizzazioni dell'account vCenter attualmente collegato. Assicurati che il gruppo Enterprise Administrator sia impostato nell'IU del gestore del dispositivo lato cloud HCX.

## Problemi di migrazione
{: #hcxclient-troubleshooting-mig-issues}

I problemi di migrazione nelle attuali versioni di HCX sono di solito in tre categorie: licenze, connettività di rete del gateway cloud e compatibilità dell'hardware di destinazione.

### Licenze
{: #hcxclient-troubleshooting-licensing}

Se una migrazione non riesce a causa di un problema di licenze, le attuali versioni di HCX visualizzano chiaramente questo problema nel messaggio di errore con l'IU web client all'interno dell'IU vCenter.

### Connettività di rete (WAN)
{: #hcxclient-troubleshooting-wan-connect}

Se si verifica un problema con la connettività WAN, controlla sempre la schermata **Interconnect -> HCX Components** all'interno dell'IU HCX per verificare lo stato del tunnel. Di norma non è necessario reimpostare o riavviare i componenti della flotta. Se la connettività WAN viene ripristinata, si riconnettono automaticamente.

Se erano stati applicati aggiornamenti o correzioni agli HCX Manager (client e cloud) e tali aggiornamenti correggono anche dei problemi con i componenti della flotta, devi ridistribuire il gateway cloud e qualsiasi L2C distribuito. È possibile eseguire un ulteriore debug dello stato del tunnel stabilendo una connessione a HCX Manager tramite un client SSH come ad esempio ccli  

1. Esegui un SSH a HCX Manager utilizzando l'account di amministratore e la password fornita.
2. Esegui il comando `su –` e immetti la password dell'utente `root` (uguale alla password dell'amministratore) per andare alla root.
3. Passa alla directory `/opt/vmware/bin` ed esegui il comando `./ccli`. Se tale tentativo non riesce perché l'ambiente non è impostato per root, esegui il comando `./ccliSetup.pl`.
4. Esegui il comando `list` nella shell `ccli` per elencare i componenti della flotta registrati presso HCX Manager.
5. Specifica l'ID flotta per `ccli` immettendo l'ID elencato per il componente della flotta. Ad esempio, `go 8`.
6. Esegui il comando `debug remoteaccess enable` per stabilire una connessione utilizzando SSH al componente della flotta desiderato.
7. Esci da `ccli` e stabilisci una connessione utilizzando SSH all'indirizzo IP del componente della flotta abilitato a SSH.
9. Continua la risoluzione dei problemi.
10. Ritorna a `ccli` e disabilita il servizio `ssh` per il componente.
11. Se necessario, utilizza il comando ccli `hc` per eseguire un controllo di integrità sui componenti.

## Problemi di compatibilità dell'hardware di destinazione
{: #hcxclient-troubleshooting-hw-compatibility}

La migrazione vMotion può essere un problema quando il lato di origine client è a una versione hardware e una release vSphere più recenti rispetto al cloud. Poiché la migrazione basata sulla replica copia i dati in una VM (Virtual Machine) di nuova creazione sul lato di destinazione, la modifica del tipo di migrazione come “Bulk Migration” dovrebbe consentire la corretta esecuzione della migrazione nella maggior parte dei casi.

## Problemi di L2 Concentrator esteso
{: #hcxclient-troubleshooting-stretched-l2}

Sono stati riscontrati pochissimi problemi relativi al funzionamento di L2C (L2 Concentrator). Analogamente a CGW, se L2C perde la connettività, si riconnette automaticamente dopo che la connettività di rete è stata ripristinata. Utilizza la shell ccli per controllare l'integrità e il funzionamento. Dopo che SSH è abilitato e L2C è connesso, esegui i comandi `ip tunnel` e `ip link |grep t_` per visualizzare lo stato dei tunnel.

## Link correlati
{: #hcxclient-troubleshooting-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
