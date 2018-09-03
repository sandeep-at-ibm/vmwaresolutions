---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Notas sobre a Liberação para V2.3

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em liberações diferentes, problemas conhecidos com o produto e dicas adicionais para usar o {{site.data.keyword.vmwaresolutions_full}}, veja o [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obter mais informações, veja [Tratando as vulnerabilidades Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

Esta liberação apresenta a oferta VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle. O vCenter Server with Hybridity Bundle é uma nuvem particular host que ajuda a estender de forma rápida e fácil sua infraestrutura no local na nuvem. O ambiente do VMware é baseado em licenças do VMware Software Defined Data Center fornecidas pela IBM e inclui o serviço VMware HCX on {{site.data.keyword.cloud_notm}} que conecta de forma fácil e segura um ambiente do vSphere 5.0+ no local a sites do {{site.data.keyword.cloud_notm}} para hibridismo de infraestrutura contínua e mobilidade de aplicativo verdadeira.

O serviço HCX on {{site.data.keyword.cloud_notm}} está disponível somente por meio da instância do vCenter Server with Hybridity Bundle. É possível fazer upgrade de sua instância do vCenter Server existente para uma instância do vCenter Server with Hybridity Bundle depois de aplicar pela primeira vez a atualização de software do vCenter Server V2.3 base. Para obter mais informações, veja [Aplicando atualizações em instâncias do vCenter Server](../vcenter/vc_applyingupdates.html).

Para obter mais informações sobre o vCenter Server with Hybridity Bundle, consulte os tópicos a seguir:

* [vCenter Server com visão Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_orderinginstance.html)

## Excluir suporte de cluster para as instâncias do vCenter Server e do Cloud Foundation

Agora é possível excluir clusters de uma instância sem ter que excluir a instância inteira. Para clusters implementados em instâncias da V2.2 ou anteriores, deve-se fazer upgrade da instância para a V2.3 para ser possível excluir os clusters incluídos na instância.

Para obter mais informações, veja os tópicos a seguir:

* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Incluindo, visualizando e excluindo clusters para instâncias do Cloud Foundation](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## Atualizações para instâncias do VMware vCenter Server

Esta liberação aplica os upgrades e melhorias a seguir:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 com o nível de correção ESXi650-201803001 aplicado)
*	VMware vCenter Server 6,5 Atualização 1g

### Aprimoramentos para instâncias e clusters do vCenter Server

Começando com a liberação V2.3, os novos modelos de CPU a seguir estão disponíveis para implementação quando você escolhe a configuração de Bare Metal **Customizado**:
* Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz
* Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz

Para obter mais informações, veja os tópicos a seguir:

* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Atualizações para instâncias do VMware Cloud Foundation

Esta liberação aplica os upgrades e melhorias a seguir:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 com o nível de correção ESXi650-201803001 aplicado)
*	VMware vCenter Server 6,5 Atualização 1g
*	VMware NSX for vSphere 6.3.5

## Atualizações para instâncias do VMware Federal

### Configuração de DNS para instâncias do VMware Federal

Agora, você tem a opção de selecionar a implementação de um único VSI (Virtual Server Instance) do Microsoft Windows Server para o Microsoft Active Directory (AD) ou duas máquinas virtuais do Microsoft Windows de alta disponibilidade no cluster de gerenciamento. Para V2.2, o único VSI do Microsoft Windows para Microsoft AD foi implementado automaticamente por padrão. A nova opção para selecionar duas máquinas virtuais do Microsoft Windows fornece mais privacidade a e opção para fazer backup e restauração das máquinas virtuais usando o serviço Veeam.

**Nota:** deverão ser fornecidas duas licenças do Microsoft Windows Server 2012 R2 se você configurar sua instância para usar as duas máquinas virtuais do Microsoft Windows. Use a licença da edição Microsoft Windows Server 2012 R2 Standard e/ou a licença da edição Microsoft Windows Server 2012 R2 Datacenter. Você tem 30 dias para ativar as máquinas virtuais.

Para obter mais informações, veja a seção *Configurações de interface de rede* em [Pedindo instâncias do VMware Federal](../vcenter/vc_fed_orderinginstance.html#network-interface-settings).

### Incluir e excluir o suporte de cluster para instâncias do VMware Federal

Agora é possível usar clusters para gerenciar servidores ESXi em instâncias do VMware Federal que são implementadas na V2.3 e liberações mais recentes para melhor gerenciamento de recursos e alta disponibilidade. Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão. É possível visualizar os detalhes do cluster na página de visão geral da instância ou incluir até um total de 10 clusters em uma instância. Quando você estiver expandindo ou contraindo a capacidade de uma instância, será possível selecionar em qual cluster incluir ou de qual cluster remover servidores ESXi.

Você também tem a opção de excluir um ou mais clusters da instância sem excluir a instância inteira.

Para obter mais informações, veja [Incluindo, visualizando e excluindo clusters para instâncias do VMware Federal](../vcenter/fed_addviewdeleteclusters.html).

## Atualizações para serviços complementares

### HyTrust CloudControl on IBM Cloud

O serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}} está agora disponível para instâncias do VMware Cloud Foundation e do VMware vCenter Server que estão executando o vSphere 6.5 e que são implementadas na V2.3 ou em liberações mais recentes ou submetidas a upgrade para elas. O serviço cumpre e controla a conformidade com relação a padrões de segurança e fornece controle de acesso baseado na função (RBAC). Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no data center do {{site.data.keyword.cloud_notm}}.

É possível pedir instâncias com o serviço incluído quando você pede a sua instância ou incluir esse serviço em suas instâncias existentes posteriormente.

Para obter mais informações, veja os tópicos a seguir:
* [Componentes e considerações para o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)
* [Gerenciando o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

O serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}} está agora disponível para instâncias do VMware Cloud Foundation e do VMware vCenter Server que estão executando o vSphere 6.5 e que são implementadas na V2.3 ou em liberações mais recentes ou submetidas a upgrade para elas. O serviço oferece criptografia avançada com gerenciamento de chave integrado para assegurar as cargas de trabalho ao longo de seus ciclos de vida. O serviço pode fornecer criptografia no nível do sistema operacional e no nível de dados, o que significa que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho pode ser criptografado e decriptografado.

É possível pedir instâncias com o serviço incluído quando você pede a sua instância ou incluir esse serviço em suas instâncias existentes posteriormente.

Para obter mais informações, veja os tópicos a seguir:
* [Componentes e considerações para o HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)
* [Gerenciando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

A liberação atual instala o IBM Spectrum Protect&trade; Plus V10.1.1, como o serviço de backup padrão, em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.1, consulte [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentação nova e atualizada

Uma nova orientação do developerWorks está disponível com instruções passo a passo sobre como incluir armazenamento na pós-implementação do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Para obter mais informações, veja [Incluindo armazenamento na pós-implementação do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Atualizações e aprimoramentos da interface com o usuário

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:
* **Consistência**: a interface com o usuário agora fornece uma aparência consistente com outros serviços no {{site.data.keyword.cloud_notm}}.
* **Facilidade de acesso**: agora é possível acessar as ofertas do VMware diretamente do **Catálogo** do {{site.data.keyword.cloud_notm}}.
* **Experiência de pedido aperfeiçoado e simplificado**: agora é possível concluir o pedido de uma instância do VMware e implementar seus serviços complementares em uma única interface. Além disso, o custo estimado é calculado e mostrado instantaneamente na mesma interface para que seja possível ajustar sua configuração com base em seu plano de custo.
* A opção de Bring Your Own License (BYOL) ao pedir instâncias ou incluir clusters não está disponível para usuários do Parceiro de Negócios.
* Várias mensagens de erro e aprimoramentos de dica de ferramenta foram feitos para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
