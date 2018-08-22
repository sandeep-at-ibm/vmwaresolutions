---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Excluindo instâncias do vCenter Server

Para liberar os componentes que você pediu em uma instância do VMware vCenter Server, exclua a instância.

Quando você excluir uma instância do vCenter Server, os componentes a seguir serão liberados sequencialmente:
1. Todos os serviços implementados
2. Taxa de suporte e serviços
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e as VLANs não podem ser excluídas até que os servidores do ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud}}, o que acontece no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}. No final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e VLANs são excluídas e a exclusão da instância é concluída.

**Atenção:** você é cobrado até o término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para a instância excluída.

## Excluindo instâncias da página Instâncias implementadas

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, localize a instância a ser excluída.
3. Na coluna **Ações**, clique no ícone Excluir.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Na coluna **Ações**, clique no ícone Excluir novamente.
   2. Na janela **Excluir instância**, clique em **OK**.

## Excluindo instâncias da página de detalhes da instância

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser excluída.
3. Clique no ícone de menu overflow à direita do **Console do vCenter** e clique em **Excluir instância**.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Clique no ícone de menu overflow à direita do **Console do vCenter** novamente e clique em **Excluir instância**.
   2. Na janela **Excluir instância**, clique em **OK**.

### Links relacionados

* [Excluindo instâncias do vCenter Server em uma configuração de vários sites](vc_deletinginstance_multi.html)
* [Pedindo instâncias do vCenter Server](vc_orderinginstance.html)
* [Visualizando instâncias do vCenter Server](vc_viewinginstances.html)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server](vc_addingremovingservers.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
