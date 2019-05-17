---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Excluindo o vCenter Server com instâncias do NSX-T
{: #vc_nsx-t_deletinginstance}

Para liberar os componentes que você pediu em uma instância do VMware vCenter Server com NSX-T, exclua a instância.

Ao excluir uma instância do vCenter Server com NSX-T, os componentes a seguir são liberados sequencialmente:
2. Taxas de suporte
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e as VLANs não podem ser excluídas até que os servidores do ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud}}, o que acontece no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}. No final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e VLANs são excluídas e a exclusão da instância é concluída.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para a instância excluída.
{:note}

## Procedimento para excluir instâncias da página Recursos
{: #vc_nsx-t_deletinginstance-procedure1}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, localize a instância a ser excluída.
3. Na coluna **Ações**, clique no ícone Excluir.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Na coluna **Ações**, clique no ícone Excluir novamente.
   2. Na janela **Excluir instância**, clique em **OK**.

## Procedimento para excluir instâncias da página Detalhes da instância
{: #vc_nsx-t_deletinginstance-procedure2}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser excluída.
3. Clique no ícone do menu overflow próximo ao **Console do vCenter** e clique em **Excluir instância**.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Clique no ícone do menu overflow próximo ao **Console do vCenter** novamente e clique em **Excluir instância**.
   2. Na janela **Excluir instância**, clique em **OK**.

## Links relacionados
{: #vc_nsx-t_deletinginstance-related}

* [Excluindo instâncias do vCenter Server em uma configuração de vários sites](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance_multi)
* [ Pedindo o vCenter Server com instâncias do NSX-T ](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Expandindo e contraindo a capacidade para o servidor vCenter com instâncias do NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
