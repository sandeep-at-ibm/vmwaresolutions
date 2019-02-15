---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo clusters do vSphere com base nas configurações existentes

É possível pedir um cluster do VMware vSphere com base em um modelo de configuração que você salvou. Use este procedimento para definir uma nova configuração de cluster com base em uma configuração de cluster existente.

## Requisitos

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud}} na página **Configurações**. Para obter mais informações, veja [Contas e configurações do usuário](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Você revisou os requisitos e as considerações em [Requisitos e planejamento para clusters do vSphere](/docs/services/vmwaresolutions/vsphere/vs_planning.html).
*  Você criou um modelo de configuração para ser reutilizado.

## Procedimento para pedir clusters do vSphere com base nas configurações existentes

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação à esquerda e, em seguida, clique em **VMware vSphere** na seção **Datacenters virtuais**.
2. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.  
3. Clique na guia **Criar novo** e selecione um modelo de configuração na lista **Configurações de cluster**.
4. Insira um novo nome do cluster.
5. Revise as configurações do cluster que são concluídas automaticamente e atualize as configurações de acordo com suas necessidades. Para obter mais informações sobre as configurações, veja [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html).
6. Na área de janela **Resumo do pedido**, verifique a configuração da instância e o custo estimado.
   * Para salvar a configuração como um modelo sem fazer um pedido, clique em **Salvar configuração**.
   * Para fazer o pedido, assegure-se de que a conta a ser cobrada está correta, revise e aceite os termos e, em seguida, clique em **Provisão**.

   Somente os {{site.data.keyword.baremetal_short}} estão instalados. Você é responsável por instalar e configurar vários componentes após a implementação do cluster, como o VMware vCenter, o VMware NSX, o VMware vSAN.
   {:note}

## Resultados

Se salvou a configuração de cluster como um modelo, você receberá uma notificação do console de que a configuração foi salva. É possível então localizar o modelo na lista **Configurações de cluster**.

Se você fez um pedido, a implementação do cluster será iniciada automaticamente. Você recebe uma confirmação por e-mail de que a ordem está sendo processada. Quando o cluster estiver pronto para ser usado, você também será notificado por e-mail.

Os clusters do vSphere, ao contrário das instâncias do vCenter Server e do Cloud Foundation, não são exibidos na página **Instâncias implementadas**.
{:note}

### Links relacionados

* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [Ajustando a escala dos clusters do vSphere existentes](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)
* [Ajustando a escala de clusters criados fora do console](/docs/services/vmwaresolutions/vsphere/vs_orderingforclustersoutside.html)
