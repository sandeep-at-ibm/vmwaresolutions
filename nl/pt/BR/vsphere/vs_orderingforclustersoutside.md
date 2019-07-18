---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: vSphere scale cluster, scale vSphere, external vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ajustando a escala de clusters criados fora do console
{: #vs_orderingforclustersoutside}

É possível usar a oferta do VMware vSphere para escalar clusters do vSphere existentes que são criados fora do console do {{site.data.keyword.vmwaresolutions_full}}. Para escalar um cluster do vSphere que é criado fora do console, recrie o cluster com as mesmas configurações com o console e, em seguida, escale o cluster.

## Requisitos
{: #vs_orderingforclustersoutside-req}

Assegure-se de que tenha concluído as tarefas a seguir:
* Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Você revisou os requisitos e as considerações em [Requisitos e planejamento para o VMware vSphere
on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Procedimento para escalar clusters criados fora do console
{: #vs_orderingforclustersoutside-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** da área de janela de navegação esquerda e, em seguida, clique no cartão **VMware vSphere on IBM Cloud** da seção **Data centers virtuais do VMware**.
2. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.  
   Assegure-se de que está na guia **Criar novo** e que **Novo cluster** está exibido na lista **Configurações de cluster**.
3. Crie um cluster com as mesmas configurações que o cluster existente que foi criado fora do console do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, veja [Pedindo novos clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).  
   Para a interface de rede, para escalar um cluster que é criado fora do console do {{site.data.keyword.vmwaresolutions_short}}, deve-se selecionar as VLANs existentes para o cluster.
   {:note}
4. Na área de janela **Resumo**, verifique a configuração de cluster e, em seguida, clique em **Salvar configuração**.   
5. Na página **Introdução**, clique no cartão **VMware vSphere on IBM Cloud**.
6. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.
7. Clique na guia  ** Escala Existente ** . Na lista **Configurações de cluster**, selecione o cluster que você criou recentemente.
8. Na seção **{{site.data.keyword.baremetal_short}}**, especifique o número de {{site.data.keyword.baremetal_short}} que você deseja incluir no cluster.
9. Se o cluster não incluir o Par de HA do FortiGate 300 Series Security Appliance em sua VLAN pública, será possível pedir um selecionando **Incluir com a compra** em **Par de HA do FortiGate Physical Appliance 300 Series**.
10. Na área de janela **Resumo da ordem**, verifique a configuração da instância e o custo estimado, assegure-se de que a conta a ser cobrada esteja correto, revise e aceite os termos e, em seguida, clique em **Provisão**.

## Resultados
{: #vs_orderingforclustersoutside-results}

A implementação do cluster começa automaticamente e você recebe uma confirmação por e-mail de que o pedido está sendo processado. Quando o cluster estiver pronto para usar, você será notificado por e-mail.

Os clusters vSphere não são exibidos na página **Recursos** junto com as instâncias do vCenter Server.
{:note}

## Links relacionados
{: #vs_orderingforclustersoutside-related}

* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Pedindo clusters do vSphere com base nas configurações existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Ajustando a escala dos clusters do vSphere existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
