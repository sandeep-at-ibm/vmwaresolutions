---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Design de gerenciamento de infraestrutura

O gerenciamento de infraestrutura se refere aos componentes que estão gerenciando a infraestrutura do VMware. Esse design usa uma única instância externa do Platform Services Controller (PSC) e uma única instância do vCenter Server:
* O vCenter Server é a plataforma centralizada para gerenciar ambientes do vSphere e é um dos componentes fundamentais nessa solução.
* O PSC é usado nesta solução para fornecer um conjunto de serviços de infraestrutura, que incluem o VMware vCenter Single Sign On, o serviço de licença, o serviço de consulta e a autoridade de certificação do VMware.

As instâncias do PSC e as instâncias do vCenter Server são máquinas virtuais (VMs) separadas.

## Design do PSC

Esse design implementa um único PSC externo como um dispositivo virtual em uma sub-rede móvel na VLAN privada que está associada às VMs de gerenciamento. Seu gateway padrão é configurado para o Back-end Customer Router (BCR). O dispositivo virtual é configurado com as especificações na tabela a seguir.

Esses valores são configurados no momento da implementação e não podem ser mudados.
{:note}

Tabela 1. Especificações do Platform Services Controller

| Atributo                    | Especificação                  |
|------------------------------|--------------------------------|
| Platform Services Controller | Dispositivo Virtual              |
| Número de vCPUs              | 2                              |
| Memória                       | 4 GB                           |
| Disco                         | 114 GB no armazenamento de dados VMFS local |
| Tipo de disco                    | Thin provisioned               |

O PSC localizado na instância primária é designado ao domínio de SSO padrão de `vsphere.local`.

## Design do vCenter Server

O vCenter Server também é implementado como um dispositivo virtual. Além disso, o vCenter Server é instalado em uma sub-rede móvel na VLAN privada que está associada a VMs de gerenciamento. Seu gateway padrão é configurado para o endereço IP designado no BCR para essa sub-rede específica. O dispositivo virtual é configurado com as especificações na tabela a seguir.

Tabela 2. Especificações do vCenter Server Appliance

| Atributo                    | Especificação                       |
|------------------------------|-------------------------------------|
| vCenter Server               | Dispositivo Virtual                   |
| Tamanho da instalação do dispositivo  | Médio (até 400 hosts, 4.000 VMs) |
| Platform Services Controller | Externo                            |
| Número de vCPUs              | 8                                   |
| Memória                       | 24 GB                               |
| Disco                         | 400 GB no armazenamento de dados local           |
| Tipo de disco                    | Thin provisioned                    |

### Banco de dados do vCenter Server

A configuração do vCenter Server usa um banco de dados PostgreSQL local e integrado que é incluído com o dispositivo. O banco de dados integrado é usado para remover qualquer dependência e licenciamento de bancos de dados externos.

### Especificação de cluster do vCenter Server

Com esse design, é possível agrupar os hosts vSphere ESXi que são provisionados por meio da solução. No entanto, antes que os clusters possam ser criados, um objeto de data center é criado, que significa o local dos hosts vSphere ESXi, bem como o pod dentro do data center. Um cluster é criado após a criação do objeto data center. O cluster é implementado com o VMware vSphere High Availability (HA) e o VMware vSphere Distributed Resource Scheduler (DRS) ativados.

### Planejador de Recurso Distribuído do vSphere

Esse design usa o vSphere Distributed Resource Scheduling (DRS) no cluster inicial para colocar VMs e usa o DRS em clusters adicionais para migrar dinamicamente as VMs para alcançar clusters balanceados. O nível de automação é configurado para totalmente automatizado para que as recomendações iniciais de posicionamento e migração sejam executadas automaticamente pelo vSphere. Além disso, o limite de migração é configurado para moderado para que o vCenter aplique recomendações de prioridade 1, 2 e 3, para alcançar pelo menos uma melhoria decente no balanceamento de carga do cluster.

O gerenciamento de energia por meio do recurso **Distributed Power Management** não é usado neste design.
{:note}

### Alta Disponibilidade do vSphere

Esse design usa o vSphere High Availability (HA) no cluster inicial e clusters extras para detectar falhas de cálculo e recuperar VMs que são executadas dentro de um cluster. O recurso vSphere HA neste design é configurado com as opções **Monitoramento do host** e **Controle de admissão** ativadas no cluster. Além disso, o cluster inicial reserva os recursos de um nó como a capacidade sobressalente para a política de controle de admissão.

Você será responsável por ajustar a política de controle de admissão quando o cluster for expandido ou contraído posteriormente.
{:note}

Por padrão, a opção **Prioridade de reinicialização da VM** está configurada como média e a opção **Resposta de isolamento do host** está desativada. Além disso, o **Monitoramento de VM** está desativado e o recurso **Pulsação de armazenamento de dados** está configurado para incluir qualquer um dos armazenamentos de dados do cluster. Essa abordagem usará os armazenamentos de dados NAS se eles estiverem presentes.

## Automação

O elemento fundamental para essas soluções é a automação. A automação traz os benefícios a seguir:
* Reduz a complexidade da implementação.
* Drasticamente reduz o tempo de implementação.
* Assegura que a instância do VMware seja implementada de maneira consistente.

As VMs do {{site.data.keyword.IBM}} CloudBuilder, do IBM CloudDriver e do SDDC Manager trabalham juntas para iniciar uma nova instância do VMware e executar funções de gerenciamento de ciclo de vida.

### IBM CloudBuilder e IBM CloudDriver

O IBM CloudBuilder e o IBM CloudDriver Virtual Server Instance (VSI) são componentes desenvolvidos pela IBM que você não pode acessar.
* O IBM CloudBuilder é uma Virtual Server Instance (VSI) provisória do {{site.data.keyword.cloud_notm}} que autoinicializa a implementação, a configuração e a validação dos componentes da solução dentro dos hosts ESXi bare metal provisionados.
* O IBM CloudDriver VSI é implementado para criação de instância e então periodicamente, conforme necessário, com o código mais recente do {{site.data.keyword.cloud_notm}} for VMware para operações, como a implementação de mais nós, clusters ou serviços. O IBM CloudDriver se comunica com o console do {{site.data.keyword.vmwaresolutions_short}} por meio de um VMware NSX Edge Services Gateway, que é implementado exclusivamente para propósito de gerenciamento de instância e atua como um agente para manter a instância. O IBM CloudDriver é responsável por ações contínuas, como a adição de novos hosts bare metal ao cluster e a implementação de serviços de complemento para a instância. Para instâncias do Cloud Foundation, o IBM CloudDriver se comunica com a VM do VMware SDDC Manager para executar funções, como adição de host e correção.

É possível para o usuário excluir ou danificar as VMs descritas nas seções a seguir. Quando uma VM é removida, encerrada ou ela se torna inoperável, as operações a seguir do Cloud Foundation ou do vCenter Server no console do {{site.data.keyword.vmwaresolutions_short}} são interrompidas:
* Visualizando o status da instância ou do host
* Incluindo ou removendo clusters
* Incluindo ou removendo hosts ESXi
* Incluindo ou removendo serviços
* Corrigindo

### SDDC Manager

Para instâncias do Cloud Foundation, a VM do SDDC Manager é um componente que é desenvolvido e mantido pelo VMware. Ela permanece como parte da instância durante seu ciclo de vida inteiro. Ela é responsável pelas funções de ciclo de vida a seguir das instâncias:
* Gerenciamento de componentes do VMware: vCenter Server, Platform Services Controller (PSC), vSAN e NSX, incluindo alocação de endereço IP e resolução do nome do host.
* Expansão e retração de hosts ESXi dentro do cluster, que inclui qualquer serviço afetado, como NSX VTEP, vSAN e conjuntos de recursos.

Para instâncias do vCenter Server, essas atividades são executadas pelo IBM CloudDriver, uma vez que não há nenhum SDDC Manager.

### Fluxo de automação

O procedimento a seguir descreve a ordem de eventos quando uma instância do VMware é solicitada por meio do console do {{site.data.keyword.vmwaresolutions_short}}:
1.  Pedindo VLANs e sub-redes para rede do {{site.data.keyword.cloud_notm}}.
2.  Pedindo o  {{site.data.keyword.baremetal_short}}  com o vSphere Hypervisor instalado.
3.  Se aplicável, pedir o Microsoft Windows Virtual Server Instance (VSI) para servir como controlador de domínio do Active Directory.
4.  Validação da rede e do hardware implementado.
5.  Se aplicável, configuração inicial do vSAN de nó único.
6.  Se aplicável, implementação e configuração de duas máquinas virtuais do Microsoft Windows para servir como controladores de domínio do Active Directory.
7.  Implementação e configuração do vCenter, PSC e NSX.
8.  Armazenamento em cluster de nós ESXi restantes, expansão de vSAN se aplicável e configuração de componentes NSX (VTEP).
9.  Implementando a VM do VMware Cloud Foundation SDDC Manager, se aplicável, e o VSI do IBM CloudDriver.
10.  Validando a instalação e a configuração do ambiente.
11. Remoção do VSI do CloudBuilder.
12. Implementação de serviços opcionais, como servidor de backup e armazenamento.

### Links relacionados

* [ Design da infraestrutura física ](design_physicalinfrastructure.html)
* [ Design de infraestrutura virtual ](design_virtualinfrastructure.html)
* [ Design de serviços comuns ](design_commonservice.html)
