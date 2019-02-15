---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo instâncias do Cloud Foundation

Para implementar uma plataforma unificada de data center definido por software (SDDC) com configuração padrão de cálculo, armazenamento e rede, peça uma instância do VMware Cloud Foundation. Durante o pedido inicial, também é possível incluir serviços, como o [Zerto on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services/addingzertodr.html) para recuperação de desastre.

## Requisitos

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Você revisou os requisitos e considerações em [Requisitos e planejamento para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_planning.html).

Não modifique nenhum valor que seja configurado durante o pedido ou a implementação da instância. Fazer isso pode tornar sua instância inutilizável. Por exemplo, se a rede pública for encerrada, se os servidores e as Virtual Server Instances (VSIs) ficarem atrás de uma provisão intermediária do Vyatta ou se o IBM CloudBuilder VSI parar ou for excluído. Além disso, não mude o nome da instância, o nome do domínio-raiz, o rótulo do subdomínio ou o prefixo de nome do host depois que a instância for implementada.
{:important}

## Configurações do sistema

Deve-se especificar as seguintes configurações do sistema ao pedir uma instância do Cloud Foundation.

### Nome da instância

O nome da instância deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome da instância deve iniciar com um caractere alfabético e terminar com um caractere alfanumérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

### Principal ou secundário

Selecione se pedirá uma nova instância primária ou uma instância secundária para uma instância primária existente.

## Configurações de licenciamento

Especifique as opções de licenciamento para os seguintes componentes do VMware na instância:  
* Licença do vCenter Server - Padrão
* Licença do vSphere - Enterprise Plus
* Licença NSX - Enterprise
* Licença do vSAN: selecione o Advanced ou Enterprise Edition

Para usuários do Parceiro de Negócios, a licença do vCenter Server (Standard Edition), a licença do vSphere (Enterprise Plus Edition), a licença do NSX e a licença do vSAN são incluídas e compradas em seu nome. No entanto, deve-se especificar a edição da licença vSAN.

Para usuários que não são do Parceiros de negócios, é possível usar as licenças do VMware fornecidas pela IBM para esses componentes selecionando **Incluir com a compra** ou é possível usar Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo as suas próprias chaves de licença.

## Configurações do Bare Metal Server

### Local do datacenter

Selecione o {{site.data.keyword.CloudDataCent_notm}} no qual a instância deve ser hospedada.

### Skylake

Quando você seleciona **Skylake**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades.

Tabela 1. Opções para Skylake  {{site.data.keyword.baremetal_short}}

| Opções de modelo da CPU  | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Broadwell

Quando você seleciona **Broadwell**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades.

Tabela 2. Opções para Broadwell  {{site.data.keyword.baremetal_short}}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Número de Bare Metal Servers

Uma instância do Cloud Foundation inclui quatro Bare Metal Servers na implementação inicial. Não é possível mudar o número de Bare Metal Servers quando você coloca a ordem.

## Configurações de armazenamento

Para instâncias do Cloud Foundation, é possível pedir somente o armazenamento VMware vSAN.

Quando você seleciona a configuração **Skylake** ou **Broadwell** do Bare Metal Server, é possível customizar o armazenamento vSAN para sua instância. Especifique as seguintes configurações vSAN:
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade além do limite de oito, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e maior rendimento de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível apenas para os modelos de CPU Dual Intel Xeon Gold 5120 e Dual Intel Xeon Gold 6140 do Skylake.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.

## Configurações da interface de rede

Deve-se especificar as seguintes configurações de interface de rede ao pedir uma instância do Cloud Foundation.

### Prefixo de Nome do Host

O prefixo de nome do host deve atender aos requisitos a seguir:
*  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
*  O prefixo de nome do host deve iniciar e terminar com um caractere alfanumérico.
*  O comprimento máximo do prefixo do nome do host é de 10 caracteres.

### Rótulo do subdomínio

O rótulo do subdomínio deve atender aos requisitos a seguir:
*  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
*  O rótulo do subdomínio deve iniciar com um caractere alfabético e terminar com um caractere alfanumérico.
*  O comprimento máximo do rótulo do subdomínio é de 10 caracteres.
*  O rótulo do subdomínio deve ser exclusivo em sua conta.

### Nome de domínio

O nome do domínio-raiz deve atender aos requisitos a seguir:
* O nome de domínio deve consistir em duas ou mais sequências separadas por ponto (.)
* A primeira sequência deve começar com um caractere alfabético e terminar com um caractere alfanumérico.
* Todas as sequências, exceto a última, podem conter apenas caracteres alfanuméricos e de traço (-).
* A última sequência pode conter apenas caracteres alfabéticos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.

O comprimento máximo do nome completo do domínio (FQDN) para hosts e máquinas virtuais (MVs) é de 50 caracteres. Os nomes de domínio devem ajustar-se a este comprimento máximo.
{:note}

### Formato de valor para as configurações de rede

O nome de domínio e o rótulo do subdomínio são usados para gerar o nome do usuário e nomes de servidor da instância, conforme mostrado na tabela a seguir.

Tabela 3. Formato do valor para nomes de usuário, nomes de domínio e nomes de servidor

| Nome        | Formato do valor      |
  |:------------- |:------------- |
  | Nome de domínio | `<root_domain>` |  
  | Nome do servidor ESXi totalmente qualificado | `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que `<n>` é a sequência do servidor ESXi. O comprimento máximo é de 50 caracteres. |   
  | Nome do usuário de login do vCenter Server | `<user_id>@<root_domain>` (Usuário do Microsoft Active Directory) ou `administrator@vsphere.local` |
  | FQDN do vCenter Server | `vcenter-1.<subdomain_label>.<root_domain>`. O comprimento máximo é de 50 caracteres. |  
  | FQDN do SDDC Manager | `sddcmanager.<subdomain_label>.<root_domain>`. O comprimento máximo é de 50 caracteres. |
  | Nome do site de Conexão única (SSO) | `<subdomain_label>`
  | FQDN do PSC | `PSC-<subdomain_label>.<subdomain_label>.<root_domain>`. O comprimento máximo é de 50 caracteres. |  

  O FQDN do SDDC Manager não pode ser resolvido publicamente. Caso contrário, a configuração da instância do Cloud Foundation pode falhar e não é recuperável. Antes de especificar um nome de domínio, revise [Considerações ao escolher um nome de domínio-raiz](/docs/services/vmwaresolutions/vmonic/trbl_limitations.html#considerations-when-choosing-a-root-domain-name-for-cloud-foundation-instances).

### VLANs

As configurações de rede se baseiam em sua seleção de **Pedir novas VLANs** ou **Selecionar VLANs existentes**.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

#### Pedir novas VLANs
Selecione para pedir uma nova VLAN pública e duas novas VLANs privadas.

#### Selecionar VLANs existentes  
Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

Ao selecionar para reutilizar VLANs públicas e privadas existentes, especifique as VLANs e as sub-redes:
  * **VLAN pública** é para acesso à rede pública.
  * **VLAN privada** é para conectividade entre os data centers e os serviços dentro do {{site.data.keyword.cloud_notm}}.
  * **VLAN privada secundária** é para recursos do VMware, como vSAN.
  * **Sub-rede primária** é designada a hosts físicos para o acesso à rede pública.
  * **Sub-rede primária privada** é designada a hosts físicos para tráfego de gerenciamento.

##### Importante

* Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento.
* Assegure-se de que todas as VLANs selecionadas estejam no mesmo pod, porque os servidores ESXi não podem ser provisionados em VLANs de pods mistos.

## Serviços

Ao pedir uma instância do Cloud Foundation, também é possível pedir serviços complementares. Para obter mais informações sobre os serviços disponíveis, veja [Serviços para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_planning.html#services-for-cloud-foundation-instances).

## Resumo do Pedido

Com base em sua configuração selecionada para a instância e os serviços de complemento, o custo estimado é gerado instantaneamente e exibido na área de janela à direita. Clique em **Detalhes de precificação** na área de janela direita para gerar um documento PDF que forneça os detalhes da estimativa.

## Procedimento para pedir instâncias do Cloud Foundation

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **Cloud Foundation** na seção **Data centers virtuais**.
2. Na página **VMware Cloud Foundation on IBM Cloud**, clique em **Criar**.
3. Na página **Cloud Foundation**, insira o nome da instância.
4. Selecione o tipo de instância:
   * Clique em **Instância primária** para implementar uma única instância no ambiente ou para implementar a primeira instância em uma topologia multissite.
   * Clique em **Instância secundária** para conectar a instância a uma instância existente (primária) no ambiente para alta disponibilidade. Conclua as etapas a seguir:
     1. Selecione a instância primária à qual deseja que a instância secundária seja conectada.
     2. Para instâncias primárias V2.5 ou mais recentes, insira o valor para o campo **Senha do administrador para o PSC da instância primária**.
     3. Para instâncias primárias V2.4 ou anteriores, verifique se o valor pré-preenchido para o campo **Senha do administrador para o PSC da instância primária** está correto.
5. Conclua as configurações de licença para os componentes da instância:
   *  Para usar licenças fornecidas pela IBM, selecione **Incluir com a compra**.
   *  Para usar sua própria licença, selecione **Eu fornecerei** e insira a chave de licença.  
6. Conclua as configurações do Bare Metal Server:
   1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
   2. Selecione a configuração do Bare Metal Server e, em seguida, especifique o modelo de CPU e o tamanho da RAM.
7. Conclua a configuração de armazenamento.
   1. Especifique os tipos de disco para a capacidade da vSAN e os discos de cache e o número de discos.
   2. Se você desejar mais armazenamento, marque a caixa de seleção **Alto desempenho com o Intel Optane**.
8. Conclua as configurações da interface de rede:
   1. Insira o prefixo de nome do host, o rótulo do subdomínio e o nome do domínio-raiz. Para uma instância secundária, o nome de domínio é preenchido automaticamente.
   2. Selecione as configurações de VLAN:
      * Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
      * Se quiser reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e especifique as VLANs e as sub-redes.

9. Selecione os serviços complementares a serem implementados na instância clicando no cartão de serviço correspondente. Se um serviço requerer configuração, conclua as configurações específicas do serviço e clique em **Incluir serviço** na janela de configuração pop-up. Para obter mais informações sobre como fornecer configurações para um serviço, consulte o tópico de serviços de solicitação correspondentes.

10. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
    1. Revise as configurações para a instância.
    2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
    3. Assegure-se de que a conta a ser cobrada esteja correta e, em seguida, marque a caixa de seleção **Entendo que a conta listada abaixo será cobrada**.
    4. Clique no link ou nos links dos termos que se aplicam ao seu pedido. Assegure-se de que concorda com esses termos e, em seguida, marque a caixa de seleção **Li e concordei com os Contratos de Prestação de Serviços de Terceiros listados abaixo**.
    5. Clique em **Provisão**.

## Resultados

A implementação da instância é iniciada automaticamente. Você recebe confirmação de que o pedido está sendo processado e pode verificar o status da implementação visualizando os detalhes da instância.

Quando a instância for implementada com êxito, os componentes descritos em [Especificações técnicas para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances) serão instalados em sua plataforma virtual do VMware. Os servidores ESXi que você pediu são agrupados como **SDDC-Cluster** por padrão. Se você pediu serviços complementares, a implementação dos serviços será iniciada após a conclusão de seu pedido.

Quando a instância estiver pronta para usar, seu status mudará para **Pronta para usar** e você receberá uma notificação por e-mail.

Quando você pedir uma instância secundária, o VMware vSphere Web Client da instância primária (vinculado à secundária) poderá ser reiniciado depois que o pedido da instância secundária estiver concluído.

## O que fazer a seguir

Visualizar e gerenciar a instância do Cloud Foundation que você pediu.

Deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do
{{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console. Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.
{:important}

**CUIDADO:** Gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) de fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:

*  Incluindo, modificando, retornando ou removendo componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Desativando componentes
*  Reinício dos serviços

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhados.

### Links relacionados

* [Inscrevendo-se em uma conta do {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/vmonic/signing_softlayer_account.html)
* [Visualizando instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_viewinginstances.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingviewingclusters.html)
* [Expandindo e contraindo a capacidade para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservers.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Excluindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_deletinginstance.html)
* [Pergunta mais frequente sobre BYOL](/docs/services/vmwaresolutions/vmonic/faq_byol.html)
