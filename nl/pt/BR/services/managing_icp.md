---

copyright:

  years:  2016, 2019

lastupdated: "2018-09-27"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Solicitando o IBM Cloud Private Hosted - Descontinuado

As informações neste tópico estão sendo descontinuadas. Para obter as informações mais atualizadas sobre o IBM Cloud Private Hosted, veja [Visão geral do IBM Cloud Private Hosted](icp_overview.html).
{:deprecated}

O {{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} implementa automaticamente o {{site.data.keyword.cloud_notm}} Private Hosted nas instâncias do VMware vCenter Server.

O {{site.data.keyword.cloud_notm}} Private Hosted traz o poder de microsserviços e contêineres para o ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.

## Especificações técnicas para o IBM Cloud Private Hosted

A seguir estão os requisitos mínimos para solicitar o serviço {{site.data.keyword.cloud_notm}} Private Hosted:

* VMware vCenter Server no  {{site.data.keyword.cloud_notm}}.
  **Nota:** o VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle não é suportado.
* VMware NSX Advanced ou Enterprise Edition
* Três  {{site.data.keyword.baremetal_long}}
* Processador Dual Intel Xeon Gold 5120/Total de 28 núcleos, 2,2 GHz
* 384 GB de RAM por servidor
* Um compartilhamento de arquivo de armazenamento NFS compartilhado com 8.000 GB em 4 IOPS/GB
* 33 licenças de núcleo do processador virtual do IBM Cloud Private
* Para backup de dados, o serviço Veeam on IBM Cloud é recomendado.

## Procedimento para solicitar o IBM Cloud Private Hosted

1. Peça uma nova instância do vCenter Server seguindo as etapas em [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html). Também é possível solicitar o IBM Cloud Private Hosted para uma instância existente.
  **Importante:** assegure-se de que seu ambiente atenda aos requisitos mínimos listados anteriormente.
2. Assegure-se de que tenha as autorizações do IBM Cloud Private.
3. Depois de ter recebido confirmação de que sua instância do vCenter Server está pronta para uso, continue com as etapas a seguir para solicitar o IBM Cloud Private Hosted.
4. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Introdução** na área de janela de navegação esquerda.
5. Role para baixo na página e, em **Pedir serviços adicionais**, clique no cartão **IBM Cloud Private Hosted**.
6. Na página **IBM Cloud Private Hosted on vCenter Server on IBM Cloud**, na caixa **Entre em contato com a equipe do DevOps do IBM Cloud Private Hosted**, insira uma descrição de seus requisitos e clique em **Solicitar uma consulta**.

Um representante do DevOps do {{site.data.keyword.cloud_notm}} Private Hosted entra em contato com você por meio de suas informações de contato do {{site.data.keyword.cloud_notm}} para começar.
