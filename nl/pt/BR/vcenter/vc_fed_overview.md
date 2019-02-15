---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do VMware Federal on IBM Cloud

Com o VMware Federal on {{site.data.keyword.cloud}}, é possível pedir uma instância base do vCenter Server além de fornecer às agências do Governo federal dos EUA a opção de proteger as instâncias implementadas do vCenter Server. Ao proteger uma instância implementada, as informações confidenciais armazenadas sobre a instância são removidas. Além disso, a conexão aberta para acesso à instância é removida, o que significa que as funções de gerenciamento, como inclusão e remoção de hosts e clusters, não ficam mais disponíveis. Depois de selecionar a opção segura, a única função disponível é a exclusão da instância.

Para obter mais informações sobre o vCenter Server on {{site.data.keyword.cloud_notm}} e a arquitetura do vCenter Server, veja [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html).

O VMware Federal on {{site.data.keyword.cloud_notm}} oferece somente um subconjunto das ofertas do vCenter Server. A configuração multisite, Bring Your Own License e a opção para pedir serviços complementares não são suportados.
{:note}

## Especificações técnicas para instâncias do VMware Federal on IBM Cloud

Os componentes a seguir estão incluídos:

### Bare Metal Server

É possível pedir dois ou mais {{site.data.keyword.baremetal_short}} com uma das configurações a seguir:

* Geração Intel Broadwell de 2 CPUs (Série Intel Xeon E5-2600 v4)
* Geração Intel Skylake de 2 CPUs (série Intel Xeon 4100/5100/6100)

Para configuração de armazenamento NFS, o número recomendado de {{site.data.keyword.baremetal_short}} é configurado para o padrão de três.

Se você selecionar o armazenamento vSAN, a configuração exigirá quatro {{site.data.keyword.baremetal_short}}.
{:note}

### Rede

Os componentes de rede a seguir são pedidos:
*  Três VLANs (Virtual LANs): uma VLAN pública e duas VLANs privadas
*  Uma VXLAN (Virtual eXtensible LAN) com DLR (Distributed Logical Router) para comunicação leste-oeste potencial entre cargas de trabalho locais conectadas a redes de camada 2 (L2). A VXLAN é implementada como uma topologia de roteamento de amostra, que pode ser modificada, usada para construção ou ser removida. Também é possível incluir zonas de segurança, conectando mais VXLANs a novas interfaces lógicas no DLR.
*  Dois VMware NSX Edge Services Gateways:
  * Um serviço de gerenciamento seguro VMware NSX Edge Services Gateway (ESG) para tráfego de gerenciamento de saída HTTPS, que é implementado pela IBM como parte da tipologia de rede de gerenciamento. Este ESG é usado pelas máquinas virtuais de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação. Para obter mais informações, veja [Configurando sua rede para usar o ESG gerenciado pelo cliente](/docs/services/vmwaresolutions/vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Este ESG não está acessível a você e não pode ser usado. Se você modificá-lo, poderá não ser capaz de gerenciar a instância do vCenter Server do console do {{site.data.keyword.vmwaresolutions_short}}. Além disso, usar um firewall ou desativar as comunicações ESG para os componentes de gerenciamento externos da IBM fará com que o {{site.data.keyword.vmwaresolutions_short}} se torne inutilizável.
    {:important}
  * Um VMware NSX Edge Services Gateway seguro e gerenciado pelo cliente para tráfego de carga de trabalho de entrada e saída HTTPS, que é implementado pela IBM como um modelo que pode ser modificado por você para fornecer acesso VPN ou acesso público. Para obter mais informações, veja [O NSX Edge gerenciado pelo cliente representa um risco de segurança?](/docs/services/vmwaresolutions/vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-).

  O VMware NSX Edge Services Gateway (ESG) para o tráfego de gerenciamento HTTPS de saída foi removido como parte da ação para proteger a instância implementada do VMware Federal. Para obter mais informações, veja [Protegendo as instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html).
  {:note}

### Virtual Server Instances

As VSIs (Virtual Server Instances) a seguir são pedidas:
* Um VSI for IBM CloudBuilder, que será encerrado depois que a implementação da instância for concluída.
* (Para instâncias V2.3 e mais recentes) É possível escolher a implementação de um único Microsoft Windows Server VSI for Microsoft Active Directory (AD) ou duas MVs Microsoft Windows de alta disponibilidade no cluster de gerenciamento para ajudar a aprimorar a segurança e a confiabilidade.
* (Para instâncias V2.2) Um Microsoft Windows Server VSI for Microsoft Active Directory (AD) é implementado e pode ser consultado. Esse VSI funciona como o DNS para a instância em que os hosts e as máquinas virtuais são registrados.

### Armazenamento

Durante a implementação inicial, é possível escolher entre as opções de armazenamento vSAN e NFS.

#### Armazenamento vSAN

A opção vSAN oferece configurações customizadas, com várias opções para tipo de disco e quantidade:
* Quantidade de disco: 2, 4, 6 ou 8.
* Disco de armazenamento: SSD SED de 960 GB, SSD SED de 1,9 TB ou SSD SED de 3,8 TB.

  Além disso, são pedidos dois discos de cache de 960 GB por host.
* Opção Intel Optane de alto desempenho, que fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade. Essa opção depende do modelo de CPU.

#### Armazenamento NFS

A opção NFS oferece armazenamento compartilhado customizado no nível de arquivo para cargas de trabalho com várias opções para tamanho e desempenho:
* Tamanho: 1, 2, 4, 8 ou 12 TB.
* Desempenho: 2, 4 ou 10 IOPS/GB.
* Configure individualmente os compartilhamentos de arquivos.

Se você escolher a opção NFS, um compartilhamento de arquivo de 2 TB, 4 IOPS/GB para componentes de gerenciamento será pedido.

### Licenças e taxas fornecidas pela IBM

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
* (Para clusters do vSAN) VMware vSAN Advanced ou Enterprise 6.6

## Especificações técnicas para nós de expansão do VMware Federal on IBM Cloud

Cada nó de expansão do vCenter Server implementará e incorrerá em encargos para os componentes a seguir em sua conta do {{site.data.keyword.cloud_notm}}.

### Hardware para nós de expansão

Um Bare Metal Server com a configuração apresentada nas
[Especificações
técnicas para instâncias do VMware Federal on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances).

### Licenças e taxas para os nós de expansão

* Um VMware vSphere Enterprise Plus 6.5u1
* Um VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
* (Para clusters do vSAN) VMware vSAN Advanced ou Enterprise 6.6

Deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do
{{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console. Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.
{:important}

**CUIDADO:** gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}}, que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você solicitou a instância, fora do console do {{site.data.keyword.vmwaresolutions_short}} pode tornar seu ambiente instável. Estas atividades de gerenciamento incluem:
*  Incluindo, modificando, retornando ou removendo componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Desativando componentes

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhados.

### Links relacionados

* [Requisitos e planejamento para as instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html)
* [Pedindo instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/fed_addviewdeleteclusters.html)
* [Expandindo e contraindo a capacidade para instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_addingremovingservers.html)
* [Protegendo instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)
* [Armazenamento de arquivo e de bloco do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
