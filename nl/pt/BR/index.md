---

copyright:

  years: 2016, 2019

lastupdated: "2019-04-16"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Tutorial de introdução
{: #getting-started}

Neste tutorial de introdução, levaremos você pelo processo de solicitação de uma instância e de alguns serviços complementares para ela.
{:shortdesc}

## Antes de iniciar
{: #getting-started-prereqs}

Antes de começar a trabalhar com o {{site.data.keyword.vmwaresolutions_full}}, revise as informações importantes a seguir sobre requisitos do navegador, contas de usuários, opções de implementação e serviços complementares.

### Requisitos do navegador
{: #getting-started-browser-req}

Os seguintes navegadores são suportados:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

O Microsoft Internet Explorer não é suportado.
{:note}

Para obter uma visualização ideal e trabalhar no console do {{site.data.keyword.vmwaresolutions_short}}, configure a resolução da tela para pelo menos 1024 px de largura por 500 px de altura.

### Contas de usuário
{: #getting-started-user-accts}

Você precisa de uma conta do {{site.data.keyword.cloud_notm}} e de uma conta de infraestrutura do {{site.data.keyword.cloud_notm}}. Essas contas devem atender a determinados requisitos.

   Tabela 1. Contas de Usuário Necessárias
   <table>
   <tr>
      <th>Conta</th>
      <th>Descrição</th>
   </tr>
   <tr>
      <td>IBMid</td>
      <td>Usando o **IBMid**, é possível ter um nome do usuário de login único para todos os produtos e serviços IBM que você usa, incluindo {{site.data.keyword.cloud_notm}}. O {{site.data.keyword.vmwaresolutions_short}} é fornecido como uma solução de infraestrutura no catálogo do {{site.data.keyword.cloud_notm}}. Para acessar o console do {{site.data.keyword.vmwaresolutions_short}}. deve-se ter um **IBMid**.<br><br>Para usar seu **IBMid** para efetuar login no console do {{site.data.keyword.vmwaresolutions_short}}, deve-se associar o **IBMid** a uma conta do {{site.data.keyword.cloud_notm}}. Ao efetuar login no console pela primeira vez, você será orientado a associar o seu **IBMid** existente a uma conta do {{site.data.keyword.cloud_notm}} ou a se inscrever para uma nova conta do {{site.data.keyword.cloud_notm}}. A nova conta do {{site.data.keyword.cloud_notm}} é automaticamente associada ao seu **IBMid**. É necessário passar por esse processo apenas uma vez.<br><br>Se você tiver problemas ao associar seu **IBMid** a uma conta do {{site.data.keyword.cloud_notm}}, consulte [Resolução de problemas para acessar o {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-accessing#accessing).</td>
   </tr>
   <tr>
      <td>Conta do IBM Cloud</td>
      <td>Para solicitar e usar os serviços do {{site.data.keyword.cloud_notm}}, é necessária uma conta do {{site.data.keyword.cloud_notm}}. As informações de faturamento estão associadas à conta do {{site.data.keyword.cloud_notm}}. O custo da infraestrutura física e virtual e as licenças resultantes são debitados de sua conta do {{site.data.keyword.cloud_notm}}.</td>
   </tr>
   <tr>
      <td>Conta de infraestrutura do IBM Cloud</td>
      <td>Para obter informações sobre os requisitos para uma conta de infraestrutura do {{site.data.keyword.cloud_notm}}, consulte [Requisitos para a conta de infraestrutura do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).<br><br>É possível vincular contas de infraestrutura do {{site.data.keyword.cloud_notm}} com contas do {{site.data.keyword.cloud_notm}} para usar os recursos combinados infraestrutura como serviço (IaaS) e plataforma como serviço (PaaS). Em seguida, é possível acessar recursos de IaaS e
de PaaS por meio de um login único. A vinculação de suas contas também fornece uma única fatura para todos os recursos PaaS e IaaS que você usa.<ul><li>Se você não tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}}, solicite uma seguindo o procedimento em [Inscrevendo-se para uma conta de infraestrutura do IBM Cloud](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account#signing_softlayer_account-infra) e, em seguida, vincule sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} à sua conta do {{site.data.keyword.cloud_notm}} seguindo o procedimento em [Alternando para o IBMid e vinculando contas](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).</li><li>Se você tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}}, será possível vinculá-la à sua conta do {{site.data.keyword.cloud_notm}} seguindo o procedimento em [Alternando para o IBMid e vinculando contas](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).</li></ul></td>
   </tr>
   </table>

### Ofertas de implementação
{: #getting-started-depl-offerings}

Revise e escolha sua oferta de implementação.

  Tabela 2. Ofertas de implementação
  <table>
    <tr>
       <th>Oferta de implementação</th>
       <th>Descrição</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)</td>
       <td>Com a oferta do vCenter Server, é possível implementar um ambiente virtual VMware usando recursos customizados de cálculo, de armazenamento e de rede para melhor se adequar às suas necessidades de negócios.</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)</td>
       <td>A oferta vCenter Server with Hybridity é uma nuvem particular host que ajuda a estender de forma rápida e fácil sua infraestrutura no local para a nuvem. O ambiente do VMware é baseado nas licenças do Data Center definido pelo software VMware fornecido pela IBM e ele inclui o VMware Hybrid Cloud Extension (HCX). Usando o HCX, é possível conectar com segurança um ambiente do vSphere 5.0+ no local com os sites do {{site.data.keyword.cloud_notm}} para hibridismo de infraestrutura contínua e mobilidade de aplicativo verdadeira.</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)</td>
       <td>A oferta vSphere on {{site.data.keyword.cloud_notm}} fornece um serviço de virtualização customizável que combina o {{site.data.keyword.baremetal_short}} compatível com VMware, os componentes de hardware e as licenças para construir seu próprio ambiente VMware hospedado pela IBM.</td>
    </tr>
    <tr>
       <td>[NetApp  ONTAP  Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)</td>
       <td>A oferta NetApp ONTAP Select permite implementar um cluster de armazenamento definido por software que direciona as suas necessidades para um dispositivo de armazenamento dedicado e altamente disponível com base no NetApp ONTAP Select.</td>
    </tr>
  </table>

### Serviços de complemento
{: #getting-started-add-on-services}

Revise e escolha os serviços complementares para a oferta de implementação.

  Tabela 3. Serviços complementares disponíveis para ofertas de implementação
  <table>
    <tr>
       <th>Nome do Serviço</th>
       <th>Descrição</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)</td>
       <td>O F5 no serviço {{site.data.keyword.cloud_notm}} (F5 BIG-IP® Virtual Edition) fornece serviços inteligentes de gerenciamento de tráfego e balanceamento de carga L4-L7 em escala local e global, rede robusta e proteção de firewall de aplicativo da web e acesso a aplicativo seguro e federado.</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)</td>
       <td>O serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} implementa um par de dispositivos FortiGate Security Appliance (FSA) série 300 em um modo altamente disponível para fornecer serviços de firewall, roteamento, NAT e VPN para proteger todos os servidores e máquinas virtuais na VLAN pública de suas instâncias.</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)</td>
       <td>O serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} implementa um par de FortiGate Virtual Appliances em seu ambiente, o que pode ajudá-lo a reduzir o risco ao implementar controles de segurança crítica em sua infraestrutura virtual.</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)</td>
       <td>O serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}} cumpre e controla a conformidade com relação a padrões de segurança e fornece os recursos detalhados de controle de acesso baseado na função (RBAC), aprovação e auditoria. Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no {{site.data.keyword.CloudDataCent_notm}}.</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)</td>
       <td>O serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}} oferece criptografia avançada com o gerenciamento de chave integrado para assegurar as cargas de trabalho em todo o seu ciclo de vida. O serviço pode fornecer criptografia no nível do sistema operacional e no nível de dados, o que significa que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho pode ser criptografado e decriptografado.</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)</td>
       <td>O serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}} simplifica o gerenciamento de cargas de trabalho criptografadas automatizando e simplificando o ciclo de vida de chaves de criptografia. O serviço pode gerenciar facilmente as chaves de criptografia em escala usando a criptografia compatível com FIPS 140-2.</td>
    </tr>
    <tr>
       <td>[IBM Cloud Privado Hospedado](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)</td>
       <td>O serviço {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} traz o poder de microsserviços e contêineres para o ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)</td>
       <td>O serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementar o serviço como uma solução independente ou integrá-lo ao ambiente do IBM Spectrum Protect para transferir cópias para armazenamento e controle de dados de longo prazo.</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)</td>
       <td>O serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} fornece um serviço altamente disponível para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia. Ele também fornece a capacidade de gerenciamento para manter as
associações entre as credenciais do cliente e as chaves de criptografia.</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)</td>
       <td>O serviço Veeam no {{site.data.keyword.cloud_notm}} se integra continuamente diretamente com os hypervisors do VMware para ajudar sua empresa a alcançar alta disponibilidade. Este serviço pode fornecer pontos de recuperação e objetivos de tempo para seus aplicativos e dados. Os pontos de recuperação e os objetivos de tempo podem ser fornecidos em menos de 15 minutos após a conclusão da configuração. Ao usar esse serviço, é possível controlar diretamente o backup e a restauração de todas as máquinas virtuais para sua infraestrutura do console do Veeam.</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)</td>
       <td>O serviço HCX no {{site.data.keyword.cloud_notm}} pode ampliar continuamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, que permite que máquinas virtuais (VMs) sejam migradas para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)</td>
       <td>O serviço Zerto on {{site.data.keyword.cloud_notm}} fornece recursos de replicação e de recuperação de desastre, que podem ser integrados às ofertas de implementação para proteger e recuperar dados no ambiente virtual do VMware no {{site.data.keyword.cloud_notm}}.</td>
    </tr>
   </table>

## Etapa 1: Acessando o console do IBM Cloud for VMware Solutions
{: #getting-started-step1}

O console do {{site.data.keyword.vmwaresolutions_short}} é a interface em que você pede e gerencia suas implementações. Cada implementação é gerenciada como uma instância no console. O console é uma interface com o usuário independente que é separada do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}}.

Para acessar o console do {{site.data.keyword.vmwaresolutions_short}}:
1. Acesse https://cloud.ibm.com/infrastructure/vmware-solutions/console.
2. Efetue login no console com seu **IBMid**.

## Etapa 2: Configurando a conta do usuário e as configurações
{: #getting-started-step2}

Antes de pedir uma instância, deve-se inserir o nome do usuário e a chave de API de sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações** do console.

Para obter informações sobre como configurar a conta do usuário e as configurações, consulte [Gerenciando contas do usuário e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Etapa 3: Solicitando uma Instância
{: #getting-started-step3}

Depois de decidir sobre uma oferta de implementação, que é gerenciada como uma instância no console, inicie o processo de solicitação.

Para obter informações sobre como solicitar uma instância, consulte os tópicos a seguir com base em sua seleção de oferta de implementação:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Pedindo instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Etapa 4: Visualizando a instância
{: #getting-started-step4}

Depois de efetuar um pedido de instância na **Etapa 3**, a implementação da instância é iniciada automaticamente. É possível rastrear o status da implementação visualizando os detalhes da instância. Quando a implementação da instância é concluída, também é possível visualizar as informações de resumo e detalhadas da instância e seus serviços complementares na página de detalhes da instância.

Para obter informações sobre como visualizar a instância que você solicitou, consulte os tópicos a seguir:
* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Visualizando instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Visualizando instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
