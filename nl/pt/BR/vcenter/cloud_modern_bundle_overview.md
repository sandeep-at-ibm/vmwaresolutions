---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do Single-node Trial for Migration and App Modernization

O Single-node Trial for Migration and App Modernization permite que você teste a unidade do IBM Cloud para migrar cargas de trabalho do VMware para o IBM Cloud e, em seguida, modernizar cargas de trabalho simples usando contêineres.

O Single-node Trial é uma versão de avaliação do IBM Cloud Private Hosted no VMware vCenter Server on IBM Cloud que fornece a plataforma de gerenciamento do Kubernetes para contêineres e a plataforma VMware de único locatário que pode ser gerenciada usando as mesmas ferramentas que em ambientes no local. É possível aproveitar a velocidade e a escala da nuvem enquanto mantém o mesmo nível de controle e visibilidade que é fornecido no local.

A avaliação é projetada para migração de até 20 cargas de trabalho de desenvolvimento ou de teste simples usando o vCenter Server on IBM Cloud with Hybridity Bundle e a conteinerização dessas cargas de trabalho com a plataforma de desenvolvimento de aplicativo IBM Cloud Private Hosted baseada em Kubernetes. A automação instalará e configurará o VMware HCX no IBM Cloud, fornecerá uma chave de ativação do HCX no local e instalará e configurará uma pequena topologia de desenvolvimento/teste do IBM Cloud Private Hosted em uma questão de horas.

O Single-node Trial for Migration and App Modernization é somente para prova de conceito (POC). Não execute cargas de trabalho de trabalho de produção nesse ambiente. Funções de gerenciamento, como a inclusão e a remoção de hosts e clusters, o pedido de serviços complementares e a aplicação de atualizações, não são suportadas.
{:important}

Para obter o máximo da instância do Single-node Trial, é possível usar o [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf) por meio de [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html), que pode ajudar a migrar suas cargas de trabalho do VMware para o IBM Cloud. Além disso, o [IBM Cloud Garage Services](https://www.ibm.com/cloud/garage/) pode ajudar a acelerar a modernização de aplicativo por meio das práticas nativas de nuvem mais recentes.

Essa avaliação é destinada ao uso de até 90 dias. Quando você tiver concluído a avaliação, será possível excluir esse ambiente e provisionar um novo ambiente que atenda às suas necessidades de capacidade.
{:note}

## Especificações técnicas para instâncias do Single-node Trial for Migration and App Modernization

Os componentes a seguir estão incluídos em sua instância do Single-node Trial for Migration and App Modernization.

A disponibilidade e a precificação de configurações padronizadas de hardware podem variar com base no {{site.data.keyword.CloudDataCent_notm}} que é selecionado para implementação.
{:note}

### Bare Metal Server

Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2.2 GHz com 384 GB de RAM) para até cerca de 20 MVs

#### CPUs sobre-confirmações

* Supercomprometimento da CPU de 16:1 para gerenciamento do vCenter Server, HCX e 20 MVs de carga de trabalho do cliente
* Supercomprometimento da CPU de 11:1 para o IBM Cloud Private

#### Supercomprometimentos de RAM

* Supercomprometimento de RAM de 1.22:1 para uma implementação de cluster de 20 MVs de carga de trabalho com 8 GB cada
* 1:1 (sem supercomprometimento) para uma implementação de cliente de nove MVs de carga de trabalho com 8 GB cada

### Armazenamento NFS

* 2 TB para gerenciamento
* 1 TB para a carga de trabalho do cliente (para 20 MVs do cliente)
* 4 TB para o IBM Cloud Private Hosted

### Especificações de rede para instâncias do Single-node Trial for Migration and App Modernization

Os componentes de rede a seguir são pedidos:
*  Uplinks duais de rede pública e privada de 10 Gbps
*  Três VLANs (Virtual LANs): uma VLAN pública e duas VLANs privadas
*  Uma VXLAN (Virtual eXtensible LAN) com DLR (Distributed Logical Router) para comunicação leste-oeste potencial entre cargas de trabalho locais conectadas a redes de camada 2 (L2). A VXLAN é implementada como uma topologia de roteamento de amostra, que pode ser modificada, usada para construção ou ser removida. Também é possível incluir zonas de segurança, conectando mais VXLANs a novas interfaces lógicas no DLR.
*  Dois VMware NSX Edge Services Gateways:
  * Um serviço de gerenciamento seguro VMware NSX Edge Services Gateway (ESG) para tráfego de gerenciamento de saída HTTPS, que é implementado pela IBM como parte da tipologia de rede de gerenciamento. Esse ESG é usado pelas MVs de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação.

    Este ESG não está acessível a você e não pode ser usado. Se você o modificar, talvez não seja possível gerenciar a instância do Single-node Trial for Migration and App Modernization por meio do console do {{site.data.keyword.vmwaresolutions_short}}. Além disso, observe que usar um firewall ou desativar as comunicações ESG para os componentes de gerenciamento externo da IBM fará com que o {{site.data.keyword.vmwaresolutions_short}} se torne inutilizável.
    {:important}
  * Um VMware NSX Edge Services Gateway seguro e gerenciado pelo cliente para tráfego de carga de trabalho de entrada e saída HTTPS, que é implementado pela IBM como um modelo que pode ser modificado por você para fornecer acesso VPN ou acesso público.

### Virtual Server Instances

Os virtual server instances (VSIs) a seguir são pedidos:

* Uma VSI para o IBM CloudBuilder, que é cancelada após a conclusão da implementação da instância.
* Um VSI do Microsoft Windows Server para o Microsoft Active Directory (AD) é implementado e pode ser consultado. O VSI funciona como o DNS para a instância em que os hosts e as MVs são registrados.

### Licenças e taxas fornecidas pela IBM

As licenças a seguir são incluídas com sua ordem de instância do Single-node Trial for Migration and App Modernization.

* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* IBM Cloud Privado Hospedado V3.1

As instâncias do Single-node Trial for Migration and App Modernization não suportam o Bring Your Own License.
{:note}

## Especificações técnicas para o VMware HCX on IBM Cloud

O Single-node Trial for Migration and App Modernization inclui o HCX on {{site.data.keyword.cloud_notm}}. Os componentes a seguir são ordenados e incluídos no serviço HCX on {{site.data.keyword.cloud_notm}}.

As instâncias do HCX local incluem apenas licenciamento e ativação.
{:note}

### Um par ativo/passivo de VMware NSX Edge Services Gateways para gerenciamento do HCX

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### HCX Management Appliance-máquina virtual

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: VMDK de 60 GB

Os dispositivos HCX adicionais são implementados durante a configuração, conforme necessário, para conectividade L2, otimização de WAN e conexões de gateway.

### Especificações de rede para o serviço HCX on IBM Cloud

* Uma sub-rede móvel pública com 16 endereços IP
* Duas sub-redes portáteis privadas com 64 endereços IP
* Oito endereços IP da sub-rede vMotion móvel privada

## Especificações técnicas para o IBM Cloud Private Hosted

O IBM Cloud Private Hosted V3.1 é instalado usando a topologia de Desenvolvimento/Teste em todas as instâncias do Single-node Trial for Migration and App Modernization. Para obter mais informações sobre o IBM Cloud Private Hosted, veja [Visão geral do IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services/icp_overview.html).

### Links relacionados

* [Guia do vCenter Server e do IBM Cloud Private](/docs/services/vmwaresolutions/archiref/vcsicp/vcsicp-intro.html)
* [Abra um chamado para o IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=en_US)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Obtendo o HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
