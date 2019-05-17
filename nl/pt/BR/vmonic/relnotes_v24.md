---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a Liberação para V2.4
{: #relnotes_v24}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown
{: #relnotes_v24-spectre}

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Suporte ao Idioma Nacional
{: #relnotes_v24-nls}

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
{: #relnotes_v24-skylake}

A partir da liberação da V2.4, os novos modelos de CPU do Bare Metal Server a seguir estão disponíveis para implementação para instâncias e clusters do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} e do VMware vSphere on {{site.data.keyword.cloud_notm}}:

* Processador Dual Intel Skylake Xeon Silver 4110/Total de 16 núcleos, 2.1 GHz
* Processador Dual Intel Skylake Xeon Gold 5120/Total de 28 núcleos, 2.2 GHz
* Processador Dual Intel Skylake Xeon Gold 6140/Total de 36 núcleos, 2.3 GHz

Para obter mais informações, consulte [Configurações do Bare Metal Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-bare-metal-settings).

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v24-vcs}

### Network File System aprimoramento de desempenho
{: #relnotes_v24-nfs}

O nível de desempenho de 10 IOPS/GB, projetado para os tipos de carga de trabalho mais exigentes, não é mais limitado a um {{site.data.keyword.CloudDataCent_notm}} específico, mas agora está disponível para todos. Para obter mais informações, consulte [Armazenamento](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vc_vcenterserveroverview-storage).

## Atualizações para serviços complementares
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

A liberação atual instala a correção 1 do IBM Spectrum Protect&trade; Plus V10.1.1 em todas as instâncias
recém-implementadas. Para obter mais informações sobre os novos recursos no IBM Spectrum Protect Plus V10.1.1 Patch 1, consulte [Atualizações do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

Uma nova opção agora está disponível para você escolher entre rede pública e rede privada para interconexões do HCX ao pedir esse serviço. Para obter mais informações, veja [Pedindo o VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering).

## Documentação nova e atualizada
{: #relnotes_v24-new-docs}

### Arquitetura de Referência da documentação
{: #relnotes_v24-ref-archi}

O documento de arquitetura do {{site.data.keyword.vmwaresolutions_short}} agora está disponível na seção *Referência* da documentação do usuário. Para obter mais informações, consulte [Visão Geral da Solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

### Serviços de documentação
{: #relnotes_v24-docs-services}

As informações de serviço são reestruturadas e a navegação é melhorada para localizar facilmente informações relevantes ao pedir serviços.

Para obter mais informações, veja os tópicos a seguir:

* [Solicitando F5 no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [Solicitando FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Solicitando FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Solicitando Hytrust CloudControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Solicitando Hytrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Solicitando IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Pedindo o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Solicitando on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v24-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* As áreas de janela incluir cluster e incluir serviço agora usam um formato de página, com um layout melhor organizado, que permite concluir tarefas de forma mais eficiente.
* A funcionalidade da página **Recursos** é aprimorada com recursos de procura, paginação e classificação. Essas melhorias permitem localizar suas instâncias rapidamente.
* A página de detalhes da instância agora usa um menu de navegação à esquerda, que permite acessar as informações da instância fácil e rapidamente.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
