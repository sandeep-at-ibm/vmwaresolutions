---

copyright:

  years:  2016

lastupdated: "2016-12-12"

subcollection: vmwaresolutions


---

# Notas sobre a liberação para V1.2
{: #relnotes_v12}

Esta liberação inclui novos recursos, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Atualizações de componentes
{: #relnotes_v12-comp}

A nova versão do VMware ESXi é vSphere 6.0 u2 p03, atualizada do ESXi 6.0 u2 na liberação anterior.

## Associação de contas IBMid e Bluemix
{: #relnotes_v12-ibm-id}

O {{site.data.keyword.vmwaresolutions_full}} é fornecido como uma solução de infraestrutura no catálogo do IBM Bluemix®. Deve-se associar a conta **IBMid** a uma conta do Bluemix para usar a conta **IBMid** para efetuar login no console do {{site.data.keyword.vmwaresolutions_short}}.

Para obter mais informações, veja os tópicos a seguir:
* [Introdução](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Resolução de problemas para acessar o Bluemix](/docs/account?topic=account-accessing){:new_window}

## Recuperação de desastre Zerto
{: #relnotes_v12-zerto}

É possível pedir instâncias do VMware Cloud Foundation e do VMware vCenter Server com a recuperação de desastre Zerto incluída quando você pede suas instâncias. É possível também incluir a recuperação de desastre Zerto em suas instâncias existentes do Cloud Foundation e do vCenter Server na página de detalhes da instância.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Recuperação de desastre Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)

## Informações de precificação
{: #relnotes_v12-price}

Agora, é possível ver e revisar o custo estimado da instância pedida antes de você decidir fazer um pedido. Depois de selecionar seus componentes ao pedir sua instância, o custo total e a precificação detalhada de todos os componentes são exibidos na página **Resumo**.

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Aprimoramentos para o processo de pedido da instância
{: #relnotes_v12-inst-order}

O processo de ordem da instância foi aprimorado significativamente por meio dos aprimoramentos a seguir:
* Para instâncias do Cloud Foundation e do vCenter Server, novas verificações de validação estão em vigor para assegurar que a conta do usuário do SoftLayer® que você está usando tenha as permissões de usuário necessárias, que a ampliação da VLAN esteja ativada e que a chave API correta seja fornecida. Se algum requisito não for atendido, você obterá instruções diretamente na interface com o usuário para corrigir os problemas.
*  Para instâncias do vCenter Server, o pedido no qual você seleciona os componentes da instância é otimizado para que apenas os data centers que têm o hardware disponível e os servidores ESXi que você precisa sejam exibidos. Essa mudança minimiza a possibilidade de erros mais tarde.

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Notificações adicionais por e-mail
{: #relnotes_v12-email}

Agora, você recebe uma notificação por e-mail quando novos servidores ESXi são incluídos em suas instâncias e quando servidores ESXi existentes são removidos. Além disso, você é notificado por e-mail quando uma instância é excluída. As configurações de notificação são ativadas por padrão. Com base em suas preferências, é possível configurar quais notificações você deseja receber na página **Configurações**.

Para obter mais informações, veja [Configurações e conta do usuário](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
