---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-30"

---

# Notas sobre a liberação para V1.5

Esta liberação inclui novos recursos, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em liberações diferentes, problemas conhecidos com o produto e dicas adicionais para usar o {{site.data.keyword.vmwaresolutions_full}}, veja o [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Requisitos da conta SoftLayer VRF versus clássica

Para contas SoftLayer® clássicas, a ampliação da VLAN é uma configuração que pode ser ativada no nível de conta. O {{site.data.keyword.vmwaresolutions_short}} requer que a ampliação da VLAN seja ativada.

Para contas SoftLayer VRF (Virtual Routing and Forwarding), o equivalente da ampliação da VLAN é uma configuração permanente que não pode ser mudada. Nenhuma configuração de usuário é necessária para contas VRF.

Antes de fazer um pedido de instância, assegure-se de que sua conta SoftLayer seja uma conta VRF ou uma conta clássica (não VRF) com a ampliação da VLAN ativada. Caso contrário, o pedido pode falhar.

Para confirmar se sua conta SoftLayer é uma conta VRF, verifique com o Suporte IBM Bluemix. Para contas clássicas, deve-se ativar a ampliação da VLAN seguindo as instruções de [Ativar ou Desativar a VLAN Spanning](../../../infrastructure/vlans/vlan-spanning.html){:new_window}.

## Atualizações do modelo de cobrança de serviço

Para instâncias do Cloud Foundation, uma nova licença _SDDC Manager_ é introduzida, que é uma taxa mensal aplicada a cada nó. Para obter mais informações, veja [Componentes da instância do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

## Aprimoramentos de usabilidade

São feitas melhorias em toda a interface com o usuário:

* A disponibilidade de vários data centers e se eles têm inventário suficiente para atender o pedido é claramente indicado na interface com o usuário para que você possa tomar uma decisão informada sobre o data center a selecionar durante o pedido da instância. para obter mais informações, veja [Requisitos e planejamento para instâncias do Cloud Foundation](../sddc/sd_planning.html) e [Requisitos e planejamento para instâncias do vCenter Server](../vcenter/vc_planning.html).
* Para instâncias do Cloud Foundation, informações como o nome da instância, nome de domínio e subdomínio, e local do data center, são automaticamente exibidas no formato gráfico enquanto você está inserindo as informações necessárias nos campos de entrada. Para obter mais informações, veja [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html).
