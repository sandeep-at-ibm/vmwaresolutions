---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

keywords: release notes, what's new, version 3.0

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas sobre a liberação para V3.0
{: #relnotes_v30}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Fim do suporte para o VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

Em um esforço para consolidar nossas ofertas para uma melhor experiência do cliente, a plataforma {{site.data.keyword.vmwaresolutions_short}} não oferecerá mais o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, efetivo em 13 de maio de 2019.

Seguindo adiante, todos os clientes serão direcionados para o VMware vCenter Server on {{site.data.keyword.cloud_notm}}, nossa solução VMware Software-Defined Data Center principal no {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}}.

Os clientes existentes que usam o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} serão auxiliados a converter para o VMware vCenter Server on {{site.data.keyword.cloud_notm}} na data de término de suporte de 13 de maio de 2019.

Após 13 de maio, os recursos de gerenciamento para o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} serão congelados por meio do console do {{site.data.keyword.vmwaresolutions_short}} até que eles tenham sido convertidos para o VMware vCenter Server on {{site.data.keyword.cloud_notm}}. Os clientes que escolheram não ter sua instância do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} migrada ou convertida para o VMware vCenter Server on {{site.data.keyword.cloud_notm}} podem acessar suas instâncias por meio do console de infraestrutura do {{site.data.keyword.cloud_notm}}.

## Suporte removido para servidores Broadwell 2-CPU
{: #relnotes_v30-broadwell}

Iniciando com a liberação da V3.0, os servidores Broadwell 2-CPU não estão mais disponíveis para implementação para novas instâncias e clusters do vCenter Server, vCenter Server com Hybridity Bundle, vCenter Server with NSX-T e vSphere on {{site.data.keyword.cloud_notm}}. Ainda é possível incluir servidores em clusters existentes.

## Aprimoramentos de operação do Network File System
{: #relnotes_v30-nfs}

Iniciando com a liberação V3.0, é possível incluir ou remover simultaneamente o armazenamento NFS e os servidores ESXi em clusters que estão no estado **Pronto para uso**. Por exemplo, é possível incluir ou remover um servidor ESXi em um cluster e incluir ou remover o armazenamento NFS em outro cluster. Isso se aplica a todas as instâncias do vCenter Server e do vCenter Server with NSX-T.

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v30-vcs}

Esta liberação aplica os upgrades e melhorias a seguir:

* vSphere ESXi 6.7 Atualização 1 (construção 6.7.0-13004448)
* vSphere ESXi 6.5 Atualização 2 (construção 6.5.0-13004031)
* vCenter Server Appliance 6.7 Atualização 1b (construção 6.7.0-11727113)
* Platform Services Controller 6.7 Atualização 1b (construção 6.7.0-11727113) 

Para obter mais informações, consulte [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

O software Windows que é pedido para os serviços Microsoft Active Directory (AD) e DNS (Sistema de Nomes de Domínio) é submetido a upgrade para o Windows Server 2016 para ambas as opções de configuração: as VSIs (Instâncias de Servidor Virtual) e as duas VMs do Windows altamente disponíveis. Para obter mais informações sobre como selecionar os componentes do VMware, consulte [Software BOM para instâncias do vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software).

### Aprimoramentos de armazenamento vSAN
{: #relnotes_v30-vcs-vsan}

* Ao usar o armazenamento vSAN, o número de Bare Metal Servers que você pode pedir agora pode ser maior que quatro. Isso se aplica a todas as instâncias do vCenter Server, vCenter Server with Hybridity e vCenter Server with NSX-T.
* Iniciando com a liberação da V3.0, uma unidade de estado sólido M.2 é pedida com sua instância de armazenamento vSAN. Será possível pedir até 10 discos de capacidade ou um total de 12 discos de capacidade, se você selecionar a opção **Alto desempenho com Intel Optaine**.

Para obter mais informações, consulte a seção *Configurações de armazenamento* em:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [Ordenando o vCenter Server com instâncias do NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## Atualizações para serviços complementares
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

Na liberação atual, o HyTrust CloudControl 5.5 é instalado em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no HyTrust CloudControl 5.5, consulte [O que há de novo no HyTrust CloudControl Versão 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

A liberação atual instala o HyTrust DataControl 4.3 em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no HyTrust DataControl 4.3, consulte [O que há de novo no KeyControl e no DataControl Versão 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

A liberação atual instala o HyTrust KeyControl 4.3 em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no HyTrust KeyControl 4.3, consulte [O que há de novo no KeyControl e no DataControl Versão 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

A liberação atual instala o {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2, junto com o {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, em todas as instâncias recém-implementadas.

Para obter mais informações sobre os novos recursos no {{site.data.keyword.cloud_notm}} Private v3.1.2, consulte [O que há de novo no {{site.data.keyword.cloud_notm}} Private v3.1.2](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}.
Para obter mais informações sobre os novos recursos no {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, consulte [O que há de novo no {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Dois novos terminais estão agora disponíveis em Londres e no Leste dos EUA para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Configuração do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config).

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

A liberação atual instala o IBM Spectrum Protect™ Plus V10.1.3 em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.3, consulte [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

Agora você é capaz de incluir o Zerto on {{site.data.keyword.cloud_notm}} nas instâncias que são somente privadas. Se você escolhe instalar o Zerto em instâncias somente privadas, deve-se configurar seu próprio servidor proxy e também configurar o recurso Call Home para o Zerto. Para obter mais informações, consulte [Pedindo o Zerto on {{site.data.keyword.cloud_notm}} para instâncias que são somente de rede privada](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only).

## Documentação nova e atualizada

* A documentação está agora disponível para ajudar no upgrade de componentes do {{site.data.keyword.vmwaresolutions_short}} para o VMware vSphere 6.7. Esse upgrade será necessário se você desejar continuar se beneficiando da automação do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, consulte [Fazendo upgrade do software vCenter Server vSphere do VMware vSphere 6.5 para 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade).
* A documentação de referência está agora disponível para fornecer os IDs de usuário que o {{site.data.keyword.vmwaresolutions_short}} mantém para uso pela automação do {{site.data.keyword.cloud_notm}}. As mensagens possíveis que são exibidas nos logs do histórico da instância também estão disponíveis para sua revisão. Para obter mais informações, consulte [IDs de usuário da IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) e [Mensagens do histórico da instância](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages).
* A permissão **Reinicialização/Controle** foi incluída na tabela que descreve as permissões necessárias para a conta de infraestrutura do IBM Cloud. Para obter mais informações, consulte [Permissões para a conta de infraestrutura do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-cloud-infra-acct-req#cloud-infra-acct-req-permissions).
* A nova documentação de referência está disponível para as APIs a seguir. Para obter mais informações, consulte [Referência da API](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
  * Listar todas as mensagens de histórico para uma instância especificada do VMware vCenter Server
  * Incluir armazenamentos compartilhados em um cluster especificado
  * Excluir armazenamentos NFS de um cluster especificado

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v30-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
