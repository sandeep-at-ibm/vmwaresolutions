---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# Requisitos e planejamento para instâncias do NetApp ONTAP Select

Revise os seguintes requisitos antes de pedir suas instâncias do NetApp ONTAP Select. Planeje sua instância com base na localização do {{site.data.keyword.CloudDataCent}}, no desempenho da sua carga de trabalho e nos requisitos de capacidade.

## Requisitos da conta do IBM Cloud

A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos de conta do {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidade do data center do IBM Cloud

A implementação do NetApp ONTAP Select possui requisitos rigorosos na infraestrutura física. Portanto, é possível implementar instâncias apenas em {{site.data.keyword.CloudDataCents_notm}} que atendam aos requisitos. Os {{site.data.keyword.CloudDataCents_notm}} a seguir estão disponíveis para implementação do NetApp ONTAP Select:

Tabela 1. {{site.data.keyword.CloudDataCents_notm}} disponíveis para instâncias do NetApp ONTAP Select

| {{site.data.keyword.CloudDataCent_notm}} | Localização | Região | Opções do servidor |
|:------|:----------------|:----------------|:---------------------------|
| AMS03 | Amsterdã | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| CHE01 | Chennai | Ásia Pacífico | Alta capacidade
| DAL09 | Dallas | NA Sul | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| DAL10 | Dallas | NA Sul | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| DAL12 | Dallas | NA Sul | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| DAL13 | Dallas | NA Sul | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| FRA02 | Frankfurt | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| FRA04 | Frankfurt | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| HKG02 | Hong Kong | Ásia Pacífico | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| LON02 | Londres | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| LON04 | Londres | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| LON06 | Londres | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| MEL01 | Melbourne | Ásia Pacífico | Alto desempenho (Médio), alta capacidade
| MEX01 | Querétaro | NA Sul | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| MIL01 | Milão | Europa | Alto desempenho (Médio), alta capacidade
| MON01 | Montreal | NA Leste | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| OSL01 | Oslo | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| PAR01 | Paris | Europa | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| SAO01 | São Paulo | América do Sul | Alto desempenho (Grande), alta capacidade
| SEO01 | Seul | Ásia Pacífico | Alto desempenho (Grande), alta capacidade
| SJC03 | São José | Oeste ND | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| SJC04 | São José | Oeste ND | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| SNG01 | Cingapura | Ásia Pacífico | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| SYD01 | Sydney | Ásia Pacífico | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| SYD04 | Sydney | Ásia Pacífico | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| TOK02 | Tóquio | Ásia Pacífico | Alto desempenho (Grande), alta capacidade
| TOR01 | Toronto | NA Leste | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| WDC04 | Washington, DC | NA Leste | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| WDC06 | Washington, DC | NA Leste | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade
| WDC07 | Washington, DC | NA Leste | Alto desempenho (Médio), alto desempenho (Grande), alta capacidade

<!--## Capacity considerations-->

<!--For capacity information and considerations, see the _Bill of
Materials_ document on the [Reference Architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page.-->

## Links relacionados

* [Visão geral do NetApp ONTAP Select](np_netappoverview.html)
* [Pedindo instâncias do NetApp ONTAP Select](np_orderinginstances.html)
