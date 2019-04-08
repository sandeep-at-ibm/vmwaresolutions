---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a Liberação para V2.3
{: #relnotes_v23}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown
{: #relnotes_v23-spectre}

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware vCenter Server on IBM Cloud with Hybridity Bundle
{: #relnotes_v23-vcs-hybrid}

Esta liberação apresenta a oferta VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle. O vCenter Server with Hybridity Bundle é uma nuvem particular host que ajuda a estender de forma rápida e fácil sua infraestrutura no local na nuvem. O ambiente do VMware é baseado em licenças do VMware Software Defined Data Center fornecidas pela IBM e inclui o serviço VMware HCX on {{site.data.keyword.cloud_notm}} que conecta de forma fácil e segura um ambiente do vSphere 5.0+ no local a sites do {{site.data.keyword.cloud_notm}} para hibridismo de infraestrutura contínua e mobilidade de aplicativo verdadeira.

O serviço HCX on {{site.data.keyword.cloud_notm}} está disponível somente por meio da instância do vCenter Server with Hybridity Bundle. É possível fazer upgrade de sua instância do vCenter Server existente para uma instância do vCenter Server with Hybridity Bundle depois de aplicar pela primeira vez a atualização de software do vCenter Server V2.3 base. Para obter mais informações, veja [Aplicando atualizações em instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

Para obter mais informações sobre o vCenter Server with Hybridity Bundle, consulte os tópicos a seguir:

* [VCenter Server with Hybridity Bundle Visão Geral](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## Excluir suporte de cluster para as instâncias do vCenter Server e do Cloud Foundation
{: #relnotes_v23-delete-cluster}

Agora é possível excluir clusters de uma instância sem ter que excluir a instância inteira. Para clusters implementados em instâncias da V2.2 ou anteriores, deve-se fazer upgrade da instância para a V2.3 para ser possível excluir os clusters incluídos na instância.

Para obter mais informações, consulte [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances).

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v23-vcs}

Esta liberação aplica os upgrades e melhorias a seguir:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 com o nível de correção ESXi650-201803001 aplicado)
*	VMware vCenter Server 6,5 Atualização 1g

Começando com a liberação V2.3, os novos modelos de CPU a seguir estão disponíveis para implementação quando você escolhe a configuração de Bare Metal **Customizado**:
* Processador Dual Intel Xeon Silver 4110/Total de 16 núcleos, 2,1 GHz
* Processador Dual Intel Xeon Gold 5120/Total de 28 núcleos, 2,2 GHz

Para obter mais informações, veja os tópicos a seguir:

* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## Atualizações para instâncias do VMware Cloud Foundation
{: #relnotes_v23-vcf}

Esta liberação aplica os upgrades e melhorias a seguir:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 com o nível de correção ESXi650-201803001 aplicado)
*	VMware vCenter Server 6,5 Atualização 1g
*	VMware NSX for vSphere 6.3.5

## Atualizações para serviços complementares
{: #relnotes_v23-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v23-htcc}

O serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}} está agora disponível para instâncias do VMware Cloud Foundation e do VMware vCenter Server que estão executando o vSphere 6.5 e que são implementadas na V2.3 ou em liberações mais recentes ou submetidas a upgrade para elas. O serviço cumpre e controla a conformidade com relação a padrões de segurança e fornece controle de acesso baseado na função (RBAC). Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no data center do {{site.data.keyword.cloud_notm}}.

É possível pedir instâncias com o serviço incluído quando você pede a sua instância ou incluir esse serviço em suas instâncias existentes posteriormente.

Para obter mais informações, veja os tópicos a seguir:
* [Componentes e considerações para o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Gerenciando o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud
{: #relnotes_v23-htdc}

O serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}} está agora disponível para instâncias do VMware Cloud Foundation e do VMware vCenter Server que estão executando o vSphere 6.5 e que são implementadas na V2.3 ou em liberações mais recentes ou submetidas a upgrade para elas. O serviço oferece criptografia avançada com gerenciamento de chave integrado para assegurar as cargas de trabalho ao longo de seus ciclos de vida. O serviço pode fornecer criptografia no nível do sistema operacional e no nível de dados, o que significa que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho pode ser criptografado e decriptografado.

É possível pedir instâncias com o serviço incluído quando você pede a sua instância ou incluir esse serviço em suas instâncias existentes posteriormente.

Para obter mais informações, veja os tópicos a seguir:
* [Componentes e considerações para o HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Gerenciando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v23-spp}

A liberação atual instala o IBM Spectrum Protect&trade; Plus V10.1.1, como o serviço de backup padrão, em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.1, consulte [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentação nova e atualizada
{: #relnotes_v23-new-docs}

Uma nova orientação do developerWorks está disponível com instruções passo a passo sobre como incluir armazenamento na pós-implementação do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Para obter mais informações, veja [Incluindo armazenamento na pós-implementação do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v23-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:
* **Consistência**: a interface com o usuário agora fornece uma aparência consistente com outros serviços no {{site.data.keyword.cloud_notm}}.
* **Facilidade de acesso**: agora é possível acessar as ofertas do VMware diretamente do **Catálogo** do {{site.data.keyword.cloud_notm}}.
* **Experiência de pedido aperfeiçoado e simplificado**: agora é possível concluir o pedido de uma instância do VMware e implementar seus serviços complementares em uma única interface. Além disso, o custo estimado é calculado e mostrado instantaneamente na mesma interface para que seja possível ajustar sua configuração com base em seu plano de custo.
* A opção de Bring Your Own License (BYOL) ao pedir instâncias ou incluir clusters não está disponível para usuários do Parceiro de Negócios.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
