---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-31"

---

# Tabella di confronto delle offerte

Consulta la seguente tabella per comprendere le differenze nel supporto delle funzioni per le istanze VMware Cloud Foundation, VMware vCenter Server, VMware vCenter Server with Hybridity Bundle e i cluster VMware vSphere.

Tabella 1. Funzioni supportate per le istanze Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle e i cluster vSphere

| Funzione                          | Cloud Foundation    | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Automazione avanzata con tecnologia {{site.data.keyword.IBM}} <sup>1</sup> | Sì | Sì | Sì | No. Auto-costruito e configurato |
| Opzioni di archiviazione        | vSAN                | vSAN o archiviazione a livello di file condivisa (NFS) | vSAN | vSAN o archiviazione a livello di file condivisa (NFS) |
| Numero di server ESXi nel cluster iniziale | 4 | 4 per vSAN e un minimo di 2 (con 3 fortemente consigliato) per NFS | 4 | 1 per ridimensionare un cluster esistente, 4 per il nuovo cluster vSAN e almeno 3 per il nuovo cluster con NFS |
| Numero massimo di server ESXi <sup>2</sup> | 32 per cluster      | 59 per cluster     | 59 per cluster | 60 per cluster     |
| Distribuzione multisito automatizzata Cloud | Supportato per le nuove istanze distribuite nella V2.0 o successive | Supportato per le nuove istanze distribuite nella V2.0 o successive | Supportato | Supportato. Configurazione automatizzata non inclusa |
| Aggiunta di server ESXi              | Supportato           | Supportato | Supportato | Supportato. Configurazione automatizzata non inclusa |
| Rimozione di server ESXi           | Supportato           | Supportato | Supportato | Supportato. Configurazione automatizzata non inclusa |
| Supporto multicluster         | 5 cluster | 10 cluster | 10 cluster | Supportato. Configurazione automatizzata non inclusa |
| Aggiornamento e correzione gestiti dal client dello stack VMware | Aggiornamenti VMware | Non incluso | Non incluso | Non incluso |
| Backup e ripristino            | Manualmente utilizzando IBM Spectrum Protect Plus o Veeam | Manualmente utilizzando IBM Spectrum Protect Plus o Veeam | Manualmente utilizzando IBM Spectrum Protect Plus o Veeam | Soluzione di backup e ripristino non inclusa |
| SDN (software-defined networking)   | NSX Enterprise   | NSX Base, Advanced o Enterprise | NSX Advanced o Enterprise | NSX Standard, Base o Enterprise. Configurazione automatizzata non inclusa |
| BYOL per vSphere e vSAN | Completamente supportato per cluster   | Completamente supportato per cluster     | Non supportato | Supportato |
| BYOL per vCenter e NSX | Completamente supportato per istanza   | Completamente supportato per istanza     | Non supportato | Supportato |
| Opzioni di aggiornamento licenze NSX           | Nessuna   | Aggiornamento disponibile da NSX Base ad Advanced o Enterprise e da NSX Advanced a Enterprise. Aggiornamento disponibile a vCenter Server with Hybridity Bundle. | Aggiornamento disponibile da NSX Advanced a Enterprise  | Nessuna |
| Edizioni della licenza vSAN         | vSAN Advanced o Enterprise  | vSAN Advanced o Enterprise  | vSAN Advanced o Enterprise | vSAN Advanced o Enterprise  |
| Servizi aggiuntivi               | Supportato, HCX on {{site.data.keyword.cloud_notm}} escluso.  | Supportato, HCX on {{site.data.keyword.cloud_notm}} escluso. Aggiornamento disponibile a vCenter Server with Hybridity Bundle. | Supportato, HCX on {{site.data.keyword.cloud_notm}} incluso. | Non supportato dall'automazione di questa soluzione, ma puoi portare e installare il tuo proprio software. |

**Note**:

<sup>1</sup> Secondo un progetto convalidato e con verifica durante la distribuzione.

<sup>2</sup> Puoi aumentare il numero di server ESXi in un cluster vSAN fino a un massimo di 64. Per ulteriori informazioni, vedi _Quanti server ESXi posso aggiungere a un cluster?_ in [Domande frequenti sui server ESXi](faq_esxi.html).

### Link correlati

* [Domande frequenti](faq.html)
* [Panoramica di Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Panoramica di vCenter Server Hybridity](../vcenter/vc_hybrid_overview.html)
* [Panoramica di Vmware vSphere](../vsphere/vs_vsphereclusteroverview.html)
* [Distinta base di Cloud Foundation](../sddc/sd_bom.html)
* [Distinta base di vCenter Server](../vcenter/vc_bom.html)
* [Distinta base di Vmware vSphere](../vsphere/vs_bom.html)
