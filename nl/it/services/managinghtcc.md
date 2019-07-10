---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione di HyTrust CloudControl on IBM Cloud
{: #managinghtcc}

Per gestire il servizio HyTrust CloudControl on {{site.data.keyword.cloud}} (HTCC), accedi alla GUI web HTCC dalla console {{site.data.keyword.vmwaresolutions_short}} o accedi alla console HTCC dal client web vSphere.

## Accesso alla GUI web HyTrust CloudControl dalla console IBM Cloud for VMware Solutions
{: #managinghtcc-accessing-webgui}

Per accedere alla GUI web del dispositivo HTCC primario o secondario, utilizza le credenziali della GUI web corrispondente disponibili nella pagina dei dettagli del servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

## Accesso alla console HyTrust CloudControl dal client web vSphere
{: #managinghtcc-accessing-console}

Per accedere alla console HTCC dal client web vSphere, utilizza la seguente procedura:
1. Nel client web vSphere, individua le VM (Virtual Machine) denominate **CC1** e **CC2**.
2. Fai clic con il tasto destro del mouse su **CC1** o **CC2** e quindi seleziona **Apri console**.
3. Accedi alla console utilizzando le relative credenziali che puoi trovare nella pagina dei dettagli del servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Abilitazione dell'accesso a internet per la VM HyTrust CloudControl
{: #managinghtcc-internet-access}

Per HTCC 5.5.1 e versioni successive, {{site.data.keyword.vmwaresolutions_short}} fornisce un supporto di rinnovo automatico per le licenze HyTrust per cui è abilitata la funzione Call Home. Per le istanze vCenter Server che non sono solo private, HTCC viene distribuito con le regole firewall e SNAT (Source Network Address Translation) definite nell'**mgmt-nsx-edge** dell'ESG dei servizi di gestione.

Queste regole ti consentono di abilitare l'accesso a internet per le macchine virtuali (VM, Virtual Machine) HyTrust. Se l'accesso a internet non è abilitato, la licenza che viene applicata all'installazione HTCC scadrà dopo un anno.

Per gli ambienti vCenter Server solo privati, l'**mgmt-nsx-edge** dell'ESG (Edge Services Gateway) VMware NSX non viene aggiunto; pertanto, le regole firewall e SNAT non sono definite. Di conseguenza, la connettività a internet non può essere abilitata per le istanze solo private e le licenze HyTrust scadono annualmente.
{:note}

### Procedura per trovare le regole firewall e SNAT definite
{: #managinghtcc-proc-find-firewall}

1. Accedi al client web VMware vSphere (FLEX) e trova **mgmt-nsx-edge** ESG.
2. Fai clic su **Home > Networking & Security > NSX Edges**.
3. Fai doppio clic su **mgmt-nsx-edge** e fai clic nella scheda **Manage**.
4. Vai alla scheda **Firewall** e trova le regole HyTrust. Prendi nota degli indirizzi IP di origine. Questi sono gli indirizzi IP per le VM HyTrust.
5. Vai alla scheda **NAT** e trova le regole SNAT create per le VM HyTrust. Gli indirizzi IP di origine corrisponderanno agli indirizzi IP che hai annotato nel passo precedente.

### Procedura per abilitare la connettività internet per HTCC
{: #managinghtcc-enable-internet}

La seguente procedura si applica per l'aggiornamento delle impostazioni di rete HTCC sulla macchina virtuale (VM, Virtual Machine) primaria, che viene utilizzata per gli upgrade delle licenze. Non hai bisogno di aggiornare le impostazioni per la VM secondaria.
{:note}

1. Completa i passi da 1 a 3 nella procedura precedente.
2. Fai clic su **Settings** e fai quindi clic su **Interfaces**. Prendi nota dell'indirizzo IP per l'uplink privato, che diventa il nuovo gateway predefinito.
3. Vai alla pagina dei dettagli del servizio HyTrust CloudControl on IBM Cloud, fai clic su **View HTCC Web UI** ed esegui l'accesso con le credenziali dalla pagina dei dettagli del servizio.
4. Prendi nota del gateway predefinito esistente. Ad esempio, per HTCC 5.5.1, fai clic su **Configuration > Network**. Prendi nota dell'indirizzo IP gateway elencato, che diventa il gateway per la rotta statica.
5. Aggiungi una rotta statica. Ad esempio, per HTCC 5.5.1, fai clic su **Configuration > Static Routes**. Fai clic su **Add**, immetti le seguenti informazioni e fai clic su **OK**.

  ```
  Network Address: 10.0.0.0
  Mask: 255.0.0.0
  Gateway: IP noted in step 4
  Device: Network 1
  ```

6. Modifica il gateway predefinito. Ad esempio, per HTCC 5.5.1, fai clic su **Configuration > Network** e sostituisci l'indirizzo IP nel campo **Gateway** con quello di cui hai preso nota nel Passo 3 e fai clic su **Save**. 

  Assicurati di avere impostato la rotta statica prima di modificare il gateway predefinito, altrimenti la console web potrebbe diventare irraggiungibile.
  {:important}

  La VM primaria avrà ora accesso a internet.

7. Per confermare che la VM primaria ha accesso a internet, esegui un comando `ping` a un sito web o a un indirizzo IP pubblico. Per eseguire tale operazione, torna a vCenter e fai clic con il tasto destro del mouse su **CC1 > Open Console**. Esegui l'accesso alla console utilizzando le credenziali della console dalla pagina dei dettagli del servizio HyTrust CloudControl on IBM Cloud. Esegui un comando `ping`, come ad esempio `ping www.ibm.com` e dovresti ottenere una risposta immediata. Premi `Ctrl + C` per terminare il ping e assicurati che la perdita di pacchetti sia dello 0%. 
## Link correlati
{: #managinghtcc-related}

* [Panoramica di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web HyTrust](https://www.hytrust.com/)
