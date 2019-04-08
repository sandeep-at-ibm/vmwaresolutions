---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a liberação para V2.2
{: #relnotes_v22}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correção para Spectre e Meltdown
{: #relnotes_v22-spectre}

O {{site.data.keyword.vmwaresolutions_short}} liberou correções do VMware em resposta às vulnerabilidades conhecidas como Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Upgrade da máquina virtual do IBM CloudDriver
{: #relnotes_v22-cloud-driver}

Durante o processo de upgrade da V2.2, a máquina virtual do IBM CloudDriver é reimplementada com o CentOS Linux liberação 7.4.1708. Além disso, todas as novas instâncias fornecidas incluem o CentOS Linux liberação 7.4.1708 no IBM CloudDriver.

**Importante:**

* Se você estiver usando uma solução de backup que faça referência à máquina virtual do IBM CloudDriver, depois de fazer upgrade para a V2.2, assegure-se de que a solução de backup esteja fazendo referência à nova máquina virtual do IBM CloudDriver.
* Antes de fazer upgrade para a V2.2, assegure-se de substituir o VSI do Legacy Veeam pelo serviço Veeam on {{site.data.keyword.cloud_notm}}. O Legacy Veeam não é mais suportado na V2.2 e liberações futuras, portanto, os backups de componente de gerenciamento associados ao Legacy Veeam não estão disponíveis para restauração.

Para obter mais informações sobre como usar o Veeam no serviço do {{site.data.keyword.cloud_notm}}, consulte os tópicos a seguir:
* [Componentes e considerações para o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Definições de configuração avançadas em servidores ESXi
{: #relnotes_v22-config-esxi}

Para a V2.2 ou liberações mais recentes, novas instâncias são pedidas com um novo conjunto de definições de configuração avançadas para servidores ESXi.
Para instâncias que foram submetidas a upgrade de uma liberação anterior para liberações V2.2 ou mais recentes, algumas configurações requerem a reinicialização dos servidores ESXi. Portanto, apenas um subconjunto de definições de configuração é aplicado automaticamente.

Recomenda-se que você mude as definições de configuração restantes para os novos valores para consistência em todas as instâncias e para permitir o suporte adequado para a expansão de armazenamento. A IBM planeja testar apenas com essas novas configurações para todas as liberações futuras do {{site.data.keyword.cloud_notm}} for VMware Solutions.

Para obter mais informações, consulte _Definições de configuração avançada para servidores ESXi_ em [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers).

## Suporte para até 51 servidores ESXi para um cluster inicial e até 59 servidores ESXi para clusters adicionais
{: #relnotes_v22-esxi-cluster}

Para a V2.2 e liberações mais recentes, é possível aumentar o número de servidores ESXi para um máximo de 51 para um cluster inicial e até 59 para clusters adicionais.

Para instâncias implementadas na V2.1 ou liberações anteriores, deve-se ativar o suporte de vSAN necessário para aumentar o tamanho do cluster além de 32. Para obter mais informações sobre as etapas para aumentar o número de servidores ESXi, consulte _Quantos servidores ESXi posso incluir em um cluster?_ em [Perguntas mais frequentes sobre servidores ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-).
{:important}

## Mais opções de configuração de rede para instâncias do vCenter Server e do Cloud Foundation
{: #relnotes_v22-network-config}

Para pedidos de instância do vCenter Server e do Cloud Foundation, agora é possível reutilizar VLANs públicas e privadas existentes para a configuração da rede. Quando as VLANs existentes não estiverem disponíveis, será possível pedir uma nova VLAN pública e duas novas VLANs privadas.

Para obter considerações importantes antes de selecionar VLANs existentes, consulte as seções *Configurações da interface de rede* em [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v22-vcs}

### Atualizações da definição de configuração do componente NSX e do grupo da porta
{: #relnotes_v22-nsx}

A liberação atual se aplica à atualização do componente VMware NSX for vSphere 6.3.5. Para obter mais informações sobre componentes, consulte [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Para instâncias do VMware vCenter Server que são implementadas na V2.2 ou liberações mais recentes, as definições de configuração do NSX e do grupo da porta mudaram. Para obter mais informações, veja a seção *Definições de configuração do NSX e do grupo da porta* em [Lista de materiais do vCenter Server Software](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings).

### Nova opção para configuração do DNS
{: #relnotes_v22-dns}

Agora é possível selecionar a implementação de uma única Virtual Server Instance (VSI) do Microsoft Windows Server para o Microsoft Active Directory (AD) ou duas máquinas virtuais de alta disponibilidade do Microsoft Windows no cluster de gerenciamento. Para liberações anteriores à V2.2, o único VSI do Microsoft Windows para Microsoft AD foi implementado automaticamente por padrão. A nova opção para selecionar duas máquinas virtuais do Microsoft Windows fornece mais privacidade e a opção de fazer backup e restaurar as máquinas virtuais que usam o serviço Veeam.

Deve-se fornecer duas licenças do Microsoft Windows Server 2012 R2 caso você configure sua instância para usar as duas máquinas virtuais do Microsoft Windows. Use a licença da edição Microsoft Windows Server 2012 R2 Standard e/ou a licença da edição Microsoft Windows Server 2012 R2 Datacenter. Você tem 30 dias para ativar as máquinas virtuais.
{:note}

Para obter mais informações, veja a seção *Configurações do sistema* em [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings)​.

### Maior número de clusters por instância
{: #relnotes_v22-clusters-per-inst}

É possível incluir até 10 clusters nas instâncias do VMware vCenter Server que são implementadas em ou têm upgrade feito para a V2.2. e liberações mais recentes. Para obter mais informações, veja [Incluindo e visualizando clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)​.

## Atualizações para clusters do VMware vSphere
{: #relnotes_v22-vss}

### Pacotes configuráveis de licença do componente disponíveis para clientes do Parceiro de Negócios
{: #relnotes_v22-license-bundles}

Os usuários do Parceiro de Negócios agora podem selecionar entre quatro pacotes configuráveis de licença do componente ao pedir um novo cluster do vSphere. Escolha entre Padrão com Gerenciamento, Avançado, Avançado com Rede ou Avançado com Rede e Gerenciamento. É possível também incluir componentes adicionais do VMware em seu pedido. No entanto, a opção de Bring Your Own License não está disponível.

Para obter mais informações, veja a seção *Configurações de licenciamento* em [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Atualizações para instâncias do NetApp ONTAP Select
{: #relnotes_v22-netapp}

A liberação atual se aplica à atualização do NetApp ONTAP Select 9.3.

### Maior número de unidades SATA para Bare Metal Servers do IBM Cloud de alta capacidade
{: #relnotes_v22-sata-drives}

Trinta e quatro unidades SATA estão, agora, disponíveis para o {{site.data.keyword.baremetal_short}} de alta capacidade do NetApp ONTAP Select. Para obter mais informações, veja [Especificações técnicas para instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs).

## Atualizações para serviços complementares
{: #relnotes_v22-services}

### Opção de largura de banda aumentada para o F5 on IBM Cloud
{: #relnotes_v22-bandwidth}

Agora é possível selecionar uma largura de banda máxima de 10 Gbps ao instalar o serviço F5 on {{site.data.keyword.cloud_notm}} para instâncias do Cloud Foundation e do vCenter Server. Para obter mais informações, veja [Considerações para o F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations).

### KMIP for VMware on IBM Cloud
{: #relnotes_v22-kmip}

É possível pedir uma instância do Cloud Foundation ou do vCenter Server com o serviço KMIP para VMware on {{site.data.keyword.cloud_notm}} incluído ou incluir o serviço em uma instância existente do Cloud Foundation ou do vCenter Server após a implementação inicial.

Esse serviço fornece um serviço altamente disponível 24x7 para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e excluam as chaves de criptografia. Além disso, esse serviço fornece capacidade de gerenciamento para manter as associações entre as credenciais do cliente e essas chaves de criptografia.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v22-spp}

O serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} está disponível para instâncias que são implementadas em (ou têm upgrade feito para a) V2.2 ou liberações mais recentes.

Este serviço fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementá-lo como uma solução independente ou integrá-lo ao ambiente do IBM Spectrum Protect&trade; Plus para transferir cópias para armazenamento de longo prazo e controle de dados.

O serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fornece proteção de dados somente para as MVs de carga de trabalho.

Para obter mais informações, veja [Gerenciando o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp).

### Serviços gerenciados
{: #relnotes_v22-managed-services}

Serviços gerenciados para o Veeam on {{site.data.keyword.cloud_notm}} e para o Zerto on {{site.data.keyword.cloud_notm}} estão disponíveis para instâncias do VMware vCenter Server e do VMware Cloud Foundation. Solicite esses serviços gerenciados se não quiser gerenciar a complexidade de sua própria solução e ambiente.

O serviço Veeam on {{site.data.keyword.cloud_notm}} se integra continuamente com os hypervisors do VMware para ajudar sua empresa a alcançar alta disponibilidade (HA). Um ambiente de backup totalmente gerenciado pode ser implementado usando o software de backup Veeam e o IBM Resiliency Backup as a Service.

O serviço Zerto on {{site.data.keyword.cloud_notm}} fornece recursos de replicação e de recuperação de desastre, que podem ser integrados às ofertas de implementação para proteger e recuperar dados no ambiente virtual do VMware no {{site.data.keyword.cloud_notm}}. Um ambiente de recuperação de desastre (DR) totalmente gerenciado pode ser implementado usando o software Zerto DR e o IBM Resiliency Services.

É possível solicitar serviços gerenciados para suas instâncias da página **Introdução**, seja colocando um novo pedido da instância ou incluindo o serviço em uma instância existente.

Para obter mais informações, veja os tópicos a seguir:
* [Solicitando serviços para o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Solicitando serviços para o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

## Documentação nova e atualizada
{: #relnotes_v22-new-docs}

* A tabela de comparação com as funções suportadas para instâncias do Cloud Foundation e do vCenter Server, bem como clusters do VMware vSphere, está disponível na documentação. É possível ver, em uma visão rápida, as diferenças entre as funções que cada tipo de instância fornece. Para obter mais informações, veja [Gráfico de comparação de oferta](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

* As VLANs e a Lista de materiais (BOM) de software agora são fornecidas na documentação dos clusters do Cloud Foundation, do vCenter Server e do VMware vSphere.

  Para obter mais informações, veja os tópicos a seguir:

  * [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [Lista de materiais do VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v22-ui}

São feitas melhorias em toda a interface com o usuário:

* Quando você pede uma instância, todas as opções de hardware são filtradas por local e as opções indisponíveis são exibidas no estado desativado.
* A configuração do **{{site.data.keyword.baremetal_short}}** é preenchida automaticamente quando você pede um cluster do vSphere com base nas configurações existentes. É possível atualizar a configuração de acordo com seus requisitos.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
