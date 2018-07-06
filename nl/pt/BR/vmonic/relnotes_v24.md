---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Notas sobre a Liberação para V2.4

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em liberações diferentes, problemas conhecidos com o produto e dicas adicionais para usar o {{site.data.keyword.vmwaresolutions_full}}, veja o [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obter mais informações, veja [Tratando as vulnerabilidades Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## Suporte ao Idioma Nacional

Iniciando com a liberação V2.4, o Suporte ao Idioma Nacional (NLS) está disponível para o IBM Cloud for VMware Solutions.
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

**Nota**: os documentos de arquitetura de referência estão disponíveis somente em inglês.

## Suporte de CPU Xeon Skylake

Iniciando com a liberação V2.4, os novos modelos de CPU Bare Metal Server a seguir estão disponíveis para implementação para instâncias e clusters do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}} e VMware Federal on {{site.data.keyword.cloud_notm}}:

* Processador Dual Intel Skylake Xeon Silver 4110/total de 16 núcleos, 2.1 GHz
* Processador Dual Intel Skylake Xeon Gold 5120/total de 28 núcleos, 2.2 GHz
* Processador Dual Intel Skylake Xeon Gold 6140/total de 36 núcleos, 2.3 GHz

Para obter mais informações, veja a seção *Configurações do Bare Metal Server* em:

* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [Pedindo instâncias do VMware Federal](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## Atualizações para instâncias do VMware vCenter Server

### Network File System aprimoramento de desempenho

O nível de desempenho de 10 IOPS/GB, projetado para os tipos de carga de trabalho mais exigentes, não é mais limitado a um {{site.data.keyword.CloudDataCent_notm}} específico, mas agora está disponível para todos. Para obter mais informações, veja a seção *Armazenamento* em [Visão geral do vCenter Server](../vcenter/vc_vcenterserveroverview.html#vcenter-server-technical-specifications).

## Atualizações para instâncias do VMware Federal

### Novo IBM Cloud Data Center opção

Agora é possível implementar instâncias do VMware Federal para o {{site.data.keyword.CloudDataCent_notm}} DAL08 - Dallas, TX. Para obter mais informações, veja a seção *Disponibilidade do IBM Cloud Data Center* em [Requisitos e planejamento para instâncias do VMware Federal](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability).

## Atualizações para serviços complementares

### IBM Spectrum Protect Plus on IBM Cloud

A liberação atual instala a correção 1 do IBM Spectrum Protect&trade; Plus V10.1.1 em todas as instâncias
recém-implementadas. Para obter informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.1 Correção 1, veja [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

Uma nova opção agora está disponível para você escolher entre rede pública e rede privada para interconexões do HCX ao pedir esse serviço. Para obter mais informações, veja [Pedindo o VMware HCX on IBM Cloud](../services/hcx_ordering.html).

## Documentação nova e atualizada

### Arquitetura de Referência da documentação

O documento de arquitetura do {{site.data.keyword.vmwaresolutions_short}} agora está disponível na seção *Referência* da documentação do usuário. O documento de arquitetura de referência está disponível somente em inglês. Para obter mais informações, consulte [Visão Geral da Solução](../archiref/solution/solution_overview.html).

### Serviços de documentação

As informações de serviços foram reestruturadas e a navegação foi melhorada para localizar facilmente informações relevantes ao pedir serviços.

Para obter mais informações, veja:

* [Solicitando F5 no IBM Cloud](../services/f5_ordering.html)
* [Pedindo o FortiGate Security Appliance on IBM Cloud](../services/fsa_ordering.html)
* [Pedindo o FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_ordering.html)
* [Pedindo o HyTrust CloudControl on IBM Cloud](../services/htcc_ordering.html)
* [Solicitando Hytrust on IBM Cloud](../services/htdc_ordering.html)
* [Pedindo o IBM Spectrum Protect Plus on IBM Cloud](../services/spp_ordering.html)
* [Pedindo o KMIP for VMware on IBM Cloud](../services/kmip_ordering.html)
* [Solicitando Veeam no IBM Cloud](../services/veeam_ordering.html)
* [Solicitando Zerto on IBM Cloud](../services/zerto_ordering.html)

## Atualizações e aprimoramentos da interface com o usuário

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* As áreas de janela incluir cluster e incluir serviço agora usam um formato de página, com um layout melhor organizado, que permite concluir tarefas de forma mais eficiente.
* A funcionalidade da página **Instâncias implementadas** foi aprimorada com recursos de procura, paginação e classificar. Essas melhorias permitem localizar as suas instâncias muito rapidamente.
* A página de detalhes da instância agora usa um menu de navegação à esquerda, que permite acessar as informações da instância fácil e rapidamente.
* Várias mensagens de erro e aprimoramentos de dica de ferramenta foram feitos para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
