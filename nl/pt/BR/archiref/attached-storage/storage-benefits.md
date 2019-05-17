---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-13"

subcollection: vmware-solutions


---

# Sobre Armazenamento Anexado para o Servidor vCenter
{: #storage-benefits}

O armazenamento conectado é uma extensão da oferta VMware vCenter Server on {{site.data.keyword.cloud}}. A arquitetura da solução de armazenamento conectado para o VMware vCenter Server on {{site.data.keyword.cloud_notm}} detalha os componentes da solução e a configuração de alto nível de cada componente no design.

Para obter mais informações sobre o design do vCenter Server, consulte [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Benefícios importantes do armazenamento conectado para o vCenter Server
{: #storage-benefits-key-benefits}

Embora o armazenamento anexado não seja um pré-requisito para ambientes do VMware, seu uso como um dispositivo de armazenamento compartilhado fornece muitos benefícios aos usuários para operações de TI. O uso de dispositivos de armazenamento compartilhado pode ajudar a alcançar alta disponibilidade, planejador de recursos distribuídos, uso eficiente da capacidade de armazenamento e gerenciamento simplificado por meio da ativação das funções do vSphere descritas na tabela a seguir.

Tabela 1. Descrição das funções para armazenamento conectado para o vCenter Server

| Função | Descrição |
|:------- |:----------- |
| vSphere Distributed Resource Scheduler e Conjuntos de recursos | Esse recurso permite a abstração e o gerenciamento flexível de recursos por meio do balanceamento de carga e do posicionamento da máquina virtual (MV). Os conjuntos de recursos podem ser agrupados em hierarquias e usados para particionar hierarquicamente recursos de CPU e de memória disponíveis. |
| Alta Disponibilidade do vSphere | Esse recurso fornece HA para MVs (agrupando-as) e para os hosts que residem em um cluster. Os hosts no cluster são monitorados. Se ocorrer uma falha, as MVs em um host com falha serão reiniciadas em hosts alternativos. |
| Clusters do vSphere Datastore | Esse recurso fornece uma coleção de armazenamentos de dados com recursos compartilhados e uma interface de gerenciamento compartilhada. |
| Tolerância de Falhas do vSphere | Esse recurso fornece disponibilidade contínua para MVs, eliminando o tempo de inatividade e a interrupção, mesmo se ocorrer uma falha completa do host. |

## Links relacionados
{: #storage-benefits-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
