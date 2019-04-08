---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas sobre a Liberação para V2.7
{: #relnotes_v27}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Suporte ao servidor 6140 do SAP-certificado
{: #relnotes_v27-sap}

Iniciando com a liberação V2.7, os novos modelos de CPU do {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} estão disponíveis para implementação para instâncias e clusters do VMware vCenter Server on {{site.data.keyword.cloud_notm}} e do VMware vSphere on {{site.data.keyword.cloud_notm}}:
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 192 GB de RAM
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.2 GHz / 384 GB de RAM
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 768 GB de RAM

Para obter mais informações, veja a seção *Configurações do {{site.data.keyword.baremetal_short_sing}}* em:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Atualizações para serviços complementares
{: #relnotes_v27-services}

### IBM Cloud Privado Hospedado
{: #relnotes_v27-icp}

O serviço {{site.data.keyword.cloud_notm}} Private Hosted está agora disponível para instâncias do VMware vCenter Server with Hybridity Bundle, além das instâncias do VMware vCenter Server que são implementadas em (ou submetidas a upgrade para) liberações da V2.5 e mais recente. Agora é possível pedir uma instância do vCenter Server ou uma instância do vCenter Server with Hybridity Bundle com o serviço incluído. Também é possível incluir o serviço em uma instância existente do vCenter Server ou em uma instância do vCenter Server with Hybridity Bundle após a implementação inicial.

Para obter mais informações, veja os tópicos a seguir:
* [Visão geral do {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [ Ordenando  {{site.data.keyword.cloud_notm}}  Privado Hospedado ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)

### Mission Critical VMware on IBM Cloud
{: #relnotes_v27-mcv}

O serviço Mission Critical VMware on {{site.data.keyword.cloud_notm}} agora está disponível para instâncias que estão implementadas em, ou foram submetidas a upgrade para, liberações da V2.7 ou mais recente.

O Mission Critical VMware on {{site.data.keyword.cloud_notm}} entrega uma arquitetura de nuvem multizona para ajudar as empresas a evitar o tempo de inatividade para aplicativos em nuvem e para automatizar failovers dentro de uma região de nuvem. Com essa arquitetura de nuvem, é possível alcançar uma taxa de sucesso de disponibilidade e de failover mais alta do que a maioria dos clientes do VMware podem alcançar com ambientes no local ou plataformas de nuvem concorrentes.

Para obter mais informações, consulte [Visão geral do Mission Critical VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mcv_overview).

### F5 on IBM Cloud
{: #relnotes_v27-f5}

Agora, ao pedir o serviço F5 on {{site.data.keyword.cloud_notm}}, é possível selecionar se você deseja que o F5 aplique a licença por meio de rede pública ou de rede privada com um servidor proxy. Para obter mais informações, veja [Pedindo o F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering).

### FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v27-fva}

No 3Q 2018, o Fortinet mudou seus pacotes de assinaturas. Para obter mais informações, consulte [Pedindo o dispositivo virtual FortiGate no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering).

Para o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} que é implementado em instâncias do Cloud Foundation V2.7 e mais recente e em instâncias do vCenter Server, o FortiOS 6.0.3 é provisionado.

Ao pedir o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, é possível selecionar se deseja que o FortiGuard aplique atualizações de licença e de segurança na rede pública ou na rede privada com um servidor proxy. Para obter mais informações, consulte [Pedindo o dispositivo virtual FortiGate no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering).

### Atualizações de componentes de serviço Zerto on IBM Cloud
{: #relnotes_v27-zerto}

Para o serviço Zerto on {{site.data.keyword.cloud_notm}} que é implementado em instâncias do Cloud Foundation V2.7 e mais recente e em instâncias do vCenter Server, o Zerto Virtual Replication 6.0, atualização 3, é provisionado. Para obter mais informações, consulte [Visão geral do Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

### Integração do KMIP for VMware on IBM Cloud com o IBM Cloud Activity Tracker
{: #relnotes_v27-kmip-icat}

Além dos eventos de instância do VMware, os eventos para o KMIP for VMware on {{site.data.keyword.cloud_notm}}, como criação de chave, exclusão de chave e acesso de chave, agora estão integrados à sua instância do {{site.data.keyword.cloud_notm}} Activity Tracker.

### KMIP for VMware on IBM Cloud - Descontinuado
{: #relnotes_v27-kmip-deprecated}

(Atualizado em 14 de dezembro de 2018) A versão atual do KMIP for VMware on {{site.data.keyword.cloud_notm}} está sendo descontinuada. Para obter mais informações, [entre em contato com o suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).
{:deprecated}

## Documentação nova e atualizada
{: #relnotes_v27-new-docs}

### Arquitetura de Referência da documentação
{: #relnotes_v27-ref-archi}

Os documentos técnicos a seguir estão agora disponíveis na seção *Referência* da documentação do usuário:

* [ Arquitetura da solução do NSX Edge Services Gateway ](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview)
* [ Guia do VMware Update Manager ](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro)
* [ Guia de rede do vCenter Server ](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)
* [ vCenter Server e  {{site.data.keyword.cloud_notm}}  Guia privado ](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Guia de serviço do vCenter Server e do IBM Kubernetes](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro)
* [Guia do VMware e do Skate Advisor Concept Car](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro)
* [VMware - A jornada de modernização do Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney)

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v27-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* A guia **Customizado** na qual você especifica o modelo de CPU e a RAM para as configurações do {{site.data.keyword.baremetal_short_sing}} ao pedir instâncias agora é dividida nas guias **Skylake** e **Broadwell** com base no tipo de servidor para ajudá-lo na seleção do servidor.
* As opções **Pré-configurado** para configuração do Bare Metal Server não estão mais disponíveis.
* Agora, a coluna **Tipo** está incluída na tabela **Instâncias do vCenter Server** na página **Recursos** para identificar as instâncias do vCenter Server, do vCenter Server with Hybridity Bundle e do vCenter Limited Test Drive.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
