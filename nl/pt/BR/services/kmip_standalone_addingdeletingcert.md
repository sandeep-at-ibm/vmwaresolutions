---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Incluindo, visualizando e excluindo certificados para instâncias do KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert}

Depois que a instância do KMIP for VMware on {{site.data.keyword.cloud}} estiver pronta, certificados deverão ser incluídos nela. Quando você não precisar mais de um certificado, exclua-o de sua instância.

## Procedimento para incluir certificados em instâncias do KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert-add}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Role para baixo até a tabela **Instâncias do KMIP for VMware on IBM Cloud**, clique na instância na qual você deseja incluir certificados.
3. Clique em  ** Incluir **.
4. Na janela **Incluir certificado SSL do cliente**, insira o nome do certificado e o conteúdo.

   O nome do certificado não pode ser reutilizado dentro de sua instância selecionada. O conteúdo do certificado deve ser válido e conter as tags BEGIN CERTIFICATE e END CERTIFICATE e o certificado não pode ser reutilizado na região selecionada na qual a instância é implementada.
   {:note}
5. Clique em  ** Incluir **.

## Procedimento para visualizar certificados para instâncias do KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert-view}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Role para baixo até a tabela **Instâncias do KMIP for VMware on IBM Cloud**, clique na instância para a qual visualizar os certificados.
3. Visualize a lista de certificados incluídos sob a seção **Certificados SSL do cliente**.
4. Para visualizar o conteúdo de um certificado específico, clique em **Download**.

## Procedimento para excluir certificados de instâncias do KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert-delete}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Role para baixo até a tabela **Instâncias do KMIP for VMware on IBM Cloud**, clique na instância da qual você deseja excluir certificados.
3. Na tabela **Certificados SSL do cliente**, localize o certificado que você deseja excluir e clique no ícone **Excluir**.

   O cliente perde imediatamente o acesso a todas as chaves com o propósito de criptografar e decriptografar dados ou dados de backup. Para que o cliente obtenha acesso novamente, deve-se incluir o certificado SSL do cliente novamente.
   {:note}

## Links relacionados
{: #kmip_standalone_addingdeletingcert-related}

* [Visualizando instâncias do KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Pedindo instâncias do KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Excluindo instâncias do KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Eventos de rastreador de atividade](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
