---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---
# Requisiti di accesso alla porta per VMware HCX on IBM Cloud
{: #hcx-archi-port-req}

HCX deve attraversare internet pubblico e le linee private e connettersi ai componenti del data center, come ad esempio le reti, gli switch e i gruppi di porte.

La seguente tabella elenca le porte che devono essere aperte in modo che i dispositivi virtuali Hybrid Cloud Services possano essere installati correttamente. Sia l'ambiente vSphere che IBM Cloud devono consentire la sincronizzazione dell'orologio NTP (Network Time Protocol) con i dispositivi in loco vSphere e IBM Cloud. La porta UDP 123 deve essere accessibile alle reti e ai dispositivi virtuali Hybrid Cloud Services. Possono essere specificati dei server NTP installati quando viene installato il dispositivo Hybrid Cloud Services.

Tabella 1. Requisiti di accesso alla porta

| Origine | Destinazione       | Porta | Protocollo | Scopo         | Servizi |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | DNS cliente | 53   | TCP/UDP  | Risoluzione nomi | DNS      |
| HCX    | NSX LB in IBM Cloud | 443 | TCP | Servizio di registrazione | HTTPS |
| HCX    | vCenter in IBM Cloud | 443 | TCP | Servizio HCX REST | HTTPS |
| HCX    | PSC in IBM Cloud | 443 | TCP | Servizio HCX REST | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | Servizio di registrazione | HTTPS |
| Browser web | HCX | 9443 | TCP | Interfaccia di gestione del dispositivo virtuale HCX per la configurazione del sistema HCX | HTTPS |
| Rete di gestione | HCX | 22 | SSH | Accesso SSH di amministrazione a Hybrid Cloud Services | SSH |
| HCX | Host ESXi | 902 | TCP | Invio delle istruzioni di provisioning e gestione da HCX agli host ESXi in IBM Cloud. | Interna |
| HCX | vCenter SSO Server | 7444 | TCP | vSphere Lookup Service |  |
| HCX | Server NTP | 123 | UDP | Sincronizzazione temporale | |
| HCX | Syslog |   | Utente configurato | Connessione tra HCX (il client) e il server Syslog. I valori per il protocollo e la porta Syslog sono specificati nel client vSphere. Ad esempio, la porta 514 per il protocollo UDP. | |
| HCX | Gateway cloud | 8123 | TCP | Invio delle istruzioni del servizio di replica basato sull'host a Hybrid Cloud Gateway. | HTTP |
| HCX | Gateway cloud | 9443 | TCP | Invio delle istruzioni di gestione all'Hybrid Cloud Gateway locale utilizzando l'API REST. | HTTP</br>HTTPS |
| Gateway cloud | L2C | 443 | TCP | Invio delle istruzioni di gestione dal gateway cloud a L2C quando L2C utilizza lo stesso percorso dell'Hybrid Cloud Gateway. | HTTP</br>HTTPS |
| Gateway cloud | L2C | 8443 | TCP | Istruzioni di gestione bidirezionale dal gateway cloud a L2C, quando L2C utilizza un percorso dati alternativo. | HTTP</br>HTTPS |
| L2C | L2C (remoto) | 443 | TCP | Istruzioni di gestione bidirezionale dal gateway cloud a L2C, quando L2C utilizza un percorso dati alternativo. | HTTP</br>HTTPS |
| Gateway cloud | Host ESXi | 80, 902  | TCP | Gestione e distribuzione OVF | Interna |
| Host ESXi | Gateway cloud | 31031, 44046 | TCP | Traffico di replica basato sull'host interno | Interna |
| Gateway cloud | Host ESXi | 8000  | TCP | vMotion (migrazione senza tempo di inattività) |  |
| Gateway cloud (locale) | Gateway cloud</br>(remoto) | 4500  | UDP | Internet Key Exchange (IKEv2) per incapsulare i carichi di lavoro per il tunnel bidirezionale | IPSEC |
| Gateway cloud (locale) | Gateway cloud</br>(remoto) | 500  | UDP | Internet Key Exchange (ISAKMP) per il tunnel bidirezionale | IPSEC |

## Link correlati
{: #hcx-archi-port-req-related}

* [Installazione e configurazione dell'HCX sull'origine](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
