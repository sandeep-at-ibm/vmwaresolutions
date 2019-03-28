---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementazione e gestione di KMIP for VMware
{: #kmip-implementation}

## Connessione al server di gestione delle chiavi
{: #kmip-implementation-connecting-kms}

Per abilitare la codifica vSphere o vSAN utilizzando KMIP for VMware on {{site.data.keyword.cloud_notm}}, devi completare le seguenti attività:

1. [Abilita il tuo account per gli endpoint del servizio](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started).
2. Crea un'istanza [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial).
3. Crea una chiave root del cliente (CRK) in IBM Key Protect.
4. Crea [un ID del servizio e una chiave API](/docs/iam?topic=iam-serviceidapikeys) Identity and Access Management (IAM) da utilizzare con KMIP for VMware. Concedi a questo ID del servizio l'accesso come visualizzatore alla piattaforma e come scrittore al servizio per la tua istanza Key Protect.
5. Crea un'istanza [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering) dal catalogo {{site.data.keyword.cloud_notm}}.
6. All'interno di VMware vCenter, crea un cluster del server di gestione delle chiavi (KMS) con due server, uno per ogni endpoint KMIP for VMware nella regione di tua scelta.
7. Seleziona uno dei metodi VMware per generare o installare un certificato client KMS in vCenter.
8. Esporta la versione pubblica del certificato e configuralo come un certificato client consentito nella tua istanza KMIP for VMware.

## Abilitazione della codifica
{: #kmip-implementation-enable-encrypt}

Per utilizzare la codifica vSAN, modifica le impostazioni generali vSAN nel tuo cluster vCenter e seleziona la casella di spunta della codifica.

Il controllo di integrità vSAN può emettere delle avvertenze periodiche in cui attesta di non potersi connettere al cluster KMS da uno o più dei tuoi host vSphere. Queste avvertenze si verificano perché la connessione del controllo di integrità vSAN va in timeout troppo velocemente. Puoi ignorare queste avvertenze. Per ulteriori informazioni, vedi [vSAN KMS Health Check intermittently fails with SSL Handshake Timeout error](https://kb.vmware.com/s/article/67115){:new_window}.
{:note}

Per utilizzare la codifica vSphere, modifica le tue politiche di archiviazione della VM (Virtual Machine) in modo da richiedere la codifica del disco.

## Rotazione delle chiavi
{: #kmip-implementation-key-rotation}

[Ruota la tua chiave root del cliente (CRK) Key Protect](/docs/services/key-protect?topic=key-protect-key-rotation#key-rotation) utilizzando la console o l'API {{site.data.keyword.cloud_notm}}.

Per la codifica VMware vSAN, ruota le tue chiavi di codifica della chiave (KEK) e facoltativamente le chiavi di codifica dei dati (DEK) dalle impostazioni generali vSAN nel tuo cluster vCenter.

Per la codifica VMware vSphere, ruota le tue KEK e DEK (facoltativamente) VMware utilizzando il comando **Set-VMEncryptionKey** PowerShell.

## Revoca delle chiavi
{: #kmip-implementation-key-revocation}

Puoi revocare tutte le chiavi utilizzate da KMIP for VMware eliminando la tua CRK scelta da Key Protect.

Quando le chiavi vengono revocate, tutti i dati protetti da queste chiavi e dalla tua istanza KMIP for VMware vengono frammentati in modo crittografico da questo metodo. VMware conserva alcune chiavi quando un host ESXi è acceso, per cui devi riavviare il tuo cluster vSphere per assicurarti che tutti i dati codificati non vengano più utilizzati.
{:important}

KMIP for VMware archivia delle KEK impacchettate individuali nella tua istanza Key Protect utilizzando dei nomi associati agli ID della chiave noti a VMware. Puoi eliminare le chiavi individuali per revocare la codifica di dischi o unità individuali.

VMware non elimina le chiavi dal KMS quando una VM che dispone di dischi codificati viene rimossa dall'inventario. Questo per consentire il ripristino di tale VM da un backup o se viene ripristinata nell'inventario. Se vuoi recuperare queste chiavi e annullare la validità in modo crittografico di tutti i backup, devi eliminare le chiavi da Key Protect dopo aver eliminato le tue VM.
{:note}

## Link correlati
{: #kmip-implementation-related}

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [Progettazione della soluzione](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
