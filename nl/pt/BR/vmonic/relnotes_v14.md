---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# Notas sobre a liberação para V1.4

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Atualizações de componentes para instâncias do Cloud Foundation

Os componentes a seguir são novos ou atualizados:

* VC e PSC (vCenter e Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* Um novo VSI (Virtual Server Instance) do Windows é pedido para os serviços Microsoft Active Directory (AD) e DNS (Domain Name System), que são necessários para o suporte de configuração de vários sites nesta liberação. Este VSI tem as seguintes especificações: Windows 2012 R2 (8 GB de RAM / 2 núcleos de CPU / 100 GB de disco / uplinks privados dual de 1 Gbps).

Para obter mais informações, veja [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Atualizações de componentes para instâncias do vCenter Server

Os componentes a seguir são novos ou atualizados:

### VMware NSX for vSphere 6.2.4

Agora, o VMware NSX for vSphere 6.2.4 é instalado por padrão em todas as instâncias do vCenter Server (anteriormente apenas em instâncias do Cloud Foundation).

Como parte da instalação do NSX, o NSX Manager é instalado e licenciado em todas as novas instâncias que são implementadas. Além disso, um NSX Edge é criado para gerenciamento de instância, mas é possível criar seus próprios componentes do NSX Edge, se necessário. Para obter mais informações sobre o NSX Edge, veja a seção _VMware NSX Edge_ nesta página.

**Nota**: o NSX Controller não é instalado em instâncias do vCenter Server (a maneira como ele é instalado em instâncias do Cloud Foundation). Se você estiver usando a VXLAN ou roteadores lógicos distribuídos para suas instâncias do vCenter Server, você mesmo deverá instalar o NSX Controller.

Para obter mais informações sobre os aprimoramentos que foram introduzidos no VMware NSX for vSphere 6.2.4, seus requisitos e problemas conhecidos, consulte [Notas sobre a liberação do NSX for vSphere 6.2.4](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### VMware NSX Edge

Agora, o NSX Edge é incluído como parte das novas instâncias do vCenter Server que você está pedindo. O NSX Edge fornece serviços de segurança e de gateway de rede de ponta para isolar uma rede virtualizada.

Durante a implementação da instância, um Management VMware NSX Edge Services Gateway (ESG) é implementado pela IBM. Este ESG é usado pelas máquinas virtuais de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação. Esse ESG é implementado para incluir duas interfaces: uma interface é conectada à VLAN privada do {{site.data.keyword.cloud_notm}} e a outra é conectada à VLAN pública do {{site.data.keyword.cloud_notm}}.

Para garantir a segurança, as regras de firewall estão em vigor para permitir apenas comunicações HTTPS de saída iniciadas pelas máquinas virtuais de gerenciamento. Este ESG é implementado em uma configuração Grande e somente o Suporte IBM pode modificar a configuração. Para obter mais informações, veja os tópicos a seguir:

* [especificações técnicas do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [O NSX Edge de serviços de gerenciamento representa um risco de segurança?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentação do VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### Licença do NSX

É pedida uma licença do VMware NSX Base for Service Providers Edition por nó.

### Novo bloco de endereço de sub-rede

É pedido um bloco de sub-rede de 16 endereços móveis públicos por nó.

## Atualizações do modelo de cobrança de serviço

O modelo de cobrança de serviço é simplificado:

* Para instâncias do Cloud Foundation, as taxas do _serviço da instância do VMware Cloud Foundation_, _serviço de armazenamento do VMware Cloud Foundation_ e
   _VMware Solutions Hypervisor_ são descontinuadas.
* Para instâncias do vCenter Server, as taxas da _instância do VMware vCenter Server_ e do _VMware Solutions Hypervisor_ são descontinuadas.
* Para ambos os tipos de instância, uma nova taxa de _Suporte e Serviços_ é introduzida, que é uma taxa mensal aplicada a cada nó.

## Atualizações para a topologia de rede da instância

Esta liberação inclui os seguintes aprimoramentos de topologia para suas instâncias:

* Para instâncias do Cloud Foundation e do vCenter Server: a configuração de rede otimizada, ou seja, apenas os endereços IP públicos e privados primários que são designados pelo SoftLayer® são conectados aos servidores ESXi. Endereços privados móveis não são mais implementados para o tráfego de gerenciamento.
* Para instâncias do Cloud Foundation apenas: servidor Windows AD SSO (Active Directory Single Sign-On) e servidor DNS (Sistema de Nomes de Domínio)

**Nota**: por causa dessas mudanças, não é possível usar suas instâncias pré-V1.4 existentes na liberação atual. Para reutilizar a configuração de suas instâncias existentes, deve-se fazer upgrade delas para a versão atual. Para obter mais informações, veja [Fazendo upgrade de instâncias da pré-V1.4](movinginstances.html).

## Suporte de configuração de vários sites para instâncias do Cloud Foundation

Agora, é possível implementar uma única instância do Cloud Foundation, como em liberações anteriores ou, além disso, implementar instâncias secundárias que estão conectadas a uma instância primária. O modelo de configuração multisite usa uma topologia hub-and-spoke com um site primário e um máximo de sete sites secundários.

Para obter mais informações, veja [Configuração de vários sites para instâncias do Cloud Foundation](../sddc/sd_multisite.html).

## Aprimoramentos para a implementação de recuperação de desastre do Zerto

* Para instâncias do Cloud Foundation, a implementação da recuperação de desastre Zerto é automatizada em vez de ser manipulada por meio de um chamado de suporte. Todos os componentes do Zerto, como uma sub-rede móvel privada, uma VSI (Virtual Service Instance) do Windows e os encargos de licença do Zerto são listados no custo estimado para que você possa revisar antes de fazer o seu pedido.
* Para instâncias do vCenter Server, a implementação da recuperação de desastre Zerto é feita por meio de um chamado de suporte, como na liberação anterior. No entanto, o NSX Edge e a sub-rede móvel pública não são mais necessários, pois são incluídos, agora, na implementação base. Os encargos para uma sub-rede móvel privada, um VSI (Virtual Service Instance) do Windows e a licença do Zerto ainda se aplicam.

Para obter mais informações, veja [Recuperação de desastre do Zerto](../services/addingzertodr.html).

## Processo de pedido da instância

O processo de pedido da instância é muito simplificado:

* Para as instâncias do Cloud Foundation e do vCenter Server, a página Credenciais do SoftLayer não é mais exibida durante o processo de pedido. As credenciais do SoftLayer que são definidas na página Configurações são usadas por padrão e será solicitado que você as atualize apenas se elas não atenderem aos requisitos.
* Além disso, para instâncias do vCenter Server, apenas a opção **Grande** para o tipo **Hardware** e a configuração **10 Gbps Dual** para a **Velocidade da Porta de Uplink** estão disponíveis, o que reduz o número de configurações a especificar ao fazer o pedido.

Para obter mais informações, veja os tópicos a seguir:

* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)

## Gerenciamento de Instância

Novos recursos e aprimoramentos são feitos no processo de gerenciamento da instância:

* Para instâncias do Cloud Foundation, é possível visualizar o nome do usuário e as senhas para vários componentes da instância na página de detalhes da instância. Para obter mais informações, veja [Visualizando instâncias do Cloud Foundation](../sddc/sd_viewinginstances.html).
* Para instâncias do vCenter Server, é possível instalar atualizações e correções de software para componentes IBM diretamente do console. Para obter mais informações, veja [Aplicando atualizações e correções a instâncias do vCenter Server](../vcenter/vc_applyingupdates.html).

## Notificações do console

Agora, é possível configurar notificações do console na página **Configurações**. Por padrão, a configuração é ativada, o que significa que você recebe uma notificação no console para todos os eventos. É possível também desativar notificações para o console na página **Configurações**.

Para obter mais informações, veja os tópicos a seguir:

* [Configurações e contas do usuário](useraccount.html)
* [Notificações](notifications.html)
