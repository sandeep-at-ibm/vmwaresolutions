---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

# Convidando usuários para acessar serviços e recursos
{: #iamuserinvite}

O {{site.data.keyword.vmwaresolutions_full}} é integrado ao {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) para colaboração entre múltiplos usuários. Depois de se inscrever para uma conta do {{site.data.keyword.cloud_notm}} e efetuar login no console do {{site.data.keyword.vmwaresolutions_short}}, é possível incluir usuários na conta do {{site.data.keyword.cloud_notm}}. Esses usuários incluídos podem compartilhar os serviços e os recursos que são provisionados para a conta.

## Antes de iniciar
{: #iamuserinvite-reqs}

* Assegure-se de que você seja o proprietário da conta ou de que sua função de gerenciamento de plataforma para o serviço **VMware Solutions** seja **Administrador**.
* Assegure-se de ter revisado as funções de usuário e as permissões em [Gerenciando o acesso de usuário com o Identity and Access Management](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam).

## Procedimento para convidar usuários para acessar serviços e recursos
{: #iamuserinvite-procedure}

1. No lado esquerdo do banner, clique em ** Gerenciar > Segurança > Identidade e acesso**.
2. Na página **Usuários**, clique em **Convidar usuários**.
3. Na página **Convidar usuários**, na seção **Usuários**, insira os endereços de e-mail dos usuários que você deseja convidar no campo **Endereço de e-mail**.
4. Na seção **Acesso**, expanda **Serviços** e, em seguida, conclua as tarefas a seguir:
   1. Selecione **Recurso** na lista **Designar acesso a**.
   2. Selecione **Soluções do VMware** na lista **Serviços**.
   3. Selecione a função de acesso à plataforma que você deseja designar aos usuários. Ela pode ser **Administrador**, **Editor**, **Operador** ou **Visualizador**.
5. Clique em **Convidar usuários**.

## Resultados
{: #iamuserinvite-results}

Depois que os usuários incluídos aceitarem seu convite, eles poderão efetuar login no console do {{site.data.keyword.vmwaresolutions_short}} e alternar para sua conta. Para isso, nas configurações de perfil, os usuários clicam no ícone de contas de usuário no banner do console do {{site.data.keyword.vmwaresolutions_short}}. Em seguida, os usuários incluídos podem colaborar e compartilhar os serviços e recursos disponíveis em sua conta especificada.

## Links relacionados
{: #iamuserinvite-related}

* [ Convidando usuários e designando acesso ](/docs/iam?topic=iam-iamuserinv)
* [ Gerenciando a identidade e o acesso ](/docs/iam?topic=iam-getstarted)
* [ Gerenciando usuários e o acesso ](/docs/iam/iamusermanage.html)
* [ O que é IAM ](/docs/iam?topic=iam-iamoverview)
* [Migrando instâncias do vCenter Server pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [Migrando instâncias do vCenter Server with Hybridity Bundle pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [Migrando instâncias do Cloud Foundation pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addinstancetousraccount)
* [Migrando instâncias do NetApp ONTAP Select pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)
