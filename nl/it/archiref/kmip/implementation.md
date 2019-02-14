---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementazione e gestione di KMIP for VMware

**Nota**: in questa release, KMIP for VMware on {{site.data.keyword.cloud_notm}} è limitato solo alla crittografia vSphere.

## Connessione al server di gestione delle chiavi

Per abilitare la crittografia vSphere o vSAN utilizzando KMIP for VMware on {{site.data.keyword.cloud_notm}}, devi completare le seguenti attività:

1. [Abilita il tuo account per gli endpoint del servizio](/docs/services/service-endpoint/enable-servicepoint.html#getting-started).
2. Crea un'istanza [IBM Key Protect](/docs/services/key-protect/index.html).
3. Crea una chiave root del cliente (CRK) in IBM Key Protect.
4. Crea [un ID del servizio e una chiave API](/docs/iam/serviceid_keys.html) Identity and Access Management (IAM) da utilizzare con KMIP for VMware. Concedi a questo ID del servizio l'accesso come visualizzatore alla piattaforma e come scrittore al servizio per la tua istanza Key Protect.
5. Crea un'istanza [KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html) dal catalogo {{site.data.keyword.cloud_notm}}.
6. All'interno di VMware vCenter, crea un cluster del server di gestione delle chiavi (KMS) con due server, uno per ogni endpoint KMIP for VMware nella regione di tua scelta.
7. Seleziona uno dei metodi VMware per generare o installare un certificato client KMS in vCenter.
8. Esporta la versione pubblica del certificato e configuralo come un certificato client consentito nella tua istanza KMIP for VMware.

## Abilitazione della crittografia

Per utilizzare la crittografia vSAN, modifica le impostazioni generali vSAN nel tuo cluster vCenter e seleziona la casella di spunta della crittografia.

Per utilizzare la crittografia vSphere, modifica le tue politiche di archiviazione della macchina virtuale in modo da richiedere la crittografia del disco.

## Rotazione delle chiavi

[Ruota la tua chiave root del cliente (CRK) Key Protect](/docs/services/key-protect/rotate-keys.html) utilizzando la console o l'API {{site.data.keyword.cloud_notm}}.

Per la crittografia VMware vSAN, ruota le tue chiavi di crittografia della chiave (KEK, key encryption key) e facoltativamente le chiavi di crittografia dei dati (DEK, data encryption key) dalle impostazioni generali vSAN nel tuo cluster vCenter.

Per la crittografia VMware vSphere, ruota le tue KEK e DEK (facoltativamente) VMware utilizzando il comando **Set-VMEncryptionKey** PowerShell.

## Revoca delle chiavi

Puoi revocare tutte le chiavi utilizzate da KMIP for VMware eliminando la tua CRK scelta da Key Protect.

Quando le chiavi vengono revocate, tutti i dati protetti da queste chiavi e dalla tua istanza KMIP for VMware vengono frammentati in modo crittografico da questo metodo. VMware conserva alcune chiavi quando un host ESXi è acceso, per cui devi riavviare il tuo cluster vSphere per assicurarti che tutti i dati crittografati non vengano più utilizzati.
{:important}

KMIP for VMware archivia delle KEK impacchettate individuali nella tua istanza Key Protect utilizzando dei nomi associati agli ID della chiave noti a VMware. Puoi eliminare le chiavi individuali per revocare la crittografia di dischi o unità individuali.

VMware non elimina le chiavi dal KMS quando una VM che dispone di dischi crittografati viene rimossa dall'inventario. Questo per consentire il ripristino di tale VM da un backup o se viene ripristinata nell'inventario. Se vuoi recuperare queste chiavi e annullare la validità in modo crittografico di tutti i backup, devi eliminare le chiavi da Key Protect dopo aver eliminato le tue VM.
{:note}

### Link correlati

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/kmip/overview.html)
* [Progettazione della soluzione](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
