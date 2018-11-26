---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-11"

---

# Convidando usuários para acessar serviços e recursos

O {{site.data.keyword.vmwaresolutions_full}} é integrado ao {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) para colaboração entre múltiplos usuários. Depois de se inscrever para uma conta do {{site.data.keyword.cloud_notm}} e efetuar login no console do {{site.data.keyword.vmwaresolutions_short}}, é possível incluir usuários na conta do {{site.data.keyword.cloud_notm}}. Esses usuários incluídos podem compartilhar os serviços e os recursos que são provisionados para a conta.

## Antes de iniciar

* Assegure-se de que você seja o proprietário da conta ou de que sua função de gerenciamento de plataforma para o serviço **VMware Solutions** seja **Administrador**.
* Assegure-se de ter revisado as funções de usuário e as permissões em [Gerenciando o acesso de usuário com o Identity and Access Management](iam.html).

## Procedimento para convidar usuários para acessar serviços e recursos

1. No lado esquerdo do banner, clique em ** Gerenciar > Segurança > Identidade e acesso**.
2. Na página **Usuários**, clique em **Convidar usuários**.
3. Na página **Convidar usuários**, na seção **Usuários**, insira os endereços de e-mail dos usuários que você deseja convidar no campo **Endereço de e-mail**.
4. Na seção **Acesso**, expanda **Serviços** e, em seguida, conclua as tarefas a seguir:
   1. Selecione **Recurso** na lista **Designar acesso a**.
   2. Selecione **Soluções do VMware** na lista **Serviços**.
   3. Selecione a função de acesso à plataforma que você deseja designar aos usuários. Ela pode ser **Administrador**, **Editor**, **Operador** ou **Visualizador**.
5. Clique em **Convidar usuários**.

## Resultados

Depois que os usuários incluídos aceitarem seu convite, eles poderão efetuar login no console do {{site.data.keyword.vmwaresolutions_short}} e alternar para sua conta. Para isso, nas configurações de perfil, os usuários clicam no ícone de contas de usuário no banner do console do {{site.data.keyword.vmwaresolutions_short}}. Em seguida, os usuários incluídos podem colaborar e compartilhar os serviços e recursos disponíveis em sua conta especificada.

### Links relacionados

* [ Convidando usuários e designando acesso ](../../../iam/iamuserinv.html)
* [ Gerenciando a identidade e o acesso ](../../../iam/quickstart.html)
* [ Gerenciando usuários e o acesso ](../../../iam/iamusermanage.html)
* [ O que é IAM ](../../../iam/index.html)
* [Migrando instâncias do vCenter Server anteriores à V2.5 para contas do IBM Cloud](../vcenter/vc_addinstancetousraccount.html)
* [Migrando instâncias do vCenter Server with Hybridity Bundle anteriores à V2.5 para contas do IBM Cloud](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Migrando instâncias do Cloud Foundation anteriores à V2.5 para contas do IBM Cloud](../sddc/sd_addinstancetousraccount.html)
* [Migrando instâncias do NetApp ONTAP Select anteriores à V2.5 para contas do IBM Cloud](../netapp/np_addinstancetousraccount.html)
* [Migrando instâncias do VMware Federal anteriores à V2.5 para contas do IBM Cloud](../vcenter/vc_fed_addinstancetousraccount.html)
