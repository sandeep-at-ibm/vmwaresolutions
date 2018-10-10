---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Os Zerto Virtual Replication Appliances não são exibidos para servidores ESXi recém-criados.

## Problema
O Virtual Replication Appliances (VRA) não é exibido no console do Zerto Virtual Replication depois de incluir servidores ESXi em uma instância do VMware vCenter Server que tem a recuperação de desastre Zerto instalada.

## Resolução
Para instâncias do vCenter Server, o serviço de recuperação de desastre Zerto é instalado apenas no servidor ESXi do cluster padrão, **cluster1**. Quaisquer clusters adicionais no mesmo ambiente do vCenter Server não têm a recuperação de desastres do Zerto instalada automaticamente quando o cluster adicional é criado nem quando o servidor ESXi é incluído nesse cluster adicional.

Nos clusters adicionais, deve-se instalar a recuperação de desastre do Zerto separadamente.

Abra um chamado de suporte {{site.data.keyword.cloud}} e trabalhe com o Suporte IBM para obter os endereços IP disponíveis para você instalar os VRAs do console do Zerto em vez do console do {{site.data.keyword.vmwaresolutions_short}}.

Para acessar o console do Zerto, clique no cartão Zerto na guia **Serviços** da instância e clique em **Visualizar Detalhes** e em **Visualizar o Console do Zerto**.

Para obter mais informações sobre como entrar em contato com o Suporte IBM, consulte [Contatando o Suporte IBM](trbl_support.html).
