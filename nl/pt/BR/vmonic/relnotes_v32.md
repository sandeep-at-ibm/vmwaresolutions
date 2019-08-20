---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas sobre a liberação para a V3.2
{: #relnotes_v32}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Disponibilidade do VMware HCX for IBM Cloud
{: #relnotes_v32-HCX}

A partir da liberação 3.2, agora você tem a opção de pedir o serviço VMware HCX on {{site.data.keyword.cloud_notm}} com instâncias do VMware vCenter Server. Anteriormente, você podia somente pedir o serviço HCX on {{site.data.keyword.cloud_notm}} por meio da instância do VMware vCenter Server with Hybridity Bundle. A instância do vCenter Server with Hybridity Bundle não está mais disponível.

Um compromisso de 12 meses é necessário quando você pede o serviço HCX on {{site.data.keyword.cloud_notm}}. Depois que o compromisso de 12 meses expirar, será possível instalar e desinstalar o serviço HCX on {{site.data.keyword.cloud_notm}} e será possível incluir e remover hosts e clusters sem restrições. Sua conta será então cobrada em uma base mensal e será possível cancelar a qualquer momento.

Para obter mais informações, consulte [Visão geral do VMware HCX on IBM Cloud](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations).

## Suporte ao VMware vSphere 6.7 Atualização 2
{: #relnotes_v32-vsphere-v67}

Agora você tem a opção de pedir o VMware vSphere versão 6.7 Atualização 2 com suas instâncias do VMware vCenter Server, VMware vCenter Server with NSX-T e VMware vSphere on IBM Cloud. O vSphere Enterprise Plus 6.7u2 substitui a opção para pedir o vSphere Enterprise Plus 6.7u1 com novas instâncias. Além disso, as instâncias do Single-node Trial for Migration and App Modernization e do Single-node Trial for Data Protection and Disaster Recovery são agora pedidas com o vSphere Enterprise Plus 6.7u2.

O vSphere Enterprise Plus 6.7u2 está disponível para {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Skylake, Cascade Lake e Broadwell.

Se tiver uma instância existente com o vSphere Enterprise Plus 6.7u1, você terá a opção de incluir novos hosts com o vSphere Enterprise Plus 6.7u1 ou o vSphere Enterprise Plus 6.7u2. No entanto, a inclusão de um novo host 6.7u1 não é segura. É recomendado que você atualize seus hosts para a versão mais recente do servidor ESXi assim que possível.
{:note}

## Suporte ao Cascade Lake
{: #relnotes_v32-cascade}

A partir da liberação V3.2, os novos modelos de CPU do {{site.data.keyword.baremetal_short_sing}} a seguir estão disponíveis para implementação com instâncias e clusters com o VMware vSphere 6.7 Atualização 2. Isso se aplica ao vCenter Server, vCenter Server with NSX-T e VMware vSphere.

* Processador Dual Intel Xeon Gold 4210/Total de 20 núcleos, 2.3 GHz
* Processador Dual Intel Xeon Gold 5218/Total de 32 núcleos, 2.3 GHz
* Processador Dual Intel Xeon Gold 6248/Total de 40 núcleos, 2.5 GHz

Os {{site.data.keyword.baremetal_short}} Cascade Lake estão disponíveis nos
{{site.data.keyword.CloudDataCents_notm}} de região de multizona. Para obter mais informações, consulte [Visão geral da região de multizona (MZR)
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Para obter mais informações sobre as configurações do {{site.data.keyword.baremetal_short_sing}}, consulte:

* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [Ordenando o vCenter Server com instâncias do NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v32-vcs}

Essa liberação aplica os upgrades e as melhorias a seguir para instâncias, clusters e hosts recém-implementados:

* VMware NSX for vSphere 6.4.5 (construção 13282012)
* vSphere ESXi 6.7 EP 10 (construção 6.7.0-13981272)
* vCenter Server Appliance 6.7 Atualização 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Atualização 2b (6.7.0.-13843469)

Para obter mais informações, consulte [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Nomenclatura do cluster inicial
{: #relnotes_v32-vcs-initial-cluster}

Agora é possível especificar o nome de seu cluster inicial para ser criado ao mesmo tempo em que você faz o pedido da instância. Para obter mais informações, veja:

* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Ordenando o vCenter Server com instâncias do NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Atualizações para instâncias do VMware vSphere
{: #relnotes_v32-vss}

Uma VLAN pública não é mais necessária quando você pede um novo cluster do vSphere somente com uma rede privada.

Para obter mais informações, consulte a seção *Configurações da interface de rede* em [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings).

## Atualizações para serviços complementares
{: #relnotes_v32-services}

Esta liberação instala as versões de serviço a seguir em instâncias implementadas recentemente:

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Atualização 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Atualização 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

O serviço vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} está agora disponível para instâncias do VMware vCenter Server que são implementadas ou submetidas a upgrade para a V3.2 ou liberações mais recentes.

Esse serviço fornece o VMware vRealize Log Insight (vRLI) integrado ao vRealize Operations Manager (vROps), para ajudar a monitorar e gerenciar proativamente o funcionamento e o desempenho de seu ambiente virtualizado, bem como para executar a análise de causa raiz de um problema filtrando e procurando nos logs.

É possível pedir instâncias do vCenter Server com o vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} incluído ou incluir esse serviço em suas instâncias existentes posteriormente na guia Serviços na página de detalhes da instância.

Também é possível trazer as licenças corporativas do Enterprise vRealize Operations e do vRealize Log Insight para a nuvem (por CPU ou OSI) ou alugar licenças do IBM Cloud.

Para obter mais informações, consulte [Visão geral do VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview).

## Documentação nova e atualizada
{: #relnotes_v32-updated-doc}

* A documentação do Activity Tracker está atualizada. Para obter mais informações, consulte [Eventos do Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v32-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* Os requisitos de nome da instância foram mudados. Para obter mais informações, consulte o tópico apropriado para o tipo de instância que você está pedindo.
* O formato do servidor ESXi totalmente qualificado foi mudado. Para obter mais informações, consulte o tópico apropriado para o tipo de instância que você está pedindo.
* Os zeros à esquerda foram incluídos nos nomes do host e do cluster para permitir a classificação adequada.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
