---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Design da infraestrutura de armazenamento conectado

O {{site.data.keyword.vmwaresolutions_full}} fornece a tecnologia VMware que é implementada de maneira automatizada no {{site.data.keyword.CloudDataCents_notm}} em todo o globo. Dentro do portfólio de soluções do {{site.data.keyword.cloud_notm}}, a oferta base VMware vCenter Server on {{site.data.keyword.cloud_notm}} consiste em até 10 clusters, cada um contendo até 59 hosts do vSphere, um único Platform Services Controller (PSC) e um vCenter Server Appliance capaz de gerenciar até 400 hosts e 4 mil máquinas virtuais.

A arquitetura apresentada aqui complementa a solução do vCenter Server, incluindo armazenamento conectado como um dispositivo de armazenamento compartilhado para o ambiente. O dispositivo de armazenamento conectado está localizado dentro do mesmo {{site.data.keyword.CloudDataCent_notm}} que a implementação do vCenter Server e consiste em um único compartilhamento do Network File System (NFS) ou múltiplas exportações do NFS do {{site.data.keyword.cloud_notm}}.

O gráfico a seguir descreve a arquitetura geral do armazenamento conectado na implementação do vCenter Server.

Figura 1. Arquitetura de alto nível do armazenamento conectado no {{site.data.keyword.cloud_notm}}

![Arquitetura de armazenamento conectado](../solution/physical_nfs.svg "Arquitetura de alto nível do armazenamento conectado no IBM Cloud")

## Design da infraestrutura física

A infraestrutura física consiste em três componentes principais: cálculo físico, armazenamento físico e rede física. A infraestrutura física inclui a rede de serviços do {{site.data.keyword.cloud_notm}} e o armazenamento físico que é usado pela infraestrutura.

## Design de rede física

A rede física é manipulada pelo {{site.data.keyword.cloud_notm}}. A seção a seguir descreve a rede física que é fornecida pelo {{site.data.keyword.cloud_notm}}, pois ela está relacionada ao armazenamento conectado.

### Visão geral da rede do IBM Cloud

A rede física do {{site.data.keyword.cloud_notm}} é separada em três redes distintas: pública, privada e de gerenciamento. Para obter mais informações sobre as redes pública, privada e de gerenciamento, consulte [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html).

Para obter mais informações sobre a rede do {{site.data.keyword.cloud_notm}}, consulte [A rede do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud-computing/bluemix/our-network){:new_window}.

Revise as informações a seguir para obter uma descrição da rede de serviços que faz parte da rede privada.

### Rede de serviços privados

O {{site.data.keyword.cloud_notm}} tem uma rede de serviços privados que fornece serviços comuns, como armazenamento de bloco, armazenamento de arquivo, Object Storage, resolvedores de DNS e servidores NTP. Essa rede privada é separada da rede privada do cliente e permite que os ambientes se conectem ininterruptamente aos serviços localizados no {{site.data.keyword.cloud_notm}}. A rede privada vem com multicamadas, em que os servidores e outra infraestrutura são conectados a comutadores de clientes de backend agregados (BCS). Esses comutadores agregados são conectados a um par de roteadores separados, como roteadores do cliente de back-end ou BCR, para rede L3. A rede privada também suporta a capacidade de usar quadros gigantes, como MTU 9000, para conexões de host físico.

### VLANs

Para obter mais informações sobre as VLANs, consulte a seção _Design da rede física_ em [Design da infraestrutura física](/docs/services/vmwaresolutions/archiref/solution/design_physicalinfrastructure.html).

## Design de armazenamento físico

A seção a seguir descreve a configuração do dispositivo de armazenamento conectado que está presente no {{site.data.keyword.cloud_notm}}. O dispositivo de armazenamento conectado complementa a solução existente do vCenter Server. Como resultado, os discos conectados localmente que são internos para os hosts físicos não são apresentados.

## Desempenho de Armazenamento Anexado

O desempenho e o armazenamento do Endurance são soluções de armazenamento do {{site.data.keyword.cloud_notm}} projetadas para suportar aplicativos de E/S alta que requerem níveis previsíveis de desempenho. Esse desempenho previsível é alcançado por meio da alocação de operações de entrada/saída por segundo (IOPS) no nível de protocolo para volumes individuais.

Os IOPS que variam de 100 a 48.000 podem ser pedidos com tamanhos de armazenamento de 20 GB a 12 TB. Os volumes de armazenamento do Performance e do Endurance estão disponíveis para armazenamento de bloco e armazenamento de arquivo.

Nesse design, a solução do vCenter Server oferece armazenamento do Endurance para armazenamento conectado. Como resultado, é possível selecionar e anexar (por meio de automação) as exportações de NFS do Endurance, cujo tamanho varia de 20 GB a um máximo de 12 TB. O {{site.data.keyword.cloud_notm}} permite que até 64 hosts do vSphere ESXi se conectem a uma única exportação de NFS do Endurance.

A Resistência está disponível em três camadas de desempenho de IOPS para suportar diferentes necessidades
do aplicativo.

Depois que um compartilhamento do NFS é solicitado, ele pode ser redimensionado ou reconfigurado para permitir mais ou menos IOPS.
{:note}

Para obter opções detalhadas de IOPS, consulte a seção _Configurações de armazenamento_ em [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html).

Além das camadas de armazenamento, o armazenamento do Endurance do {{site.data.keyword.cloud_notm}} suporta uma ampla seleção de necessidades do aplicativo, incluindo capturas instantâneas e replicação, além de criptografia em repouso nas localizações do {{site.data.keyword.CloudDataCent_notm}}.

### Links relacionados

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
