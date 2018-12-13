---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# Progettazione dettagliata

## Componenti di servizi comuni
I servizi comuni forniscono i servizi che vengono utilizzati da altri servizi nella piattaforma di gestione cloud. I servizi comuni includono i servizi di identità e di accesso, i servizi di nome dominio e i servizi NTP.

Figura 1. Servizi comuni di ICP ({{site.data.keyword.cloud_notm}} Private)

![Servizi comuni ICP](vcsicp-icp-commonservices.svg)

### Servizi di identità e accesso
Come parte dell'automazione di VMware vCenter Server on {{site.data.keyword.cloud}}, per la gestione delle identità viene utilizzato un Microsoft AD (Active Directory). Viene distribuita una singola VSI (Virtual Server Instance) AD. Il vCenter è configurato per utilizzare l'autenticazione AD e puoi configurare ICP per l'autenticazione LDAP.

###	DNS (Domain Name Service)
La distribuzione di vCenter Server utilizza le VSI AD distribuite come server DNS per l'istanza. Tutti i componenti distribuiti, quali gli host ESXi, vCenter, PSC e NSX, sono configurati per puntare ad AD come loro DNS predefinito.

###	Servizi NTP
La distribuzione vCenter Server utilizza i server NTP dell'infrastruttura {{site.data.keyword.cloud_notm}}. Tutti i componenti distribuiti sono configurati per utilizzare questi server NTP. Per il corretto funzionamento dei certificati e dell'autenticazione AD, è fondamentale che tutti i componenti all'interno della progettazione utilizzino gli stessi server NTP.

## Rete

### Rete NSX-V

NSX-V è progettata in modo che una singola piattaforma del gestore NSX-V sia collegata ad una singola istanza vCenter Server. Fornisce i servizi di rete alle applicazioni che vengono eseguite all'interno di un ambiente vSphere.

Utilizzando la rete NSX-V inclusa nella distribuzione VCS, possiamo distribuire ICP in una rete di sovrapposizione VXLAN.

ICP è distribuito con lo stack di rete Calico predefinito per Kubernetes, che fornisce l'isolamento di rete all'interno del tuo cluster.

Figura 2. ICP con rete NSX-V

![ICP con rete NSX-V](vcsicp-nsxv-networking.svg)

Per ulteriori informazioni, vedi [Guida di rete di vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

### Rete NSX-T

NSX-T è progettata in modo che una singola piattaforma di rete possa connettersi a qualsiasi tipo di applicazione, basata su macchina virtuale o contenitore, in esecuzione all'interno o all'esterno di un ambiente vSphere.

ICP fornisce un'opzione per sostituire la rete di Calico con un'istanza NSX-T, fornendo una singola ubicazione per la gestione della rete e della sicurezza.

Figura 3. ICP con rete NSX-T

![ICP con rete NSX-T](vcsicp-icp-nsxt-networking.svg)

### Link correlati

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
