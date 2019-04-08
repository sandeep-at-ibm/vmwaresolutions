---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Excluindo instâncias do Cloud Foundation
{: #sd_deletinginstance}

Para liberar os componentes que você pediu em uma instância do VMware Cloud Foundation, exclua a instância.

Quando você excluir uma instância do Cloud Foundation, os componentes a seguir serão liberados sequencialmente:
1. Todos os serviços implementados
2. Taxa de suporte e serviços
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e as VLANs não poderão ser excluídas até que os servidores ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud}}, que acontece no término do ciclo de faturamento do {{site.data.keyword.cloud_notm}}. No término do ciclo de faturamento do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e as VLANs são excluídas e a exclusão da instância é concluída.

Você é faturado até o final do ciclo de faturamento do {{site.data.keyword.cloud_notm}} para a instância excluída.
{:note}

## Procedimento para excluir instâncias da página Recursos
{: #sd_deletinginstance-procedure1}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, localize a instância a excluir.
3. Na coluna **Ações**, clique no ícone Excluir.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Na coluna **Ações**, clique no ícone Excluir novamente.
   2. Na janela **Excluir instância**, clique em **OK**.

## Procedimento para excluir instâncias da página Detalhes da instância
{: #sd_deletinginstance-procedure2}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância a excluir.
3. Clique no ícone do menu overflow próximo ao **Console do vCenter** e clique em **Excluir instância**.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Clique no ícone do menu overflow próximo ao **Console do vCenter** novamente e clique em **Excluir instância**.
   2. Na janela **Excluir instância**, clique em **OK**.

## Links relacionados
{: #sd_deletinginstance-related}

* [Excluindo instâncias do Cloud Foundation em uma configuração de vários sites](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Visualizando instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Expandindo e contraindo a capacidade para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Excluindo configurações de vários sites](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
