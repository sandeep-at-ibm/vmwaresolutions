---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Excluindo instâncias do VMware Federal

Para liberar os componentes que você pediu em uma instância do VMware Federal, exclua a instância.

Quando você exclui uma instância do VMware Federal, os seguintes componentes são liberados sequencialmente:

1. Taxas de Suporte e serviços
2. Licenças do produto VMware
3. Servidores ESXi
4. Subnets

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes não podem ser excluídas até que os servidores ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud}}, que acontece no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}. No término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes são excluídas e a exclusão da instância é concluída.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para a instância excluída.
{:note}

## Procedimento para excluir instâncias da página Instâncias implementadas

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, localize a instância a ser excluída.
3. Na coluna **Ações**, clique no ícone Excluir.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Na coluna **Ações**, clique no ícone Excluir novamente.
   2. Na janela **Excluir instância**, clique em **OK**.

## Procedimento para excluir instâncias da página Detalhes da instância

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser excluída.
3. Clique no ícone do menu overflow próximo ao **Console do vCenter** e clique em **Excluir instância**.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Clique no ícone do menu overflow próximo ao **Console do vCenter** novamente e clique em **Excluir instância**.
   2. Na janela **Excluir instância**, clique em **OK**.

### Links relacionados

* [Visão geral do VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Pedindo instâncias do VMware Federal](vc_fed_orderinginstance.html)
* [Protegendo instâncias do VMware Federal](vc_fed_securinginstance.html)
* [Visualizando instâncias do VMware Federal](vc_fed_viewinginstance.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
