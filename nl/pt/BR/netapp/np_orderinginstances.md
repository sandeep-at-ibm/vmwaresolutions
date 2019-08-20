---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-29"

keywords: NetApp order instance, order NetApp ONTAP, order NetApp

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo instâncias do NetApp ONTAP Select
{: #np_orderinginstances}

Para implementar uma plataforma virtualizada VMware com um dispositivo de armazenamento de definição de software dedicado e altamente disponível, peça uma instância do NetApp ONTAP Select.

## Requisitos
{: #np_orderinginstances-req}

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Você revisou os requisitos e considerações em [Requisitos e planejamento para instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning).

Não modifique nenhum valor configurado durante o pedido ou a implementação da instância. Isso tornará a instância não utilizável. Por exemplo, se a rede pública for encerrada, se os servidores e as Virtual Server Instances (VSIs) ficarem atrás de uma provisão intermediária do Vyatta ou se o IBM CloudBuilder VSI parar ou for excluído.
{:important}

## Configurações do sistema
{: #np_orderinginstances-sys-settings}

Ao pedir uma instância do NetApp ONTAP Select, deve-se especificar as configurações básicas a seguir.

### Nome da instância
{: #np_orderinginstances-instance-name}

O nome da instância deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O nome da instância deve começar com um caractere alfabético minúsculo.
* O nome da instância deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

## Configurações da interface de rede
{: #np_orderinginstances-network-interface-settings}

Deve-se especificar as configurações de interface de rede a seguir ao solicitar uma instância do NetApp ONTAP Select.

### Prefixo de nome do host
{: #np_orderinginstances-host-name-prefix}

O prefixo de nome do host deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O prefixo do nome do host deve começar com um caractere alfabético minúsculo.
* O prefixo do nome do host deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do prefixo do nome do host é de 10 caracteres.

### Rótulo do subdomínio
{: #np_orderinginstances-subdomain-label}

O rótulo do subdomínio deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O rótulo do subdomínio deve começar com um caractere alfabético minúsculo.
* O rótulo do subdomínio deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do rótulo do subdomínio é de 10 caracteres.

### Nome de domínio
{: #np_orderinginstances-domain-name}

O nome do domínio-raiz deve atender aos requisitos a seguir:
* O nome de domínio deve consistir em duas ou mais sequências separadas por ponto (.)
* A primeira sequência deve começar com um caractere alfabético minúsculo.
* A primeira sequência deve terminar com um caractere alfabético minúsculo ou numérico.
* Todas as sequências, exceto a última, podem conter somente caracteres alfabéticos minúsculos, numéricos e de traço (-).
* A última sequência pode conter somente caracteres alfabéticos minúsculos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.

O comprimento máximo do nome completo do domínio (FQDN) para hosts e máquinas virtuais (MVs) é de 50 caracteres. Os nomes de domínio devem ajustar-se a este comprimento máximo.
{:note}

## Configurações de licenciamento
{: #np_orderinginstances-licensing-settings}

Deve-se fazer upload de quatro arquivos de licenciamento NetApp, um para cada um dos quatro {{site.data.keyword.baremetal_short}}. Entre em contato com a equipe de vendas do NetApp para obter o licenciamento apropriado para sua implementação de alto desempenho ou alta capacidade.

## Configurações do Bare Metal Server
{: #np_orderinginstances-bare-metal-settings}

### Local do data center
{: #np_orderinginstances-dc-location}

Deve-se selecionar o {{site.data.keyword.CloudDataCent_notm}} no qual a instância deve ser hospedada.

### Configuração do Bare Metal Server
{: #np_orderinginstances-bare-metal-config}

Selecione uma configuração do Bare Metal Server com base em seus requisitos:
* **Alto desempenho (Médio)** – Licença Premium/Dual Intel Xeon E5-2650 v4 (Total de 24 núcleos, 2.2 GHz)/128 GB de RAM/22 unidades SSD de 1,9 TB de capacidade por nó/Capacidade efetiva de um cluster de 4 nós – 59 TB
* **Alto desempenho (Grande)** – Licença Premium/Dual Intel Xeon E5-2650 v4 (Total de 24 núcleos, 2.2 GHz)/128 GB de RAM/22 unidades SSD de 3,8 TB de capacidade por nó/Capacidade efetiva de um cluster de 4 nós – 118 TB
* **Alta capacidade** - Licença padrão/Dual Intel Xeon E5-2650 v4 (Total de 24 núcleos, 2,2 GHz)/64 GB de RAM/Capacidade de trinta e quatro unidades SATA de 4 TB por nó/Capacidade efetiva de um cluster de 4 nós – 190 TB

As unidades SSD de 3,8 TB (Disco de estado sólido) são suportadas quando são disponibilizadas geralmente em um {{site.data.keyword.CloudDataCent_notm}}.
{:note}

### Número de Bare Metal Servers
{: #np_orderinginstances-bare-metal-number}

O número de servidores ESXi de uma instância do NetApp ONTAP Select é quatro por padrão. Isso não pode ser mudado. Todos os servidores ESXi compartilham a configuração.

## Resumo do Pedido
{: #np_orderinginstances-order-summary}

Com base em sua configuração selecionada, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**.  Clique em **Detalhes da precificação** para gerar um documento PDF com o resumo de custo dos recursos do {{site.data.keyword.vmwaresolutions_short}}.

Também é possível incluir os recursos provisionados na ferramenta de estimativa do {{site.data.keyword.cloud_notm}}, clicando em **Incluir na estimativa**. Isso é útil se você desejar estimar o custo dos recursos do {{site.data.keyword.vmwaresolutions_short}} selecionados com outros recursos do {{site.data.keyword.cloud_notm}} que você talvez considere comprar.

## Procedimento para pedir instâncias do NetApp ONTAP Select
{: #ordering-netapp-ontap-select-instances}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** da área de janela de navegação esquerda e, em seguida, clique no cartão **NetApp ONTAP Select** da seção **Data centers virtuais do VMware**.
2. Na página **NetApp ONTAP Select**, clique em **Criar**.
3. Na página **NetApp ONTAP**, insira o nome da instância.
4. Conclua as configurações da interface de rede inserindo o **Prefixo de nome do host**, **Rótulo do subdomínio** e **Nome de domínio**.
5. Conclua as configurações de licenciamento clicando em **Incluir arquivos de licença** para fazer upload de quatro arquivos de licença do NetApp que são requeridos pelos quatro {{site.data.keyword.baremetal_short}}.
6. Conclua as configurações do Bare Metal Server:
   1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
   2. Selecione a configuração do Bare Metal Server.
7. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
    1. Revise as configurações para a instância.
    2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Download** na janela PDF.
    3. Assegure-se de que a conta a ser cobrada esteja correta e, em seguida, marque a caixa de seleção **Entendo que a conta listada abaixo será cobrada**.
    4. Clique no link ou nos links dos termos que se aplicam ao seu pedido. Assegure-se de que concorda com esses termos e, em seguida, marque a caixa de seleção **Li e concordei com os Contratos de Prestação de Serviços de Terceiros listados abaixo**.
    5. Clique em **Provisão**.

## Resultados depois de pedir instâncias do NetApp ONTAP
{: #np_orderinginstances-results}

* A implementação da instância é iniciada automaticamente e você recebe a confirmação de que o pedido está sendo processado. É possível verificar o status de implementação, incluindo quaisquer problemas que possam precisar de sua atenção, visualizando a seção **Histórico de implementação** dos detalhes da instância.
* Quando a instância for implementada com êxito, os componentes que estão descritos em [Especificações técnicas para instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs) serão instalados em sua plataforma virtual do VMware.
* Quando a instância estiver pronta para usar, seu status mudará para **Pronta para usar** e você receberá uma notificação por e-mail.

## O que fazer a seguir
{: #np_orderinginstances-next}

Visualizar e gerenciar a instância do NetApp ONTAP Select que você pediu.

Deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do
{{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console. Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.
{:important}

**CUIDADO:** Gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) de fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:
*  Incluindo, modificando, retornando ou removendo componentes
*  Desativando componentes

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhado.

## Links relacionados
{: #np_orderinginstances-related}

* [Visualizando instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [Excluindo instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [Centro de Documentação do NetApp ONTAP](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){: external}
* [Anexar armazenamento dedicado a implementações do NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/){: external}
