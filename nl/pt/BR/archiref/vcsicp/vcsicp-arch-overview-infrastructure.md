---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---


# Rede e infraestrutura do IBM Cloud

## Virtual Routing and Forwarding (VRF)

É possível configurar contas do {{site.data.keyword.cloud}} como uma conta VRF para fornecer funcionalidade semelhante ao VLAN Spanning, ativando o roteamento automático entre blocos de IP de sub-rede. Todas as contas com conexões de Link direto devem ser convertidas ou criadas como uma conta do VRF.

## Link Direto

I {{site.data.keyword.cloud_notm}} Direct Link Connect oferece acesso privado à sua infraestrutura do {{site.data.keyword.cloud_notm}} e a quaisquer outras nuvens vinculadas ao Provedor de Serviços de Rede por meio de seu data center local do IBM Cloud. Essa opção é perfeita para criar conectividade com múltiplas nuvens em um único ambiente. Uma topologia de largura da banda compartilhada é usada para conectar clientes à rede {{site.data.keyword.cloud_notm}} Private (ICP). Como ocorre com todos os produtos Direct Link, é possível incluir roteamento global, que permite tráfego de rede privada para todos os locais do {{site.data.keyword.cloud_notm}}.

## Redes privadas virtuais

### VPN do strongSwan

O serviço de VPN do IPSec do strongSwan fornece um canal de comunicação seguro de ponta a ponta sobre a Internet que é baseado no conjunto de protocolos padrão de mercado da Internet Protocol Security (IPSec).

### Hybridity (HCX)

O vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle amplia ininterruptamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, que permite que máquinas virtuais (VMs) sejam migradas para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.

## Estrutura física

A infraestrutura física necessária para implementar uma instância de produção do ICP em um cluster do VMware vCenter Server on {{site.data.keyword.cloud_notm}} requer a especificação mínima a seguir.

Tabela 1. Especificação do vCenter Server para o ICP

| Implementação do NFS | Implementação do vSAN | :--|:----:|:----: Número de servidores | 3 | 4 CPU | 28 núcleos 2.2 GHz | 28 núcleos 2.2 GHz de memória | 384 GB | 384 GB de armazenamento | Gerenciamento de 2.000 GB 2 IOPS/GB, Carga de trabalho de 2.000 GB 4 IOPS/GB, ICP de 4.000 GB 4 IOPS/GB | SSD mínima x 2 de 960 GB

Além dos requisitos de hardware do ICP, deve-se criar volumes persistentes no ambiente do ICP para armazenar dados do log e do banco de dados do Cloud Automation Manager (CAM). Embora o CAM suporte todos os tipos de volumes persistentes que o ICP suporta, as duas configurações de armazenamento recomendadas para o CAM são NFS e GlusterFS.

## Estrutura virtual

Figura 1. Estrutura física da implementação do vCenter Server e do ICP
![Estrutura física da implementação do VCS e do ICP](vcsicp-phy-ics-icp-deployment.svg)

Na instância do vCenter Server, a instância do ICP é implementada com um NSX Edge Services Gateway (ESG) dedicado e um Distributed Logical Router (DLR). A instalação do ICP é carregada na sub-rede VXLAN definida nos componentes anteriores.

O ESG é configurado com uma regra do Source NAT (SNAT) para permitir o tráfego de saída, ativando a conectividade de Internet para fazer download dos pré-requisitos do ICP e a conectividade com o GitHub e o Docker ou um proxy da web pode ser usado para fornecer a conectividade de Internet. O ESG também é configurado para fornecer acesso a serviços DNS e NTP.

O ESG também é configurado com uma regra de destino do NAT (DNAT) para os endereços IP virtuais do ICP Principal/Proxy da rede do {{site.data.keyword.cloud_notm}} 10.x por meio do ambiente VXLAN.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
