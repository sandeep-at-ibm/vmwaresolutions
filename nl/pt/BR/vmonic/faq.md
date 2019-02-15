---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Perguntas mais frequentes gerais sobre o IBM Cloud for VMware Solutions

Encontre respostas às perguntas mais frequentes sobre o {{site.data.keyword.vmwaresolutions_full}}.

## De quais contas do usuário eu preciso para o IBM Cloud for VMware Solutions?
{: faq}

* **Conta IBMid**. Esta conta é necessária para acessar o console do {{site.data.keyword.vmwaresolutions_short}}. O console é uma interface com o usuário independente separada do {{site.data.keyword.slportal}}. Para obter mais informações, veja
[Introdução](/docs/services/vmwaresolutions/index.html).
* **Conta {{site.data.keyword.cloud_notm}}**. Esta conta é necessária para fornecimento. É possível inscrever-se para uma conta do {{site.data.keyword.cloud_notm}} usando um **IBMid** existente ou criando um novo **IBMid**.
* ** {{site.data.keyword.cloud_notm}}  conta de infraestrutura **. Essa conta, que era conhecida anteriormente como conta do **IBM SoftLayer**, é usada para efetuar login no portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}} que fornece alguma função adicional para gerenciar produtos e serviços de infraestrutura. É possível obter uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} fazendo upgrade de sua **conta do {{site.data.keyword.cloud_notm}}** para um tipo de conta Pagamento conforme uso ou vinculando sua conta de infraestrutura existente (SoftLayer) do {{site.data.keyword.cloud_notm}} à sua conta do {{site.data.keyword.cloud_notm}}. A conta de infraestrutura do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para
obter mais informações, consulte
[Inscrevendo-se nas contas necessárias
](/docs/services/vmwaresolutions/vmonic/signing_softlayer_account.html) e os
[Requisitos
da conta de infraestrutura do {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/vmonic/slaccountrequirement.html).

## Como eu associo minhas credenciais de infraestrutura do IBM Cloud ao console do IBM Cloud for VMware Solutions?

Ao pedir sua instância pela primeira vez, siga as instruções na página **Configurações** no console para localizar e copiar o nome do usuário da infraestrutura do {{site.data.keyword.cloud_notm}} e a chave API do {{site.data.keyword.slportal}}. As credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} são armazenadas no console do {{site.data.keyword.vmwaresolutions_short}} depois do primeiro pedido. Pedidos futuros automaticamente usam as credenciais armazenadas.

## Como meus consumos da plataforma virtual do VMware são cobrados?

Todos os custos para a infraestrutura física e virtual e as licenças que resultam da instância são cobrados em sua conta do {{site.data.keyword.cloud_notm}}. Ao pedir uma instância, deve-se ter uma conta {{site.data.keyword.cloud_notm}} e fornecer a chave do {{site.data.keyword.slapi_short}} que está associada à conta.

## Quais são as diferenças entre uma instância do vCenter Server, a instância do Cloud Foundation e o cluster do VMware vSphere?

Todos os tipos de instância fornecem opções de implementação para ambientes virtuais do VMware. No entanto, a diferença é a extensão da customização e automação.

* Ao pedir uma instância do VMware vCenter Server, você implementa um ambiente virtual VMware com recursos customizados de cálculo, armazenamento e rede. Para obter mais informações sobre os componentes implementados, veja [Especificações técnicas para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).
* Ao pedir uma instância do VMware Cloud Foundation, você implementa uma plataforma unificada do data center definido por software (SDDC). Para obter mais informações sobre os componentes implementados, veja [Especificações técnicas para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).
* Ao pedir um cluster do VMware vSphere, você obtém o máximo de flexibilidade para projetar e construir o ambiente do VMware hospedado enquanto incorpora o hardware compatível com o VMware. No entanto, o {{site.data.keyword.cloud_notm}} não automatiza a instalação, a configuração e a exibição dos componentes opcionais do VMware para o cluster do VMware vSphere.
* As funções que são suportadas para instâncias do vCenter Server, instâncias do Cloud Foundation e clusters do vSphere são diferentes. Para obter mais informações, veja [Gráfico de comparação de oferta](/docs/services/vmwaresolutions/vmonic/inst_comp_chart.html).

## O que está incluído em uma instância do vCenter Server?

Para obter mais informações, veja [Especificações técnicas para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

## O que está incluído em uma instância do Cloud Foundation?

Para obter mais informações, consulte [Especificações técnicas para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## O que está incluído em um cluster do vSphere?
Para obter mais informações, veja [Componentes do VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html).

## Uma instância do vCenter Server de dois nós é altamente disponível?

É recomendável implementar cargas de trabalho de produção em ambientes que tenham pelo menos três nós.

O VMware vSphere DRS (Distributed Resource Scheduler) e o VMware HA (Alta Disponibilidade) são ativados por padrão. No entanto, as melhores práticas do VMware sugerem que você coloque cada um dos três Controladores NSX em um nó individual.

Na implementação mínima de dois nós, um nó tem um NSX Controller e o outro nó tem dois NSX Controllers. Se o nó com dois NSX Controllers ficar inativo, as operações do NSX Controller serão colocadas no modo somente leitura e as novas MVs (máquinas virtuais) ou MVs do vMotion poderão ter problemas de rede.

Quando um terceiro nó é incluído em um cluster de dois nós, o vCenter Server automaticamente reequilibra os três NSX Controllers nos três nós e cria um ambiente altamente disponível.

## Posso definir a configuração de HA do VMware vCenter 6.5?

Não, não é recomendado. Podem ocorrer falhas nas funções do {{site.data.keyword.vmwaresolutions_short}}.

## Os clusters podem ser renomeados?

Para instâncias do vCenter Server, o primeiro cluster que é criado durante a implementação tem um nome padrão de **cluster1**. É possível renomear o cluster padrão no VMware vSphere Client. Ao incluir um cluster em uma instância do vCenter Server, é possível especificar o nome que você deseja no console do {{site.data.keyword.vmwaresolutions_short}}.

**Nota:** para instâncias do Cloud Foundation, o nome do cluster padrão não pode ser mudado.

## Como as correções são gerenciadas?

A IBM fornece atualizações contínuas para o código IBM, implementando a instância do servidor virtual IBM CloudDriver (VSI) on demand. A IBM não fornece atualizações contínuas para serviços complementares, como o Zerto on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}}. Obter e instalar essas atualizações é sua responsabilidade.

As atualizações do VMware são aplicadas de uma maneira diferente com base no tipo de instância.

### Instâncias do VMware Cloud Foundation

As atualizações para os componentes vSphere ESXi, NSX, vCenter, Platform Services Controller e SDDC Manager são fornecidas por meio do console do {{site.data.keyword.vmwaresolutions_short}}.

### Instâncias do VMware vCenter Server

Para instâncias implementadas ou submetidas a upgrade para a V2.1 ou superior, os servidores e clusters ESXi recém-implementados são corrigidos com atualizações recentes, mas não necessariamente as mais recentes, do ESXi do VMware.

Você é responsável por todas as outras atualizações para componentes do VMware, incluindo assegurar que clusters e servidores ESXi recém-implementados tenham todas as atualizações mais recentes que você exigir.
{:important}

Para instâncias que foram implementadas na V2.0 ou superior, o VMware Update Manager (VUM) é integrado em seu vCenter Server. É possível configurar o VUM para fazer download de atualizações do ESXi por meio do VMware.

Para obter mais informações, consulte os recursos a seguir:
* [Suporte ao VMware](https://www.vmware.com/support.html)
* [Aplicando atualizações às instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_applyingupdates.html)
* [Aplicando atualizações a instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)
* [Aplicando atualizações a instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_applyingupdates.html)

## O NSX Edge de serviços de gerenciamento representa um risco de segurança?

Embora o VMware NSX Edge para serviços de gerenciamento esteja em uma sub-rede pública, as medidas de segurança a seguir estão em vigor para assegurar que isso não represente um risco de segurança:
*  O firewall NSX Edge é configurado para permitir somente o tráfego HTTPS de saída (porta TCP 443) que é iniciado pelas máquinas virtuais de gerenciamento.
*  O SNAT (source network address translation) é usado para que os endereços IP privados não sejam visíveis fora da rede privada.
*  O acesso remoto para o dispositivo NSX Edge de serviços de gerenciamento é desativado.
*  As senhas para acessar o NSX Edge de serviços de gerenciamento da rede privada são aleatórias e criptografadas.

## O NSX Edge gerenciado pelo cliente representa um risco de segurança?

Embora o NSX Edge gerenciado pelo cliente esteja conectado à VLAN pública, as medidas de segurança estão em vigor para assegurar que ele não represente um risco de segurança. As medidas de segurança a seguir estão em vigor:
*  Uma regra de firewall está em vigor para permitir apenas o tráfego de saída do intervalo de sub-rede privada de endereços IP.
*  Uma regra SNAT (Source Network Address Translation) (desativada por padrão) está em vigor para converter todos os endereços IP da sub-rede privada em um único endereço IP na sub-rede pública.
*  O acesso remoto para o dispositivo NSX Edge gerenciado pelo cliente é desativado.
*  As senhas para acessar o NSX Edge gerenciado pelo cliente da rede privada são aleatórias e criptografadas.

## Como escolher os data centers para minhas instâncias?

As implementações da instância têm requisitos estritos de infraestrutura física, que variam entre {{site.data.keyword.CloudDataCents_notm}}. Quando você coloca a ordem da instância, os data centers disponíveis são listados dentro de regiões e é possível selecionar aquele desejado na lista.

Para obter mais informações, veja as seções _Disponibilidade do IBM Cloud Data Center_ em:
* [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
* [Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_planning.html)
* [Requisitos e planejamento para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_planning.html)
* [Requisitos e planejamento para o VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere/vs_planning.html)
* [Requisitos e planejamento para instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp/np_planning.html)
* [Requisitos e planejamento para as instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html)

## Quanto tempo leva para que minha instância seja implementada?

É possível verificar o status da implementação da instância visualizando o histórico de implementação na página de detalhes da instância do console do {{site.data.keyword.vmwaresolutions_short}}.

## O VMware vSphere on IBM Cloud usa automação para instalar, configurar e tornar visível a pilha do VMware?

Não. O VMware vSphere on {{site.data.keyword.cloud_notm}} não usa a automação avançada que está localizada nas plataformas Cloud Foundation e vCenter Server. Com base no seu pedido, a plataforma oferece licenças opcionais do VMware, servidores ESXi e, como opção, um par de HA de firewalls físicos do FortiGate. Se um novo cluster for criado, três novas VLANs também serão provisionadas: uma VLAN pública e duas VLANs privadas.

O VMware ESXi é instalado automaticamente em cada servidor bare metal, mas você é responsável por instalar os componentes adicionais do VMware como o vCenter Server ou NSX. Embora o vSphere on {{site.data.keyword.cloud_notm}} assegure que o hardware compatível com VMware seja ordenado com base nos componentes do VMware selecionados, não existe nenhuma automação para configurar e ativar o ambiente do VMware. Você é responsável por projetar e arquitetar o ambiente hospedado pela IBM.

## Como posso visualizar uma lista de todas as notificações?

Para visualizar o histórico de notificação completo, clique em **Notificações** na área de janela de navegação esquerda.

## E se eu tiver um problema com o IBM Cloud for VMware Solutions?

Se você precisar de assistência com o {{site.data.keyword.vmwaresolutions_short}}, entre em contato com o Suporte IBM por meio de um dos canais de suporte. Para obter mais informações, veja [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html).

### Links relacionados

* [Notificações](/docs/services/vmwaresolutions/vmonic/notifications.html)
* [Instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [Instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)
* [Acessando o console](/docs/services/vmwaresolutions/vmonic/loginmethod.html)
* [Configurações e contas do usuário](/docs/services/vmwaresolutions/vmonic/useraccount.html)
