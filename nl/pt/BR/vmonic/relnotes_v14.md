---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-08"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a liberação para V1.4
{: #relnotes_v14}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Atualizações de componentes para instâncias do Cloud Foundation
{: #relnotes_v14-vcf-comp}

Os componentes a seguir são novos ou atualizados:

* VC e PSC (vCenter e Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* Um novo VSI (Virtual Server Instance) do Windows é pedido para os serviços Microsoft Active Directory (AD) e DNS (Domain Name System), que são necessários para o suporte de configuração de vários sites nesta liberação. Este VSI tem as seguintes especificações: Windows 2012 R2 (8 GB de RAM / 2 núcleos de CPU / 100 GB de disco / uplinks privados dual de 1 Gbps).

## Atualizações de componentes para instâncias do vCenter Server
{: #relnotes_v14-vcs-comp}

Os componentes a seguir são novos ou atualizados:

### VMware NSX for vSphere 6.2.4
{: #relnotes_v14-nsx}

Agora, o VMware NSX for vSphere 6.2.4 é instalado por padrão em todas as instâncias do vCenter Server (anteriormente apenas em instâncias do Cloud Foundation).

Como parte da instalação do NSX, o NSX Manager é instalado e licenciado em todas as novas instâncias que são implementadas. Além disso, um NSX Edge é criado para gerenciamento de instância, mas é possível criar seus próprios componentes do NSX Edge, se necessário. Para obter mais informações sobre o NSX Edge, veja a seção _VMware NSX Edge_ nesta página.

O NSX Controller não é instalado em instâncias do vCenter Server (a maneira como ele é instalado em instâncias do Cloud Foundation). Se você estiver usando a VXLAN ou roteadores lógicos distribuídos para suas instâncias do vCenter Server, você mesmo deverá instalar o NSX Controller.
{:note}

Para obter mais informações sobre os aprimoramentos que foram introduzidos no VMware NSX for vSphere 6.2.4, seus requisitos e problemas conhecidos, consulte [Notas sobre a liberação do NSX for vSphere 6.2.4](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### VMware NSX Edge
{: #relnotes_v14-nsx-edge}

Agora, o NSX Edge é incluído como parte das novas instâncias do vCenter Server que você está pedindo. O NSX Edge fornece serviços de segurança e de gateway de rede de ponta para isolar uma rede virtualizada.

Durante a implementação da instância, um Management VMware NSX Edge Services Gateway (ESG) é implementado pela IBM. Este ESG é usado pelas máquinas virtuais de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação. Esse ESG é implementado para incluir duas interfaces: uma interface é conectada à VLAN privada do {{site.data.keyword.cloud_notm}} e a outra é conectada à VLAN pública do {{site.data.keyword.cloud_notm}}.

Para garantir a segurança, as regras de firewall estão em vigor para permitir apenas comunicações HTTPS de saída iniciadas pelas máquinas virtuais de gerenciamento. Este ESG é implementado em uma configuração Grande e somente o Suporte IBM pode modificar a configuração. Para obter mais informações, veja os tópicos a seguir:

* [especificações técnicas do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)
* [O NSX Edge de serviços de gerenciamento representa um risco de segurança?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentação do VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### Licença do NSX
{: #relnotes_v14-nsx-license}

É pedida uma licença do VMware NSX Base for Service Providers Edition por nó.

### Novo bloco de endereço de sub-rede
{: #relnotes_v14-subnet}

É pedido um bloco de sub-rede de 16 endereços móveis públicos por nó.

## Atualizações do modelo de cobrança de serviço
{: #relnotes_v14-svc-charge}

O modelo de cobrança de serviço é simplificado:

* Para instâncias do Cloud Foundation, as taxas do _serviço da instância do VMware Cloud Foundation_, _serviço de armazenamento do VMware Cloud Foundation_ e
   _VMware Solutions Hypervisor_ são descontinuadas.
* Para instâncias do vCenter Server, as taxas da _instância do VMware vCenter Server_ e do _VMware Solutions Hypervisor_ são descontinuadas.
* Para ambos os tipos de instância, uma nova taxa de _Suporte e Serviços_ é introduzida, que é uma taxa mensal aplicada a cada nó.

## Atualizações para a topologia de rede da instância
{: #relnotes_v14-netwok-topo}

Esta liberação inclui os seguintes aprimoramentos de topologia para suas instâncias:

* Para instâncias do Cloud Foundation e do vCenter Server: a configuração de rede otimizada, ou seja, apenas os endereços IP públicos e privados primários que são designados pelo SoftLayer® são conectados aos servidores ESXi. Endereços privados móveis não são mais implementados para o tráfego de gerenciamento.
* Para instâncias do Cloud Foundation apenas: servidor Windows AD SSO (Active Directory Single Sign-On) e servidor DNS (Sistema de Nomes de Domínio)

Por causa dessas mudanças, não é possível usar as instâncias pré-V1.4 existentes na liberação atual. Para reutilizar a configuração de suas instâncias existentes, deve-se fazer upgrade delas para a versão atual.
{:note}

## Suporte de configuração de vários sites para instâncias do Cloud Foundation
{: #relnotes_v14-vcf-multisite}

Agora, é possível implementar uma única instância do Cloud Foundation, como em liberações anteriores ou, além disso, implementar instâncias secundárias que estão conectadas a uma instância primária. O modelo de configuração multisite usa uma topologia hub-and-spoke com um site primário e um máximo de sete sites secundários.

## Aprimoramentos para a implementação de recuperação de desastre do Zerto
{: #relnotes_v14-zerto}

* Para instâncias do Cloud Foundation, a implementação da recuperação de desastre Zerto é automatizada em vez de ser manipulada por meio de um chamado de suporte. Todos os componentes do Zerto, como uma sub-rede móvel privada, uma VSI (Virtual Service Instance) do Windows e os encargos de licença do Zerto são listados no custo estimado para que você possa revisar antes de fazer o seu pedido.
* Para instâncias do vCenter Server, a implementação da recuperação de desastre Zerto é feita por meio de um chamado de suporte, como na liberação anterior. No entanto, o NSX Edge e a sub-rede móvel pública não são mais necessários, pois são incluídos, agora, na implementação base. Os encargos para uma sub-rede móvel privada, um VSI (Virtual Service Instance) do Windows e a licença do Zerto ainda se aplicam.

Para obter mais informações, veja [Recuperação de desastre do Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

## Processo de pedido da instância
{: #relnotes_v14-inst-order}

O processo de pedido da instância é muito simplificado:

* Para as instâncias do Cloud Foundation e do vCenter Server, a página Credenciais do SoftLayer não é mais exibida durante o processo de pedido. As credenciais do SoftLayer que são definidas na página Configurações são usadas por padrão e será solicitado que você as atualize apenas se elas não atenderem aos requisitos.
* Além disso, para instâncias do vCenter Server, apenas a opção **Grande** para o tipo **Hardware** e a configuração **10 Gbps Dual** para a **Velocidade da Porta de Uplink** estão disponíveis, o que reduz o número de configurações a especificar ao fazer o pedido.

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Gerenciamento de Instância
{: #relnotes_v14-inst-mgmt}

Novos recursos e aprimoramentos são feitos no processo de gerenciamento da instância:

* Para instâncias do Cloud Foundation, é possível visualizar o nome do usuário e as senhas para vários componentes da instância na página de detalhes da instância.
* Para instâncias do vCenter Server, é possível instalar atualizações e correções de software para componentes IBM diretamente do console. Para obter mais informações, veja [Aplicando atualizações e correções a instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

## Notificações do console
{: #relnotes_v14-console-notif}

Agora, é possível configurar notificações do console na página **Configurações**. Por padrão, a configuração é ativada, o que significa que você recebe uma notificação no console para todos os eventos. É possível também desativar notificações para o console na página **Configurações**.

Para obter mais informações, veja os tópicos a seguir:

* [Configurações e contas do usuário](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [Notificações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
