---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Risoluzione dei problemi di HCX on IBM Cloud

## La registrazione cloud ha esito negativo

* Hybrid Cloud Services non esegue un altro tentativo se le credenziali non sono corrette. Le credenziali devono essere autenticate prima che Hybrid Cloud Services tenti di accedere e avviare la registrazione cloud.
* La registrazione cloud può avere esito negativo se le credenziali non sono state digitate correttamente o se le credenziali cloud VCF/VCS Hybrid Cloud Services sono state modificate dopo che Hybrid Cloud Services ha eseguito la registrazione al cloud VCF/VCS Hybrid Cloud Services, creando una mancata corrispondenza.
* Per aggiornare le credenziali nel client web, vai alla scheda Hybrid Cloud Services Getting Started e in **Basic tasks** scegli **Register new Cloud**.

## Indirizzo MAC duplicato

Dopo la migrazione, potrebbero verificarsi dei problemi di comunicazione tra le tue macchine virtuali. Quando l'indirizzo MAC viene conservato durante una migrazione, potrebbe essere inavvertitamente creato un indirizzo MAC duplicato.

L'indirizzo MAC per la macchina virtuale migrata può essere modificato per risolvere questo problema.

1. Nel client vSphere, spegni la macchina virtuale.
2. Nell'inventario, fai clic con il tasto destro sulla macchina virtuale e scegli **Edit Settings** dal menu.
3. Sulla scheda **Virtual Hardware**, espandi l'adattatore di rete.
4. Accanto alla casella di testo MAC Address, scegli **Manual** dal menu.
5. Specifica un indirizzo MAC univoco e fai clic su **OK**.
6. Controlla se l'indirizzo MAC univoco risolve il problema di comunicazione.

## Consumo elevato di risorse host

In rari casi, se tutte le applicazioni virtuali del servizio risiedono sullo stesso host, le macchine virtuali del servizio Hybrid Cloud Services possono esaurire le risorse disco e la CPU dell'host.

Alcuni utenti hanno riscontrato questo problema quando tutte le applicazioni virtuali sono state installate su un host fisico. Data questa configurazione, le prestazioni si degradano quando si verificano le seguenti cose contemporaneamente:
* La rete ha un'elevata latenza o una perdita di pacchetti o entrambe. La migrazione o il trasporto dei dati è lento quando utilizzi internet pubblico o una rete occupata.
* WAN Optimizer sta consumando la larghezza di banda per crittografare e comprimere (o decrittografare e decomprimere) grandi carichi di lavoro.
* È presente un elevato traffico dell'applicazione tra le VM in loco e le VM migrate.

Per risolvere il problema, utilizza la seguente procedura:

1. Prima di modificare la configurazione del data center, controlla i requisiti per il supporto dello stato stazionario.
2. Contatta il supporto dello stato stazionario se stanno per essere esaurite le risorse. Possono consigliarti su come riconfigurare l'ambiente con una quantità minima di tempo di inattività.

### Link correlati

* [Registrazione dell'HCX Manager con vCenter](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-reg-vcenter.html)
* [Modifica o disinstallazione dell'HCX](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-mod-uninstall.html)
