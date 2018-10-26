---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Panoramica di VMware vSphere on IBM Cloud

VMware vSphere on {{site.data.keyword.cloud}} è una piattaforma di ordinazione semplificata e ottimizzata per VMware. Con questa piattaforma, puoi creare il tuo proprio ambiente VMware ospitato su IBM personalizzando e ordinando l'hardware compatibile con VMware in base ai tuoi componenti VMware selezionati.

La console {{site.data.keyword.vmwaresolutions_short}} filtra l'hardware automaticamente, in base ai componenti VMware che hai selezionato. Ad esempio, quando crei un nuovo cluster VMware vSAN all-flash, viene presentato solo l'hardware convalidato rispetto alla [Guida alla compatibilità VMware](https://www.vmware.com/resources/compatibility/search.php). Inoltre, è richiesto un minimo di quattro server ESXi.

VMware vSphere on {{site.data.keyword.cloud_notm}} non automatizza l'istallazione, la configurazione e il richiamo dei componenti VMware facoltativi. La piattaforma consente il massimo della flessibilità per progettare e costruire il tuo ambiente VMware ospitato incorporando l'hardware compatibile con VMware.

Utilizza questa offerta per creare un nuovo cluster di server ESXi o ridimensionare un cluster esistente di server ESXi in un {{site.data.keyword.CloudDataCent_notm}}. A seconda dei componenti VMware che selezioni, puoi iniziare con un solo server ESXi e ridimensionare successivamente il cluster in base alle esigenze.

## Specifiche tecniche per i cluster VMware vSphere on IBM Cloud

Esamina i componenti di VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Nota:** la disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.

### Componenti VMware

Seleziona le licenze (fornite da IBM o BYOL) per i seguenti componenti VMware:
* VMware vSphere Enterprise Plus 6.0u2, 6.5u1 o 6.5u2
* I seguenti componenti VMware sono facoltativi:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced o Enterprise)
   * VMware vSAN (Advanced o Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

Seleziona uno o più {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}} con il modello di CPU e la dimensione della RAM da te selezionati:
* 2-CPU Intel Broadwell (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake (Intel Xeon 4100/5100/6100 series)

Le opzioni disponibili variano a seconda che tu abbia selezionato o meno il componente VMware vSAN.

Inoltre, le seguenti specifiche di rete e disco:
* Doppi uplink di rete privata e pubblica da 10 Gbps
* Un controller disco RAID

### Rete

* Una VLAN (Virtual LAN) pubblica e due VLAN private
* (Facoltativo) Una coppia HA di dispositivi FortiGate Security Appliance

### Archiviazione

Archiviazione personalizzata dall'utente per la configurazione vSAN quando è selezionato il componente VMware vSAN:
* Opzioni per disco di archiviazione di SED SSD da 960 GB, SED SSD da 1,9 TB o SED SSD da 3,8 TB
* Opzioni per quantità dei dischi di 2, 4, 6 o 8

  Inoltre, vengono ordinati anche due dischi di cache di 960 GB per ciascun host.

  **Nota:** le unità SSD (Solid State Disk) da 3,8 TB sono supportate quando vengono rese generalmente disponibili in un data center.
* Opzione Alte prestazioni con Intel Optane, che fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità. Questa opzione dipende dal modello di CPU.

## Specifiche tecniche per i nodi di espansione del cluster vSphere

Ogni nodo di espansione del cluster vSphere distribuisce e comporta addebiti per i seguenti componenti nel tuo account {{site.data.keyword.slportal}}.

### Hardware per i nodi di espansione

Un Bare Metal Server {{site.data.keyword.cloud_notm}} con la configurazione hardware presentata in [Specifiche tecniche per i cluster VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Rete per i nodi di espansione

Un Bare Metal Server {{site.data.keyword.cloud_notm}} con la configurazione di rete presentata in [Specifiche tecniche per i cluster VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Componenti VMware per i nodi di espansione

* Un Bare Metal Server {{site.data.keyword.cloud_notm}} con VMware vSphere Enterprise Plus 6.0u2 o 6.5u1  
* Componenti VMware facoltativi presentati in [Specifiche tecniche per i cluster VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

**Importante:** devi gestire i server ESXi, i componenti VMware facoltativi e l'hardware aggiuntivo ordinato e consegnato al tuo account {{site.data.keyword.cloud_notm}} solo attraverso il {{site.data.keyword.slportal}}. Dopo aver creato un nuovo cluster nella console {{site.data.keyword.vmwaresolutions_short}}, puoi tornare alla console e utilizzare le informazioni salvate per ridimensionare il nuovo cluster. Per ulteriori informazioni, vedi [Ridimensionamento di cluster vSphere esistenti](vs_scalingexistingclusters.html).

### Link correlati

* [Distinta base del software VMware vSphere](vs_bom.html)
* [Pianificazione per i cluster vSphere](vs_planning.html)
* [Ordine di cluster vSphere](vs_orderinginstances.html)
* [Ridimensionamento di cluster vSphere esistenti](vs_scalingexistingclusters.html)
