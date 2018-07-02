---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# Notas sobre a liberação para V1.9

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em liberações diferentes, problemas conhecidos com o produto e dicas adicionais para usar o {{site.data.keyword.vmwaresolutions_full}}, veja o [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud

Esta liberação introduz a oferta do VMware vSphere on IBM Cloud, que permite construir o seu próprio ambiente virtual do VMware hospedado pela IBM customizando e pedindo os recursos de cálculo, armazenamento e rede compatíveis com o VMware com base nos componentes selecionados do VMware. Enquanto o vSphere on IBM Cloud não automatiza a instalação, configuração e criação dos componentes opcionais do VMware, você tem flexibilidade máxima para projetar e arquitetar um ambiente que melhor atenda às suas necessidades de negócios. É possível começar criando um novo cluster vSphere de servidores ESXi ou ajustando a escala de um cluster vSphere existente em um data center do IBM Cloud.

Para obter mais informações, veja:
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html)
* [Ajustando a escala de clusters existentes do vSphere](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

Esta liberação introduz a oferta do NetApp ONTAP Select on IBM Cloud, um dispositivo virtual para armazenamento definido por software, que implementa o NetApp ONTAP Select como um serviço no {{site.data.keyword.baremetal_short}} dedicado do IBM Cloud. O NetApp ONTAP Select on IBM Cloud é oferecido em ambas as configurações, de alto desempenho (todas SSD) e de alta capacidade (todas SATA).
Ele hospeda seu armazenamento na infraestrutura dedicada e fornece recursos do NetApp, como deduplicação, compactação e criptografia de dados em repouso. Com esta oferta, é possível fornecer recursos de armazenamento com agilidade e flexibilidade enquanto protege os dados usando funções avançadas de gerenciamento de dados, como as cópias rápidas e eficientes do NetApp Snapshot®, cópias do FlexClone® e replicação do SnapMirror®.

Para obter mais informações, veja:
* [Visão geral do NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Pedindo instâncias do NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Serviço F5 on IBM Cloud

O serviço F5 BIG-IP Virtual Edition (VE) on IBM Cloud está disponível para as instâncias do VMware Cloud Foundation e do VMware vCenter Server. Este serviço fornece serviços inteligentes de balanceamento de carga e gerenciamento de tráfego L4-L7 em escala local e global, rede robusta e proteção de firewall de aplicativo da web, e acesso seguro e federado ao aplicativo.
É possível pedir instâncias com o F5 BIG-IP Virtual Edition (VE) no serviço IBM Cloud incluído quando você pede sua instância ou incluir esse serviço em suas instâncias existentes posteriormente na guia **Serviços** na página de detalhes de propriedade de instância do console do {{site.data.keyword.vmwaresolutions_short}}. Dependendo de seus requisitos, é possível selecionar uma das três opções de licenciamento para BIG-IP VEs.

Para obter mais informações, veja:
* [Considerações para o F5 on IBM Cloud](../services/f5_considerations.html)
* [Gerenciando o F5 on IBM Cloud](../services/managing_f5.html)

## Serviços gerenciados do IBM Integrated Managed Infrastructure

Os serviços gerenciados do IBM Integrated Managed Infrastructure (IMI) estão, agora, disponíveis para instâncias do VMware Cloud Foundation. O IMI pode simplificar o gerenciamento de infraestrutura virtual do VMware com serviços modulares e pode servir como um provedor único e confiável para reduzir a complexidade do monitoramento e gerenciamento de infraestruturas de TI virtuais. Transfira algumas operações do dia a dia para o IMI, como o monitoramento, para que seja possível focar em iniciativas de valor mais alto.

É possível solicitar uma consulta e uma cotação a qualquer momento na página **Introdução**.
Para obter mais informações, veja [Solicitando serviços gerenciados do IMI](../services/managing_imi.html#requesting-managed-services-from-imi).

## Restrições de nome da instância para instâncias do vCenter Server e do NetApp ONTAP Select

Os nomes de instâncias inseridos no {{site.data.keyword.vmwaresolutions_short}} quando você pede suas instâncias não podem ter caracteres especiais (como o caractere traço) neles. Apenas caracteres alfanuméricos são permitidos. Essa restrição não se aplica a instâncias do Cloud Foundation.

Para obter mais informações, veja:
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Pedindo instâncias do NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Atualizações para instâncias do VMware Cloud Foundation

### Customizar a CPU e a memória da instância

Uma opção do servidor customizado pelo usuário está disponível junto com as opções Pequeno e Padrão pré-construídas e testadas. Para melhor corresponder à razão entre CPU e RAM de suas cargas de trabalho para o hardware compatível com VMware, é possível selecionar de forma independente o número total de núcleos em um servidor de CPU dual e a quantidade de RAM. O armazenamento local não é customizável.

Para obter mais informações, veja [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html).

## Atualizações para instâncias do VMware vCenter Server

### Suporte ao cluster do data center cruzado

Para aprimorar o ajuste de escala do seu ambiente do VMware hospedado, é possível criar um novo cluster em um pode de Infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) ou um data center do IBM Cloud diferente do cluster inicial implementado na instância.

Para obter mais informações, veja [Incluindo e visualizando clusters para instâncias do vCenter Server](../vcenter/vc_addingviewingclusters.html).

### Mudando componentes

Esta liberação elimina o impacto em operações dentro do console do {{site.data.keyword.vmwaresolutions_short}} quando o administrador de Single Sign-On muda alguns recursos do vCenter Server de uma ferramenta nativa do VMware. Por exemplo, é possível, agora, modificar o data center virtual do VMware, cluster, comutadores, grupos de portas e nomes de armazenamento de dados do VMware vSphere Web Client para customizar implementações para empresas ou convenções de nomenclatura pessoal e sem nenhum impacto de recebimento de dados para as operações de dentro do console do {{site.data.keyword.vmwaresolutions_short}}.

Para obter mais informações, veja [Impactos da mudança de componentes para instâncias do vCenter Server](../vcenter/vcenter_chg_impact.html).

### Tamanhos de RAM adicionais

Ao pedir instâncias do vCenter Server ou incluir clusters para instâncias do vCenter Server, você tem mais tamanhos de RAM para escolher para ajudar na correspondência da razão entre CPU e RAM da carga de trabalho para o hardware. As opções a seguir estão disponíveis na opção de configuração **Customizado pelo usuário** ao pedir um servidor do console do {{site.data.keyword.vmwaresolutions_short}}: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB.

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html).

### Atualização de versão do Network File System

O Network File System (NFS) Versão 4.1 não está mais disponível como uma configuração de armazenamento da interface com o usuário. Todas as instâncias do vCenter Server são implementadas com o NFS V3. Embora o NFS V3 seja uma versão de protocolo mais antiga, ele permite recursos aprimorados em ambientes do VMware com suporte para o VMware Storage Distributed Resource Scheduler (SDRS) e o Storage I/O Control (SIOC).

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html).

### Nome de domínio do Servidor de Nomes de Domínio de site único

Agora, é possível fornecer o nome de domínio do Servidor de Nomes de Domínio (DNS) para uma instância do vCenter Server durante um pedido. Um Microsoft Windows Server Virtual Server Instance (VSI), que funciona como o DNS para a instância em que os hosts e máquinas virtuais são registrados, é implementado e pode ser consultado. O Microsoft Active Directory (AD) também é configurado no VSI do Microsoft Windows e o nome de domínio do DNS é a raiz de floresta do domínio do AD. Esse VSI do Microsoft Windows está disponível apenas na V1.9 e mais recente.

Para obter mais informações, veja:
* [Visão geral do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Visualizando instâncias do vCenter Server](../vcenter/vc_viewinginstances.html)

## Requisitos para instalação automática de atualizações do Windows Server

O Microsoft Active Directory (AD)/Servidor de nomes de domínio (DNS) é configurado automaticamente para fazer download apenas de atualizações. Ele não instala e reinicializa automaticamente essas atualizações. Deve-se instalar as atualizações manualmente e reinicializar em um horário planejado que evite interrupções da configuração do servidor Active Directory em andamento e outras tarefas de backup. Para aplicar atualizações do Windows, instale as atualizações manualmente.

## Documentação nova e atualizada

* Saiba como proteger suas instâncias privadas VCF de vários sites enquanto estiver estendendo seus aplicativos VMware para usar serviços públicos do IBM Cloud. Para obter mais informações, veja [Conectar com segurança suas cargas de trabalho privadas do VMware no IBM Cloud](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* Documentação adicional é fornecida para configurar firewalls que permitem toda a comunicação de protocolo das máquinas virtuais do IBM CloudDriver e do SDDC Manager. Para obter mais informações, veja [Componentes e considerações para o Fortinet on IBM Cloud](../services/fsa_considerations.html).
