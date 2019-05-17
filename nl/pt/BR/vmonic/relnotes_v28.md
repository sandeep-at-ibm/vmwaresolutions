---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

subcollection: vmware-solutions


---

# Notas sobre a Liberação para V2.8
{: #relnotes_v28}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Instâncias do Single-node Trial for Migration and App Modernization
{: #relnotes_v28-single-node-trial}

O Single-node Trial for Migration and App Modernization é uma maneira rápida de testar a unidade do {{site.data.keyword.cloud_notm}} para migrar cargas de trabalho do VMware para o {{site.data.keyword.cloud_notm}} e, em seguida, modernizar as cargas de trabalho usando contêineres. Essa avaliação é uma versão do {{site.data.keyword.icpfull_notm}} Hosted on VMware vCenter Server on {{site.data.keyword.cloud_notm}} que fornece a plataforma de gerenciamento do Kubernetes para contêineres e a plataforma VMware de único locatário que pode ser gerenciada usando as mesmas ferramentas familiares que os ambientes no local.

Para obter mais informações, veja [Visão geral do Single-node Trial for Migration and App Modernization](/docs/services/vmwaresolutions?topic=vmware-solutions-cloud_modern_bundle_overview#cloud_modern_bundle_overview).

## Incluindo e removendo o armazenamento network file system
{: #relnotes_v28-nfs}

A partir da liberação V2.8, agora é possível incluir compartilhamentos de armazenamento network file system (NFS) em um cluster existente do NFS ou vSAN vCenter Server, bem como remover compartilhamentos de arquivo NFS de um cluster existente do vCenter Server.

Agora, as opções a seguir para armazenamento de nível de arquivo compartilhado customizado estão disponíveis:

* Tamanhos de compartilhamento de NFS iniciando em 20 GB até 12 TB em incrementos de GB único
* 0,25 IOPS/GB

Para obter mais informações, veja as seções *Incluindo armazenamento NFS em instâncias do vCenter Server* e *Removendo o armazenamento NFS de instâncias do vCenter Server* em [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).

## Suporte aos servidores Broadwell E5-2690 e E7-8890 certificados pela SAP
{: #relnotes_v28-broadwell-e5-e7}

A partir da liberação V2.8, os novos modelos de CPU do {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} estão disponíveis para implementação para instâncias e clusters do VMware vCenter Server on {{site.data.keyword.cloud_notm}} e VMware vSphere on {{site.data.keyword.cloud_notm}}:

* Processador Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.60 GHz/512 GB de RAM
* Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.20 GHz/1024 GB de RAM
* Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.20 GHz/2048 GB de RAM
* Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.20 GHz/4096 GB de RAM

Para obter mais informações, veja a seção *Configurações do {{site.data.keyword.baremetal_short_sing}}* em:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Suporte ao servidor Broadwell E7-4820 e E7-4850
{: #relnotes_v28-broadwell-e7}

A partir da liberação V2.8, os novos modelos de CPU do {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} estão disponíveis para implementação para instâncias e clusters do vCenter Server, vCenter Server with Hybridity Bundle, Cloud Foundation e vSphere on {{site.data.keyword.cloud_notm}}:

* Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 2.0 GHz
* Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.1 GHz

Para obter mais informações, veja a seção *Configurações do {{site.data.keyword.baremetal_short_sing}}* em:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Platform Services Controller Incorporado
{: #relnotes_v28-psc}

A partir da liberação V2.8, o vCenter Server é implementado com um PSC (Platform Services Controller) integrado, isto é, o vCenter Server, os componentes do vCenter Server e o PSC são implementados em uma única máquina virtual. Essa mudança se aplica a todas as instâncias do vCenter Server, do vCenter Server with Hybridity e do NetApp recém-implementadas.

Para instâncias que são submetidas a upgrade de uma liberação anterior para a V2.8, o PSC não é integrado ao vCenter Server. Se deseja usar o PSC integrado, deve converter de PSC externo para integrado por si mesmo.

Em uma configuração multisite em que a instância primária é uma instância com upgrade para a qual o PSC foi convertido manualmente de externo para integrado, qualquer instância secundária V2.8 implementada recentemente terá o PSC integrado.

Para obter mais informações, veja a seção *Arquitetura do vCenter Server* em [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture).

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v28-vcs}

Esta liberação aplica os upgrades e melhorias a seguir:

* vSphere ESXi 6.5 Atualização EP11 (construção 6.5.0-10719125)
* vCenter Server 6.5 U2d (construção 6.5.0-10964411)
* Platform Services Controller 6.5 U2d (construção 6.5.0-10964411)

## Atualizações para instâncias do VMware Cloud Foundation
{: #relnotes_v28-cf}

Esta liberação aplica os upgrades e melhorias a seguir:

* vSphere ESXi 6.5 Atualização EP11 (construção 6.5.0-10719125)
* vCenter Server 6.5 U2c (construção 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (construção 6.5.0-9451637)

## Atualizações para serviços complementares
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

A liberação atual instala o IBM Spectrum Protect™ Plus V10.1.2 em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.2, veja [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

Anteriormente, seria possível pedir uma instância do Cloud Foundation ou do vCenter Server com o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} incluído ou incluir o serviço em uma instância existente do Cloud Foundation ou do vCenter Server após a implementação inicial.

A partir da liberação V2.8, o serviço está disponível como um serviço independente sem estar associado a uma instância do VMware. Cada instância do serviço pode atender a uma ou mais instâncias do Cloud Foundation, instâncias do vCenter Server ou clusters do vSphere.

Para obter mais informações, consulte [Visão geral do KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations).

## Arquitetura de Referência da documentação
{: #relnotes_v28-ref}

(Atualizado em 08 de fevereiro de 2019) Os documentos técnicos a seguir são novos ou atualizados na seção *Referência* da documentação do usuário:

* [A arquitetura do {{site.data.keyword.vmwaresolutions_short}} (com NSX-V e NSX-T)
](/docs/services/vmwaresolutions/services?topic=vmware-solutions-solution_overview#solution_overview)
* [Arquitetura de referência do Caveonix RiskForesight](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [Guia de implementação e operações do HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/vcshcx?topic=vmware-solutions-vcshcx-intro)

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v28-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
