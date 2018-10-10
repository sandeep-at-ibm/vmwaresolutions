---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# Notas sobre a liberação para V1.9

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud

Essa liberação introduz a oferta VMware vSphere on {{site.data.keyword.cloud_notm}}. Essa oferta permite construir seu próprio ambiente virtual do VMware hospedado pela IBM ao customizar e pedir os recursos de cálculo, de armazenamento e de rede compatíveis com o VMware com base em componentes selecionados do VMware. Embora o vSphere on {{site.data.keyword.cloud_notm}} não automatize a instalação, a configuração e a abertura dos componentes opcionais do VMware, você tem flexibilidade máxima para projetar e arquitetar um ambiente que melhor atenda às suas necessidades de negócios. Comece criando um novo cluster de servidores ESXi do vSphere ou ampliando a escala de um cluster existente do vSphere em um {{site.data.keyword.CloudDataCent_notm}}.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html)
* [Ajustando a escala de clusters existentes do vSphere](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

Esta liberação apresenta a oferta NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}, um dispositivo virtual para armazenamento definido por software, que implementa o NetApp ONTAP Select como um serviço no {{site.data.keyword.baremetal_short}} dedicado do IBM Cloud. O NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} é oferecido nas configurações de alto desempenho (todas SSD) e de alta capacidade (todas SATA).
Essa oferta hospeda seu armazenamento em infraestrutura dedicada e fornece recursos da NetApp, como deduplicação, compactação e criptografia de dados em repouso. Provisione recursos de armazenamento com agilidade e flexibilidade enquanto protege os dados usando funções avançadas de gerenciamento de dados. Por exemplo, use as cópias rápidas e eficientes do NetApp Snapshot®, as cópias do FlexClone® e a replicação do SnapMirror®.

Para obter mais informações, veja os tópicos a seguir:
* [Visão geral do NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Pedindo instâncias do NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Serviço F5 on IBM Cloud

O serviço F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} está agora disponível para as instâncias do VMware Cloud Foundation e do VMware vCenter Server. Este serviço fornece serviços inteligentes de balanceamento de carga e gerenciamento de tráfego L4-L7 em escala local e global, rede robusta e proteção de firewall de aplicativo da web, e acesso seguro e federado ao aplicativo.
Peça instâncias com o serviço F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} incluído ao pedir sua instância ou inclua esse serviço em suas instâncias existentes posteriormente por meio da guia **Serviços** na página de detalhes de propriedade da instância do console do {{site.data.keyword.vmwaresolutions_short}}. Dependendo de seus requisitos, é possível selecionar uma das três opções de licenciamento para o BIG-IP VEs.

Para obter mais informações, veja os tópicos a seguir:
* [ Considerações para F5 no  {{site.data.keyword.cloud_notm}} ](../services/f5_considerations.html)
* [Gerenciando o F5 no {{site.data.keyword.cloud_notm}}](../services/managing_f5.html)

## Serviços gerenciados do IBM-Integrated Managed Infrastructure

Os serviços gerenciados do IBM-Integrated Managed Infrastructure (IMI) estão agora disponíveis para instâncias do VMware Cloud Foundation. O IMI pode simplificar o gerenciamento de infraestrutura virtual do VMware com serviços modulares e pode servir como um provedor único e confiável para reduzir a complexidade do monitoramento e gerenciamento de infraestruturas de TI virtuais. Transfira algumas operações do dia a dia para o IMI, como o monitoramento, para que seja possível focar em iniciativas de valor mais alto.

É possível solicitar uma consulta e uma estimativa a qualquer momento na página **Introdução**.
Para obter mais informações, veja [Solicitando serviços gerenciados do IMI](../services/managing_imi.html#requesting-managed-services-from-imi).

## Restrições de nome da instância para instâncias do vCenter Server e do NetApp ONTAP Select

Os nomes de instâncias inseridos no {{site.data.keyword.vmwaresolutions_short}} quando você pede suas instâncias não podem ter caracteres especiais (como o caractere traço) neles. Apenas caracteres alfanuméricos são permitidos. Essa restrição não se aplica a instâncias do Cloud Foundation.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Pedindo instâncias do NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Atualizações para instâncias do VMware Cloud Foundation

### Customizar a CPU e a memória da instância

Uma opção do servidor customizado pelo usuário está disponível junto com as opções Pequeno e Padrão pré-construídas e testadas. Para melhor corresponder à razão entre CPU e RAM de suas cargas de trabalho para o hardware compatível com VMware, é possível selecionar de forma independente o número total de núcleos em um servidor de CPU dual e a quantidade de RAM. O armazenamento local não é customizável.

Para obter mais informações, veja [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html).

## Atualizações para instâncias do VMware vCenter Server

### Suporte ao cluster do data center cruzado

Para aprimorar a ampliação de seu ambiente VMware hospedado, agora é possível criar um novo cluster em um pod de Infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) ou em um {{site.data.keyword.CloudDataCent_notm}} diferente do cluster inicial implementado na instância.

Para obter mais informações, veja [Incluindo e visualizando clusters para instâncias do vCenter Server](../vcenter/vc_addingviewingclusters.html).

### Mudando componentes

Esta liberação elimina o impacto em operações dentro do console do {{site.data.keyword.vmwaresolutions_short}} quando o administrador de Single Sign-On muda alguns recursos do vCenter Server de uma ferramenta nativa do VMware. Por exemplo, agora é possível modificar o datacenter virtual, o cluster, os comutadores, os grupos de portas e os nomes de armazenamento de dados do VMware por meio do VMware vSphere Web Client para customizar implementações para convenções de nomenclatura pessoais ou da empresa e sem qualquer impacto no recebimento de dados nas operações de dentro do console do {{site.data.keyword.vmwaresolutions_short}}.

Para obter mais informações, veja [Impactos da mudança de componentes para instâncias do vCenter Server](../vcenter/vcenter_chg_impact.html).

### Tamanhos de RAM adicionais

Ao pedir instâncias do vCenter Server ou incluir clusters para instâncias do vCenter Server, agora você tem mais tamanhos de RAM dos quais escolher para ajudar a corresponder à razão de CPU para RAM da carga de trabalho para o hardware. As opções a seguir estão disponíveis na opção de configuração **Customizado pelo usuário** ao pedir um servidor do console do {{site.data.keyword.vmwaresolutions_short}}: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB.

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html).

### Atualização de versão do Network File System

O Network File System (NFS) Versão 4.1 não está mais disponível como uma configuração de armazenamento da interface com o usuário. Todas as instâncias do vCenter Server são implementadas com o NFS V3. Embora o NFS V3 seja uma versão de protocolo mais antiga, ele permite recursos aprimorados em ambientes do VMware com suporte para o VMware Storage Distributed Resource Scheduler (SDRS) e o Storage I/O Control (SIOC).

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html).

### Nome de domínio do Servidor de Nomes de Domínio de site único

Agora, é possível fornecer o nome de domínio do Servidor de Nomes de Domínio (DNS) para uma instância do vCenter Server durante um pedido. Um Microsoft Windows Server Virtual Server Instance (VSI), que funciona como o DNS para a instância em que os hosts e máquinas virtuais são registrados, é implementado e pode ser consultado. O Microsoft Active Directory (AD) também é configurado no VSI do Microsoft Windows e o nome de domínio do DNS é a raiz de floresta do domínio do AD. Esse VSI do Microsoft Windows está disponível apenas na V1.9 e mais recente.

Para obter mais informações, veja os tópicos a seguir:
* [Visão geral do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Visualizando instâncias do vCenter Server](../vcenter/vc_viewinginstances.html)

## Requisitos para instalação automática de atualizações do Windows Server

O Microsoft Active Directory (AD)/Servidor de nomes de domínio (DNS) é configurado automaticamente para fazer download somente de atualizações. Ele não instala nem reinicia automaticamente essas atualizações. Deve-se instalar as atualizações manualmente e reiniciar em um tempo de planejamento que evite interrupções da configuração em andamento do Active Directory Server e de outras tarefas de backup. Para aplicar atualizações do Windows, instale as atualizações manualmente.

## Documentação nova e atualizada

* Saiba como proteger suas instâncias multisite privadas do Cloud Foundation enquanto amplia os aplicativos do VMware para usar serviços públicos do {{site.data.keyword.cloud_notm}}. Para obter mais informações, veja [Conectar com segurança as suas cargas de trabalho privadas do VMware no {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* É fornecida mais documentação para configurar firewalls que permitem toda a comunicação de protocolo das máquinas virtuais IBM CloudDriver e SDDC Manager. Para obter mais informações, veja [ Componentes e considerações para o Fortinet on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html).
