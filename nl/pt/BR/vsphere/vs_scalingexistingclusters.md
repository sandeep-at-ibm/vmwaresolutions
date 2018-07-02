---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-08"

---

# Ajustando a escala dos clusters do vSphere existentes

É possível ampliar um cluster existente do VMware vSphere que você pediu ou salvou no console do {{site.data.keyword.vmwaresolutions_full}} incluindo servidores ESXi ou pedindo um par de HA do FortiGate Security Appliance série 300 para ele.

## Requisitos

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Contas e configurações do usuário](../vmonic/useraccount.html).
*  Você revisou os requisitos e as considerações em [Requisitos e planejamento para clusters do vSphere](vs_planning.html).

## Procedimento

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **VMware vSphere** na seção **Data centers virtuais**.
2. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.  
3. Clique na guia **Escalar existente** e selecione o cluster que deseja escalar na lista **Configurações de cluster**.
4. Revise as configurações de cluster que são preenchidas automaticamente.
5. Na seção **{{site.data.keyword.baremetal_short}}**, especifique o número de {{site.data.keyword.baremetal_short}} que você deseja incluir no cluster.
6. Se o cluster não incluir o Par de HA do FortiGate 300 Series Security Appliance em sua VLAN pública, será possível pedir um selecionando **Incluir com a compra** em **Par de HA do FortiGate Physical Appliance 300 Series**.
7. Na área de janela **Resumo do pedido**, verifique a configuração da instância e o custo estimado.
   * Para salvar a configuração como um modelo sem fazer um pedido, clique em **Salvar configuração**.
   * Para fazer o pedido, assegure-se de que a conta a ser cobrada está correta, revise e aceite os termos e, em seguida, clique em **Provisão**.

## Resultados

A implementação de ajuste de escala do cluster é iniciada automaticamente e você receberá uma confirmação por e-mail de que a ordem está sendo processada. Quando o cluster estiver pronto para usar, você será notificado por e-mail.

**Nota:** os clusters do vSphere, ao contrário das instâncias do vCenter Server e do Cloud Foundation, não são exibidos na página **Instâncias implementadas**.

## Links relacionados

* [Pedindo novos clusters do vSphere](vs_orderinginstances.html)
* [Pedindo clusters do vSphere com base em configurações existentes](vs_orderingbasedonexistingconfig.html)
* [Ajustando a escala de clusters criados fora do console](vs_orderingforclustersoutside.html)
