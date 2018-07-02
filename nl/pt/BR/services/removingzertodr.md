---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-05"

---

# Processo de remoção para o Zerto on IBM Cloud
<!-- Do not remove this topic. Though it's no longer in the TOC, it's referenced from the V1.3 release notes -->

O processo de remoção do serviço Zerto on IBM® Cloud é automatizado. As etapas a seguir são concluídas para a remoção bem-sucedida do serviço Zerto on IBM Cloud.

## Como remover o Zerto on IBM Cloud

1. Clique em **Instâncias implementadas** na área de janela de navegação esquerda e clique na instância da qual você deseja remover o serviço.
2. Clique na guia **Serviços**.
3. Na guia **Serviços instalados**, clique no ícone de menu overflow na parte superior direita do cartão de serviços e, em seguida, clique em **Remover serviço**.
4. Na janela **Remover serviço**, revise as considerações ou os avisos, se houver algum. Clique em **Eu entendo**.
5. Depois que sua solicitação de remoção de serviço é aceita, o status de serviço é mudado para **Removendo** e as seguintes etapas de remoção são concluídas:   
   1. Remova os Zerto Virtual Replication Appliances que foram implementados em todos os servidores ESXi.
   2. Desinstale o Zerto Virtual Replication.
   3. Exclua a VSI (Instância de Serviço Virtual) do Windows na qual o Zerto Virtual Replication foi instalado.
   4. Retorne a sub-rede móvel privada que foi pedida para comunicação do Zerto Virtual Replication à infraestrutura do IBM Cloud.   
   5. Remova os encargos do serviço de recuperação de desastre Zerto da instrução de faturamento do IBM Cloud.

      **Nota**: você será cobrado até o final do ciclo de faturamento pelo serviço de recuperação de desastre Zerto removido.

## Resultados

Depois que a remoção do serviço for concluída com êxito, você será notificado por e-mail e a entrada de serviço será excluída da guia **Serviços instalados**.

## Links relacionados

* [Solicitando Zerto on IBM Cloud](zerto_ordering.html)
* [Gerenciando o Zerto on IBM Cloud](managingzertodr.html)
* [Instâncias do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Instâncias do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Website zerto.com](https://www.zerto.com){:new_window}
* [Documentação técnica do Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
