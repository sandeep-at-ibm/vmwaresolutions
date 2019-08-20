---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview}

O Single-node Trial for Data Protection and Disaster Recovery permite testar
o {{site.data.keyword.cloud}} para migrar e recuperar cargas de trabalho do VMware para o {{site.data.keyword.cloud_notm}}. Além disso, o Single-node Trial for Data Protection and Disaster Recovery inclui os serviços Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}}.

O Single-node Trial é uma versão de avaliação do VMware vCenter Server on {{site.data.keyword.cloud_notm}} que fornece a plataforma VMware de único locatário que pode ser gerenciada usando as mesmas ferramentas que em ambientes locais. É possível aproveitar a velocidade e a escala da nuvem enquanto mantém o mesmo nível de controle e visibilidade que é fornecido no local.

A avaliação é projetada para migração de até 20 cargas de trabalho de desenvolvimento ou de teste simples usando o vCenter Server. A automação instalará e configurará o VMware HCX no {{site.data.keyword.cloud_notm}}, fornecerá uma chave de ativação local do HCX e instalará o Veeam on {{site.data.keyword.cloud_notm}} e o Zerto on {{site.data.keyword.cloud_notm}} em questão de horas. É possível fazer backup e replicar 20 máquinas virtuais (VMs) com o Veeam on {{site.data.keyword.cloud_notm}} e o Zerto on {{site.data.keyword.cloud_notm}}. 

O Single-node Trial for Data Protection and Disaster Recovery é somente para prova de conceito (POC). Não execute cargas de trabalho de trabalho de produção nesse ambiente. As funções de gerenciamento, como a inclusão e a remoção de hosts e clusters, o pedido de serviços de complemento adicionais e a aplicação de atualizações, não são suportadas.
{:important}

Após a implementação da instância do Single-node Trial, é possível usar o [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external} por meio do [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external} para obter assistência com sua assistência. Além disso, o [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} pode ajudar a acelerar a modernização do aplicativo por meio das práticas nativas de nuvem mais recentes.

Essa avaliação é destinada ao uso de até 90 dias. Os encargos contínuos mensais são cobrados com base em seu planejamento de faturamento e não quando a instância é solicitada. Se a instância não for cancelada no último dia de seu ciclo de faturamento ou antes, você será cobrado pelo mês seguinte. Uma avaliação de 90 dias pode resultar em quatro meses de cobranças, a menos que o cancelamento seja concluído antes do início do quarto mês.
{:note}

Quando você tiver concluído a avaliação, será possível excluir esse ambiente e provisionar um novo ambiente que atenda às suas necessidades de capacidade.

## Especificações técnicas para instâncias do Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview-tech-specs}

Os componentes a seguir estão incluídos em sua instância do Single-node Trial for Data Protection and Disaster Recovery.

A disponibilidade e a precificação de configurações padronizadas de hardware podem variar com base no {{site.data.keyword.CloudDataCent_notm}} que é selecionado para implementação.
{:note}

### Bare Metal Server
{: #dr_backup_bundle_overview-bare-metal}

Processador Skylake Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz com 384 GB de RAM para até cerca de 20 VMs

#### CPUs sobre-confirmações
{: #dr_backup_bundle_overview-cpu}

Supercomprometimento da CPU de 16:1 para gerenciamento do vCenter Server, HCX e 20 MVs de carga de trabalho do cliente

#### Supercomprometimentos de RAM
{: #dr_backup_bundle_overview-ram}

* Supercomprometimento de RAM de 1.22:1 para uma implementação de cluster de 20 MVs de carga de trabalho com 8 GB cada
* 1:1 (sem supercomprometimento) para uma implementação de cliente de nove MVs de carga de trabalho com 8 GB cada

### Armazenamento NFS
{: #dr_backup_bundle_overview-nfs-storage}

* 2 TB para gerenciamento
* 1 TB para a carga de trabalho do cliente (para 20 MVs do cliente)

### Especificações de rede para instâncias do Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview-networking-specs}

Os componentes de rede a seguir são pedidos:
*  Uplinks duais de rede pública e privada de 10 Gbps
*  Três VLANs (Virtual LANs): uma VLAN pública e duas VLANs privadas
*  Uma VXLAN (Virtual eXtensible LAN) com DLR (Distributed Logical Router) para comunicação leste-oeste potencial entre cargas de trabalho locais conectadas a redes de camada 2 (L2). A VXLAN é implementada como uma topologia de roteamento de amostra, que pode ser modificada, usada para construção ou ser removida. Também é possível incluir zonas de segurança, conectando mais VXLANs a novas interfaces lógicas no DLR.
*  Dois VMware NSX Edge Services Gateways:
  * Um serviço de gerenciamento seguro VMware NSX Edge Services Gateway (ESG) para tráfego de gerenciamento de saída HTTPS, que é implementado pela IBM como parte da tipologia de rede de gerenciamento. Esse ESG é usado pelas MVs de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação.

    Este ESG não está acessível a você e não pode ser usado. Se você o modificar, poderá não ser capaz de gerenciar a instância do Single-node Trial for Data Protection and Disaster Recovery por meio do console do {{site.data.keyword.vmwaresolutions_short}}. Além disso, observe que usar um firewall ou desativar as comunicações ESG para os componentes de gerenciamento externo da IBM fará com que o {{site.data.keyword.vmwaresolutions_short}} se torne inutilizável.
    {:important}
  * Um VMware NSX Edge Services Gateway seguro e gerenciado pelo cliente para tráfego de carga de trabalho de entrada e saída HTTPS, que é implementado pela IBM como um modelo que pode ser modificado por você para fornecer acesso VPN ou acesso público.

### Virtual Server Instances
{: #dr_backup_bundle_overview-vsi}

Os virtual server instances (VSIs) a seguir são pedidos:

* Uma VSI para o IBM CloudBuilder, que é cancelada após a conclusão da implementação da instância.
* Um VSI do Microsoft Windows Server para o Microsoft Active Directory (AD) é implementado e pode ser consultado. O VSI funciona como o DNS para a instância em que os hosts e as MVs são registrados.
* Uma VSI para o Zerto on {{site.data.keyword.cloud_notm}} - Zerto Virtual Manager.
* Uma VSI com o Complemento do S.O. Veeam Backup and Replication 9.5 e o Veeam Availability Suite 9.5.

### Licenças e taxas fornecidas pela IBM
{: #dr_backup_bundle_overview-license-and-fee}

As licenças a seguir são incluídas com seu pedido de instância do Single-node Trial for Data Protection and Disaster Recovery.

* As licenças do vCenter Server:
  * VMware vSphere Enterprise Plus 6.7u2
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

As instâncias do Single-node Trial for Data Protection and Disaster Recovery não suportam o recurso Bring Your Own License.
{:note}

## Especificações técnicas para o VMware HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-tech-specs}

O Single-node Trial for Data Protection and Disaster Recovery inclui o HCX on {{site.data.keyword.cloud_notm}}. Os componentes a seguir são ordenados e incluídos no serviço HCX on {{site.data.keyword.cloud_notm}}.

As instâncias do HCX local incluem apenas licenciamento e ativação.
{:note}

### Um par ativo/passivo de VMware NSX Edge Services Gateways para gerenciamento do HCX
{: #dr_backup_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gerenciamento HCX - Máquina virtual
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: VMDK de 60 GB

Os dispositivos HCX adicionais são implementados durante a configuração, conforme necessário, para conectividade L2, otimização de WAN e conexões de gateway.

### Especificações de rede para o HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-networking-specs}

* Uma sub-rede móvel pública com 16 endereços IP
* Duas sub-redes portáteis privadas com 64 endereços IP
* Oito endereços IP da sub-rede vMotion móvel privada

## Especificações técnicas para o Veeam on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-veeam-tech-specs}

O Single-node Trial for Data Protection and Disaster Recovery inclui o Veeam on {{site.data.keyword.cloud_notm}}. Os componentes a seguir são pedidos e incluídos no serviço Veeam on {{site.data.keyword.cloud_notm}}.

* Licença de 25 pacotes do Veeam Availability Suite
* Armazenamento de 4.000 GB
* Desempenho de armazenamento de 0,25 IOPS/GB
* Windows Server 2016 Standard Edition (64 bits)
* Cores de 4 x 2,0 GHz
* 8 GB de RAM
* Uplink de rede privada de 1 Gbps
* Disco de 100 GB (SAN)

## Especificações técnicas para o Zerto on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-zerto-tech-specs}

O Single-node Trial for Data Protection and Disaster Recovery inclui o Zerto on {{site.data.keyword.cloud_notm}}. Os componentes a seguir são pedidos e incluídos no serviço Zerto on {{site.data.keyword.cloud_notm}}.

* Licença do Zerto Virtual Replication V6.5u3
* Uma Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 núcleos x 2,0 GHz
* RAM de 4 GB
* Windows Server 2016 Standard Edition (64 bits)
* 100 GB (SAN) de disco

## Especificações técnicas para o IBM Cloud Automation Manager
{: #dr_backup_bundle_overview-cam-tech-specs}

O {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 é instalado usando a topologia de Desenvolvimento/Teste em todas as instâncias do Single-node Trial for Data Protection and Disaster Recovery. Para obter mais informações sobre o {{site.data.keyword.cloud_notm}} Automation Manager, consulte a [Documentação do {{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}.

## Links relacionados
{: #dr_backup_bundle_overview-related}

* [Recursos do VMware HCX](https://hcx.vmware.com/#/docs){:external}
* [Guia do Usuário do VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Gerenciando o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
