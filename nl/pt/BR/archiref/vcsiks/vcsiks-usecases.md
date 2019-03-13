---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-18"

---

# Casos de uso
{: #vcsiks-usecases}

## Migração de carga de trabalho para o IBM Cloud
{: #vcsiks-usecases-workload-mig}

A Acme Skateboards deseja ampliar de forma contínua seu VMware SDDC no local para uma instância do VMware vCenter Server on {{site.data.keyword.cloud}}. Ela precisa manter seus negócios em funcionamento e manter seu tempo de inatividade para o mínimo. Reconfigurar seus aplicativos para execução na nuvem não é uma solução ideal.

O VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle permite a criação de conexões contínuas entre o {{site.data.keyword.cloud_notm}} e um data center virtualizado do VMware no local.

A oferta vCenter Server with Hybridity Bundle do {{site.data.keyword.cloud_notm}} permite conexões seguras entre o site peer de origem no local e o site de destino do {{site.data.keyword.cloud_notm}}.

Figura 1. Serviços VMware Hybridity ![Serviços do VMware Hybrid Cloud Extension](vcsiks-hcx.svg)

O vCenter Server with Hybridity Bundle cria uma interconectividade fracamente acoplada entre o {{site.data.keyword.cloud_notm}} e no local e permite recursos como:
- **Interconectividade simples** – as conexões de rede lógica são estabelecidas facilmente sobre qualquer conexão física, incluindo a Internet pública, a VPN privada ou o {{site.data.keyword.cloud_notm}} Direct Link.
- **Extensão da camada 2** – as redes locais que incluem sub-redes no local e endereçamento IP são ampliadas para a nuvem.
- **Criptografia** – o tráfego de rede é criptografado com segurança entre os sites do mesmo nível.
- **Otimização de rede** – seleciona a melhor conexão e inunda eficientemente a conexão para que o tráfego da rede seja movido o mais rápido possível.
- **Deduplicação de dados** – até 50% de redução no tráfego de rede pode ser alcançado.
- **Roteamento inteligente** - quando uma carga de trabalho é movida, o roteamento de proximidade pode mudar o caminho de rede ou gateway para que o tráfego de rede use o gateway do site de destino e não “se prenda” de volta ao site de origem.
- **Migração de tempo de inatividade zero** - uma máquina virtual em execução pode ser movida para (ou voltar de) a nuvem usando vMotion.
- **Migração planejada** – qualquer número de máquinas virtuais pode ser replicado para o site de destino e, em seguida, ativado nesse site em um tempo designado para substituir os sistemas em execução no site de origem.
- **Migração de políticas de segurança** – se o NSX for usado no local, quaisquer políticas de segurança, firewalls e assim por diante serão movidos juntamente com a carga de trabalho.

Usando essa solução, a Acme Skateboards migrou com êxito suas cargas de trabalho do VMware no local para o {{site.data.keyword.cloud_notm}} atendendo a seus requisitos de pouco a nenhum tempo de inatividade e nenhuma reconfiguração de aplicativo.

## Implementação de arquitetura híbrida
{: #vcsiks-usecases-hybrid-archi-deployment}

O Acme Skateboards deseja implementar uma arquitetura híbrida no {{site.data.keyword.cloud_notm}} que consiste no vCenter Server e no {{site.data.keyword.icpfull_notm}}, para sua jornada para a modernização do aplicativo. Seus requisitos devem executar seus bancos de dados em máquinas virtuais, os aplicativos e os serviços da web em contêineres e usar um conjunto comum de ferramentas para gerenciamento de rede e segurança.

Figura 2. Aplicativo híbrido Acme Skateboards
![Diagrama do aplicativo híbrido Acme Skateboards](vcsiks-acme-app-arch.svg)

O {{site.data.keyword.vmwaresolutions_short}} fornece automação para implementar componentes de tecnologia do VMware em {{site.data.keyword.CloudDataCents_notm}} em todo o mundo. A arquitetura consiste em uma única região de nuvem e suporta a capacidade de ampliação para mais regiões de nuvem localizadas em outra geografia ou em outro pod do {{site.data.keyword.cloud_notm}} dentro do mesmo data center.

Os produtos {{site.data.keyword.icpfull_notm}} e Cloud Automation Manager (CAM) são implementados manualmente em sua plataforma de virtualização local, permitindo o gerenciamento de nuvem no local. Como alternativa, o {{site.data.keyword.icpfull_notm}} e o CAM são oferecidos como uma extensão de serviço para uma implementação nova ou existente do vCenter Server, via automação, permitindo o gerenciamento de nuvem por meio do {{site.data.keyword.cloud_notm}}.

O diagrama a seguir representa o {{site.data.keyword.icpfull_notm}} em execução na parte superior de uma instância do vCenter Server. O NSX-V é configurado com um comutador/VXLAN dedicado, um DLR e um ESG especificamente para a rede de sobreposição do {{site.data.keyword.icpfull_notm}}. O roteamento é configurado por meio do ESG para acesso à rede subjacente.

Usando a automação do {{site.data.keyword.cloud_notm}}, o Acme Skateboards pode provisionar uma solução híbrida que abrange o VMware on {{site.data.keyword.cloud_notm}} para executar suas MVs de banco de dados e o {{site.data.keyword.icpfull_notm}} on VMware on {{site.data.keyword.cloud_notm}} para executar seus apps e serviços da web de front-end em contêineres. O NSX fornece a eles um conjunto comum de ferramentas de gerenciamento para rede e segurança na rede de sobreposição.

## Links relacionados
{: #vcsiks-usecases-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
