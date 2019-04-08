---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.baremetal_short}}, {{site.data.keyword.cloud_notm}}, database, application server

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 5. Determinazione della tua configurazione
{: #determine_configuration}

Le seguenti tabelle elencano le configurazioni {{site.data.keyword.baremetal_long}} disponibili con l'offerta {{site.data.keyword.cloud}} SAP-Certified Infrastructure. Per ulteriori considerazioni sull'esecuzione di SAP HANA in un ambiente virtualizzato, consulta [Distribuzioni server VMware ESXi](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server).

## Decifratura dei nomi server
{: #server-names}

Questo è un esempio di come decifrare i nomi server SAP HANA.

|Nome server |Convenzione di denominazione del componente |Significato|
| --- | --- | --- |
| BI.S2.H8401 | BI | Interfaccia Bluemix |
| | S2 | Series 2 (generazione processore) |
| | | S1 è Ivy Bridge/Haswell |
| | | S2 è Broadwell |
| | | S3 è Skylake/Kaby Lake |
| | H | Server certificato SAP |
| | 8 | 8-socket server |
| | 4 | 4 TB RAM |
| | 01 | Numero di revisione (00 viene avviata, 01 è la prima revisione e così via) |

## BI.S1.H512
{: #512_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1851 GB |
| Global hot spare | 1x 800 GB s3710 | `hdd8` | 800 GB GHS | 800 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | 50 |
|   | `/dev/sda3` | `/usr/sap` | 50 |
|   | `/dev/sda4` | `/hana/shared` | 512 |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 550 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 1851 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H1000
{: #1024_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2400 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3200 GB |
| Global hot spare | 1x 800 GB s3710 | `hdd16` | 800 GB GHS | 800 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | 50 |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 2400 |
|   | `/dev/sdb1` | `/hana/shared` | 1104 |
|   |  | `/hana/log` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 3200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4101
{: #H4101}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 1 + hot spare | 3x 3.84 TB 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3.84 TB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` |
|   | `/dev/sda4` | `/hana/log` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |

## BI.S2.H4100
{: #H4100}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 800 GB s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 1600 GB |
| RAID 5 | 4x 800 GB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 2400 GB |
| Dedicated hot spare | 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS | 800 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4201
{: #4201}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 1.92 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 5.76 TB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4200
{: #H4200}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 1.2 TB s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 2.4 TB |
| RAID 5 | 5x 1.2 TB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 4.8 TB |
| Dedicated hot spare | 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS | 800 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H2000
{: #2048_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4800 GB |
| RAID 10 | 106x 1.2 TB S3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7200 GB |
| Global hot spare | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |
| RAID 10-C hot spare | 1x 1.2 TB S3710 | `hdd23` | 1.2 TB Hotspare | 1.2 TB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4401
{: #H4401}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7.68 TB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8401
{: #H8401}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7.68 TB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `hana/data` | `rest` |


## BI.S2.H4400
{: #4096_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1.2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1.2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
|Global hot spare | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4400
{: #H4400}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1.2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1.2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
|Global hot spare | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |



## BI.S2.H8801
{: #H8801}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 15.36 TB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8800
{: #8192_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | +1 Hotspare | RAID1-A | 800 GB |
| RAID 5 | 8x 1.2 TB S3710 |  | RAID5-B | 8400 GB |
| RAID 5 | 18x 1.2 TB S3710 | +1 Hotspare | RAID5-C | 20400 GB |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | `rest` |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID5-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S3.H2192
{: #2192_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 | `hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 1 | 2x 960 GB 5100 | `hdd2, hdd3` | RAID1-B | 960 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd4` |  |  |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## BI.S3.H2384
{: #2384_GB_memory}

| RAID | Componenti | Unità | Array | Dimensione |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd` |  |  |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Array | Partizione | Nome | Dimensione (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## VMware
{: #vmware}

Sei responsabile per l'impostazione delle configurazioni correlate a VMware del tuo server. Puoi scegliere tra tre dimensioni-1 TB (BI.S2.H4100 (VMware)), 2 TB (BI.S2.H4200 (VMware)) e 4 TB (BI.S2.4400 (VMware)). Per ulteriori informazioni sulla configurazione di VMware sul tuo {{site.data.keyword.baremetal_short}} certificato SAP, consulta [Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window} (PDF).

## Passi successivi

Sei ora pronto ad avviare il provisioning del tuo {{site.data.keyword.baremetal_short}}. Consulta [Provisioning del tuo ambiente SAP HANA](/docs/infrastructure/sap-hana?topic=sap-hana-provision_environment#provision_environment) per i tuoi passi successivi.
