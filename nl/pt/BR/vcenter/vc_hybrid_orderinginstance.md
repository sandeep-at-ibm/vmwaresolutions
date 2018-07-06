---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Pedindo instâncias do vCenter Server with Hybridity Bundle

Para implementar uma plataforma virtualizada VMware flexível e customizável que melhor se ajuste às suas necessidades de carga de trabalho, peça uma instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Sua ordem da instância do vCenter Server with Hybridity Bundle inclui o licenciamento do VMware Hybrid Cloud Extension (HCX) e autoriza você para o serviço VMware HCX on IBM Cloud. Também é possível incluir serviços, como [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html), para recuperação de desastre.

## Requisitos

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](../vmonic/useraccount.html).
*  Você revisou as informações em [Requisitos e planejamento para o vCenter Server with Hybridity Bundle](vc_hybrid_planning.html).
* Você revisou o formato de nome da instância e do domínio. O nome do domínio e o rótulo do subdomínio são usados para gerar o nome do usuário e os nomes do servidor da instância.

Tabela 1. Formato de valor para nomes de instância e de domínio

| Nome        | Formato do valor      |
  |:------------- |:------------- |
  | Nome de domínio | `<root_domain>` |  
  | Nome do usuário de login do vCenter Server | `<user_id>@<root_domain>` (Usuário do Microsoft Active Directory) ou `administrator@vsphere.local` |
  | FQDN do vCenter Server | `vcenter.<subdomain_label>.<root_domain>`. O comprimento máximo é de 50 caracteres. |
  | Nome do site de Conexão única (SSO) | `<subdomain_label>` |
  | Nome do servidor ESXi totalmente qualificado | `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que `<n>` é a sequência do servidor ESXi. O comprimento máximo é de 50 caracteres. |  
  | FQDN do PSC | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. O comprimento máximo é de 50 caracteres. |

**Importante**: não modifique quaisquer valores que são configurados durante o pedido e a implementação da instância. Isso pode fazer com que a instância se torne inutilizável. Por exemplo, a rede pública pode ser encerrada, os servidores e os Virtual Server Instances (VSIs) podem se mover para trás de uma meia provisão do Vyatta ou o IBM CloudBuilder VSI pode ser parado ou excluído.

## Configurações do sistema

Deve-se especificar as configurações do sistema a seguir ao pedir uma instância do vCenter Server with Hybridity Bundle.

### Nome da instância

O nome da instância deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome da instância deve iniciar e terminar com um caractere alfanumérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

### Principal ou secundário

Selecione se pedirá uma nova instância primária ou uma instância secundária para uma instância primária existente.

## Configurações de licenciamento

As licenças a seguir são incluídas no seu pedido de instância do vCenter Server with Hybridity Bundle. Deve-se especificar **Advanced** ou **Enterprise** para as edições de licença do NSX.

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Advanced or Enterprise) 6.3
* Edição de licença do VMware vSAN 6.6 (Advanced ou Enterprise).

**Atenção:**
* As instâncias do vCenter Server with Hybridity Bundle não suportam Bring Your Own License.
* As edições de licença mínimas são indicadas na interface com o usuário. Se diferentes edições de componentes forem suportadas, será possível selecionar a edição desejada.

## Configurações do Bare Metal Server

As configurações do Bare Metal baseiam-se na configuração do {{site.data.keyword.CloudDataCent_notm}} e customizada.

Quatro servidores ESXi são necessários para os clusters iniciais e pós-implementação para configurações do vSAN. Todos os servidores ESXi compartilham a mesma configuração. Na pós-implementação, é possível incluir mais quatro clusters.

### Local do datacenter

Selecione o {{site.data.keyword.CloudDataCent_notm}} no qual a instância deve ser hospedada.

### Customizado

Especifique o modelo de CPU e a quantia de RAM para o Bare Metal Server customizado.

Tabela 2. Opções para {{site.data.keyword.baremetal_short}} customizados

| Opções de CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
### Número de Bare Metal Servers

Quatro servidores ESXi são selecionados por padrão e não podem ser mudados.

## Configurações de armazenamento

O VMware vSAN 6.6 é incluído no seu pedido de instância do vCenter Server with Hybridity Bundle. Deve-se especificar as configurações de armazenamento a seguir ao pedir a instância:

* **Tipo e tamanho do disco para discos de capacidade vSAN**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Número de discos de capacidade vSAN**: selecione o número de discos para o armazenamento compartilhado vSAN que você deseja incluir. As quantidades de disco devem ser 2, 4, 6 ou 8.

## Configurações da interface de rede

Deve-se especificar as configurações da interface de rede a seguir ao pedir uma instância do vCenter Server with Hybridity Bundle.

### Prefixo de nome do host

  O prefixo de nome do host deve atender aos requisitos a seguir:
  *  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
  *  O prefixo de nome do host deve iniciar e terminar com um caractere alfanumérico.
  *  O comprimento máximo do prefixo do nome do host é de 10 caracteres.

### Rótulo do subdomínio

O rótulo do subdomínio deve atender aos requisitos a seguir:
*  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
*  O rótulo do subdomínio deve iniciar e terminar com um caractere alfanumérico.
*  O comprimento máximo do rótulo do subdomínio é de 10 caracteres.
*  O rótulo do subdomínio deve ser exclusivo em sua conta.

### Nome de domínio

O nome do domínio-raiz deve atender aos requisitos a seguir:
* O nome de domínio deve consistir em duas ou mais sequências separadas por ponto (.)
* A primeira sequência deve começar com um caractere alfabético e terminar com um caractere alfanumérico.
* Todas as sequências, exceto a última, podem conter apenas caracteres alfanuméricos e de traço (-).
* A última sequência pode conter apenas caracteres alfabéticos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.

**Nota:** o comprimento máximo do FQDN (Nome completo do domínio) para hosts e VMs (máquinas virtuais) é de 50 caracteres. Os nomes de domínio devem ajustar-se a este comprimento máximo.

### Pedir novas VLANs

Selecione **Pedir novas VLANs** para pedir uma nova VLAN pública e duas novas VLANs privadas.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

### Selecionar VLANs existentes

Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

Selecione **Selecionar VLANs existentes** para reutilizar VLANs públicas e privadas existentes e escolher entre as VLANs e sub-redes disponíveis.

**Importante:**
* Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento.
* Assegure-se de que todas as VLANs selecionadas estejam no mesmo pod, porque os servidores ESXi não podem ser provisionados em VLANs de pod misto.

### Configuração de DNS

Selecione a configuração do Sistema de Nomes de Domínio (DNS) para sua instância:

* **VSI pública única do Windows para o Active Directory/DNS**: uma VSI única do Microsoft Windows Server para o Microsoft Active Directory (AD), que funciona como o DNS para a instância na qual os hosts e as VMs são registrados, é implementada e pode ser consultada.
* **Duas VMs do Windows Server dedicadas, altamente disponíveis no cluster de gerenciamento**: duas VMs do Microsoft Windows são implementadas, ajudando a aprimorar a segurança e a robustez.

**Importante:** deve-se fornecer duas licenças do Microsoft Windows Server 2012 R2 caso você configure a sua instância para usar as duas VMs do Microsoft Windows. Use a licença de edição do Microsoft Windows Server 2012 R2 Standard ou a licença de edição do Microsoft Windows Server 2012 R2 Datacenter, ou ambas.

Cada licença pode ser designada apenas a um único servidor físico e abrange até dois processadores físicos. Uma licença de edição Standard é capaz de executar duas VMs virtualizadas do Microsoft Windows por servidor de dois processadores. Portanto, duas licenças são necessárias, pois duas VMs do Microsoft Windows são implementadas em dois hosts diferentes.

Você tem 30 dias para ativar as VMs.

Para obter mais informações sobre como pedir o licenciamento do Windows, veja [Documentação do Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Configurações de Serviços

Ao pedir uma instância do vCenter Server with Hybridity Bundle, é possível também pedir serviços adicionais. Para obter mais informações sobre os serviços, veja [Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Resumo do Pedido

Com base em sua configuração selecionada para os serviços de instância e complemento, o custo estimado é gerado instantaneamente e exibido na seção **Resumo do pedido** na área de janela direita. Clique em **Detalhes da precificação** na parte inferior da área de janela direita para gerar um documento PDF que forneça os detalhes da estimativa.

## Procedimento

1. No catálogo do IBM Cloud, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **vCenter Server** na seção **Data centers virtuais**.
2. Na página **VMware vCenter Server on IBM Cloud**, clique no cartão **vCenter Server with Hybridity Bundle** e clique em **Criar**.
3. Na página **vCenter Server**, insira o nome da instância.
4. Selecione o tipo de instância:
   * Clique em **Instância primária** para implementar uma única instância no ambiente ou para implementar a primeira instância em uma topologia multissite.
   * Clique em **Instância secundária** para conectar a instância a uma instância existente (primária) no ambiente para alta disponibilidade e conclua as etapas a seguir:
     1. Selecione a instância primária à qual deseja que a instância secundária seja conectada.
     2. Insira a senha do administrador do PSC para a instância primária.
5. Selecione a edição de licença do NSX e a edição de licença do vSAN.
6. Conclua as configurações de Bare Metal Server.
  1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
  2. Selecione o modelo de CPU **Customizado** e a quantia de **RAM**.

  **Nota:** o **Número de Bare Metal Servers** é configurado para quatro por padrão e não pode ser mudado.

7. Conclua a configuração de armazenamento.
  1. Selecione o **Tipo e tamanho do disco para discos de capacidade de vSAN**.
  2. Selecione o **Número de discos de capacidade de vSAN**.
8. Conclua a configuração da interface de rede.
  1. Insira o prefixo de nome do host, o rótulo do subdomínio e o nome do domínio-raiz.
  2. Selecione a configuração de VLAN.
     *  Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
     *  Se você desejar reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e, em seguida, selecione a VLAN pública, a sub-rede primária, a VLAN privada, a sub-rede primária privada e a VLAN privada secundária.
  3. Selecione a configuração do DNS.
9. Selecione os serviços complementares a serem implementados na instância clicando no cartão de serviço correspondente. Se um serviço requerer configuração, conclua as configurações específicas do serviço e clique em **Incluir serviço** no cartão.  
Para obter informações sobre como fornecer configurações para um serviço, veja o tópico de ordem de pedido correspondente.

8. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
   1. Revise as configurações para a instância.
   2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de pedir a instância.
   4. Clique em **Provisão**.

## Resultados

A implementação da instância é iniciada automaticamente. Você recebe confirmação de que o pedido está sendo processado e pode verificar o status da implementação visualizando os detalhes da instância.

Quando a instância é implementada com êxito, os componentes que são descritos na seção _Especificações técnicas do vCenter Server with Hybridity Bundle_ na [Visão geral do vCenter Server with Hybridity Bundle](vc_hybrid_overview.html) são instalados em sua plataforma virtual VMware. Os servidores ESXi pedidos são agrupados como **cluster1** por padrão. Se tiver pedido serviços adicionais, a implementação dos serviços iniciará após a conclusão do pedido.

Quando a instância estiver pronta para usar, seu status mudará para **Pronta para usar** e você receberá uma notificação por e-mail.

Quando você pedir uma instância secundária, o VMware vSphere Web Client da instância primária (vinculado à secundária) poderá ser reiniciado depois que o pedido da instância secundária estiver concluído.

## O que fazer a seguir

Visualizar e gerenciar a instância do vCenter Server with Hybridity Bundle que você pediu.

**Importante**: deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} criados em sua conta do {{site.data.keyword.cloud_notm}} apenas por meio do console do {{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console.
Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.

**CUIDADO**: gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:
*  Incluindo, modificando, retornando ou removendo componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Desativando componentes
*  Reiniciando os serviços

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhados.

## Links relacionados

* [Inscrevendo-se para uma conta do {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Visualizando instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_viewinginstances.html)
* [Configuração multisite para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_multisite.html)
* [Incluindo e visualizando clusters para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingviewingclusters.html)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html)
* [Excluindo instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_deletinginstance.html)
