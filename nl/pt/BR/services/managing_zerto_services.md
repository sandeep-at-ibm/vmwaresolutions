---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

# Solicitando serviços gerenciados para Zerto on IBM Cloud
{: #managing_zerto_services}

O serviço Zerto on {{site.data.keyword.cloud}} fornece recursos de replicação e de recuperação de desastre. Esses recursos podem ser integrados às ofertas de implementação para proteger e recuperar dados em seu ambiente virtual VMware no {{site.data.keyword.cloud_notm}}.

Quando você solicita serviços gerenciados para o Zerto on {{site.data.keyword.cloud_notm}}, um ambiente de recuperação de desastre (DR) totalmente gerenciado pode ser implementado usando o software Zerto DR e o IBM Resiliency Services.

Os modelos a seguir para serviços gerenciados para Zerto on {{site.data.keyword.cloud_notm}} estão disponíveis.

## IBM Orchestrated Managed Services para Zerto
{: #managing_zerto_services-orchestrated}

Este modelo é adequado se você estiver usando a oferta Zerto on {{site.data.keyword.cloud_notm}}.

Nesse modelo, o serviço {{site.data.keyword.cloud_notm}} Resiliency Orchestration é fornecido para o Zerto on {{site.data.keyword.cloud_notm}}. Esse modelo pode proteger continuamente as máquinas virtuais, sistemas operacionais e dados no {{site.data.keyword.cloud_notm}}, com teste de DR ininterrupto, visibilidade de RTO/RPO (Objetivo de Tempo de Recuperação/Objetivo do Ponto de Recuperação), capacidade de failover e de failback.

Todas as funções são gerenciadas por meio do painel do {{site.data.keyword.cloud_notm}} Resiliency Orchestration pelo IBM Resiliency Services Global Command Center.

Para obter mais informações, veja [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration).

## IBM Managed Services para Zerto (sem Orchestration)
{: #managing_zerto_services-without-orchestrated}

Nesse modelo, uma solução de DR totalmente gerenciada é fornecida para o Zerto on {{site.data.keyword.cloud_notm}}. Esse modelo será adequado se você quiser apenas um serviço gerenciado para o Zerto Virtual Replication, sem o serviço {{site.data.keyword.cloud_notm}} Resiliency Orchestration no {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top).

## Procedimento para solicitar serviços gerenciados para o Zerto on IBM Cloud
{: #managing_zerto_services-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Introdução** na área de janela de navegação esquerda.
2. Role para baixo na página e em **Pedir serviços gerenciados adicionais**, clique no cartão **Serviços gerenciados para o Zerto on IBM Cloud**.
3. Na página **Zerto on IBM Cloud**, revise a descrição e as especificações técnicas para o Zerto on {{site.data.keyword.cloud_notm}} como um serviço gerenciado e, em seguida, clique em **Criar**.
4. Especifique as definições de configuração de acordo com seus requisitos ou aceite os valores padrão.
5. Clique em **vCenter Server** ou **Cloud Foundation** para incluir o serviço em uma de suas instâncias.
6. Para incluir o serviço enquanto você pede uma nova instância, clique em **Incluir na nova instância** e, em seguida, continue com a solicitação de uma nova instância do [servidor do vCenter](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance) ou [do servidor do vCenter com Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance).
7. Para incluir o serviço em uma instância existente, clique em **Incluir na instância existente**, selecione a instância desejada na lista e, em seguida, confirme se deseja continuar com o pedido clicando em **Provisão**.

## Links relacionados
{: #managing_zerto_services-related}

* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
