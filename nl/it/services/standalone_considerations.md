---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-23"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Considerazioni sulle istanze VMware HCX on IBM Cloud in loco
{: #standalone_considerations}

Esamina le seguenti considerazioni prima di installare o eliminare le istanze HCX on {{site.data.keyword.cloud}} che hai ordinato per l'utilizzo in loco.

Un'istanza vCenter Server con HCX on {{site.data.keyword.cloud_notm}} è limitata a tre connessioni simultanee dai siti in loco.
{:note}

## Considerazioni prima di installare le istanze HCX on IBM Cloud in loco
{: #standalone_considerations-install}

I componenti di HCX on {{site.data.keyword.cloud_notm}} devono essere installati sia su {{site.data.keyword.cloud_notm}} che nel tuo ambiente vSphere in loco. Si consiglia di installare il servizio HCX on {{site.data.keyword.cloud_notm}} nella tua istanza vCenter Server with Hybridity Bundle su {{site.data.keyword.cloud_notm}} prima di installare l'istanza HCX on {{site.data.keyword.cloud_notm}} in loco. Per ulteriori informazioni, vedi [Considerazioni sull'installazione di HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-hcx_considerations#hcx_considerations-install).

### Requisiti dell'indirizzo IP
{: #standalone_considerations-ip}

Per la piena funzionalità di HCX, hai bisogno di almeno cinque indirizzi IP privati che hanno accesso a internet. 

### Processo di distribuzione per le istanze HCX on IBM Cloud in loco
{: #standalone_considerations-deploy}

Per una corretta installazione dell'istanza HCX on {{site.data.keyword.cloud_notm}} in loco, devi completare le seguenti attività:
1. Nella console {{site.data.keyword.vmwaresolutions_short}}, ordina l'istanza HCX on {{site.data.keyword.cloud_notm}} in loco. Per ulteriori informazioni, vedi [Ordine di istanze HCX in loco](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
2. Nella **Console cloud HCX**, completa la seguente procedura:
    1. Fai clic sulla scheda **Amministrazione**.
    2. Nella scheda **Aggiornamenti di sistema**, fai clic su **RICHIEDI LINK DI DOWNLOAD**.
    3. Fai clic su **COPIA LINK** e utilizza quindi questo link per scaricare HCX Enterprise Client in un ambiente in loco con accesso al tuo ambiente vSphere in loco.
3. Nel client web VMware vSphere, distribuisci HCX Enterprise Client come dispositivo virtuale HCX Manager nel tuo ambiente in loco.

   Devi distribuire l'HCX Manager in loco su una rete privata e consentirgli l'accesso alla rete pubblica. Puoi utilizzare un gateway Edge NSX, Vyatta o simile per consentire l'accesso Internet all'HCX Manager in loco. Se i gateway utilizzati per l'accesso alla rete privata e l'accesso alla rete pubblica sono diversi, si consiglia di utilizzare il gateway predefinito per consentire l'accesso alla rete pubblica e la **Console di gestione HCX Manager** per creare una rotta statica per l'accesso alla rete privata.
   {:note}
4. Una volta completata la distribuzione di HCX Manager, utilizza la **Console di gestione HCX Manager** per attivare HCX Manager in loco. Per ottenere una chiave di attivazione per l'HCX Manager in loco, ordina un'istanza HCX on {{site.data.keyword.cloud_notm}} in loco nella console {{site.data.keyword.vmwaresolutions_short}}. Per ulteriori informazioni, vedi [Ordine di istanze HCX in loco](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
5. Se hai utilizzato un certificato SSL autofirmato al momento dell'ordine del servizio HCX on {{site.data.keyword.cloud_notm}}, devi importare il certificato nell'HCX Manager in loco completando la seguente procedura:
    1. Nella **Console di gestione HCX Manager** in loco, fai clic sulla scheda **Amministrazione**.
    2. Dal riquadro di navigazione a sinistra, fai clic su **Certificato CA attendibile** e quindi su **IMPORTA** sulla destra.
    3. Fai clic su **URL** e immetti l'URL del certificato che vuoi applicare, ossia l'**IP cloud HCX** (``https://<cloud-side public IP>``), che puoi trovare nella pagina dei dettagli del servizio HCX on {{site.data.keyword.cloud_notm}} nella console {{site.data.keyword.vmwaresolutions_short}}.
    4. Fai clic su **APPLICA**.

Hai completato la configurazione di base dell'HCX Manager in loco. Puoi procedere ad accoppiare il sito di HCX on {{site.data.keyword.cloud_notm}} in loco con il sito di HCX lato cloud.

Per ulteriori informazioni, vedi [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Considerazioni prima di eliminare le istanze HCX on IBM Cloud in loco
{: #standalone_considerations-delete}

Esamina le seguenti considerazioni prima di eliminare un'istanza HCX on {{site.data.keyword.cloud_notm}} che è stata ordinata per l'utilizzo in loco:
1. Nel client web VMware vSphere, vai all'interfaccia utente HCX e controlla i seguenti elementi: 
    1. Assicurati che non vi siano operazioni di migrazione o di ripristino di emergenza HCX in esecuzione.
    2. Assicurati che tutte le reti estese siano state rimosse.
    3. Assicurati che tutti i componenti di interconnessione con i siti cloud abbinati siano stati rimossi.

   Devi completare tutti i passi precedenti prima di procedere con il passo successivo. In caso contrario, la licenza per l'istanza HCX on {{site.data.keyword.cloud_notm}} in loco viene annullata. Se la licenza viene annullata, le migrazioni non possono essere eseguite e potrebbero verificarsi degli errori per i componenti HCX.   
   {:important}
2. Nella console {{site.data.keyword.vmwaresolutions_short}}, elimina l'istanza HCX on {{site.data.keyword.cloud_notm}} in loco che era stata ordinata per ottenere la chiave di attivazione per l'HCX Manager in loco. Assicurati che l'istanza eliminata non sia più disponibile nella console prima di procedere al passo successivo.

   Per ulteriori informazioni, vedi [Eliminazione di istanze HCX on {{site.data.keyword.cloud_notm}} in loco](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_deletingserviceinstances).
3. Nel client web VMware vSphere, elimina l'HCX Manager in loco.

## Link correlati
{: #standalone_considerations-related}

* [Visualizzazione delle istanze HCX on {{site.data.keyword.cloud_notm}} in loco](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_viewingserviceinstances)
* [Glossario dei termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Documentazione di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
