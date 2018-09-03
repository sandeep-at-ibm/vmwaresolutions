---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-08"

---

# Migrando instâncias do vCenter Server pré-V2.5 para contas do IBM Cloud

As instâncias do VMware vCenter Server que são implementadas na V2.5 e liberações mais recentes em sua conta do {{site.data.keyword.cloud}} são incluídas automaticamente em sua conta e são gerenciadas pelo {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

Para instâncias que foram implementadas na V2.4 e liberações anteriores, é possível migrá-las para as contas do {{site.data.keyword.cloud_notm}} especificadas para gerenciamento de usuário ativado pelo IAM.


## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. No canto superior direito do console, clique em seu avatar e, em seguida, clique no campo **Conta** para selecionar a conta do usuário para a qual você deseja migrar a instância.
3. Na tabela **Instâncias do vCenter Server**, localize a instância anterior à V2.5.
4. Na coluna **Ações**, clique no ícone de menu overflow e, em seguida, clique em **Migrar instância para a conta**.
5. Na janela **Migrar instância para a conta**, confirme a conta para a qual migrar a instância e, em seguida, clique em **Migrar**.

## Resultados

1. Você obtém uma notificação do console de que sua solicitação para migrar a instância para a conta especificada do {{site.data.keyword.cloud_notm}} foi aceita.
2. Quando a migração da instância for concluída, a instância será exibida na página **Instâncias implementadas** na conta para a qual foi migrada. A instância migrada não é mais exibida na conta original da qual foi migrada.

### Links relacionados

* [ Gerenciando o acesso de usuário com o IAM ](../vmonic/iam.html)
* [Convidando usuários para acessar serviços e recursos](../vmonic/iamuserinvite.html)
* [ O que é IBM Cloud IAM ](../../../iam/index.html)
