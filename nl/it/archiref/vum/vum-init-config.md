---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

# Configurazione iniziale
{: #vum-init-config}

L'automazione {{site.data.keyword.vmwaresolutions_full}} configura il VCSA con un gateway predefinito impostato sul BCR (Backend Customer Router) di {{site.data.keyword.cloud}}. Tuttavia, non esiste una rotta a Internet tramite il BCR. La rotta standard a Internet dall'istanza VMware vCenter Server on {{site.data.keyword.cloud_notm}} avviene tramite l'ESG di gestione. Poiché non è consigliabile modificare la configurazione di VCSA o dell'ESG di gestione, è più opportuno implementare un server proxy sulla sottorete del cliente per abilitare VUM.

Questo approccio significa che non devi riconfigurare il VCSA o l'ESG di gestione, tuttavia, è necessario installare una piccola VM (Virtual Machine) o un piccolo dispositivo. Un server proxy è un sistema che si trova tra due dispositivi endpoint e funge da dispositivo intermedio. In questo caso, si trova tra VUM e i server di aggiornamento presso VMware.

Quando VUM richiede una risorsa dal server di aggiornamento su VMware, la richiesta viene prima inviata al server proxy e il server proxy invia quindi la richiesta al server di aggiornamento. Dopo che il server proxy ottiene la risorsa, la invia a VUM. Un server proxy può essere utilizzato per facilitare la sicurezza, i controlli di amministrazione e servizi di cache.

Puoi utilizzare un server proxy basato su CentOS e Squid. Squid Proxy è un proxy cache open source per il web e supporta molti protocolli, tra cui HTTP e HTTPS. Sono disponibili diversi proxy basati su dispositivi e VM, pertanto devi selezionare quello appropriato in base ai requisiti della tua azienda e installarlo e configurarlo seguendo le indicazioni del fornitore. I clienti che scelgono di utilizzare un'implementazione CentOS/Squid devono continuare con il seguente processo.

* Scarica l'ISO CentOS su un server jump
* Crea una libreria vCenter
* Carica l'ISO nella libreria vCenter
* Crea una VM, installa e configura CentOS e installa Squid

## Ricerca delle informazioni sulla sottorete
{: #vum-init-config-subnet}

Prima di poter iniziare questa attività, raccogli le informazioni per popolare la seguente tabella. Esamina i valori suggeriti e assicurati che siano appropriati per la tua azienda. Questa configurazione è basata su un piccolo proxy per VUM che utilizza solo CentOS-Minimal e Squid.

Per trovare la sottorete portatile privata del cliente:

1. Vai alla pagina **Resources** nella console {{site.data.keyword.vmwaresolutions_short}}.
2. Seleziona l'istanza (**Instance**) necessaria, seleziona l'infrastruttura (**Infrastructure**) e il cluster (**Cluster**) necessario.
3. Seleziona **Private VLAN** e individua la sottorete etichettata `Private subnet for customer workload edge`.
4. Seleziona la **sottorete** e verrai reindirizzato alla pagina dei dettagli della sottorete che visualizza gli indirizzi IP e le relative assegnazioni.
5. Utilizzando le informazioni, seleziona un indirizzo IP non assegnato e aggiorna la nota (**Note**) con i commenti appropriati. Utilizza questo indirizzo IP per il parametro `proxy ip` nella seguente tabella.

Tabella 1. Valori di distribuzione

| Parametro | Valori suggeriti | Note |
|:--------- |:-------------- |:------ |
| CPU proxy | 1 vCPU | Squid non ha requisiti minimi |
| RAM proxy | 2 GB | Squid non ha requisiti minimi |
| Disco proxy | 25 | GB	Squid non ha requisiti minimi |
| Nome host | Proxy01 | |
| Indirizzo | proxy ip | Deve essere utilizzato un indirizzo IP di riserva dalla sottorete portatile privata del cliente assegnata durante il processo di provisioning. Solo due indirizzi IP vengono riservati su questa sottorete; uno per il BCR e l'altro per il customer-esg
| Maschera di rete | 255.255.255.192 | |
| Gateway| ip uplink privato customer-nsx-edge | Questa è l'impostazione predefinita del gateway per il server proxy, che è l'indirizzo di uplink privato di customer-nsx-edge. L'indirizzo IP può essere trovato riesaminando la scheda **Settings** per **customer-nsx-edge**. |
| Server DNS | ip AD/DNS | Questo indirizzo IP può essere trovato nella pagina dell'istanza nella console {{site.data.keyword.vmwaresolutions_short}} **Risorse**. |
| IP BCR | ip bcr | Sulla stessa pagina dove hai selezionato l'IP proxy in alto, nota l'indirizzo etichettato Gateway. Questo indirizzo è l'indirizzo IP del BCR (Backend Customer Router) di {{site.data.keyword.cloud_notm}} ed è il gateway per 10.0.0.0/8 e 161.26.0.0/16. Utilizzerai questo indirizzo in una rotta statica nel server proxy in modo che possa raggiungere il VCSA e il server AD/DNS. |
| IP NAT | ip uplink pubblico customer-nsx-edge | L'indirizzo pubblico dell'ESG NSX del cliente fungerà da indirizzo NAT pubblico per il proxy. Questo indirizzo IP può essere trovato riesaminando la scheda **Settings** per **customer-nsx-edge**. |

## Configurazione di NSX
{: #vum-init-config-config-nsx}

Le impostazioni NAT e firewall dell'ESG del cliente NSX sono necessarie per abilitare il traffico del server proxy.

### Firewall
{: #vum-init-config-firewall}

1. Passa a **Home** > **Networking & Security**.
2. Seleziona **NSX Edges**, customer-nsx-edge e quindi **Firewall**.
3. Fai clic sul simbolo **+** e aggiungi una regola del firewall.
4. Fornisci i parametri obbligatori come indicato nella seguente tabella. La nuova regola del firewall deve precedere l'ultima regola, la regola di negazione predefinita.

Tabella 2. Regola del firewall

| Parametro | Valori suggeriti |
|:--------- |:-------------- |
| Nome | Proxy01 in uscita |
| Tipo | Utente |
| Origine | ip server proxy |
| Destinazione | qualsiasi |
| Servizio | HTTP/HTTPS/ICMP Echo |
| Azione | Accetta |

Dopo aver fornito i parametri, fai clic su **Publish Changes**.

### NAT
{: #vum-init-config-nat}

1. Seleziona **NAT**.
2. Fai clic sul simbolo **+** e aggiungi una regola SNAT.
3. Fornisci i parametri obbligatori come indicato nella seguente tabella e fai clic su **OK**. Quindi fai clic su **Publish Changes**.

Tabella 3. Regola NAT

| Parametro | Valori suggeriti |
|:--------- |:-------------- |
| Tipo di regola | USER |
| Azione | SNAT |
| Applicato su | Uplink pubblico |
| Protocollo originale | qualsiasi |
| IP di origine originale | ip server proxy |
| Porte di origine originali | qualsiasi |
| IP di destinazione originale | qualsiasi |
| Porte di destinazione originali | qualsiasi |
| Indirizzo IP tradotto | ip NAT |
| Intervallo di porte tradotte | qualsiasi |
| Stato | Abilita |
| Registrazione | Abilita |
| Descrizione | Proxy01 SNAT |

### Installazione e configurazione di un server proxy
{: #vum-init-config-inst-cfg-proxy}

Il seguente processo distribuisce una VM per ospitare CentOS e Squid dalla libreria di contenuti e comprende i seguenti passi. Si presuppone che tu disponga di una VSI di Windows da utilizzare come jumpbox e che utilizzi un Remote Desktop Protocol per connetterti all'interfaccia pubblica della VSI:

* Scarica il file ISO CentOS-Minimal
* Configura una libreria di contenuti vCenter e inserisci il file ISO CentOS al suo interno
* Configura la VM proxy, installa CentOS e Squid

### Download del file ISO CentOS-Minimal
{: #vum-init-config-downloading-centos}

Utilizzando un browser sul tuo server jump, scarica il file ISO CentOS-Minimal da [CentOS](https://www.centos.org/download/). Nota che {{site.data.keyword.cloud_notm}} mantiene un mirror di diverse distribuzioni Linux diffuse. Questo mirror è disponibile solo sulla rete privata e gli ISO CentOS sono disponibili al seguente indirizzo: `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Configurazione di una libreria di contenuti e inserimento del file ISO CentOS
{: #vum-init-config-config-conent-library}

Crea una libreria di contenuti vCenter locale. La libreria è accessibile solo nell'istanza vCenter Server in cui viene creata. Popola la libreria con i template e gli ISO richiesti per distribuire le VM.

1. Tramite il client web vSphere, passa a **Home** > **Content library** > **Objects** > **Create a new content library** > **Create subscribed library on the vCenter**.
2. Immetti un nome per la libreria di contenuti, ad esempio ISO, e nella casella di testo Notes immetti una descrizione per la libreria, quindi fai clic su **Next**.
3. Seleziona **Local content library** e fai clic su **Next**.
4. Seleziona un archivio dati e fai quindi clic su un archivio dati appropriato, ad esempio `vsanDatastore`.
5. Esamina le informazioni nella pagina **Ready to Complete** e fai clic su **Finish**.

### Configurazione della VM proxy, installazione di CentOS e Squid
{: #vum-init-config-config-proxy}

Questa attività include le seguenti operazioni:

*	Crea una nuova VM
*	Installa CentOS
*	Installa Squid

#### Crea una nuova VM
{: #vum-init-config-create-new-vm}

Questa attività crea una nuova VM pronta per l'uso come server proxy. Per popolare la configurazione, utilizza le impostazioni indicate nella Tabella 1. Valori di distribuzione.

1.	Tramite il client web vSphere, passa a **Home** > **VMs and Templates**.
2.	Nel riquadro di navigazione, fai clic su **datacenter1**, quindi fai clic con il tasto destro del mouse e seleziona **New Virtual Machine** > **New Virtual Machine**.
3.	Seleziona **Create a new Virtual Machine** e fai clic su **Next**.
4.	Immetti un nome per la VM, ad esempio Proxy01, quindi seleziona **datacenter1** e fai clic su **Next**.
5.	Seleziona **cluster1** e fai clic su **Next**.
6.	Seleziona un archivio dati appropriato, ad esempio vsanDatastore, fai clic su **Next** e di nuovo su **Next**.
7.	In **Guest OS Family**, seleziona **Linux** e in **Guest OS version** seleziona **CentOS 7 (64-bit)** e fai clic su **Next**.
8.	Nella scheda **Customized Hardware** per Virtual Hardware, imposta **CPU su 1**, **Memory su 2048 MB** e **New Hard disk su 25 GB**. In **New CD/DVD drive**, seleziona **Content Library ISO File** e poi **CentOS-7-x86_64-Minimal**, fai clic su **OK** e seleziona la casella **Connected**.
9.	Nella casella New device, seleziona **Network** e fai clic su **Add**.
10.	Seleziona la rete **SDDC-DPortGroup-Mgmt**, assicurati che la casella di spunta Connect sia seleziona, quindi fai clic su **Next**.
11.	Esamina le informazioni e fai clic su **Finish**.

#### Installa CentOS
{: #vum-init-config-install-centos}

Questa attività installa e configura la VM appena creata pronta per l'installazione di Squid

1.	Nel riquadro di navigazione del client web vSphere, seleziona la **VM** appena creata, Proxy01 e poi seleziona la scheda **Summary**.
2.	Fai clic su **"Play"** per accendere la VM.
3.	La VM si accende e viene avviata dall'ISO CentOS 7. Avvia una **console remota o una console web** nella VM. Devi installare la console remota e il sistema che esegue il browser web deve risolvere gli host vSphere ESXi in base al nome.
4.	Nella schermata iniziale di CentOS 7, seleziona la lingua desiderata e fai clic su **Continue**.
5.	Nella schermata **LOCALIZATION**, fai clic su **DATE & TIME**, seleziona il tuo fuso orario e fai clic su **Done**.
6.	Nella schermata **LOCALIZATION**, fai clic su **KEYBOARD** per modificare l'impostazione predefinita laddove necessario e quindi premi **Done**.
7.	Nella schermata **LOCALIZATION**, fai clic su **INSTALLATION DESTINATION**, fai clic sull'**icona del disco virtuale VMware** e quindi su **Done**.
8.	Nella schermata **LOCALIZATION**, fai clic su **NETWORK & HOSTNAME**, modifica il nome host con quello da te scelto, ad esempio Proxy01.
9.	Fai clic su **Configure** e quindi su **IPv4 Settings**. Nella casella **Method**, seleziona **Manual**.
10.	Utilizzando il pulsante **Add**, inserisci la _Maschera di rete dell'indirizzo_ e il _Gateway_ dalla _Tabella 1 – Valori di distribuzione_.
11.	Immetti l'_Indirizzo IP del server DNS_ dalla Tabella 1 – Valori di distribuzione.
12.	Fai clic sul pulsante **Routes** e aggiungi le seguenti rotte statiche: _10.0.0.0/8 e 161.26.0.0/16_ con l'indirizzo IP del gateway di _Indirizzo IP BCR_ indicato dalla Tabella 1. Valori di distribuzione, come gateway. Questa rotta statica consente al server proxy di raggiungere il server DNS.
13.	Fai clic su **Save** e assicurati che l'interfaccia Ethernet sia accesa e mostrata come connessa. Fai clic su **Done** e su **Begin Installation**.
14.	Mentre l'installazione continua, imposta una password root e configura un utente.
15.	Al termine dell'installazione, accedi come utente e immetti il comando _ping vmware.com_. Il nome viene risolto in un indirizzo IP e ricevi una risposta. Se non ottieni risposte, verifica gli indirizzi IP, le regole del firewall e le impostazioni NAT.

#### Installa e configura Squid
{: #vum-init-config-install-cfg-squid}

Squid non ha requisiti hardware minimi, ma la quantità di RAM può variare a seconda degli utenti che accedono a Internet tramite il tuo proxy e degli oggetti che sono memorizzati nella cache. Poiché al server proxy accede solo VUM e la cache non è abilitata, viene configurata solo una piccola VM.

1. Utilizzando la console web o la console remota dal client web vSphere Web, accedi al server proxy ed esegui `su` nella root.
2. Prima di installare qualsiasi pacchetto, devi utilizzare il seguente comando per aggiornare il sistema e i pacchetti:
  `yum -y update`

3. Per installare Squid, devi installare il repository EPEL sul sistema poiché Squid non è disponibile nel repository yum predefinito. Per installare il repository EPEL, immetti il seguente comando:
  `yum -y install epel-release`

4. Esegui l'aggiornamento e l'eliminazione utilizzando i seguenti comandi:

  `yum -y update`
  `yum clean all`

5. Squid viene installato utilizzando il seguente comando: `yum -y install squid`.
6. Una volta installato, avvia Squid immediatamente utilizzando il seguente comando: `systemctl start squid`.
7. Immetti il seguente comando per avviare automaticamente Squid all'avvio: `systemctl enable squid`.
8. Immetti il seguente comando per verificare che Squid sia in esecuzione: `systemctl status squid`.
9. Il firewall CentOS deve consentire l'accesso alla porta Squid, TCP 3128, utilizzando il seguente comando:  `firewall-cmd –add-port=3128/tcp –permanent`.
10. Per salvare la regola e riavviare il servizio, utilizza il seguente comando: `firewall-cmd –reload`.

## Configurazione iniziale di VUM
{: #vum-init-config-init-setup-vum}

Configura VUM per utilizzare il server proxy per l'accesso ai repository su Internet.
1. Utilizzando il client web vSphere, passa a **Home** > **Update Manager**. Fai clic sul tuo vCenter Server.
2. Seleziona la scheda **Manage** e fai clic su **Settings**.
3. Seleziona **Download Settings** e quindi, nelle _impostazioni proxy_, fai clic su **Edit**.
4. Spunta la casella **Use Proxy** e immetti l'_indirizzo IP del server proxy_ e la _porta 3128_, quindi fai clic su **OK**. Lo stato di connettività diventa _Validating_ e poi _Connected_.
    **Nota**: non preoccuparti se ricevi il messaggio ``Some URLs have been accessed successfully, but others are inaccessible`` mentre provi la connessione al server proxy.
5. Fai clic su **Download Now**. Nel pannello _Recent Tasks_ dovresti visualizzare questa attività completa.
6. Se questa attività non riesce, riavvia vCenter Server Appliance (vCSA):
  1. Accedi all'interfaccia di gestione vCSA all'indirizzo `https://vcsaFQDN:5480` come **root**.
  2. Fai clic su **Summary** e fai clic su **Reboot**.
  3. Nella casella di conferma, fai clic su **Yes** per confermare l'operazione.

## Link correlati
{: #vum-init-config-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (dimostrazioni)
