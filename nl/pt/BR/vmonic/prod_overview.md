---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-05"

---

# Sobre o IBM Cloud for VMware Solutions

O {{site.data.keyword.vmwaresolutions_full}} permite que você integre ou migre rápida e continuamente suas cargas de trabalho do VMware locais para o {{site.data.keyword.cloud_notm}} usando a infraestrutura do {{site.data.keyword.cloud_notm}} escalável, segura e de alto desempenho e a tecnologia de virtualização híbrida do VMware líder do setor.

O {{site.data.keyword.vmwaresolutions_short}} permite implementar facilmente seus ambientes virtuais do VMware e gerenciar os recursos de infraestrutura no {{site.data.keyword.cloud_notm}}. Ao mesmo tempo, é possível também usar seu console do produto VMware nativo familiar para gerenciar as cargas de trabalho do VMware.

## Benefícios do IBM Cloud for VMware Solutions

O {{site.data.keyword.vmwaresolutions_short}} fornece os seguintes benefícios principais:
* **Alcance global**: permite expandir sua área de cobertura em nuvem híbrida para até 30 {{site.data.keyword.CloudDataCents_notm}} de classe corporativa em todo o mundo.
* **Integração contínua**: ativa a integração contínua através da nuvem híbrida com a infraestrutura do {{site.data.keyword.cloud_notm}}.
* **Fornecimento rápido**: automatiza a implementação e a configuração do ambiente do VMware, que permite implementar rapidamente um ambiente do VMware de classe corporativa com {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} e servidores virtuais on demand.
* **Simplificação**: permite consumir uma plataforma de nuvem do VMware sem a necessidade de identificar, comprar, implementar e gerenciar a infraestrutura física subjacente (cálculo, armazenamento e rede) e as licenças de software.
* **Flexibilidade de expansão e contração**: permite expandir e contrair facilmente suas cargas de trabalho do VMware de acordo com suas necessidades de negócios.
* **Único console de gerenciamento**: fornece um único console para implementar, acessar e gerenciar os ambientes do VMware no {{site.data.keyword.cloud_notm}}.

## Ofertas de implementação

O {{site.data.keyword.vmwaresolutions_short}} fornece opções de implementação padronizadas e customizáveis de ambientes virtuais do VMware. Os tipos de implementação a seguir são oferecidos:
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: a oferta do vCenter Server permite implementar um ambiente virtual do VMware usando recursos customizados de cálculo, armazenamento e rede para melhor atender às suas necessidades de negócios.
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle**: a oferta vCenter Server with Hybridity é uma nuvem particular host que ajuda a estender de forma rápida e fácil sua infraestrutura no local para a nuvem. O ambiente do VMware é baseado nas licenças do Data Center definido pelo software VMware fornecido pela IBM e ele inclui o VMware Hybrid Cloud Extension (HCX). Usando o HCX, é possível conectar-se com segurança a um ambiente do vSphere 5.0+ no local com sites do IBM Cloud para hibridismo de infraestrutura contínua e mobilidade de aplicativo verdadeira.
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**: a oferta do Cloud Foundation fornece um ambiente virtual do VMware unificado usando recursos de cálculo, armazenamento e rede do {{site.data.keyword.cloud_notm}} padrão que são dedicados a cada implementação do usuário.
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**: a oferta do vSphere on {{site.data.keyword.cloud_notm}} fornece um serviço de virtualização customizável que combina o {{site.data.keyword.baremetal_short}} compatível com VMware, componentes de hardware e licenças para construir o seu próprio ambiente do VMware hospedado pela IBM.
* **NetApp ONTAP Select**: a oferta do NetApp ONTAP Select permite implementar um cluster de armazenamento definido por software que aborda suas necessidades para um dispositivo de armazenamento dedicado e altamente disponível com base no NetApp ONTAP Select.
* **VMware Federal on {{site.data.keyword.cloud_notm}}**: a oferta VMware Federal on {{site.data.keyword.cloud_notm}} fornece suporte para pedir uma instância do vCenter Server base além de fornecer a opção para proteger as instâncias implementadas, removendo informações confidenciais e a conexão de gerenciamento aberta para acesso contínuo à instância para funções de gerenciamento.

## Serviços adicionais

O {{site.data.keyword.vmwaresolutions_short}} permite incluir vários serviços no horário de pedido da instância ou após a implementação da instância. Os serviços a seguir são oferecidos:

### FortiGate Security Appliance on IBM Cloud

Este serviço implementa um par de HA de dispositivos da série FortiGate Security Appliance (FSA) 300 que podem fornecer serviços de firewall, roteamento, NAT e VPN para proteger a conexão de rede pública com o seu ambiente.

Este serviço está disponível somente para instâncias implementadas na V1.8 ou liberações mais recentes.

Para obter mais informações, veja [Gerenciando o FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

Este serviço implementa um par de HA de FortiGate Virtual Appliances que pode permitir a redução do risco ao implementar controles de segurança críticos em sua infraestrutura virtual.

Este serviço está disponível somente para instâncias implementadas na V2.0 ou liberações mais recentes.

Para obter mais informações, veja [Gerenciando o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

Este serviço otimiza o desempenho e assegura disponibilidade e segurança para aplicativos com o F5 BIG-IP Virtual Edition (VE).

Este serviço está disponível somente para instâncias implementadas na V1.9 ou em liberações mais recentes.

Para obter mais informações, veja [Gerenciando o F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### IBM Spectrum Protect Plus on IBM Cloud

Este serviço fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementá-lo como uma solução independente ou integrá-lo ao ambiente do IBM Spectrum Protect&trade; Plus para transferir cópias para armazenamento de longo prazo e controle de dados.

**Notas**:
* Este serviço está disponível apenas para instâncias que são implementadas na (ou que têm upgrade feito para a) V2.2 ou liberações mais recentes.
* Para instâncias que são implementadas na V2.3 ou liberações mais recentes, o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} é o serviço de backup padrão. O serviço fornece backup para VMs de gerenciamento automaticamente.
* Para instâncias que são implementadas na V2.2, esse serviço fornece proteção de dados somente para as VMs de carga de trabalho.

Para obter mais informações, veja [Gerenciando o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html).

### Veeam on IBM Cloud

Este serviço se integra continuamente ao seu ambiente do VMware para ajudá-lo a gerenciar o backup e restauração de todas as máquinas virtuais (VMs) em seu ambiente, incluindo o backup e restauração dos componentes de gerenciamento. Ele pode fornecer um objetivo do ponto de recuperação (RPO) de menos de 15 minutos após a configuração para seus dados.

Este serviço é configurado para fazer backup das VMs de gerenciamento imediatamente após a implementação de sua instância.

Este serviço está disponível somente para instâncias implementadas na V1.8 ou liberações mais recentes.

Para obter mais informações, veja [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

Este serviço fornece recursos de replicação e de recuperação de desastre para ajudar a proteger suas cargas de trabalho. Para obter mais informações, veja [Gerenciando o Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

### Serviços gerenciados do IMI

Estes serviços permitem que o IBM Integrated Managed Infrastructure (IMI) entregue serviços de gerenciamento remoto dinâmicos para uma ampla faixa de infraestruturas em nuvem.

Estes serviços estão disponíveis apenas para instâncias do Cloud Foundation.

Para obter mais informações, veja [Solicitando serviços gerenciados do IMI](../services/managing_imi.html).

## Links relacionados

* [Iniciar](../index.html)
* [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Visão geral do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
