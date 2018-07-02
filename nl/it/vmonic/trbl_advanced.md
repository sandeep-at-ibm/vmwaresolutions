---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# Risoluzione dei problemi assistita

## Problema

In alcune situazioni, potrebbe verificarsi un problema più complicato e i file di log non sono sufficienti per completare l'analisi della causa principale e fornire una soluzione.

## Risoluzione

Per risolvere questo tipo di problemi, il team di supporto di {{site.data.keyword.vmwaresolutions_full}} deve accedere alla macchina virtuale (VM) di gestione di {{site.data.keyword.cloud_notm}}. Questa VM di gestione, chiamata IBM CloudDriver, è l'interfaccia principale utilizzata per gestire le istanze VMware Cloud Foundation e VMware vCenter Server distribuite.

Per motivi di sicurezza, l'accesso a IBM CloudDriver è limitato. Il team di supporto di {{site.data.keyword.vmwaresolutions_short}} richiederà l'approvazione del cliente e dopo averla ottenuta potrà accedere al componente CloudDriver utilizzando un server virtuale dell'infrastruttura {{site.data.keyword.cloud_notm}}. Questo server si collega all'ambiente attraverso la rete pubblica FCR (Frontend Customer Router) dell'infrastruttura {{site.data.keyword.cloud_notm}}.

Successivamente, il team di supporto di {{site.data.keyword.vmwaresolutions_short}} utilizza la chiave {{site.data.keyword.slapi_short}} dell'infrastruttura {{site.data.keyword.cloud_notm}} che era stata fornita per l'ordine e la configurazione dell'istanza (o, se necessario, la chiave aggiornata fornita dal cliente) per distribuire un server virtuale orario dell'infrastruttura {{site.data.keyword.cloud_notm}}.

All'account del cliente viene addebitato l'utilizzo degli strumenti IBM CloudBuilder per la risoluzione dei problemi. Al termine del debug e della correzione, il componente IBM CloudBuilder viene rilasciato.

Il server virtuale dell'infrastruttura {{site.data.keyword.cloud_notm}} utilizzato per la risoluzione del problemi viene distribuito con le seguenti specifiche:

* Viene utilizzata una VSI (Virtual Service Instance) del nodo pubblico CentOS 7 con 1 CPU e 1 GB di RAM.
* La VSI viene distribuita nello stesso data center e sulla stessa VLAN pubblica e privata primaria su cui si trova l'istanza.
* Uno script di post-installazione viene utilizzato con la distribuzione di VSI per impostare le regole del firewall che consentono solo le connessioni SSH in entrata da un insieme specifico di indirizzi IP che sono di proprietà e utilizzati dal team di supporto di {{site.data.keyword.vmwaresolutions_short}}.
* Il sistema di avvio del supporto che utilizza tali indirizzi IP viene eseguito su una VM dell'infrastruttura {{site.data.keyword.cloud_notm}} accessibile solo tramite una rete privata dell'infrastruttura {{site.data.keyword.cloud_notm}} privata e protetta da una coppia di sistemi Vyatta HA (alta disponibilità) dell'infrastruttura{{site.data.keyword.cloud_notm}}.
* Gli strumenti di sicurezza IBM, come QRadar®, Nessus e IBM BigFix®, vengono utilizzati per monitorare il sistema di avvio del supporto da eventuali minacce alla sicurezza.
