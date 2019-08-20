---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando recursos do Shared
{: #shared_managing}

O {{site.data.keyword.vmwaresolutions_full}} Shared é fornecido como uma oferta experimental.
{:note}

Os clientes gerenciam o ciclo de vida de data centers virtuais usando a oferta {{site.data.keyword.vmwaresolutions_short}}.

As funções a seguir são suportadas, usando a IU da web ou a API pública:
- Visualizar instâncias do Virtual Data Center
- Acessar o vCloud Management Console
- Redimensionar instâncias do Virtual Data Center
- Excluir instâncias do Virtual Data Center
- Incluindo e removendo Serviços do VMware para instâncias do Virtual Data Center (**Futuro**)

## Visualizando instâncias do Virtual Data Center
{: #shared_managing-viewing}

Para visualizar um resumo de todas as instâncias do Virtual Data Center que são provisionadas para uma conta do usuário, conclua as etapas a seguir:

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. No banner do console, clique em seu ícone de conta do usuário e, em seguida, clique no campo **Conta** para selecionar a conta do usuário da qual você deseja verificar as instâncias.  
3. Na tabela **IBM Cloud VMware Solutions Shared**, visualize a lista de instâncias que são provisionadas na conta do usuário selecionada.

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome da instância |
| Tipo | O tipo de Virtual Data Center |
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada |  
| Horário de criação | A data e hora em que a instância foi criada |
| Barra de Status | O status da instância |

{: caption="Tabela 1. Itens da instância do Virtual Data Center" caption-side="top"}

A instância pode ter um intervalo de status.

| Barra de Status        | Descrição       |
|:------------- |:------------- |
| Criando | A instância está sendo criada. |
| Pronto para usar | A instância está pronta para uso. |
| Modificando | A instância está sendo modificada. |
| Excluindo | A instância está sendo excluída. |
| Excluído | A instância foi excluída. |

{: caption="Tabela 2. Descrições de status para instâncias do Virtual Data Center" caption-side="top"}

## Procedimento para visualizar os detalhes do Virtual Data Center
{: #vc_viewinginstances-procedure-view-vdc-details}

Para visualizar os detalhes da propriedade de uma instância:

1. Na tabela **IBM Cloud VMware Solutions Shared**, clique em um nome da instância.
2. Em **Propriedades**, visualize os detalhes da instância.

| Propriedade        | Descrição       |
|:------------- |:------------- |
| Nome | O nome da instância. |
| Tipo | O tipo de data center virtual. |
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada. |
| ID | O ID da instância. |
| Horário de criação | A data e a hora em que a instância foi criada, que também é quando o faturamento é iniciado. |
| vCPU | A quantia limite ou reservada de CPU que pode ser usada a qualquer momento pelo data center virtual.  |
| RAM | A quantia limite ou reservada de memória que pode ser usada a qualquer momento pelo data center virtual.  |
| IP Público | Cada data center virtual é fornecido com cinco endereços IP públicos que podem ser usados para conectar vApps e VMs à Internet. |

{: caption="Tabela 3. Propriedades do Virtual Data Center" caption-side="top"}

## Acessando o vCloud Director Management Console
{: #shared_managing-accessing}

Gerencie o data center virtual por meio do vCloud Director Management Console.

O primeiro acesso ao vCloud Director Management Console é feito usando a credencial **admin**. Gerar uma senha na página de detalhes do Virtual Data Center com o link **Reconfigurar senha de local**. Essa ação gera uma senha aleatória complexa inicial, que pode ser reconfigurada a qualquer momento.

A oferta {{site.data.keyword.vmwaresolutions_short}} não armazena a senha **admin**. Depois que uma senha é gerada, deve-se capturá-la. Se a senha for perdida, uma nova senha deverá ser gerada.

Todos os data centers virtuais no mesmo local têm a mesma senha **admin**. Reconfigurar a senha em uma instância do Virtual Data Center reconfigura a senha **admin** para acessar o vCloud Director Management Console para todas as instâncias do Virtual Data Center no mesmo local.

Depois que a primeira senha **admin** é gerada, o botão **Portal do vCloud Director** se torna disponível no canto superior direito da página de detalhes. Clique em **Portal do vCloud Director** para acessar o vCloud Director Management Console. Para efetuar login, use o nome do usuário **admin** e a senha que é obtida com o link **Reconfigurar senha de local**.

## Redimensionando instâncias do Virtual Data Center
{: #shared_managing-resizing}

A qualquer momento em que uma instância do Virtual Data Center está no estado **Pronto para uso**, é possível mudar a quantia de recursos que são designados a um data center virtual. 

Redimensione os recursos de vCPU ou RAM para uma instância do Virtual Data Center na página de detalhes do Virtual Data Center. Clique no ícone de lápis ao lado de **Recursos** na página de detalhes e mude os valores das propriedades de vCPU ou RAM.

Por último, verifique a configuração e o custo estimado antes de fazer o pedido.

  A mudança na configuração falhará se os recursos de vCPU e RAM estiverem sendo usados enquanto estiverem sendo reduzidos, porque os recursos do Virtual Data Center não podem ser reduzidos para um nível menor do que o uso de recurso atualmente ativo.
  {:note}

A instância do Virtual Data Center entra no estado **Modificando** enquanto a mudança está sendo feita. Quando os recursos estiverem prontos para uso, o status será mudado para **Pronto para uso**.

## Excluindo instâncias do Virtual Data Center
{: #shared_managing-deleting}

Uma instância do Virtual Data Center pode ser excluída quando ela está no estado **Pronto para uso**. Execute a operação de exclusão na página de detalhes do Virtual Data Center ou na tabela Recurso compartilhado do IBM Cloud VMware Solutions.

Na página de detalhes, clique no ícone **Excluir** na opção de menu overflow no canto superior direito da página de detalhes. Em seguida, confirme se deseja excluir a instância.

Na tabela Recurso compartilhado do IBM Cloud VMware Solutions, localize a instância que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**. Em seguida, confirme se deseja excluir a instância.

## Links relacionados
{: #shared_managing-related}

* [Visão geral do {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Pedindo o Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Pedindo o Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
