---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

---

# Notas sobre a liberação para V1.5
{: #relnotes_v15}

Esta liberação inclui novos recursos, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Requisitos da conta SoftLayer VRF versus clássica
{: #relnotes_v15-vrf}

Para contas SoftLayer® clássicas, a ampliação da VLAN é uma configuração que pode ser ativada no nível de conta. O {{site.data.keyword.vmwaresolutions_short}} requer que a ampliação da VLAN seja ativada.

Para contas SoftLayer VRF (Virtual Routing and Forwarding), o equivalente da ampliação da VLAN é uma configuração permanente que não pode ser mudada. Nenhuma configuração de usuário é necessária para contas VRF.

Antes de fazer um pedido de instância, assegure-se de que sua conta SoftLayer seja uma conta VRF ou uma conta clássica (não VRF) com a ampliação da VLAN ativada. Caso contrário, o pedido pode falhar.

Para confirmar se sua conta SoftLayer é uma conta VRF, verifique com o Suporte IBM Bluemix. Para contas clássicas, deve-se ativar a ampliação da VLAN seguindo as instruções de [Ativar ou Desativar a VLAN Spanning](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}.

## Atualizações do modelo de cobrança de serviço
{: #relnotes_v15-svc-charge}

Para instâncias do Cloud Foundation, uma nova licença _SDDC Manager_ é introduzida, que é uma taxa mensal aplicada a cada nó.

## Aprimoramentos de usabilidade
{: #relnotes_v15-ui}

São feitas melhorias em toda a interface com o usuário:

* A disponibilidade de vários {{site.data.keyword.CloudDataCents_notm}} e se eles têm inventário suficiente para atender o pedido é claramente indicado na interface com o usuário. Use esses detalhes para tomar uma decisão informada sobre o {{site.data.keyword.CloudDataCent_notm}} a ser selecionado ao pedir uma instância. Para obter mais informações, consulte [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Para instâncias do Cloud Foundation, informações como o nome da instância, o nome do domínio e do subdomínio, além do local do data center, são exibidas automaticamente no formato gráfico ao inserir as informações necessárias nos campos de entrada.
