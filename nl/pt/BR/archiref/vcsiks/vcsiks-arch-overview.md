---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Visão geral da arquitetura
As ofertas do {{site.data.keyword.vmwaresolutions_full}} fornecem automação para implementar componentes de tecnologia do VMware em {{site.data.keyword.CloudDataCents_notm}} em todo o mundo. A arquitetura consiste em uma única região de nuvem e suporta a capacidade de se estender em mais regiões de nuvem localizadas em outra geografia e/ou em outro pod do {{site.data.keyword.cloud_notm}} dentro do mesmo data center.

É possível implementar manualmente os produtos {{site.data.keyword.cloud_notm}} Private (ICP) e Cloud Automation Manager (CAM) na plataforma de virtualização no local, ativando o gerenciamento da nuvem por meio de localizações no local. Como alternativa, o ICP e o CAM são oferecidos como extensões de serviço para uma implementação nova ou existente do VMware vCenter Server on {{site.data.keyword.cloud_notm}} por meio da automação, permitindo o gerenciamento de nuvem por meio do {{site.data.keyword.cloud_notm}}.

O ICP é uma plataforma de aplicativo para desenvolvimento e gerenciamento de aplicativos conteinerizados no local. O ICP é um ambiente integrado para gerenciar contêineres, que inclui o orquestrador de contêiner Kubernetes, um repositório de imagem privada, um console de gerenciamento e estruturas de monitoramento.

O IBM Multi-Cluster Manager fornece visibilidade do usuário, gerenciamento centrado
no aplicativo (política, implementações, funcionamento, operações) e conformidade
com base em política entre nuvens e clusters. Com o IBM Multi-Cluster Manager, você tem controle de seus clusters do Kubernetes. É possível assegurar que os clusters sejam seguros, operando com eficiência e entregando os níveis de serviço que os aplicativos esperam.

O {{site.data.keyword.cloud_notm}} Automation Manager é uma plataforma de gerenciamento de autoatendimento
multinuvem que é executada no {{site.data.keyword.cloud_notm}} Private que confere poderes aos Desenvolvedores e
administradores para atender às demandas de negócios. O Cloud Automation Manager
Service Composer permite que você exponha os serviços de nuvem híbrida no
catálogo do IBM Cloud Private.

## Plataforma de gerenciamento de nuvem do IBM Cloud

O diagrama a seguir exibe o ICP e o CAM implementados com a infraestrutura do
{{site.data.keyword.cloud_notm}}, com conexões ao vCenter no local e ao
serviço IBM Kubernetes Service (IKS) implementado no {{site.data.keyword.cloud_notm}}. Os usuários podem implementar máquinas virtuais (VMs) no local e VMs em
instâncias e contêineres do vCenter Server para o cluster do ICP e IKS.

Figura 1. Gerenciamento de nuvem do lado da nuvem
![Na nuvem - gerenciamento de nuvem](vcsiks-oncloud-cloudmgt.svg)

No diagrama, o CAM cria logicamente conexões em nuvem para os ambientes de vCenters, de provedores em nuvem, de ICP e de IKS. Os Clusters do ICP devem ser
implementados em cada data center ou ambiente de nuvem, com o MCM fornecendo o
mecanismo para conectar os clusters do ICP a uma única visualização de gerenciamento.

O ICP pode ser implementado com os componentes NSX-V ou NSX-T. O ICP com NSX-V permite que as VMs do ICP sejam executadas na rede VXLAN e usem a rede interna Calico do Kubernetes.

O ICP com o NSX-T permite que os usuários controlem e configurem a rede, a sub-rede, as políticas da UI central (NSX-T Manager). Para obter informações sobre as diferenças entre NSX-V e NSX-T, veja a
[Arquitetura de referência de Rede VCS do {{site.data.keyword.cloud_notm}}] (../vcsnsxt/vcsnsxt-intro.html).

## Plataforma de gerenciamento de nuvem no local

O diagrama a seguir exibe o ICP e o CAM implementados na infraestrutura
no local, com conexões com o vCenter e o IKS implementados no {{site.data.keyword.cloud_notm}}. Os usuários podem implementar VMs e contêineres
no local, VMs em instâncias e contêineres do vCenter Server
para o cluster do IKS.

Figura 2. Gerenciamento de nuvem do lado no local
![No local - gerenciamento de nuvem](vcsiks-onprem-cloudmgt.svg)

A VPN do strongSwan é usada para estabelecer conectividade com os contêineres implementados do IKS. O strongSwan pode eventualmente ser substituído por conectividade
de link direto.

No diagrama, o CAM cria logicamente conexões em nuvem para os ambientes de vCenters, de provedores em nuvem, de ICP e de IKS. Os clusters do ICP devem ser
implementados em cada data center ou ambiente de nuvem, com o MCM fornecendo o
mecanismo para conectar os clusters do ICP a uma única visualização de gerenciamento.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
