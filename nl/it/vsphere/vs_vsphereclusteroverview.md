---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-26"

keywords: vSphere, vSphere component, tech specs vSphere

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di VMware vSphere on IBM Cloud
{: #vs_vsphereclusteroverview}

VMware vSphere on {{site.data.keyword.cloud}} è una piattaforma di ordinazione semplificata e ottimizzata per VMware. Con questa piattaforma, puoi creare il tuo proprio ambiente VMware ospitato su IBM personalizzando e ordinando l'hardware compatibile con VMware in base ai tuoi componenti VMware selezionati.

La console {{site.data.keyword.vmwaresolutions_short}} filtra l'hardware automaticamente, in base ai componenti VMware che hai selezionato. Ad esempio, quando crei un nuovo cluster VMware vSAN all-flash, viene presentato solo l'hardware convalidato rispetto alla [Guida alla compatibilità VMware](https://www.vmware.com/resources/compatibility/search.php){:external}. Inoltre, è richiesto un minimo di quattro server ESXi.

VMware vSphere on {{site.data.keyword.cloud_notm}} non automatizza l'istallazione, la configurazione e il richiamo dei componenti VMware facoltativi. La piattaforma consente il massimo della flessibilità per progettare e costruire il tuo ambiente VMware ospitato incorporando l'hardware compatibile con VMware.

Utilizza questa offerta per creare un nuovo cluster di server ESXi o ridimensionare un cluster esistente di server ESXi in un {{site.data.keyword.CloudDataCent_notm}}. A seconda dei componenti VMware che selezioni, puoi iniziare con un solo server ESXi e ridimensionare successivamente il cluster in base alle esigenze.

## Specifiche tecniche per i cluster VMware vSphere on IBM Cloud
{: #vs_vsphereclusteroverview-specs}

Esamina i componenti di VMware vSphere on {{site.data.keyword.cloud_notm}}.

La disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.
{:note}

### Componenti VMware
{: #vs_vsphereclusteroverview-specs-vmware-components}

Seleziona le licenze (fornite da IBM o BYOL) per i seguenti componenti VMware:
* VMware vSphere Enterprise Plus 6.7 U2 o 6.5 U2
* I seguenti componenti VMware sono facoltativi:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced o Enterprise)
   * VMware vSAN (Advanced o Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server
{: #vs_vsphereclusteroverview-specs-bare-metal}

Puoi ordinare una o più {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} con una delle seguenti configurazioni:
* **Skylake**: server di generazione 2-CPU Intel Skylake (Intel Xeon 4100/5100/6100 series) con il modello di CPU e la dimensione della RAM da te selezionati.
* **Cascade**: server di generazione 2-CPU Intel Cascade (Intel Xeon 4200/5200/6200 series) con il modello di CPU e la dimensione della RAM da te selezionati.
* **Certificato**: server di generazione Intel Skylake o Intel Broadwell (Intel Xeon 6140/E5-2690/E7-8890 series) con il modello di CPU da te selezionato.
* **Broadwell**: server di generazione 4-CPU Intel Broadwell (Intel Xeon E7-4800 series) con il modello di CPU e la dimensione della RAM da te selezionati.

Le opzioni disponibili variano a seconda che tu abbia selezionato o meno il componente VMware vSAN.

Inoltre, le seguenti specifiche di rete e disco:
* Doppi uplink di rete privata e pubblica da 10 Gbps
* Un controller disco RAID

### Rete
{: #vs_vsphereclusteroverview-specs-network}

* Una VLAN (Virtual LAN) pubblica e due VLAN private
* (Facoltativo) Una coppia HA di dispositivi FortiGate Security Appliance

### Archiviazione
{: #vs_vsphereclusteroverview-specs-storage}

Archiviazione personalizzata dall'utente per la configurazione vSAN quando è selezionato il componente VMware vSAN:
* Opzioni per disco di archiviazione di SED SSD da 960 GB, SED SSD da 1,9 TB o SED SSD da 3,8 TB
* Opzioni per quantità dei dischi di 2, 4, 6 o 8

  Inoltre, vengono ordinati anche due dischi di cache di 960 GB per ciascun host.

  Le unità SSD (Solid State Disk) da 3,8 TB sono supportate quando vengono rese generalmente disponibili in un data center.
  {:note}
* Opzione Alte prestazioni con Intel Optane, che fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità. Questa opzione dipende dal modello di CPU.

## Specifiche tecniche per i nodi di espansione del cluster vSphere
{: #vs_vsphereclusteroverview-expansion-node-specs}

Ogni nodo di espansione del cluster vSphere distribuisce e comporta addebiti per i seguenti componenti nel tuo account {{site.data.keyword.slportal}}.

### Hardware per i nodi di espansione
{: #vs_vsphereclusteroverview-expansion-node-specs-hardware}

Un Bare Metal Server {{site.data.keyword.cloud_notm}} con la configurazione hardware presentata in [Specifiche tecniche per i cluster VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

### Rete per i nodi di espansione
{: #vs_vsphereclusteroverview-expansion-node-specs-network}

Un Bare Metal Server {{site.data.keyword.cloud_notm}} con la configurazione networking presentata in [Specifiche tecniche per i cluster VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

### Componenti VMware per i nodi di espansione
{: #vs_vsphereclusteroverview-expansion-node-specs-vmware-components}

* Un Bare Metal Server {{site.data.keyword.cloud_notm}} con VMware vSphere Enterprise Plus 6.7u2 o 6.5u2.  
* Componenti VMware facoltativi presentati in [Specifiche tecniche per i cluster VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

Devi gestire i server ESXi, i componenti VMware facoltativi e l'hardware aggiuntivo ordinato e consegnato al tuo account {{site.data.keyword.cloud_notm}} solo attraverso il {{site.data.keyword.slportal}}. Dopo aver creato un nuovo cluster nella console {{site.data.keyword.vmwaresolutions_short}}, puoi tornare alla console e utilizzare le informazioni salvate per ridimensionare il nuovo cluster. Per ulteriori informazioni, vedi [Ridimensionamento di cluster vSphere esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).
{:important}

## Link correlati
{: #vs_vsphereclusteroverview-related}

* [Distinta base del software VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
* [Pianificazione per i cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Ordine di cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ridimensionamento di cluster vSphere esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
