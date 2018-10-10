---

copyright:

  years: 2016, 2018

lastupdated: "2018-09-07"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Introdução ao IBM Cloud for VMware Solutions

Neste tutorial de introdução, levaremos você pelo processo de solicitação de uma instância e de alguns serviços complementares para ela.
{:shortdesc}

## Antes de iniciar
{: #prereqs}

Antes de começar a trabalhar com o {{site.data.keyword.vmwaresolutions_full}}, revise as informações importantes a seguir sobre requisitos do navegador, contas de usuários, opções de implementação e serviços complementares.

### Requisitos do navegador

Os seguintes navegadores são suportados:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

**Nota**: o Microsoft Internet Explorer não é suportado.

Para obter uma visualização ideal e trabalhar no console do {{site.data.keyword.vmwaresolutions_short}}, configure a resolução da tela para pelo menos 1024 px de largura por 500 px de altura.

### Contas de usuário

É necessária uma conta do {{site.data.keyword.cloud_notm}} e uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer). Essas contas devem atender a determinados requisitos.

   Tabela 1. Contas de Usuário Necessárias
   <table>
   <tr>
      <th>Conta</th>
      <th>Descrição</th>
   </tr>
   <tr>
      <td>IBMid</td>
      <td>Usando o **IBMid**, é possível ter um nome do usuário de login único para todos os produtos e serviços IBM que você usa, incluindo {{site.data.keyword.cloud_notm}}. O {{site.data.keyword.vmwaresolutions_short}} é fornecido como uma solução de infraestrutura no catálogo do {{site.data.keyword.cloud_notm}}. Para acessar o console do {{site.data.keyword.vmwaresolutions_short}}. deve-se ter um **IBMid**.<br><br>Para usar seu **IBMid** para efetuar login no console do {{site.data.keyword.vmwaresolutions_short}}, deve-se associar o **IBMid** a uma conta do {{site.data.keyword.cloud_notm}}. Ao efetuar login no console pela primeira vez, você será orientado a associar o seu **IBMid** existente a uma conta do {{site.data.keyword.cloud_notm}} ou a se inscrever para uma nova conta do {{site.data.keyword.cloud_notm}}. A nova conta do {{site.data.keyword.cloud_notm}} é automaticamente associada ao seu **IBMid**. É necessário passar por esse processo apenas uma vez.<br><br>Se você tiver problemas ao associar seu **IBMid** a uma conta do {{site.data.keyword.cloud_notm}}, consulte [Resolução de problemas para acessar o {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html).</td>
   </tr>
   <tr>
      <td>Conta do IBM Cloud</td>
      <td>Para solicitar e usar os serviços do {{site.data.keyword.cloud_notm}}, é necessária uma conta do {{site.data.keyword.cloud_notm}}. As informações de faturamento estão associadas à conta do {{site.data.keyword.cloud_notm}}. O custo da infraestrutura física e virtual e as licenças resultantes são debitados de sua conta do {{site.data.keyword.cloud_notm}}.</td>
   </tr>
   <tr>
      <td>Conta de infraestrutura do IBM Cloud (SoftLayer)</td>
      <td>A conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) era conhecida anteriormente como a conta do IBM SoftLayer.  Para obter mais informações sobre os requisitos que a conta deve atender, consulte [Requisitos para a conta de infraestrutura do {{site.data.keyword.cloud_notm}}](vmonic/slaccountrequirement.html).<br><br>É possível vincular contas de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) a contas do {{site.data.keyword.cloud_notm}} para usar recursos combinados de infraestrutura como serviço (IaaS) e plataforma como serviço (PaaS). Em seguida, é possível acessar recursos de IaaS e
de PaaS por meio de um login único. A vinculação de suas contas também fornece uma única fatura para todos os recursos PaaS e IaaS que você usa.<ul><li>Se você não tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer), solicite uma seguindo o procedimento em [Assinando uma conta de infraestrutura do IBM Cloud (SoftLayer)](vmonic/signing_softlayer_account.html) e, em seguida, vincule sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) à sua conta do {{site.data.keyword.cloud_notm}} seguindo o procedimento em [Vinculando contas do IBMid](https://console.bluemix.net/docs/account/softlayerlink.html).</li><li>Se você tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer), poderá vinculá-la à sua conta do {{site.data.keyword.cloud_notm}} seguindo o procedimento em [Vinculando contas do IBMid](https://console.bluemix.net/docs/account/softlayerlink.html).</li></ul></td>
   </tr>
   </table>

Para obter mais informações, veja os tópicos a seguir:
* [Inscrevendo-se para contas necessárias](vmonic/signing_softlayer_account.html)
* [Requisitos para a conta de infraestrutura do {{site.data.keyword.cloud_notm}}](vmonic/slaccountrequirement.html)

### Ofertas de implementação

Revise e escolha sua oferta de implementação.

  Tabela 2. Ofertas de implementação
  <table>
    <tr>
       <th>Oferta de implementação</th>
       <th>Descrição</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](vcenter/vc_vcenterserveroverview.html)</td>
       <td>Com a oferta do vCenter Server, é possível implementar um ambiente virtual VMware usando recursos customizados de cálculo, de armazenamento e de rede para melhor se adequar às suas necessidades de negócios.</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](vcenter/vc_hybrid_overview.html)</td>
       <td>A oferta vCenter Server with Hybridity é uma nuvem particular host que ajuda a estender de forma rápida e fácil sua infraestrutura no local para a nuvem. O ambiente do VMware é baseado nas licenças do Data Center definido pelo software VMware fornecido pela IBM e ele inclui o VMware Hybrid Cloud Extension (HCX). Usando o HCX, é possível conectar com segurança um ambiente do vSphere 5.0+ no local com os sites do {{site.data.keyword.cloud_notm}} para hibridismo de infraestrutura contínua e mobilidade de aplicativo verdadeira.</td>
    </tr>
    <tr>
       <td>[VMware Cloud Foundation on IBM Cloud](sddc/sd_cloudfoundationoverview.html)</td>
       <td>A oferta do Cloud Foundation fornece um ambiente virtual VMware unificado usando os recursos padrão de cálculo, armazenamento e rede do {{site.data.keyword.cloud_notm}}, que são dedicados a cada implementação do usuário.</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](vsphere/vs_vsphereclusteroverview.html)</td>
       <td>A oferta vSphere on {{site.data.keyword.cloud_notm}} fornece um serviço de virtualização customizável que combina o {{site.data.keyword.baremetal_short}} compatível com VMware, os componentes de hardware e as licenças para construir seu próprio ambiente VMware hospedado pela IBM.</td>
    </tr>
    <tr>
       <td>[NetApp ONTAP Select](netapp/np_netappoverview.html)</td>
       <td>A oferta NetApp ONTAP Select permite implementar um cluster de armazenamento definido por software que direciona as suas necessidades para um dispositivo de armazenamento dedicado e altamente disponível com base no NetApp ONTAP Select.</td>
    </tr>
    <tr>
       <td>[Federal do VMware on IBM Cloud](vcenter/vc_fed_overview.html)</td>
       <td>A oferta VMware Federal on {{site.data.keyword.cloud_notm}} fornece suporte para solicitar uma instância base do vCenter Server, além de fornecer a opção de proteger as instâncias implementadas, remover informações confidenciais e abrir a conexão de gerenciamento para acesso contínuo à instância para funções de gerenciamento.</td>
    </tr>
  </table>

### Serviços de complemento

Revise e escolha os serviços complementares para a oferta de implementação.

  Tabela 3. Serviços complementares disponíveis para ofertas de implementação
  <table>
    <tr>
       <th>Nome do Serviço</th>
       <th>Descrição</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](services/f5_considerations.html)</td>
       <td>O F5 no serviço {{site.data.keyword.cloud_notm}} (F5 BIG-IP® Virtual Edition) fornece serviços inteligentes de gerenciamento de tráfego e balanceamento de carga L4-L7 em escala local e global, rede robusta e proteção de firewall de aplicativo da web e acesso a aplicativo seguro e federado.</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](services/fsa_considerations.html)</td>
       <td>O serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} implementa um par de dispositivos FortiGate Security Appliance (FSA) série 300 em um modo altamente disponível para fornecer serviços de firewall, roteamento, NAT e VPN para proteger todos os servidores e máquinas virtuais na VLAN pública de suas instâncias.</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](services/fortinetvm_considerations.html)</td>
       <td>O serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} implementa um par de FortiGate Virtual Appliances em seu ambiente, o que pode ajudá-lo a reduzir o risco ao implementar controles de segurança crítica em sua infraestrutura virtual.</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](services/htcc_considerations.html)</td>
       <td>O serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}} cumpre e controla a conformidade com relação a padrões de segurança e fornece os recursos detalhados de controle de acesso baseado na função (RBAC), aprovação e auditoria. Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no {{site.data.keyword.CloudDataCent_notm}}.</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](services/htdc_considerations.html)</td>
       <td>O serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}} oferece criptografia avançada com o gerenciamento de chave integrado para assegurar as cargas de trabalho em todo o seu ciclo de vida. O serviço pode fornecer criptografia no nível do sistema operacional e no nível de dados, o que significa que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho pode ser criptografado e decriptografado.</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](services/htkc_considerations.html)</td>
       <td>O serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}} simplifica o gerenciamento de cargas de trabalho criptografadas automatizando e simplificando o ciclo de vida de chaves de criptografia. O serviço pode gerenciar facilmente as chaves de criptografia em escala usando a criptografia compatível com FIPS 140-2.</td>
    </tr>
    <tr>
       <td>[IBM Cloud Privado Hospedado](services/managing_icp.html)</td>
       <td>O serviço {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} traz o poder de microsserviços e contêineres para o ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](services/spp_considerations.html)</td>
       <td>O serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementar o serviço como uma solução independente ou integrá-lo ao ambiente do IBM Spectrum Protect para transferir cópias para armazenamento e controle de dados de longo prazo.</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](services/kmip_considerations.html)</td>
       <td>O serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} fornece um serviço altamente disponível para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia. Ele também fornece a capacidade de gerenciamento para manter as
associações entre as credenciais do cliente e as chaves de criptografia.</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](services/veeam_considerations.html)</td>
       <td>O serviço Veeam no {{site.data.keyword.cloud_notm}} se integra continuamente diretamente com os hypervisors do VMware para ajudar sua empresa a alcançar alta disponibilidade. Este serviço pode fornecer pontos de recuperação e objetivos de tempo para seus aplicativos e dados. Os pontos de recuperação e os objetivos de tempo podem ser fornecidos em menos de 15 minutos após a conclusão da configuração. Ao usar esse serviço, é possível controlar diretamente o backup e a restauração de todas as máquinas virtuais para sua infraestrutura do console do Veeam.</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](services/hcx_considerations.html)</td>
       <td>O serviço HCX no {{site.data.keyword.cloud_notm}} pode ampliar continuamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, que permite que máquinas virtuais (VMs) sejam migradas para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](services/addingzertodr.html)</td>
       <td>O serviço Zerto on {{site.data.keyword.cloud_notm}} fornece recursos de replicação e de recuperação de desastre, que podem ser integrados às ofertas de implementação para proteger e recuperar dados no ambiente virtual do VMware no {{site.data.keyword.cloud_notm}}.</td>
    </tr>
   </table>

## Etapa 1: Acessando o console do IBM Cloud for VMware Solutions

O console do {{site.data.keyword.vmwaresolutions_short}} é a interface em que você pede e gerencia suas implementações. Cada implementação é gerenciada como uma instância no console. O console é uma interface com o usuário independente que é separada do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}}.

Para acessar o console do {{site.data.keyword.vmwaresolutions_short}}:
1. Acesse https://console.ng.bluemix.net/infrastructure/vmware-solutions/console.
2. Efetue login no console com seu **IBMid**.

## Etapa 2: Configurando a conta do usuário e as configurações

Antes de solicitar uma instância, deve-se inserir o nome do usuário e a chave API de sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) na página **Configurações** do console.

Para obter informações sobre como configurar a conta do usuário e as configurações, consulte [Gerenciando contas do usuário e configurações](vmonic/useraccount.html).

## Etapa 3: Solicitando uma Instância

Depois de decidir sobre uma oferta de implementação, que é gerenciada como uma instância no console, inicie o processo de solicitação.

Para obter informações sobre como solicitar uma instância, consulte os tópicos a seguir com base em sua seleção de oferta de implementação:
* [Pedindo instâncias do vCenter Server](vcenter/vc_orderinginstance.html)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](vcenter/vc_hybrid_orderinginstance.html)
* [Pedindo instâncias do Cloud Foundation](sddc/sd_orderinginstance.html)
* [Pedindo novos clusters do vSphere](vsphere/vs_orderinginstances.html)
* [Pedindo instâncias do NetApp ONTAP Select](netapp/np_orderinginstances.html)  
* [Pedindo instâncias do VMware Federal](vcenter/vc_fed_orderinginstance.html)

## Etapa 4: Visualizando a instância

Depois de efetuar um pedido de instância na **Etapa 3**, a implementação da instância é iniciada automaticamente. É possível rastrear o status da implementação visualizando os detalhes da instância. Quando a implementação da instância é concluída, também é possível visualizar as informações de resumo e detalhadas da instância e seus serviços complementares na página de detalhes da instância.

Para obter informações sobre como visualizar a instância que você solicitou, consulte os tópicos a seguir:
* [Visualizando instâncias do vCenter Server](vcenter/vc_viewinginstances.html)
* [Visualizando instâncias do vCenter Server with Hybridity Bundle](vcenter/vc_hybrid_viewinginstances.html)
* [Visualizando instâncias do Cloud Foundation](sddc/sd_viewinginstances.html)
* [Visualizando instâncias do NetApp ONTAP Select](netapp/np_viewinginstances.html)
* [Visualizando instâncias do VMware Federal](vcenter/vc_fed_viewinginstance.html)

## Etapa 5: Gerenciando serviços complementares para a instância

Se você solicitou serviços complementares para sua instância, é possível gerenciar os serviços também.

Para obter informações sobre como gerenciar os serviços, consulte os tópicos a seguir:
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](vcenter/vc_hybrid_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](sddc/sd_addingremovingservices.html)

## Próxima etapa

Gerencie sua instância por meio do console do {{site.data.keyword.vmwaresolutions_short}} ou do Web client do VMware vSphere.
