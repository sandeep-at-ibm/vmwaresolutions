---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Pedindo instâncias do vCenter Server

Para implementar uma plataforma virtualizada VMware flexível e customizável que melhor atenda às suas necessidades de carga de trabalho, peça uma instância do VMware vCenter Server. Durante o pedido inicial, também é possível incluir serviços, como o [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) para recuperação de desastre.

## Requisitos

Assegure-se de que tenha concluído as tarefas a seguir:
* Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](../vmonic/useraccount.html).
* Você revisou as informações em [Requisitos e planejamento para instâncias do vCenter Server](vc_planning.html).
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

Deve-se especificar as configurações do sistema a seguir ao pedir uma instância do vCenter Server.

### Nome da instância

O nome da instância deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome da instância deve iniciar e terminar com um caractere alfanumérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

### Principal ou secundário

Selecione se pedirá uma nova instância primária ou uma instância secundária para uma instância primária existente.

## Configurações de licenciamento

Especifique as opções de licenciamento para os seguintes componentes do VMware na instância:
* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4

Para usuários do Parceiro de Negócios, a licença do vCenter Server (Standard Edition), a licença do vSphere (Enterprise Plus Edition) e a licença do NSX são incluídas e compradas em seu nome. No entanto, deve-se especificar a edição para a licença do NSX.

Para usuários que não são do Parceiros de negócios, é possível usar as licenças do VMware fornecidas pela IBM para esses componentes selecionando **Incluir com a compra** ou é possível usar Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo as suas próprias chaves de licença.

**Atenção**:
* É necessária uma licença com um mínimo de 8 CPUs, que é para 4 servidores com 2 CPUs por servidor. A opção de licença para cada componente do VMware se aplicará à instância de base e a quaisquer servidores ESXi que forem incluídos na instância posteriormente. Portanto, deve-se assegurar que sua licença suporte a expansão de capacidade futura em sua infraestrutura.
* As edições de licença mínimas são indicadas na interface com o usuário. Se diferentes edições de componentes forem suportadas, será possível selecionar a edição desejada. Você é responsável por assegurar que a chave de licença fornecida está correta para cada componente de VMware selecionado.
* Para o vSphere, um encargo de licença incorrerá no momento do pedido, mas esse encargo será creditado subsequentemente em sua conta.
* Será possível mudar quaisquer licenças fornecidas usando o VMware vSphere Web Client depois que a implementação da instância for concluída.
* Suporte para os componentes do VMware para os quais você fornece licenças será diretamente fornecido pelo VMware, não pelo Suporte IBM.

## Configurações do Bare Metal Server

As configurações do Bare Metal baseiam-se em sua seleção de data center e se você escolheu uma configuração customizada ou pré-configurada.

### Local do datacenter

Selecione o {{site.data.keyword.CloudDataCent_notm}} no qual a instância deve ser hospedada.

### Pré-configurado

Quando você seleciona **Pré-configurado**, não é possível alterar as configurações de CPU ou RAM.

Com base em seus requisitos, selecione uma configuração do Bare Metal Server:
  * Pequeno (Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz/128 GB de RAM/2 unidades)
  * Médio (Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz/256 GB de RAM/2 unidades)
  * Grande (Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM/2 unidades)

### Customizado

Ao selecionar **Customizado**, será possível escolher a combinação de CPU e RAM de acordo com suas necessidades.

Selecione o modelo de CPU e RAM para o Bare Metal Server.

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

Para o cluster inicial na instância, é possível configurar o número de servidores ESXi da seguinte maneira:
* Se você selecionou **Pré-configurado**, poderá configurar o número de servidores ESXi no intervalo de 2 a 10.
* Se você selecionou **Customizado**, poderá configurar o número de servidores ESXi no intervalo de 2 a 20.

Todos os servidores ESXi compartilham a mesma configuração. Após a implementação inicial, é possível incluir mais quatro clusters. Se você selecionou a configuração **Customizada** para vSAN, 4 servidores ESXi serão necessários para os clusters iniciais e pós-implementação. Para obter mais informações sobre o mínimo de servidores ESXi, veja [É uma instância de dois nós do vCenter Server altamente disponível](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-).

## Configurações de armazenamento

As configurações de armazenamento são baseadas em sua seleção de configuração do Bare Metal Server e o tipo de armazenamento.

### Armazenamento vSAN

O vSAN está disponível somente quando você seleciona a configuração **Customizado** do Bare Metal. Especifique as seguintes opções vSAN:

* **Número de discos de capacidade vSAN**: especifique o número de discos para o armazenamento compartilhado vSAN que você deseja incluir. As quantidades de disco devem ser 2, 4, 6 ou 8.
* **Tipo e tamanho do disco para discos de capacidade vSAN**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Licença do vSAN**: use a licença do VMware fornecida pela IBM para o componente vSAN selecionando **Incluir com a compra** ou Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

### Armazenamento NFS

Quando você selecionar **Armazenamento do NFS**, será possível incluir armazenamento compartilhado no nível de arquivo para a sua instância na qual todas as ações usam as mesmas configurações ou será possível especificar definições de configuração diferentes para cada compartilhamento de arquivo. Especifique as seguintes opções NFS:

**Nota:** o número de compartilhamentos de arquivos deve estar no intervalo de 1 a 32.

* **Configurar compartilhamentos individualmente**: selecione para especificar
diferentes definições de configuração para cada compartilhamento de arquivo.
* **Número de compartilhamentos**: ao usar a mesma definição de configuração para cada compartilhamento de arquivo, especifique o número de compartilhamentos de arquivos para o armazenamento compartilhado do NFS que você deseja incluir.
* **Tamanho**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Desempenho**: selecione o IOPS (Input/output Operations Per Second) por GB com base em seus requisitos de carga de trabalho.
* **ADD NFS**: selecione para incluir compartilhamentos de arquivos individuais que usam definições de configuração diferentes.

Tabela 3. Opções de nível de desempenho do NFS

| Opção        | Detalhes       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Esta opção foi projetada para a maioria de cargas de trabalho de propósito geral. Os aplicativos de exemplo incluem: hospedagem de bancos de dados pequenos, backup de aplicativos da web ou imagens de disco da máquina virtual para um hypervisor. |
  | 4 IOPS/GB | Esta opção foi projetada para cargas de trabalho de maior intensidade que possuem uma alta porcentagem de dados ativos de cada vez. Os aplicativos de exemplo incluem: bancos de dados transacionais. |
  | 10 IOPS/GB | Esta opção foi projetada para os tipos de carga de trabalho mais exigentes, como analítica. Os aplicativos de exemplo incluem: bancos de dados de alta transação e outros bancos de dados sensíveis ao desempenho. Esse nível de desempenho é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo. |

## Configurações da interface de rede

Deve-se especificar as configurações da interface de rede a seguir ao pedir uma instância do vCenter Server.

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

**Nota:** o comprimento máximo do Nome completo do domínio (FQDN) para hosts e VMs é de 50 caracteres. Os nomes de domínio devem ajustar-se a este comprimento máximo.

### VLANs

As configurações de rede se baseiam em sua seleção de **Pedir novas VLANs** ou **Selecionar VLANs existentes**.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

**Pedir novas VLANs**  
Selecione para pedir uma nova VLAN pública e duas novas VLANs privadas.

**Selecionar VLANs existentes**  
Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

Ao selecionar para reutilizar VLANs públicas e privadas existentes, especifique as VLANs e as sub-redes:
* **VLAN pública** é para acesso à rede pública.
* **VLAN privada** é para conectividade entre os data centers e os serviços dentro do {{site.data.keyword.cloud_notm}}.
* **VLAN privada secundária** é para recursos do VMware, como vSAN.
* **Sub-rede primária** é designada a hosts físicos para o acesso à rede pública.
* **Sub-rede privada primária** é designada a hosts físicos para o tráfego de gerenciamento.

**Importante:**
* Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento.
* Assegure-se de que todas as VLANs selecionadas estejam no mesmo pod, porque os servidores ESXi não podem ser provisionados em VLANs de pod misto.

### Configuração de DNS

Selecione a configuração do Sistema de Nomes de Domínio (DNS) para sua instância:

* **VSI pública única do Windows para o Active Directory/DNS**: uma VSI única do Microsoft Windows Server para o Microsoft Active Directory (AD), que funciona como o DNS para a instância na qual os hosts e as VMs são registrados, é implementada e pode ser consultada. Essa opção foi implementada por padrão para instâncias da V1.9 e mais recentes.
* **Duas VMs do Windows Server dedicadas, altamente disponíveis no cluster de gerenciamento**: duas VMs do Microsoft Windows são implementadas, ajudando a aprimorar a segurança e a robustez.

**Importante:** deve-se fornecer duas licenças do Microsoft Windows Server 2012 R2 caso você configure a sua instância para usar as duas VMs do Microsoft Windows. Use a licença de edição do Microsoft Windows Server 2012 R2 Standard ou a licença de edição do Microsoft Windows Server 2012 R2 Datacenter, ou ambas.

Cada licença pode ser designada apenas a um único servidor físico e abrange até dois processadores físicos. Uma licença de edição Standard é capaz de executar duas VMs virtualizadas do Microsoft Windows por servidor de dois processadores. Portanto, duas licenças são necessárias, pois duas VMs do Microsoft Windows são implementadas em dois hosts diferentes.

Você tem 30 dias para ativar as VMs.

Para obter mais informações sobre licenciamento do Windows, veja [Documentação do Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Configurações de Serviços

Ao pedir uma instância do vCenter Server, é possível também pedir serviços adicionais. Para obter mais informações sobre os serviços, veja [Serviços disponíveis para instâncias do vCenter Server](vc_addingremovingservices.html#available-services-for-vcenter-server-instances).

## Resumo do Pedido

Com base em sua configuração selecionada para os serviços de instância e complemento, o custo estimado é gerado instantaneamente e exibido na seção **Resumo do pedido** na área de janela direita. Clique em **Detalhes da precificação** na parte inferior da área de janela direita para gerar um documento PDF que forneça os detalhes da estimativa.

## Procedimento

1. No Catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **vCenter Server** na seção **Datacenters virtuais **.
2. Na página **VMware vCenter Server on IBM Cloud**, clique no cartão **vCenter Server** e clique em **Criar**.
3. Na página **vCenter Server**, insira o nome da instância.
4. Selecione o tipo de instância:
   * Clique em **Instância primária** para implementar uma única instância no ambiente ou para implementar a primeira instância em uma topologia multissite.
   * Clique em **Instância secundária** para conectar a instância a uma instância existente (primária) no ambiente para alta disponibilidade e conclua as etapas a seguir:
     1. Selecione a instância primária à qual deseja que a instância secundária seja conectada.
     2. Insira a senha do administrador do PSC para a instância primária.
5. Conclua as configurações de licença para os componentes da instância.  
   *  Para usar licenças fornecidas pela IBM, selecione **Incluir com a compra** e selecione a edição de licença, se necessário.
   *  Para usar sua própria licença, selecione **Eu fornecerei** e insira a chave de licença.
6. Conclua as configurações de Bare Metal Server.
    1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
    2. Selecione a configuração do Bare Metal Server.
       * Quando você selecionar **Pré-configurado**, escolha **Pequeno**, **Médio** ou **Grande** para a configuração.
       * Ao selecionar **Customizado**, especifique o modelo de CPU e o tamanho da RAM.
    3. Especifique o número de {{site.data.keyword.baremetal_short}}. Se estiver planejando usar vSAN como sua solução de armazenamento, observe que será necessário um mínimo de 4 {{site.data.keyword.baremetal_short}}.  

7. Conclua as configurações de armazenamento:
  * Quando você selecionar **Armazenamento vSAN**, especifique o **Tipo
e tamanho do disco para discos de capacidade vSAN**, o **Número de discos de
capacidade vSAN** e como a **Licença vSAN** deve ser fornecida.
  * Quando você selecionar **Armazenamento NFS** e desejar incluir e definir as mesmas configurações para todos os compartilhamentos de arquivos, especifique o **Número de compartilhamentos**, o **Tamanho** e o **Desempenho**.
  * Quando você selecionar **Armazenamento NFS** e desejar incluir e configurar compartilhamentos de arquivos individualmente, selecione **Configurar compartilhamentos
individualmente**, em seguida, clique no ícone **+** ao lado do rótulo **Incluir NFS** e selecione o **Tamanho** e o **Desempenho**
para cada compartilhamento de arquivo individual. Deve-se selecionar pelo menos um compartilhamento de arquivo.

8. Conclua as configurações da interface de rede.
   1. Insira o prefixo de nome do host, o rótulo do subdomínio e o nome do domínio-raiz. Para uma instância secundária, o nome do domínio é preenchido automaticamente.
   2. Selecione as configurações de VLAN:
      * Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
      * Se quiser reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e especifique as VLANs e as sub-redes.
   3. Especifique a configuração do DNS.

9. Selecione os serviços complementares a serem implementados na instância clicando no cartão de serviço correspondente. Se um serviço requerer configuração, conclua as configurações específicas do serviço e clique em **Incluir serviço** no cartão.
Para obter informações sobre como fornecer configurações para um serviço, veja o tópico de ordem de pedido correspondente.

10. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
   1. Revise as configurações para a instância.
   2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de pedir a instância.
   4. Clique em **Provisão**.

## Resultados

A implementação da instância é iniciada automaticamente. Você recebe confirmação de que o pedido está sendo processado e pode verificar o status da implementação visualizando os detalhes da instância.

Quando a instância for implementada com êxito, os componentes que estão descritos em [Especificações técnicas para instâncias do vCenter Server](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances) serão instalados em sua plataforma virtual VMware. Os servidores ESXi pedidos são agrupados como **cluster1** por padrão. Se tiver pedido serviços adicionais, a implementação dos serviços iniciará após a conclusão do pedido.

Quando a instância estiver pronta para usar, seu status mudará para **Pronta para usar** e você receberá uma notificação por e-mail.

Quando você pedir uma instância secundária, o VMware vSphere Web Client da instância primária (vinculado à secundária) poderá ser reiniciado depois que o pedido da instância secundária estiver concluído.

## O que fazer a seguir

Visualizar e gerenciar a instância do vCenter Server que você pediu.

**Importante**: deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} criados em sua conta do {{site.data.keyword.cloud_notm}} apenas por meio do console do {{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console.
Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.

**CUIDADO**: gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:
*  Incluindo, modificando, retornando ou removendo componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Desativando componentes
*  Reiniciando os serviços

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhados.

### Links relacionados

* [Inscrevendo-se para uma conta do {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Visualizando instâncias do vCenter Server](vc_viewinginstances.html)
* [Configuração de vários sites para instâncias do vCenter Server](vc_multisite.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](vc_addingviewingclusters.html)
* [Expandindo e contraindo capacidade para instâncias do vCenter Server](vc_addingremovingservers.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](vc_addingremovingservices.html)
* [Excluindo instâncias do vCenter Server](vc_deletinginstance.html)
