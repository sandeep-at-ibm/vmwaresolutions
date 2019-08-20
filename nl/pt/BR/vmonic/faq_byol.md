---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: FAQ, license, BYOL

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Perguntas mais frequentes sobre licenciamento e BYOL
{: #faq_byol}

Encontre respostas às perguntas mais frequentes sobre licenciamento, incluindo o recurso Bring Your Own License (BYOL) do {{site.data.keyword.vmwaresolutions_full}}.

## O que é BYOL?
{: #faq_byol-def}
{: faq}

Bring Your Own License (BYOL) é um recurso disponível para os clusters do VMware vCenter Server e VMware vSphere na V2.0 e mais recente. Com BYOL, é possível usar suas próprias licenças do VMware para um ou mais dos componentes de software do VMware a seguir:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Se você escolher usar sua própria licença para um componente do VMware e fornecer uma chave de licença válida para ele, nenhuma licença será pedida da IBM para esse componente e nenhum encargo mensal de licença será incorrido para sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} para esse componente.

O recurso BYOL não está disponível para usuários do Parceiro de Negócios.
{:note}

## Onde eu gerencio as licenças e componentes que são ordenados por meio do VMware vSphere on IBM Cloud?
{: #faq_byol-license-mgmt}
{: faq}

Após um pedido para criar um novo cluster para o VMware vSphere on {{site.data.keyword.cloud_notm}} ser feito, as licenças do VMware, os servidores ESXi e outros componentes de rede são fornecidos e podem ser gerenciados no {{site.data.keyword.slportal}}.

Após a implementação, acesse o console do {{site.data.keyword.vmwaresolutions_short}} para escalar o novo cluster usando a configuração salva. Para obter mais informações, consulte [Ajustando a escala de clusters existentes do
vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).

## Quais edições de licença e CPUs são necessárias para BYOL?
{: #faq_byol-license-cpu-reqs}
{: faq}

Os requisitos a seguir se aplicam às edições de licença para BYOL.

### Requisitos do BYOL para instâncias do vCenter Server
{: #faq_byol-vcs-reqs}

Tabela 1. Edições de licença e requisitos mínimos de CPU para instâncias do vCenter Server

  | Componente do VMware | Edição de licença necessária | Mínimo de CPU necessário
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Padrão                | N/A |
  | vSphere        | Corporativo Plus | 8 CPUs |
  | vSAN           | Advanced ou Enterprise | 8 CPUs |
  | NSX            | Standard, Advanced ou Enterprise | 8 CPUs |

## O que acontece se a chave de licença que eu forneci não estiver correta?
{: #faq_byol-incorrect-license}
{: faq}

Todas as chaves de licença que você fornece são validadas para assegurar que estejam corretas para os componentes do VMware correspondentes e que atendam aos requisitos mínimos de edição e CPU dos componentes do VMware. Se a validação de qualquer chave de licença falhar, você receberá uma notificação e não poderá continuar com o pedido da instância.

## Posso fornecer uma chave de licença com mais de 8 CPUs?
{: #faq_byol-license-key}
{: faq}

Sim. Para cada componente do VMware, uma licença por CPU é necessária. Atualmente, todos os servidores vCenter Server têm duas CPUs. Portanto, duas licenças são necessárias para cada servidor. Recomenda-se que você forneça uma chave de licença que possa suportar a instância base e todos os nós de expansão que deseja incluir na instância no futuro.

## Posso usar o recurso BYOL para alguns componentes do VMware e comprar licenças mensais para outros?
{: #faq_byol-mthly-license}
{: faq}

Sim. É possível usar o recurso BYOL ou comprar licenças para qualquer combinação dos quatro componentes do VMware. O console do {{site.data.keyword.vmwaresolutions_short}} facilita a seleção da opção de licenciamento ao pedir sua instância. Sua opção de licenciamento no momento do pedido da instância inicial se aplica durante o tempo de vida dessa instância.

## Para um componente específico do VMware, posso usar o BYOL para algumas licenças e comprar o resto das licenças da IBM?
{: #faq_byol-purchase}
{: faq}

Sim. Se BYOL foi selecionado para um componente específico do VMware ao criar um cluster, você tem as opções a seguir:
* Inserir uma nova chave BYOL
* Continuar a usar uma chave BYOL existente
* Compre o licenciamento fornecido pela IBM para esse cluster.

Atualmente, somente o VMware vSphere Enterprise e o VMware vSAN podem ser licenciados por cluster.

## Posso usar BYOL ao criar um cluster?
{: #faq_byol-cluster}
{: faq}

Sim. É possível usar BYOL de licenças BYOL existentes ou inserir um novo BYOL ao criar um cluster. Além disso, é possível comprar uma licença de assinatura fornecida pela IBM ao criar um cluster.

Atualmente, somente o VMware vSphere Enterprise e o VMware vSAN podem ser licenciados por cluster.

## Como gerenciar minhas licenças BYOL?
{: #faq_byol-mgmt}
{: faq}

É possível gerenciar suas licenças do BYOL usando o VMware vSphere Web Client após a implementação da instância ser concluída.

## Quando eu incluir mais servidores ESXi em minha instância posteriormente, a instância será validada se minhas licenças BYOL tiverem capacidade suficiente?
{: #faq_byol-add-esxi}
{: faq}

Sim. Quando você estiver incluindo mais servidores ESXi em uma instância implementada, a capacidade de suas licenças BYOL será verificada automaticamente para o número especificado de servidores ESXi. Se a capacidade não for suficiente, os servidores ESXi não serão incluídos e você receberá uma notificação do console.

## Como posso dizer o quanto eu tenho de capacidade de licença disponível em um cluster com o BYOL?
{: #faq_byol-capacity}
{: faq}

Para localizar o número de CPUs disponíveis em sua chave de licença, conclua as etapas a seguir:
1. Vá para a página  ** Recursos ** .
2. Localize e clique na instância.
3. Na guia **Infraestrutura**, clique no cluster para o qual você deseja verificar a capacidade de licença.
   O número de CPUs disponíveis é listado na tabela **Licença Fornecida pelo Usuário**.

## A IBM fornecerá suporte se eu selecionar a opção de licenciamento do BYOL?
{: #faq_byol-support}
{: faq}

O Suporte IBM continua sendo seu ponto de contato para qualquer questão de configuração da instância. No entanto, se o problema relatado for determinado como sendo de um componente do VMware do BYOL, você será direcionado para o Suporte do VMware.

## Por que os encargos de licença do vSphere aparecem na lista de estimativa de preço se eu estiver usando o BYOL? Estou sendo cobrado por isso?
{: #faq_byol-vsphere}
{: faq}

Os {{site.data.keyword.baremetal_short}} são fornecidos com o VMware vSphere já instalado e com as licenças do vSphere já incluídas. Se você selecionou o BYOL para vSphere, um processo será automaticamente iniciado após a implementação da instância para remover as licenças incluídas do vSphere. Em seguida, os encargos de licença são creditados em sua conta do {{site.data.keyword.cloud_notm}}. Você não tem que fazer nada neste processo.

## Ainda posso usar o processo manual existente para o BYOL?
{: #faq_byol-manual-process}
{: faq}

Com a introdução do recurso BYOL, o uso contínuo do processo manual não é recomendado. Se desejar usar o BYOL, forneça suas próprias licenças quando estiver pedindo a instância.

## O BYOL é suportado para outros produtos do VMware, como VMware vRealize Automation, VMware vRealize Operations ou VMware vRealize Log Insight?
{: #faq_byol-other-support}
{: faq}

Não, porque esses produtos do VMware não fazem parte da implementação da instância. Esses produtos VMware podem ser instalados além da implementação inicial, que requer que os clientes ou seus agentes instalem e licenciem esses produtos.

## Links relacionados
{: #faq_byol-related}

* [Acessando o console](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
