---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-31"

---

# Solicitando o IBM Cloud Privado Hospedado

O {{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} implementa automaticamente o {{site.data.keyword.cloud_notm}} Private Hosted nas instâncias do VMware vCenter Server.

O {{site.data.keyword.cloud_notm}} Private Hosted traz o poder de microsserviços e contêineres para o ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.

## Especificações técnicas para o IBM Cloud Private Hosted

A seguir estão os requisitos mínimos para solicitar o serviço {{site.data.keyword.cloud_notm}} Private Hosted:

* VMware vCenter Server no  {{site.data.keyword.cloud_notm}}.
  **Nota**: o VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle não é suportado.
* VMware NSX Advanced ou Enterprise Edition
* Três  {{site.data.keyword.baremetal_long}}
* Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz
* 384 GB de RAM por servidor
* Um compartilhamento de arquivo de armazenamento NFS compartilhado com 8.000 GB em 4 IOPS/GB
* 33 licenças de núcleo do processador virtual do IBM Cloud Private
* Para backup de dados, o serviço Veeam on IBM Cloud é recomendado.

## Procedimento para solicitar o IBM Cloud Private Hosted

1. Peça uma nova instância do vCenter Server seguindo as etapas em [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html). Também é possível solicitar o IBM Cloud Private Hosted para uma instância existente.
  **Importante**: assegure-se de que seu ambiente atenda aos requisitos mínimos listados anteriormente.
2. Assegure-se de que tenha as autorizações do IBM Cloud Private.
3. Depois de ter recebido confirmação de que sua instância do vCenter Server está pronta para uso, continue com as etapas a seguir para solicitar o IBM Cloud Private Hosted.
4. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Introdução** na área de janela de navegação esquerda.
5. Role para baixo na página e, em **Pedir serviços adicionais**, clique no cartão **IBM Cloud Private Hosted**.
6. Na página **IBM Cloud Private Hosted on vCenter Server on IBM Cloud**, na caixa **Entre em contato com a equipe do DevOps do IBM Cloud Private Hosted**, insira uma descrição de seus requisitos e clique em **Solicitar uma consulta**.

Um representante do DevOps do {{site.data.keyword.cloud_notm}} Private Hosted entrará em contato por meio de suas informações de contato do {{site.data.keyword.cloud_notm}} e apresentará uma introdução.

### Links relacionados

* [ IBM Cloud Privado Hospedado ](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)  (download em PDF)
* [Abra um chamado para o IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=en_US)
