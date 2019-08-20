---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-16"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas sobre a liberação da V3.1
{: #relnotes_v31}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Instâncias do Single-node Trial for Data Protection and Disaster Recovery
{: #relnotes_v31-dr-bundle}

O Single-node Trial for Data Protection and Disaster Recovery é uma maneira rápida de testar o {{site.data.keyword.cloud_notm}} para migrar e recuperar cargas de trabalho do VMware para o {{site.data.keyword.cloud_notm}}. Essa avaliação é uma versão do VMware vCenter Server on IBM Cloud, uma plataforma VMware de único locatário que pode ser gerenciada usando as mesmas ferramentas familiares que os ambientes locais. Essa avaliação inclui os serviços do Veeam on {{site.data.keyword.cloud_notm}}, do VMware HCX on {{site.data.keyword.cloud_notm}} e do Zerto on {{site.data.keyword.cloud_notm}}.

Para obter mais informações, consulte [Visão geral do Single-node Trial for Disaster Recovery](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview).

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

Agora é possível contratar o IBM Expert Services para trabalhar junto com sua equipe interna para implementar, migrar e manter sua própria solução do {{site.data.keyword.cloud_notm}}, do planejamento à modernização, ou de qualquer estágio intermediário.

É possível incluir o {{site.data.keyword.cloud_notm}} Expert Services em seu pedido de instância a qualquer momento solicitando uma consulta na página **Introdução**. Para obter mais informações, consulte [Solicitando o {{site.data.keyword.cloud_notm}} Expert Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices).

## Integração com o IBM Cloud Cost Estimator

Agora é possível estimar o custo de seus recursos do {{site.data.keyword.vmwaresolutions_short}} na ferramenta de estimativa unificada fornecida pela estrutura do {{site.data.keyword.cloud_notm}}. Com essa função, é possível salvar uma captura instantânea de recursos no Catálogo do {{site.data.keyword.cloud_notm}} e armazená-la em um único arquivo PDF que pode ser transferido por download para referência em um momento posterior. O estimador de custos não é um contrato ou uma cotação firme, mas apenas uma estimativa do custo total.

Para obter mais informações sobre o Estimador de custos, consulte [Estimando seus custos](/docs/billing-usage?topic=billing-usage-cost).

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v31-vcs}

Essa liberação aplica os upgrades e as melhorias a seguir para instâncias, clusters e hosts recém-implementados:

* vSphere ESXi 6.5 Atualização 2 (construção 6.5.0-13635690)
* vCenter Server Appliance 6.5 Atualização 2g (construção 6.5.0-13638625)

Para obter mais informações, consulte [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Configuração alternativa do servidor ESXi para clusters
{: #relnotes_v31-esxi-config}

Agora é possível incluir novos servidores ESXi em um cluster existente, selecionando uma configuração existente ou alternativa à dos hosts existentes no cluster. Ao pedir novos servidores da janela **Incluir servidor**, é possível selecionar instantaneamente uma configuração existente no cluster ou escolher uma nova configuração do {{site.data.keyword.baremetal_short_sing}}. Isso se aplica a todas as instâncias do vCenter Server, vCenter Server with Hybridity e vCenter Server with NSX-T.

Para evitar problemas de desempenho ou estabilidade, é recomendável que os clusters usem a mesma configuração ou uma semelhante em relação a CPU, RAM e armazenamento. Essa funcionalidade é útil para atualizações de hardware dentro do mesmo cluster.

Para obter mais informações, consulte [Expandindo e contraindo a capacidade para instâncias do servidor do vCenter](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers).

### Atualizações para configurações de política
{: #relnotes_v31-policy-config}

A senha do vCenter gerada para as instâncias primárias do vCenter Server tem agora 15 caracteres de comprimento e tem as configurações de política de senha e bloqueio a seguir:

* O comprimento mínimo para a política de senha do vCenter é agora de 15 caracteres.
* A política de bloqueio do vCenter agora permite um máximo de 3 tentativas falhas de login.
* A política de bloqueio do vCenter permite agora um intervalo de tempo de 900 segundos entre as falhas.

A senha do NSX Manager gerada para as instâncias primárias do vCenter Server tem agora 15 caracteres de comprimento. Anteriormente, a senha gerada tinha oito caracteres de comprimento.

 Para obter mais informações, consulte as [Informações de conformidade para instâncias do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config).

## Atualizações para serviços complementares
{: #relnotes_v31-services}

### Caveonix RiskForesight no IBM Cloud
{: #relnotes_v31-services-caveonix}

A liberação atual instala o Caveonix RiskForesight 2.2.1 em todas as instâncias recém-implementadas. Para obter mais informações sobre o Caveonix RiskForesight, consulte o [website do Caveonix](https://www.caveonix.com){:external}.

### Renovação automática para licenças do HyTrust
{: #relnotes_v31-services-ht}

O {{site.data.keyword.vmwaresolutions_short}} agora fornece suporte de renovação automática para licenças do HyTrust que têm o recurso Call Home ativado. Esse suporte é fornecido iniciando com:

* HyTrust CloudControl 5.5.1 e mais recente
* HyTrust DataControl 4.3.2 e mais recente
* HyTrust KeyControl 4.3.2 e mais recente

Deve-se concluir o procedimento para ativar o acesso à Internet para suas máquinas virtuais (VMs) do HyTrust para assegurar a renovação automática de sua licença. Se você não concluir esse procedimento, sua licença continuará expirando anualmente.
{:important}

Para obter mais informações, veja:

* [Ativando o acesso à Internet para as VMs do HyTrust CloudControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [Ativando o acesso à Internet para as VMs do HyTrust DataControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [Ativando o acesso à Internet para as VMs do HyTrust KeyControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

Na liberação atual, o Veeam Availability Suite 9.5 é instalado em todas as instâncias recém-implementadas. Além disso, são feitas várias atualizações nos repositórios de configuração do Veeam VSIs e do Veeam. Para obter mais informações, consulte [Visão geral do Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations).

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

Para novas instâncias implementadas na V3.1 e mais recente, as instalações do Zerto on {{site.data.keyword.cloud_notm}} requerem uma conta faturável do {{site.data.keyword.cloud_notm}}. O custo da replicação da VM agora usa um plano faturável do {{site.data.keyword.cloud_notm}}, em vez de faturamento de infraestrutura do {{site.data.keyword.cloud_notm}}.

Para pedir o Zerto on {{site.data.keyword.cloud_notm}}, sua conta do {{site.data.keyword.cloud_notm}} deve atender a requisitos específicos. Se você tiver uma instalação existente do Zerto on {{site.data.keyword.cloud_notm}}, será possível converter o tipo de faturamento da VM do Zerto em faturável. Para obter mais informações, consulte [Faturamento para replicação do Zerto](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).

## Documentação nova e atualizada
{: #relnotes_v31-updated-doc}

* Os eventos de gerenciamento de instância do Activity Tracker e eventos para o serviço KMIP for VMware on IBM Cloud são atualizados. Para obter mais informações, consulte [Eventos do Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).
* A documentação de referência do ID do usuário é atualizada com IDs de usuário usados para instalação e configuração de serviços por automação de serviços do {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte a seção *ID do usuário do serviço* em [IDs do usuário da IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids).
* A documentação de referência está disponível para a nova API ``Recuperar a interface de rede detalhada de um cluster``. Para obter mais informações, consulte [Referência da API](https://cloud.ibm.com/apidocs/vmware-solutions){:external}.
* Os documentos técnicos a seguir são novos na seção *Referência* da documentação do usuário:
  * [Gerenciamento de operações](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [Procedimentos operacionais do segundo dia](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v31-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:
* A página de detalhes **Clusters** exibe agora o tipo de armazenamento usado pelo cluster.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
