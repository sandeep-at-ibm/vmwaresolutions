---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Installazione e configurazione dell'HCX sull'origine

L'installazione in loco implica la distribuzione dell'applicazione di gestione HCX e la sua registrazione con il vCenter e uno o più endpoint cloud abilitati VCF/VCS HCX.

## Installazione dell'applicazione HCX Manager

Installa l'applicazione HCX Manager nel vCenter in loco.

1. Accedi a **My VMware** e scarica il file OVA di Hybrid Cloud Services dalla pagina di scaricamento del prodotto.
2. Apri un browser e accedi al client web vSphere. Questa attività non può essere eseguita dal client vSphere. Visualizza la scheda **Home**.
3. Nell'elenco **Inventories Trees**, fai clic su **Host and Clusters**.
4. Espandi la gerarchia per mostrare i data center.
5. Fai clic con il tasto destro sul data center di destinazione e seleziona **Deploy OVF Template** dal menu. La visualizzazione della voce di menu **Deploy OVF template** potrebbe richiedere alcuni secondi.
6. Scegli **Deploy OVF template**.
  1. Seleziona **Local file** e fai clic su **Browse** per trovare il file OVA scaricato sul computer. Fai clic su **Next**.
  2. Sulla pagina **Review details**, seleziona la casella **Accept extra configuration options** e fai clic su **Next**.
  3. Sulla pagina **Accept EULAs**, scorri in basso per controllare l'accordo di licenza utente VMware. Fai clic su **Accept** e **Next**.
  4. Sulla pagina **Select name and folder**, modifica il nome se necessario e seleziona l'ubicazione per Hybrid Cloud Services. Fai clic su **Next**.
  5. Sulla pagina **Select a resource**, seleziona l'ubicazione di installazione.
  6. Sulla pagina **Select storage**, seleziona l'archiviazione per Hybrid Cloud Services e fai clic su **Next**. Dall'elenco **Select virtual disk format**, puoi selezionare **thin provisioning** o **thick provisioning**.
  7. Sulla pagina **Setup networks**, associa l'adattatore Hybrid Cloud Services a una rete host scelta dall'elenco **Destination**.
7. Sulla pagina **Customized template**, immetti i valori specifici per l'ambiente:
  * Per le password, il nome utente predefinito per l'interfaccia riga di comando (CLI) e l'interfaccia utente web è **admin**. La password e l'utente **admin** sono obbligatori per accedere all'interfaccia utente web ed è presente inoltre un account utente **root** di cui può essere impostata una password.
  * Immetti e reimmetti la password utente **admin** della CLI.
  * Immetti e reimmetti la password utente **root**. In futuro, se hai bisogno di assistenza da VMware Global Support Services (GSS), questa password potrebbe dover essere condivisa in modo da poter risolvere i problemi del sistema.
  * Per le proprietà di rete, immetti il nome host per la VM HCX Manager. Immetti l'indirizzo IPv4 di rete, il prefisso IPv4 (il CIDR) e il gateway predefinito. La seguente tabella mostra i valori di esempio:

Tabella 1. Valori di esempio per le proprietà di rete

| Campo                    | Valore           |
|--------------------------|-----------------|
| Nome host                 | HCM_1           |
| Indirizzo IPv4 rete 1   | 192.168.200.101 |
| Prefisso IPv4 rete 1    | 24              |
| Gateway IPv4 predefinito     | 192.168.200.1   |
| Indirizzo IPv6 rete 1   |                 |
| Prefisso IPv6 rete 1    |                 |

8. Controlla la pagina di bind vService. Fai clic su **Next** per continuare.
9. Sulla pagina **Ready to complete**, segui questa procedura:
  * Seleziona la casella **Power on after deployment**.
  * Controlla le impostazioni di Hybrid Cloud Services e fai clic su **Finish**. Potrebbero essere necessari diversi minuti per l'accensione dell'applicazione Hybrid Cloud Services.
  * Per controllare lo stato, vai alla home page del client web e sulla scheda **Home**, vai a **Inventories** e fai clic su **Hosts and Clusters**. Espandi la gerarchia del data center e fai clic sulla macchina virtuale del servizio Hybrid Cloud Services per visualizzare un riepilogo nel pannello centrale.
  * Visualizza la scheda **Summary**, la console legge **Powered On** e il pulsante **Play** è verde.
10. L'HCX Manager è acceso ed è pronto per essere registrato con il vCenter.

### Link correlati

* [Preparazione dell'ambiente di installazione ](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-prep-install.html)
