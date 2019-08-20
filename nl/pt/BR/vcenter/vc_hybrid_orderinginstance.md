---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server Hybridity order instance, order vCenter Server Hybridity, order Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance}

Para implementar uma plataforma virtualizada VMware flexível e customizável que melhor se ajuste às suas necessidades de carga de trabalho, peça uma instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. O pedido da instância do vCenter Server with Hybridity Bundle inclui o licenciamento do VMware Hybrid Cloud Extension (HCX) e o autoriza para o serviço VMware HCX on {{site.data.keyword.cloud_notm}}. Também é possível incluir serviços, como o [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) para recuperação de desastre.

## Requisitos para pedir instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-req}

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Você revisou as informações em [Requisitos e planejamento para o vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning).
* Você revisou o formato de nome da instância e do domínio. O nome do domínio e o rótulo do subdomínio são usados para gerar o nome do usuário e os nomes do servidor da instância.

| Nome        | Formato do valor      |
|:------------- |:------------- |
| Nome de domínio | `<root_domain>` |  
| Nome do usuário de login do vCenter Server | `<user_id>@<root_domain>` (usuário do Microsoft Active Directory) ou `administrator@vsphere.local` |
| FQDN do vCenter Server (com PSC integrado) | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. O comprimento máximo é 50 caracteres. |
| Nome do site de Conexão única (SSO) | `<subdomain_label>` |
| Nome do servidor ESXi totalmente qualificado | `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que `<n>` é a sequência do servidor ESXi. O comprimento máximo é de 50 caracteres. |
{: caption="Tabela 1. Formato de valor para nomes de instância e de domínio" caption-side="top"}

Não modifique nenhum valor que seja configurado durante o pedido ou a implementação da instância. Fazer isso pode tornar sua instância inutilizável. Por exemplo, se a rede pública for encerrada, se os servidores e as Virtual Server Instances (VSIs) ficarem atrás de uma provisão intermediária do Vyatta ou se o IBM CloudBuilder VSI parar ou for excluído.
{:important}

## Configurações do sistema
{: #vc_hybrid_orderinginstance-sys-settings}

Deve-se especificar as seguintes configurações do sistema ao pedir uma instância do vCenter Server with Hybridity Bundle.

### Nome da instância
{: #vc_hybrid_orderinginstance-inst-name}

O nome da instância deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome da instância deve começar com um caractere alfabético e terminar com um caractere alfanumérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

### Licenças do VMware vSphere
{: #vc_hybrid_orderinginstance-vsphere-license}

Selecione se deve-se pedir o vSphere Enterprise Plus 6.7u1 ou o vSphere Enterprise Plus 6.5u2.

O vSphere Enterprise Plus 6.7u1 está disponível para apenas Broadwell e Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.
{:note}

### Principal ou secundário
{: #vc_hybrid_orderinginstance-primary-secondary}

Selecione se pedirá uma nova instância primária ou uma instância secundária para uma instância primária existente.

## Configurações de licenciamento
{: #vc_hybrid_orderinginstance-licensing-settings}

As licenças VMware a seguir são incluídas com o pedido da instância do vCenter Server with Hybridity Bundle. Deve-se especificar a edição das licenças NSX e vSAN.

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 ou 6.7
* NSX Service Providers 6.4 (Edição Advanced ou Enterprise)
* vSAN 6.6 (Edição Advanced ou Enterprise)

### Atenção
{: #vc_hybrid_orderinginstance-attention}

* As instâncias do vCenter Server with Hybridity Bundle não suportam Bring Your Own License.
* As edições de licença mínimas são indicadas na interface com o usuário. Se diferentes edições de componentes forem suportadas, será possível selecionar a edição desejada.

## Configurações do Bare Metal Server
{: #vc_hybrid_orderinginstance-bare-metal-settings}

As configurações de Bare Metal são baseadas em sua seleção de configuração do servidor {{site.data.keyword.CloudDataCent_notm}} e bare metal.

Quatro servidores ESXi são necessários para os clusters iniciais e pós-implementação para configurações do vSAN. Todos os servidores ESXi compartilham a mesma configuração. Na pós-implementação, é possível incluir mais quatro clusters.

### Local do data center
{: #vc_hybrid_orderinginstance-dc-location}

Selecione o {{site.data.keyword.CloudDataCent_notm}} no qual a instância deve ser hospedada.

### Skylake
{: #vc_hybrid_orderinginstance-skylake}

Quando você seleciona **Skylake**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades.

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabela 2. Opções para o Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Broadwell
{: #vc_hybrid_orderinginstance-broadwell}

Quando você seleciona **Broadwell**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades.

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabela 3. Opções para o Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Número de Bare Metal Servers
{: #vc_hybrid_orderinginstance-bare-metal-number}

* Todos os servidores que você pede têm a mesma configuração.
* É possível pedir entre 4 e 20 servidores.

## Configurações de armazenamento
{: #vc_hybrid_orderinginstance-storage-settings}

O VMware vSAN 6.6 é incluído no seu pedido de instância do vCenter Server with Hybridity Bundle. Especifique as seguintes opções vSAN:
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade acima do limite de 10, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extra para um total de 12 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e rendimento superior de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível somente para os modelos de CPU Skylake.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.

## Configurações da interface de rede
{: #vc_hybrid_orderinginstance-network-interface-settings}

Deve-se especificar as configurações da interface de rede a seguir ao pedir uma instância do vCenter Server with Hybridity Bundle.

### Prefixo de nome do host
{: #vc_hybrid_orderinginstance-host-name-prefix}

  O prefixo de nome do host deve atender aos requisitos a seguir:
  *  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
  *  O prefixo de nome do host deve iniciar e terminar com um caractere alfanumérico.
  *  O comprimento máximo do prefixo do nome do host é de 10 caracteres.

### Rótulo do subdomínio
{: #vc_hybrid_orderinginstance-subdomain-label}

O rótulo do subdomínio deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O rótulo do subdomínio deve começar com um caractere alfabético e terminar com um caractere alfanumérico.
* O comprimento máximo do rótulo do subdomínio é de 10 caracteres.
* O rótulo do subdomínio deve ser exclusivo em todas as instâncias em sua configuração de vários sites.

### Nome de domínio
{: #vc_hybrid_orderinginstance-domain-name}

O nome do domínio-raiz deve atender aos requisitos a seguir:
* O nome de domínio deve consistir em duas ou mais sequências separadas por ponto (.)
* A primeira sequência deve começar com um caractere alfabético e terminar com um caractere alfanumérico.
* Todas as sequências, exceto a última, podem conter apenas caracteres alfanuméricos e de traço (-).
* A última sequência pode conter apenas caracteres alfabéticos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.

O comprimento máximo do nome completo do domínio (FQDN) para hosts e máquinas virtuais (MVs) é de 50 caracteres. Os nomes de domínio devem ajustar-se a este comprimento máximo.
{:note}

### Rede pública ou privada
{: #vc_hybrid_orderinginstance-public-private-network}

As configurações de ativação da Placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**.

Se você seleciona a opção **Somente rede privada**:
* Os VMware NSX Edge Services Gateways (ESG) não são provisionados (nem o ESG de serviços de gerenciamento nem o ESG gerenciado pelo cliente).
* Os serviços complementares a seguir, que requerem NICs públicos, não estão disponíveis:
  * F5 on {{site.data.keyword.cloud_notm}}
  * Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
  * Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Pedir novas VLANs
{: #vc_hybrid_orderinginstance-new-vlans}

Selecione **Pedir novas VLANs** para pedir uma nova VLAN pública e duas novas VLANs privadas.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

### Selecionar VLANs existentes
{: #vc_hybrid_orderinginstance-existing-vlans}

Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

Selecione **Selecionar VLANs existentes** para reutilizar VLANs públicas e privadas existentes e escolher entre as VLANs e sub-redes disponíveis.

* Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento.
* Assegure-se de que todas as VLANs selecionadas estejam no mesmo pod, porque os servidores ESXi não podem ser provisionados em VLANs de pods mistos.
{:important}

### Configuração de DNS
{: #vc_hybrid_orderinginstance-dns-config}

Selecione a configuração do Sistema de Nomes de Domínio (DNS) para sua instância:

* **VSI pública única do Windows para o Active Directory/DNS**: uma VSI única do Microsoft Windows Server para o Microsoft Active Directory (AD), que funciona como o DNS para a instância na qual os hosts e as MVs são registrados, é implementada e pode ser consultada.
* **Duas MVs do Windows Server dedicadas, altamente disponíveis no cluster de gerenciamento**: duas MVs do Microsoft Windows são implementadas, ajudando a aprimorar a segurança e a robustez.

Deve-se fornecer duas licenças da edição Microsoft Windows Server 2016 Standard se você configurar sua instância para usar as duas VMs do Microsoft Windows.
{:important}

Cada licença pode ser designada apenas a um único servidor físico e abrange até dois processadores físicos. Uma licença de edição Standard é capaz de executar duas MVs virtualizadas do Microsoft Windows por servidor de dois processadores. Portanto, duas licenças são necessárias, pois duas MVs do Microsoft Windows são implementadas em dois hosts diferentes.

Você tem 30 dias para ativar as MVs.

Para obter mais informações sobre o pedido de licenças do Windows Server 2016, consulte [Introdução ao Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:external}.

## Configurações de Serviços
{: #vc_hybrid_orderinginstance-addon-services}

Ao pedir uma instância do vCenter Server with Hybridity Bundle, é possível também pedir serviços adicionais. Para obter mais informações sobre os serviços, veja [Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Resumo do Pedido
{: #vc_hybrid_orderinginstance-order-summary}

Com base em sua configuração selecionada para os serviços de instância e de complemento, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**. Clique em **Detalhes da precificação** para gerar um documento PDF com o resumo de custo dos recursos do {{site.data.keyword.vmwaresolutions_short}}.

Também é possível incluir os recursos provisionados na ferramenta de estimativa do {{site.data.keyword.cloud_notm}}, clicando em **Incluir na estimativa**. Isso é útil se você desejar estimar o custo dos recursos do {{site.data.keyword.vmwaresolutions_short}} selecionados com outros recursos do {{site.data.keyword.cloud_notm}} que você talvez considere comprar.

## Procedimento para pedir instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** da área de janela de navegação esquerda e, em seguida, clique no cartão **VMware vCenter Server on IBM Cloud** da seção **Data centers virtuais do VMware**.
2. Na página **VMware vCenter Server on IBM Cloud**, clique no cartão **vCenter Server with Hybridity Bundle** e clique em **Criar**.
3. Na página **vCenter Server**, insira o nome da instância.
5. Selecione a versão do vSphere.
4. Selecione o tipo de instância:
   * Clique em **Instância primária** para implementar uma única instância no ambiente ou para implementar a primeira instância em uma topologia multissite.
   * Clique em **Instância secundária** para conectar a instância a uma instância existente (primária) no ambiente para alta disponibilidade e conclua as etapas a seguir:
     1. Selecione a instância primária à qual deseja que a instância secundária seja conectada.
     2. Para instâncias primárias V2.8 ou mais recente, insira a senha do administrador do vCenter Server para a instância primária.
     3. Para as instâncias primárias V2.7 ou anterior, insira a senha do administrador do PSC para a instância primária.
6. Selecione a edição de licença do NSX e a edição de licença do vSAN.
7. Conclua as configurações de Bare Metal Server.
  1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
  2. Selecione o modelo de CPU **Skylake** ou **Broadwell** e a quantia de **RAM**.
8. Conclua a configuração de armazenamento. Especifique os tipos de disco para os discos de capacidade e de cache, além do número de discos. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
9. Conclua a configuração da interface de rede.
  1. Insira o prefixo do nome do host para a instância que está sendo provisionada, o rótulo do subdomínio e o nome de domínio-raiz.
  2. Selecione a configuração de rede de **Rede pública e privada** ou **Somente rede privada**.
  3. Selecione a configuração de VLAN.
     *  Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
     *  Se você desejar reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e, em seguida, selecione a VLAN pública, a sub-rede primária, a VLAN privada, a sub-rede primária privada e a VLAN privada secundária.
  4. Selecione a configuração do DNS.
10. Conclua a configuração do serviço HCX on {{site.data.keyword.cloud_notm}} incluído. Para obter mais informações sobre como fornecer configurações para o serviço, consulte a seção _Configuração do VMware HCX on IBM Cloud_ em [Pedindo o VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering#vmware-hcx-on-ibm-cloud-configuration).
11. Selecione os serviços complementares a serem implementados na instância clicando no cartão de serviço correspondente. Se um serviço requerer configuração, conclua as configurações específicas do serviço e clique em **Incluir serviço** no cartão.  
Para obter mais informações sobre como fornecer configurações para um serviço, consulte o tópico de pedido de serviço correspondente.

12. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
   1. Revise as configurações para a instância.
   2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de pedir a instância.
   4. Clique em **Provisão**.

## Resultados depois de pedir instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-results}

* A implementação da instância é iniciada automaticamente e você recebe a confirmação de que o pedido está sendo processado. É possível verificar o status de implementação, incluindo quaisquer problemas que possam precisar de sua atenção, visualizando a seção **Histórico de implementação** dos detalhes da instância.
* Quando a instância for implementada com êxito, os componentes que estão descritos em [Especificações técnicas para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs) serão instalados em sua plataforma virtual VMware. Os servidores ESXi pedidos são agrupados como **cluster1** por padrão. Se você pediu serviços complementares, a implementação dos serviços será iniciada após a conclusão de seu pedido.
* Quando a instância estiver pronta para usar, seu status mudará para **Pronta para usar** e você receberá uma notificação por e-mail.
* Quando você pedir uma instância secundária, o VMware vSphere Web Client da instância primária (vinculado à secundária) poderá ser reiniciado depois que o pedido da instância secundária estiver concluído.

## O que fazer a seguir
{: #vc_hybrid_orderinginstance-next}

Visualizar e gerenciar a instância do vCenter Server with Hybridity Bundle que você pediu.

Deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do
{{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console.
Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.
{:important}

**CUIDADO:** Gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) de fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:
*  Incluindo, modificando, retornando ou removendo componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Desativando componentes
*  Reiniciando os serviços

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhado.

## Links relacionados
{: #vc_hybrid_orderinginstance-related}

* [Inscrevendo-se em uma conta do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [Visualizando instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Configuração multissite para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_multisite)
* [Incluindo e visualizando clusters para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Excluindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
