---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTKC WebGUI, HTKC console, enable internet HTKC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione di HyTrust KeyControl on IBM Cloud
{: #managinghtkc}

Per gestire il servizio HyTrust KeyControl on {{site.data.keyword.cloud}} (HTKC), accedi alla GUI web HTKC dalla console {{site.data.keyword.vmwaresolutions_short}} o accedi alla console HTKC dal client web vSphere.

## Accesso alla GUI web HyTrust KeyControl dalla console IBM Cloud for VMware Solutions
{: #managinghtkc-accessing-webgui}

Per accedere alla GUI web del dispositivo HTKC primario o secondario, utilizza le credenziali della GUI web disponibili nella pagina dei dettagli del servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}.

## Accesso alla console HyTrust KeyControl dal client web vSphere
{: #managinghtkc-accessing-console}

Per accedere alla console HTKC dal client web vSphere, utilizza la seguente procedura:
1. Nel client web vSphere, individua le VM (Virtual Machine) che iniziano con i nomi **KC1** e **KC2** che hanno l'indirizzo IP corrispondente trovato nella pagina dei dettagli del servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}.
2. Fai clic con il tasto destro del mouse su **KC1** o **KC2** e quindi seleziona **Apri console**.
3. Accedi alla console utilizzando le relative credenziali che puoi trovare nella pagina dei dettagli del servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Abilitazione dell'accesso a internet per la VM HyTrust KeyControl
{: #managinghtkc-internet-access}

Per HTKC 4.3.2 e versioni successive, {{site.data.keyword.vmwaresolutions_short}} fornisce un supporto di rinnovo automatico per le licenze HyTrust per cui è abilitata la funzione Call Home. Per le istanze vCenter Server che non sono solo private, HTKC viene distribuito con le regole firewall e SNAT (Source Network Address Translation) definite nell'**mgmt-nsx-edge** dell'ESG dei servizi di gestione.

Queste regole ti consentono di abilitare l'accesso a internet per le macchine virtuali (VM, Virtual Machine) HyTrust. Se l'accesso a internet non è abilitato, la licenza che viene applicata all'installazione HTKC scadrà dopo un anno.

Per gli ambienti vCenter Server solo privati, l'**mgmt-nsx-edge** dell'ESG (Edge Services Gateway) VMware NSX non viene aggiunto; pertanto, le regole firewall e SNAT non sono definite. Di conseguenza, la connettività a internet non può essere abilitata per le istanze solo private e le licenze HyTrust scadono annualmente.
{:note}

### Procedura per trovare le regole firewall e SNAT definite
{: #managinghtkc-proc-find-firewall}

1. Accedi al client web VMware vSphere (FLEX) e trova **mgmt-nsx-edge** ESG.
2. Fai clic su **Home > Networking & Security > NSX Edges**.
3. Fai doppio clic su **mgmt-nsx-edge** e fai clic nella scheda **Manage**.
4. Vai alla scheda **Firewall** e trova le regole HyTrust. Prendi nota degli indirizzi IP di origine. Questi sono gli indirizzi IP per le VM HyTrust.
5. Vai alla scheda **NAT** e trova le regole SNAT create per le VM HyTrust. Gli indirizzi IP di origine corrisponderanno agli indirizzi IP che hai annotato nel passo precedente.

### Procedura per abilitare la connettività a internet per HTKC
{: #managinghtkc-proc-enable-internet}

1. Completa i passi da 1 a 3 nella procedura precedente.
2. Fai clic su **Settings** e quindi su **Interfaces**. Prendi nota dell'indirizzo IP per l'uplink privato. Questo indirizzo sarà il nuovo gateway predefinito.
3. Fai clic su **Home > Hosts and Clusters** e trova le VM HyTrust. Fai clic con il tasto destro del mouse su una delle VM e fai clic su **Open Console**.
4. Accedi alla console utilizzando le credenziali della console che puoi trovare nella pagina dei dettagli del servizio HyTrust KeyControl on IBM Cloud nella console {{site.data.keyword.vmwaresolutions_short}}.
5. Per ottenere l'indirizzo IP del gateway predefinito corrente dalla VM, fai clic su **Manage Network Settings > Show Current Network Configuration**. Prendi nota dell'indirizzo IP che è elencato per **Gateway**. Questo indirizzo diventa il gateway utilizzato per la rotta statica.
6. Per impostare una rotta statica per la >VM, fai clic su **Manage Network Settings > Manage Static Routes > Add Static Route**. Imposta **Network address** su `10.0.0.0/8` e **Gateway** sull'indirizzo IP annotato nel passo precedente.
7. Per impostare l'IP gateway predefinito per la VM, fai clic su **Manage Network Settings > Change Current Network Configuration**. Se ottieni un messaggio di avvertenza, fai clic su **OK** e fai quindi clic su **Custom Configuration**. Imposta il campo **Gateway** sull'indirizzo IP di uplink privato che hai annotato nel passo 2 e fai clic su **OK**. Attendi che la nuova configurazione di rete sia installata e che i servizi di rete siano riavviati.
8. Se vedi un messaggio che chiede la riautenticazione di HyTrust SecureOS, fai clic su **OK** e immetti l'indirizzo IP dell'altra VM HyTrust per questa installazione. Se ti viene richiesta una passphrase di 16 caratteri, premi Invio per ritornare al menu principale. Verifica la configurazione di rete corrente per assicurarti che le tue modifiche siano applicate.
9. Per confermare che la VM ha accesso a internet, esegui il ping di un sito web o di un indirizzo IP pubblico. Fai clic su **Manage Network Settings > Network Diagnostic Tools > Ping Another Server**. Immetti un indirizzo di sito web pubblico, ad esempio `www.ibm.com`, fai clic su **OK** e attendi che venga visualizzato un messaggio, ad esempio `www.ibm.com responds to ping`.
10. Ripeti i passi da 3 a 9 per l'altra VM HyTrust.

## Link correlati
{: #managinghtkc-related}

* [Panoramica di HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web HyTrust](https://www.hytrust.com/)
