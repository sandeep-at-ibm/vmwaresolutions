---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmware-solutions


---

# Tabella di confronto delle offerte
{: #inst_comp_chart}

Consulta il seguente grafico per comprendere le differenze nel supporto delle funzioni per le istanze VMware vCenter Server e i cluster VMware vSphere.

| Funzione | vCenter Server | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Automazione avanzata con tecnologia {{site.data.keyword.IBM}} <sup>1</sup> | Sì | No. Auto-costruito e configurato |
| Opzioni di archiviazione | vSAN o NFS (archiviazione a livello di file condivisa) | vSAN o NFS |
| Numero di server ESXi nel cluster iniziale | 4 per vSAN e un minimo di 2 (3 consigliati) per NFS | 1 per ridimensionare un cluster esistente, 4 per il nuovo cluster vSAN e almeno 3 per il nuovo cluster con NFS |
| Numero massimo di server ESXi <sup>2</sup> | 59 per cluster | 60 per cluster |
| Distribuzione multisito automatizzata Cloud |Supportato per le nuove istanze distribuite nella V2.0 o successive | Supportato. Configurazione automatizzata non inclusa |
| Aggiunta di server ESXi | Supportato | Supportato. Configurazione automatizzata non inclusa |
| Rimozione di server ESXi | Supportato | Supportato. Configurazione automatizzata non inclusa |
| Supporto multicluster | Il numero massimo dipende dalle direttive di dimensionamento VMware | Supportato. Configurazione automatizzata non inclusa |
| Aggiornamento e correzione gestiti dal client dello stack VMware | Aggiornamenti gestiti dal client:<br/>Strumenti VMware nativi (VMware Update Manager) | Aggiornamenti gestiti dal client:<br/>Strumenti VMware nativi (VMware Update Manager) |
| Backup e ripristino | Manualmente utilizzando IBM Spectrum Protect Plus o Veeam | Soluzione di backup e ripristino non inclusa |
| SDN (software-defined networking) | NSX Base, Advanced o Enterprise | NSX Standard, Base o Enterprise. Configurazione automatizzata non inclusa |
| BYOL per vSphere e vSAN | Completamente supportato per cluster | Supportato |
| BYOL per vCenter e NSX | Completamente supportato per istanza | Supportato |
| Opzioni di aggiornamento licenze NSX | Aggiornamento disponibile da NSX Base ad Advanced o Enterprise e da NSX Advanced a Enterprise. | Nessuna |
| Edizioni della licenza vSAN | vSAN Advanced o Enterprise | vSAN Advanced o Enterprise  |
| Servizi aggiuntivi | Supportato | Non supportato dall'automazione di questa soluzione, ma puoi portare e installare il tuo proprio software. |
{: caption="Tabella 1. Funzioni supportate per i cluster vCenter Server e vSphere" caption-side="top"}

## Note
{: #inst_comp_chart-notes}

<sup>1</sup> Secondo un progetto convalidato e con verifica durante la distribuzione.

<sup>2</sup> Puoi aumentare il numero di server ESXi in un cluster vSAN fino a un massimo di 64. Per ulteriori informazioni, vedi _Quanti server ESXi posso aggiungere a un cluster?_ in [Domande frequenti sui server ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi).

## Link correlati
{: #inst_comp_chart-related}

* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Panoramica di VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Distinta base di VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
