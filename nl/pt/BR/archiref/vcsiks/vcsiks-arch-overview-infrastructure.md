---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Rede e infraestrutura do IBM Cloud

## Virtual Routing and Forwarding (VRF)
As contas do {{site.data.keyword.cloud}} também podem ser configuradas como uma conta VRF. As contas VRF
fornecem funções semelhantes ao VLAN Spanning, ativando o roteamento
automático entre blocos de IP de sub-rede. Todas as contas com conexões de Link direto devem ser convertidas ou criadas como uma conta do VRF.

## Link Direto
O {{site.data.keyword.cloud_notm}} Direct Link Connect oferece acesso privado à infraestrutura do {{site.data.keyword.cloud_notm}} e a quaisquer outras nuvens vinculadas ao seu Provedor de serviços de rede por meio do {{site.data.keyword.CloudDataCent_notm}} local. Essa opção é perfeita para criar conectividade com múltiplas nuvens em um único ambiente.
Nós conectamos os clientes à rede do {{site.data.keyword.cloud_notm}} Private usando uma topologia de largura de banda compartilhada. Como ocorre com todos os produtos Direct Link, é possível incluir roteamento global, que permite tráfego de rede privada para todos os locais do {{site.data.keyword.cloud_notm}}.

## Redes privadas virtuais

### VPN do strongSwan
O serviço de VPN do IPSec do strongSwan fornece um canal de comunicação seguro de ponta a ponta sobre a Internet que é baseado no conjunto de protocolos padrão de mercado da Internet Protocol Security (IPSec).

### Hybridity (HCX)
O VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle amplia ininterruptamente as
redes de data centers no local para o {{site.data.keyword.cloud_notm}}, que permite
que máquinas virtuais (VMs) sejam migradas para e do {{site.data.keyword.cloud_notm}} sem
nenhuma conversão ou mudança.

## Estrutura física

A infraestrutura física necessária para implementar um cluster do vCenter Server requer
a especificação mínima a seguir.

Tabela 1. Especificações do vCenter Server

  | Implementação do NFS | Implementação de VSAN
---|---|---
Número de servidores | 3 | 4
CPU | 28 Núcleos 2.2 GHZ | 28 Núcleos 2.2 GHZ
Memória | 384 GB | 384 GB
Armazenamento | Mgmt: 2 TB 2 IOPS, Carga de trabalho: 2 TB 4 IOPS|Mín. SSD: 960 GB(x2)   

As opções de implementação do IKS variam com base nos requisitos do nó do trabalhador.

Tabela 2. Especificações do IKS

  | máquina virtual | Bare Metal
--|---|--
Número de servidores | 3 | 3
CPU | 2 – 56 núcleos | 4 – 28 núcleos
Memória | 4 GB - 242 GB | 32 GB - 512 GB
Armazenamento | 100 GB |  SATA: 2 TB / SSD: 960 GB

## Estrutura virtual

Figura 1. Estrutura física de implementações do IKS e do ICP

![Estrutura física do diagrama de implementação do
IKS e do ICP] (vcsiks-phy-ics-iks-deployment.svg)

Na instância do vCenter Server, os VMSs do cliente são implementados para os NSX
Edge Services Gateways (ESG) e Distributed Logical Routers (DLR) dedicados.

O ESG é configurado com um SNAT para permitir o tráfego de saída, ativando
a conectividade da Internet para fazer download dos pré-requisitos do ICP e a conectividade
com o GitHub e Docker ou um proxy da web pode ser usado para fornecer a conectividade da
Internet. O ESG é configurado para acessar serviços DNS e NTP por meio
da rede privada. A integração com a instância do IKS está disponível por meio
de rede do {{site.data.keyword.cloud_notm}} entre a instância do vCenter Server e o IKS.

## Componentes do vCenter Server

Figura 2. Componentes de plataforma do vCenter Server
![Diagrama do ambiente do vCenter Server](vcsiks-vcs-env.svg)

### Platform Service Controller
A implementação do vCenter Server usa um único platform services controller (PSC)
externo instalado em uma sub-rede móvel na VLAN privada associada a
VMs de gerenciamento. Seu gateway padrão é configurado para o backend customer router (BCR).

### vCenter Server
Como o PSC, o vCenter Server é implementado como um dispositivo.
Além disso, o vCenter é instalado em uma sub-rede móvel na
VLAN privada associada a VMs de gerenciamento. Seu gateway
padrão é configurado para o BCR.

### Gerenciador NSX
O NSX Manager é implementado no cluster do vCenter Server inicial. Além disso,
um endereço IP é designado ao NSX Manager por meio do bloco de
endereço móvel privado designado a componentes de gerenciamento.

### NSX Controllers
A automação do {{site.data.keyword.cloud_notm}} implementa três Controladores NSX dentro do cluster inicial. Os controladores são designados a endereços IP da
sub-rede móvel privada que é designada a componentes de gerenciamento.

### NSX ESGs/DLRs
Os pares do NSX Edge Services Gateway (ESG) são implementados. Em todos os casos, um par de gateway é usado para o tráfego de saída dos componentes de automação que residem na rede privada. Para o vCenter Server e o ICP, um segundo gateway, conhecido como a borda gerenciada por icp, é implementado e configurado com um uplink para a rede pública e uma interface que é designada à rede privada.
Qualquer componente NSX necessário, como o Distributed Logical Router (DLR), os comutadores lógicos e os firewalls, pode ser configurado pelo administrador. Para obter mais informações sobre os NSX Edges que são
implementados como parte da solução, veja [Guia de rede do vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

As tabelas a seguir resumem as especificações ESG/DLR do ICP.

Tabela 3. Especificações de ESG do ICP

Atributo |  Especificação
--|--
Gateway de Serviço de Edge | Dispositivo Virtual
Tamanho de borda Grande | Número de vCPUs 2
Memória	| 1 GB
Disco	| 1000 GB no armazenamento de dados local

Tabela 4. Especificações de DLR do ICP

Atributo  |  Especificação
--|--|
Roteador Lógico Distribuído |	Dispositivo Virtual
Tamanho de borda	Compacto | Número de vCPUs 1
Memória	| 512 MB
Disco | 1000 GB no armazenamento de dados local

## Componentes do IKS

Figura 3. Componentes do IKS
![Diagrama de componentes do IKS](vcsiks-iks-components.svg)

### Mestre do Kubernetes

O mestre do Kubernetes é encarregado de gerenciar todos os recursos de cálculo, rede e armazenamento no cluster. O mestre do Kubernetes assegura que seus apps e serviços conteinerizados sejam igualmente implementados nos nós do trabalhador no cluster.

###	Nó do trabalhador
Cada nó do trabalhador é uma máquina física (bare metal) ou uma VM
que é executada no hardware físico no ambiente de nuvem. Ao provisionar um nó do trabalhador, você determina os recursos que estão disponíveis para os contêineres hospedados nesse nó do trabalhador. Prontos para utilização,
os nós do trabalhador são configurados com um Mecanismo de Docker gerenciado pela IBM, recursos
de cálculo separados, rede e um serviço de volume. Os recursos de segurança integrada fornecem isolamento, capacidades de gerenciamento de recurso e conformidade de segurança do nó do trabalhador.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
