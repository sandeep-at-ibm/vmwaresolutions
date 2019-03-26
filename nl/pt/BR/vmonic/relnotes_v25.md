---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a Liberação para V2.5
{: #relnotes_v25}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown
{: #relnotes_v25-spectre}

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Atualização de componente NSX
{: #relnotes_v25-nsx}

Essa liberação instala o VMware NSX for vSphere 6.4.1 para novas implementações do VMware vCenter Server on {{site.data.keyword.cloud_notm}}, do VMware vCenter Server on {{site.data.keyword.cloud_notm}} com Hybridity Bundle e do NetApp ONTAP Select.

## Remoção da configuração de backup padrão
{: #relnotes_v25-default-backup}

O {{site.data.keyword.vmwaresolutions_short}} oferece dois serviços de complementos integrados para backup: IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} e Veeam on {{site.data.keyword.cloud_notm}}. Com esses serviços, é possível planejar e fornecer a recuperação de sua infraestrutura de gerenciamento e de sua carga de trabalho. Além disso, o IBM Resiliency Services fornece serviços gerenciados para backups do Veeam.

Iniciando com a liberação da V2.5, os serviços IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} e Veeam on {{site.data.keyword.cloud_notm}}, quando implementados, não pré-configuram mais o backup de quaisquer MVs. Com essa mudança, é possível assegurar uma configuração adequada de todos os aspectos de suas tarefas de backup, incluindo planejamento, período de retenção, uso de deduplicação, monitoramento e alertas e gerenciamento de chaves de criptografia. Além disso, a MV do IBM CloudDriver não é mais configurada como um servidor de arquivos persistente para backups do NSX.

Você é responsável pela configuração, gerenciamento e monitoramento de todos os componentes de software, incluindo o backup e a disponibilidade da infraestrutura de gerenciamento e das cargas de trabalho. Para obter mais informações, consulte [Fazendo backup de componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#backing-up-components).

Essa mudança não afeta as instâncias que são implementadas antes da V2.5 que têm o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}} instalado.
{:note}

## Resiliência do IBM CloudDriver
{: #relnotes_v25-cloud-driver}

Para instâncias implementadas ou submetidas a upgrade para liberações V2.5 ou mais recentes, o componente IBM CloudDriver não está mais configurado como uma máquina virtual (MV) dentro do cluster do vSphere. Em vez disso, ele é implementado como uma instância de servidor virtual (VSI) da infraestrutura do {{site.data.keyword.cloud_notm}}, conforme necessário, com o código mais recente do {{site.data.keyword.cloud_notm}} for VMware para operações, como a implementação de nós, clusters ou serviços adicionais. Além disso, o IBM CloudDriver foi mudado para se comunicar com o plano de gerenciamento do {{site.data.keyword.cloud_notm}}, usando a rede privada do {{site.data.keyword.cloud_notm}}. Com essa mudança, as regras de firewall de gerenciamento do NSX Edge Services Gateway (ESG) e as regras de conversão de endereço de rede (NAT) que permitem que o IBM CloudDriver comunique a saída para a rede pública são removidas.

Alguns serviços de complemento, como F5 on {{site.data.keyword.cloud_notm}}, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}}, ainda requerem acesso à rede pública, portanto o NSX ESG de gerenciamento permanece implementado em todas as instâncias.

## Usuário ativado por IAM e gerenciamento de acesso
{: #relnotes_v25-iam}

Iniciando com a liberação V2.5, o {{site.data.keyword.vmwaresolutions_short}} é integrado ao IBM Identity and Access Management (IAM) para fornecer uma abordagem unificada para gerenciar contas do usuário e acesso de usuário dentro de sua conta do {{site.data.keyword.cloud_notm}}. Por causa do qual:
* Agora é possível incluir diversos usuários na conta do {{site.data.keyword.cloud_notm}} para colaboração e gerenciar seu acesso aos serviços e recursos fornecidos em sua conta, designando diferentes funções de acesso à plataforma a eles.  
* As instâncias que são implementadas nas liberações V2.5 e mais recentes são vinculadas automaticamente à conta do usuário que está sendo usada quando a instância é pedida.
* Para instâncias que foram implementadas nas liberações V2.4 e anteriores, é possível migrá-las para uma conta especificada do {{site.data.keyword.cloud_notm}} e, em seguida, gerenciá-las usando o IAM também.

Para obter mais informações, veja os tópicos a seguir:
* [Convidando usuários para acessar serviços e recursos](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Gerenciando o acesso de usuário com o IAM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam)

## Mudanças nas contas do usuário e grupos para instâncias do VMware vCenter Server e do VMware Cloud Foundation
{: #relnotes_v25-user-acct}

O grupo de usuários **ic4v-vCenter** foi criado no Microsoft Active Directory Server e incluído nas permissões globais no vCenter Server e nos grupos de usuários para o NSX Manager. O grupo contém a conta do usuário de **automação** para instâncias do vCenter Server e contas do usuário específicas do serviço para instâncias do vCenter Server e do Cloud Foundation.

Não edite as permissões globais do grupo **ic4v-vCenter** na página **Usuários e grupos** no VMware vSphere Web Client. Fazer isso pode afetar as operações de gerenciamento.

Para instâncias do Cloud Foundation, use o ID do usuário do host **customerroot** no lugar do ID do usuário do host **raiz**.

Para instâncias do vCenter Server, continue a usar a identificação de usuário do host **raiz**. A identificação
de usuário do host **ic4vroot** foi criada apenas para uso da IBM.

Para obter mais informações sobre contas do usuário, consulte [Considerações sobre como mudar os artefatos do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact).

## Atualizações para serviços complementares
{: #relnotes_v25-services}

### IBM Cloud Private Hosted (Atualizado em 30 de agosto de 2018)
{: #relnotes_v25-scp-hosted}

O serviço {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} agora está disponível para instâncias do vCenter Server implementadas (ou submetidas a upgrade) na V2.5 ou liberações mais recentes.

O {{site.data.keyword.cloud_notm}} Private Hosted traz o poder de microsserviços e contêineres para o ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.

É possível solicitar esse serviço depois de pedir sua instância do vCenter Server.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v25-spp}

A partir da liberação da V2.5, o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} é implementado como duas MVs separadas com base nas melhores práticas, com uma MV executando o servidor IBM Spectrum Protect Plus e a outra MV executando o servidor vSnap e o proxy do VADP.

Agora é possível pedir até 10 armazenamentos de dados de backup, permitindo até 120 TB de armazenamento de backup. O vSnap e a MV do VADP são dimensionados dependendo de seu tamanho de armazenamento de backup selecionado e de acordo com as informações nos [Blueprints do IBM Spectrum Protect Plus](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).

### KMIP for VMware on IBM Cloud
{: #relnotes_v25-kmip}

Um novo terminal está agora disponível na Alemanha para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}.

## Documentação nova e atualizada
{: #relnotes_v25-new-docs}

### Documentação de armazenamento anexado
{: #relnotes_v25-docs-storage}

O armazenamento Anexado para o vCenter Server no documento técnico do IBM Cloud agora está disponível na seção *Referência* da documentação do usuário. Para obter mais informações, veja [Armazenamento anexado para o vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/attached-storage?topic=vmware-solutions-storage-benefits).

### Especificações técnicas
{: #relnotes_v25-docs-tech-specs}

As especificações técnicas para todos os tipos de instância e tipos de serviço estão agora disponíveis na documentação do usuário e vinculadas por meio da interface com o usuário. Para obter mais informações, veja o tópico de visão geral apropriado para sua instância e serviço.

### Serviços de documentação
{: #relnotes_v25-docs-services}

As informações de serviços são melhoradas para identificar facilmente o suporte de serviço com base no número da liberação em que ele foi disponibilizado.

Para obter mais informações, veja os tópicos a seguir:

* [Serviços disponíveis para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances)
* [Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v25-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* Se você tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) que esteja vinculada à sua conta do {{site.data.keyword.cloud_notm}}, agora será possível clicar no botão **Recuperar** recém-incluído na página **Configurações** para obter o nome do usuário e a chave API para sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) automaticamente.
* Uma nova guia **Histórico de implementação** foi incluída na área de janela de navegação esquerda da página de detalhes da instância para você verificar o histórico de implementação de uma instância.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
