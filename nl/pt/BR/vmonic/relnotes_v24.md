---

copyright:

  years:  2016, 2019

lastupdated: "2018-06-22"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a Liberação para V2.4

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obter mais informações, veja [Tratando as vulnerabilidades Spectre e Meltdown](/docs/services/vmwaresolutions/vmonic/trbl_fix_spectre.html).

## Suporte ao Idioma Nacional

Iniciando com a liberação V2.4, o Suporte ao Idioma Nacional (NLS) está disponível para o {{site.data.keyword.vmwaresolutions_short}}.
Todos os recursos no console, incluindo a documentação do usuário, estão disponíveis em múltiplas linguagens.

As linguagens a seguir são suportadas, além do inglês:
* Alemanha
* Espanhol
* Francês
* Italiano
* Japonês
* Coreano
* Português do Brasil
* Chinês Simplificado
* Chinês Tradicional

## Suporte de CPU Xeon Skylake

Iniciando com a liberação V2.4, os novos modelos de CPU Bare Metal Server a seguir estão disponíveis para implementação para instâncias e clusters do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}} e VMware Federal on {{site.data.keyword.cloud_notm}}:

* Processador Dual Intel Skylake Xeon Silver 4110/Total de 16 núcleos, 2.1 GHz
* Processador Dual Intel Skylake Xeon Gold 5120/Total de 28 núcleos, 2.2 GHz
* Processador Dual Intel Skylake Xeon Gold 6140/Total de 36 núcleos, 2.3 GHz

Para obter mais informações, veja a seção *Configurações do Bare Metal Server* em:

* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [Pedindo instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## Atualizações para instâncias do VMware vCenter Server

### Network File System aprimoramento de desempenho

O nível de desempenho de 10 IOPS/GB, projetado para os tipos de carga de trabalho mais exigentes, não é mais limitado a um {{site.data.keyword.CloudDataCent_notm}} específico, mas agora está disponível para todos. Para obter mais informações, consulte a seção *Armazenamento* na [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

## Atualizações para instâncias do VMware Federal

### Novo IBM Cloud Data Center opção

Agora é possível implementar instâncias do VMware Federal para o {{site.data.keyword.CloudDataCent_notm}} DAL08 - Dallas, TX. Para obter mais informações, veja a seção *Disponibilidade do IBM Cloud Data Center* em [Requisitos e planejamento para instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability).

## Atualizações para serviços complementares

### IBM Spectrum Protect Plus on IBM Cloud

A liberação atual instala a correção 1 do IBM Spectrum Protect&trade; Plus V10.1.1 em todas as instâncias
recém-implementadas. Para obter mais informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.1 Patch 1, consulte [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

Uma nova opção agora está disponível para você escolher entre rede pública e rede privada para interconexões do HCX ao pedir esse serviço. Para obter mais informações, veja [Pedindo o VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/hcx_ordering.html).

## Documentação nova e atualizada

### Arquitetura de Referência da documentação

O documento de arquitetura do {{site.data.keyword.vmwaresolutions_short}} agora está disponível na seção *Referência* da documentação do usuário. Para obter mais informações, consulte [Visão Geral da Solução](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html).

### Serviços de documentação

As informações de serviço são reestruturadas e a navegação é melhorada para localizar facilmente informações relevantes ao pedir serviços.

Para obter mais informações, veja os tópicos a seguir:

* [Solicitando F5 no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_ordering.html)
* [Solicitando FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fsa_ordering.html)
* [Solicitando FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_ordering.html)
* [Solicitando Hytrust CloudControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_ordering.html)
* [Solicitando Hytrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_ordering.html)
* [Solicitando IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/spp_ordering.html)
* [Solicitando KMIP para VMware no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_ordering.html)
* [Pedindo o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/veeam_ordering.html)
* [Solicitando on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/zerto_ordering.html)

## Atualizações e aprimoramentos da interface com o usuário

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* As áreas de janela incluir cluster e incluir serviço agora usam um formato de página, com um layout melhor organizado, que permite concluir tarefas de forma mais eficiente.
* A funcionalidade da página **Instâncias implementadas** foi aprimorada com recursos de procura, paginação e classificar. Essas melhorias permitem localizar suas instâncias rapidamente.
* A página de detalhes da instância agora usa um menu de navegação à esquerda, que permite acessar as informações da instância fácil e rapidamente.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
