---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Processo de remoção para o Zerto on IBM Cloud
{: #removingzertodr}

O processo de remoção do serviço Zerto on {{site.data.keyword.cloud}} é automatizado. As etapas a seguir são concluídas para a remoção bem-sucedida do serviço Zerto on {{site.data.keyword.cloud_notm}}.

## Como remover o Zerto on IBM Cloud
{: #removingzertodr-remove}

1. Clique em **Instâncias implementadas** na área de janela de navegação esquerda e clique na instância da qual você deseja remover o serviço.
2. Clique na guia **Serviços**.
3. Na guia **Serviços instalados**, clique no ícone de menu overflow na parte superior direita do cartão de serviços e, em seguida, clique em **Remover serviço**.
4. Na janela **Remover serviço**, revise as considerações ou os avisos, se houver algum. Clique em **Eu entendo**.
5. Depois que sua solicitação de remoção de serviço é aceita, o status de serviço é mudado para **Removendo** e as seguintes etapas de remoção são concluídas:   
   1. Remova os Zerto Virtual Replication Appliances que foram implementados em todos os servidores ESXi.
   2. Desinstale o Zerto Virtual Replication.
   3. Exclua a VSI (Instância de Serviço Virtual) do Windows na qual o Zerto Virtual Replication foi instalado.
   4. Retorne a sub-rede móvel privada que foi pedida para a comunicação do Zerto Virtual Replication para a infraestrutura do {{site.data.keyword.cloud_notm}}.   
   5. Remova os encargos do serviço de recuperação de desastre do Zerto de sua instrução de faturamento do {{site.data.keyword.cloud_notm}}.

      Você é faturado até o término do ciclo de faturamento para o serviço de recuperação de desastre Zerto removido.
      {:note}

## Resultados
{: #removingzertodr-results}

Depois que a remoção do serviço for concluída com êxito, você será notificado por e-mail e a entrada de serviço será excluída da guia **Serviços instalados**.

## Links relacionados
{: #removingzertodr-related}

* [Solicitando on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gerenciando o Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Instâncias do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Instâncias do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Website zerto.com](https://www.zerto.com){:new_window}
* [Documentação técnica do Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
