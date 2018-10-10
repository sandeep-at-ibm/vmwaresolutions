---

copyright:

  years:  2016, 2018

lastupdated: "2016-12-12"

---

# Notas sobre a liberação para V1.2

Esta liberação inclui novos recursos, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Atualizações de componentes

A nova versão do VMware ESXi é vSphere 6.0 u2 p03, atualizada do ESXi 6.0 u2 na liberação anterior.

## Associação de contas IBMid e Bluemix

O {{site.data.keyword.vmwaresolutions_full}} é fornecido como uma solução de infraestrutura no catálogo do IBM Bluemix®. Deve-se associar a conta **IBMid** a uma conta do Bluemix para usar a conta **IBMid** para efetuar login no console do {{site.data.keyword.vmwaresolutions_short}}.

Para obter mais informações, veja os tópicos a seguir:
* [Iniciar](../index.html)
* [Resolução de problemas para acessar o Bluemix](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html){:new_window}

## Recuperação de desastre Zerto

É possível pedir instâncias do VMware Cloud Foundation e do VMware vCenter Server com a recuperação de desastre Zerto incluída quando você pede suas instâncias. É possível também incluir a recuperação de desastre Zerto em suas instâncias existentes do Cloud Foundation e do vCenter Server na página de detalhes da instância.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Visualizando instâncias do Cloud Foundation](../sddc/sd_viewinginstances.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Visualizando instâncias do vCenter Server](../vcenter/vc_viewinginstances.html)
* [Recuperação de desastre Zerto](../services/addingzertodr.html)

## Informações de precificação

Agora, é possível ver e revisar o custo estimado da instância pedida antes de você decidir fazer um pedido. Depois de selecionar seus componentes ao pedir sua instância, o custo total e a precificação detalhada de todos os componentes são exibidos na página **Resumo**.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)

## Aprimoramentos para o processo de pedido da instância

O processo de ordem da instância foi aprimorado significativamente por meio dos aprimoramentos a seguir:
* Para instâncias do Cloud Foundation e do vCenter Server, novas verificações de validação estão em vigor para assegurar que a conta do usuário do SoftLayer® que você está usando tenha as permissões de usuário necessárias, que a ampliação da VLAN esteja ativada e que a chave API correta seja fornecida. Se algum requisito não for atendido, você obterá instruções diretamente na interface com o usuário para corrigir os problemas.
*  Para instâncias do vCenter Server, o pedido no qual você seleciona os componentes da instância é otimizado para que apenas os data centers que têm o hardware disponível e os servidores ESXi que você precisa sejam exibidos. Essa mudança minimiza a possibilidade de erros mais tarde.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)

## Notificações adicionais por e-mail

Agora, você recebe uma notificação por e-mail quando novos servidores ESXi são incluídos em suas instâncias e quando servidores ESXi existentes são removidos. Além disso, você é notificado por e-mail quando uma instância é excluída. As configurações de notificação são ativadas por padrão. Com base em suas preferências, é possível configurar quais notificações você deseja receber na página **Configurações**.

Para obter mais informações, veja [Configurações e conta do usuário](useraccount.html).
