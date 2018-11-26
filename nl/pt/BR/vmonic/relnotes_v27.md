---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# Notas sobre a Liberação para V2.7

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Suporte ao servidor 6140 do SAP-certificado

Iniciando com a liberação V2.7, os novos modelos de CPU do {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} estão disponíveis para implementação para instâncias e clusters do VMware vCenter Server on {{site.data.keyword.cloud_notm}} e do VMware vSphere on {{site.data.keyword.cloud_notm}}:
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 192 GB de RAM
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.2 GHz / 384 GB de RAM
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 768 GB de RAM

Para obter mais informações, veja a seção *Configurações do {{site.data.keyword.baremetal_short_sing}}* em:
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Atualizações para serviços complementares

### IBM Cloud Privado Hospedado

O serviço {{site.data.keyword.cloud_notm}} Private Hosted está agora disponível para instâncias do VMware vCenter Server with Hybridity Bundle, além das instâncias do VMware vCenter Server que são implementadas em (ou submetidas a upgrade para) liberações da V2.5 e mais recente. Agora é possível pedir uma instância do vCenter Server ou uma instância do vCenter Server with Hybridity Bundle com o serviço incluído. Também é possível incluir o serviço em uma instância existente do vCenter Server ou em uma instância do vCenter Server with Hybridity Bundle após a implementação inicial.

Para obter mais informações, veja os tópicos a seguir:
* [ {{site.data.keyword.cloud_notm}}  Visão geral do Private Hosted ](../services/icp_overview.html)
* [ Ordenando  {{site.data.keyword.cloud_notm}}  Privado Hospedado ](../services/icp_ordering.html)

### Mission Critical VMware on IBM Cloud

O serviço Mission Critical VMware on {{site.data.keyword.cloud_notm}} agora está disponível para instâncias que estão implementadas em, ou foram submetidas a upgrade para, liberações da V2.7 ou mais recente.

O Mission Critical VMware on {{site.data.keyword.cloud_notm}} entrega uma arquitetura de nuvem multizona para ajudar as empresas a evitar o tempo de inatividade para aplicativos em nuvem e para automatizar failovers dentro de uma região de nuvem. Com essa arquitetura de nuvem, é possível alcançar uma taxa de sucesso de disponibilidade e de failover mais alta do que a maioria dos clientes do VMware podem alcançar com ambientes no local ou plataformas de nuvem concorrentes.

Para obter mais informações, veja [Visão geral do Mission Critical VMware on {{site.data.keyword.cloud_notm}}](../services/mcv_overview.html).

### F5 on IBM Cloud

Agora, ao pedir o serviço F5 on {{site.data.keyword.cloud_notm}}, é possível selecionar se você deseja que o F5 aplique a licença por meio de rede pública ou de rede privada com um servidor proxy. Para obter mais informações, veja [Pedindo o F5 on {{site.data.keyword.cloud_notm}}](../services/f5_ordering.html).

### FortiGate Virtual Appliance on IBM Cloud

No 3Q 2018, o Fortinet mudou seus pacotes de assinaturas. Para obter mais informações, consulte [Pedindo o dispositivo virtual FortiGate no {{site.data.keyword.cloud_notm}}](../services/fortinetvm_ordering.html).

Para o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} que é implementado em instâncias do Cloud Foundation V2.7 e mais recente e em instâncias do vCenter Server, o FortiOS 6.0.3 é provisionado.

Ao pedir o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, é possível selecionar se deseja que o FortiGuard aplique atualizações de licença e de segurança na rede pública ou na rede privada com um servidor proxy. Para obter mais informações, consulte [Pedindo o dispositivo virtual FortiGate no {{site.data.keyword.cloud_notm}}](../services/fortinetvm_ordering.html).

### Atualizações de componentes de serviço Zerto on IBM Cloud

Para o serviço Zerto on {{site.data.keyword.cloud_notm}} que é implementado em instâncias do Cloud Foundation V2.7 e mais recente e em instâncias do vCenter Server, o Zerto Virtual Replication 6.0, atualização 3, é provisionado. Para obter mais informações, consulte [Visão geral do Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html).

### Integração do KMIP for VMware on IBM Cloud com o IBM Cloud Activity Tracker

Além dos eventos de instância do VMware, os eventos para o KMIP for VMware on {{site.data.keyword.cloud_notm}}, como criação de chave, exclusão de chave e acesso de chave, agora estão integrados à sua instância do {{site.data.keyword.cloud_notm}} Activity Tracker. Para obter mais informações sobre o KMIP for WMware on {{site.data.keyword.cloud_notm}}, veja [Visão geral do KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html).

## Documentação nova e atualizada

### Arquitetura de Referência da documentação

Os documentos técnicos a seguir estão agora disponíveis na seção *Referência* da documentação do usuário:

* [ Arquitetura da solução do NSX Edge Services Gateway ](../archiref/nsx/nsx_overview.html)
* [ Guia do VMware Update Manager ](../archiref/vum/vum-intro.html)
* [ Guia de rede do vCenter Server ](../archiref/vcsnsxt/vcsnsxt-intro.html)
* [ vCenter Server e  {{site.data.keyword.cloud_notm}}  Guia privado ](../archiref/vcsicp/vcsicp-intro.html)
* [Guia de serviço do vCenter Server e do IBM Kubernetes](../archiref/vcsiks/vcsiks-intro.html)
* [Guia do VMware e do Skate Advisor Concept Car](../archiref/vcscar/vcscar-intro.html)
* [VMware - A jornada de modernização do Stock Trader](../archiref/vcscontent/vcscontent-modjourney.html)

Alguns desses documentos de arquitetura de referência estão disponíveis somente em inglês.

## Atualizações e aprimoramentos da interface com o usuário

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* A guia **Customizado** na qual você especifica o modelo de CPU e a RAM para as configurações do {{site.data.keyword.baremetal_short_sing}} ao pedir instâncias agora é dividida nas guias **Skylake** e **Broadwell** com base no tipo de servidor para ajudá-lo na seleção do servidor.
* As opções **Pré-configurado** para configuração do Bare Metal Server não estão mais disponíveis.
* A coluna **Tipo** agora está incluída na tabela **Instâncias do vCenter Server** na página **Instâncias implementadas** para identificar as instâncias do vCenter Server, do vCenter Server with Hybridity Bundle e do vCenter Limited Test Drive.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
