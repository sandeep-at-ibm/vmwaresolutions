---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Risoluzione delle vulnerabilità Spectre e Meltdown

Per risolvere le vulnerabilità Spectre e Meltdown, devi applicare una serie di patch in un ordine specifico.

## Aggiornamento del firmware

Per le informazioni più recenti sull'aggiornamento del firmware, vedi [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Aggiornamento delle istanze distribuite nella V2.0 o successive

Le istanze della V2.0 o successive sono state distribuite con VMware vSphere 6.5 e VMware vCenter Server 6.5. Entrambi questi componenti software richiedono l'applicazione di patch.

### Istanze vCenter Server distribuite nella V2.0 o successive

#### Per VMware vSphere 6.5

* Per tutte le nuove istanze della V2.6, vSphere verrà distribuito con le seguenti patch applicate: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG e ESXi650-201808403-BG.
* Per tutte le tue istanze esistenti distribuite prima della V2.5 ma aggiornate alla V2.5, tutti i nuovi cluster e server ESXi verranno aggiornati con le seguenti patch: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG e ESXi650-201808403-BG.
* Per tutti i tuoi server ESXi esistenti e per tutti i cluster o server ESXi che continui a distribuire prima di eseguire l'aggiornamento alla V2.5, devi applicare le seguenti patch: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG e ESXi650-201808403-BG dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch).

#### Per VMware vCenter Server 6.5

* Per tutte le tue nuove istanze della V2.6, vCenter Server verrà distribuito con le patch cumulative vCenter 6.5 U2c applicate.
* Per tutte le istanze esistenti distribuite prima della V2.6, devi applicare la patch vCenter 6.5 U2c dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch).

### Istanze Cloud Foundation distribuite nella V2.0 o successive

Per applicare le patch richieste per VMware vSphere 6.5 e VMware vCenter Server 6.5, devi aggiornare le tue istanze Cloud Foundation al bundle di patch VMware più recente. Per tutte le tue istanze e i tuoi server ESXi esistenti, ti verrà richiesto di applicare le patch nella pagina **Aggiorna e applica patch** della console {{site.data.keyword.vmwaresolutions_full}}. Per ulteriori informazioni, vedi [Applicazione di aggiornamenti alle istanze Cloud Foundation](../sddc/sd_applyingupdates.html).

### Cluster VMware vSphere distribuiti nella V2.0 o successive

Per tutti i nuovi cluster e server ESXi di VMware vSphere 6.5, devi applicare le seguenti patch: ESXi650-201808401-BG, ESXi650-201808402-BG e ESXi650-201808403-BG dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch).

Per tutti i cluster VMware vSphere 6.5 esistenti, devi applicare le seguenti patch: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG e ESXi650-201808403-BG dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch).

Per VMware vCenter Server 6.5, devi applicare la patch vCenter 6.5 U2c dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch) a tutti i tuoi server vCenter, appena distribuiti o esistenti.

## Istanze distribuite nella V1.9 o precedenti

Le istanze Cloud Foundation, le istanze vCenter Server e i cluster VMware vSphere della V1.9 o precedenti, sono stati distribuiti con VMware vSphere 6.0 e VMware vCenter Server 6.0.

### Istanze vCenter Server distribuite nella V1.9 o precedenti

Sia per VMware vSphere 6.0 che per VMware vCenter Server 6.0, devi applicare le patch (ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG e ESXi600-201808403-BG per vSphere e vCenter 6.0 U3h per vCenter Server) dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch) a tutte le tue istanze e ai tuoi server ESXi, appena distribuiti o esistenti.

### Istanze Cloud Foundation distribuite nella V1.9 o precedenti

Gli aggiornamenti per queste istanze saranno disponibili quando verranno rilasciati gli aggiornamenti del fornitore necessari da cui dipendono queste istanze.

### Cluster VMware vSphere distribuiti nella V1.9 o precedenti

Sia per VMware vSphere 6.0 che per VMware vCenter Server 6.0, devi applicare le patch (ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG e ESXi600-201808403-BG per vSphere e vCenter 6.0 U3h per vCenter Server) dal [sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch) a tutti i tuoi cluster e server ESXi vSphere, appena distribuiti o esistenti.

### Link correlati

* [Applicazione di aggiornamenti alle istanze Cloud Foundation](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Sito di patch dei prodotti VMware](https://my.vmware.com/group/vmware/patch)
