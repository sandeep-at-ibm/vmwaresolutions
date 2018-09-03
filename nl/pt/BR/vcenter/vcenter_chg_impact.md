---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-08"

---

# Considerações sobre como alterar os artefatos do vCenter Server

Mudar usuários, recursos ou sub-redes que são reservados para {{site.data.keyword.vmwaresolutions_full}} pode afetar as operações de gerenciamento.

**Importante:** não edite as permissões globais do grupo **ic4v-vCenter** na página **Usuários e grupos** no VMware vSphere Web Client. Essas mudanças incluem: mudar o nome do usuário, excluir o usuário ou mudar sua senha.

## ID de automação

O ID de **automação** é uma conta do usuário que é usada pelas operações automatizadas fornecidas no console do {{site.data.keyword.vmwaresolutions_short}}.

Usuários e senhas para as operações automatizadas no console não devem ser mudados porque as operações do console que dependem dessas credenciais podem falhar.

## As contas do usuário de serviço específico

Cada serviço cria uma conta de usuário interna no vCenter Server. Esta conta é necessária para que as operações de gerenciamento associadas a um serviço possam se conectar ao vCenter Server para executar as operações no serviço.

**Importante**: para evitar indisponibilidades e problemas de conexão, se você mudar as configurações de ID do usuário, senha ou expiração de senha para essa conta do usuário, assegure-se de também atualizar as informações no serviço associado.

O ID do usuário para esta conta está no formato `<service_name>-<truncated service_uuid>@test.local` ou `<service_name>-<truncated service_uuid>@example-domain.local`. Por exemplo, o ID do usuário usado pelo serviço Veeam on {{site.data.keyword.cloud_notm}} para se conectar ao vCenter Server para executar backups planejados é `Veeam-<Veeam_uuid>@test.local`.

**Nota**: o `<service_name>` junto com o `<service_uuid>` trunca para 20 caracteres.

## Recursos do VMware para instâncias do vCenter Server (V1.9 e mais recente)

Para instâncias implementadas na V1.9 e mais recente, se a instância do vCenter Server estiver em um estado **Pronto para Uso**, será possível modificar o data center virtual do VMware, cluster, comutadores, grupos de portas e nomes do armazenamento de dados do cliente do VMware vSphere Web Client. No entanto, não se deve mudar o nome do armazenamento de dados de gerenciamento de seu valor padrão: **vsanDatastore** para instâncias do vSAN e **management-share** para instâncias do Network File System (NFS).

## Recursos do VMware para instâncias do vCenter Server (V1.8 e anterior)

A tabela a seguir lista as operações que poderão ser afetadas se o administrador SSO mudar os recursos do VMware vCenter Server fora do console do {{site.data.keyword.vmwaresolutions_short}}. Se uma solução para recuperar estiver disponível, ela também será fornecida.

Esta tabela é aplicável para instâncias implementadas na V1.8 e anterior, além das instâncias implementadas na V1.8 e anterior e depois submetidas a upgrade para a V1.9 ou mais recente.

Tabela 1. Operações que são afetadas ao mudar recursos do VMware

| Mudança tentada  | Operações afetadas  | Severidade  | Método de recuperação  |
|:------------- |:------------- |:--------------|:--------------|
| Mude o nome do data center virtual do VMware. | Incluir um data center virtual do VMware pode falhar porque o novo servidor ESXi não pode se associar ao data center virtual mudado. | Importante | Mude o nome do data center virtual do VMware de volta para o nome original. |
| Mude quaisquer nomes do grupo da porta.    | A inclusão de um servidor ESXi pode falhar. | Importante | Mude o nome do grupo da porta de volta para o nome original. |
| Mude o nome do cluster. | A inclusão de um servidor ESXi pode falhar. | Importante | Mude o nome do cluster de volta para o nome original.
| Mude o nome do Comutador virtual distribuído (DVS) público ou privado. | A inclusão de um servidor ESXi pode falhar. | Importante | Mude o nome do Distributed Virtual Switch (DVS) público ou privado para o nome original.
| Mudar o nome do armazenamento de dados do vSAN na instância que usa o vSAN. | A inclusão de um servidor ESXi pode falhar.<br><br>Atualizando a instância poderá falhar. | Importante | Mude o nome do armazenamento de dados vSAN de volta para o nome original, **vsanDatastore**.
| Mudar o nome do armazenamento de dados NFS de gerenciamento na instância que usa o NFS. | A inclusão de um servidor ESXi pode falhar.<br><br>Atualizando a instância poderá falhar. | Importante | Mude o nome do armazenamento de dados de gerenciamento NFS de volta para o nome original, **management-share**, e remonte o armazenamento de dados do NFS como somente leitura no servidor ESXi.

A tabela a seguir lista as operações que poderão ser afetadas se o usuário raiz VC/PSC mudar os recursos do vCenter Server fora do console do {{site.data.keyword.vmwaresolutions_short}}.

Tabela 2. Operações que são afetadas pelo acesso raiz VC/PSC (local)

| Mudança tentada  | Operações afetadas  | Severidade  | Método de recuperação  |
|:------------- |:------------- |:--------------|:--------------|
| Ativar ou desativar o acesso de shell.    | A correção e a atualização para o PSC e o vCenter Server podem falhar.    | Importante    | N/A    |

## Sub-redes de gerenciamento para instâncias do vCenter Server

As informações a seguir discutem as sub-redes pedidas pelo {{site.data.keyword.vmwaresolutions_short}} e fornecem opções para você pedir sub-redes extras para seu próprio uso.

**CUIDADO**: não use esses componentes para outros propósitos ou a estabilidade de seu ambiente será seriamente comprometida.

Com cada pedido do Bare Metal Server do {{site.data.keyword.cloud_notm}}, os intervalos de endereços IP a seguir são pedidos por padrão:
*  Um intervalo público primário de 32 endereços IP
*  Um intervalo privado primário de 64 endereços IP

Além disso, as sub-redes de gerenciamento a seguir também são reservadas para o {{site.data.keyword.vmwaresolutions_short}}:
*  Duas sub-redes privadas móveis de 64 endereços IP na primeira VLAN: uma para gerenciamento e a outra para VTEPS
*  Duas sub-redes privadas móveis de 64 endereços IP na segunda VLAN: uma para VMotion e uma para vSAN
*  Uma sub-rede móvel pública de 16 endereços IP na VLAN pública

Se precisar usar mais sub-redes, será possível obter endereços IP para usar em uma das maneiras a seguir:
*  **Opção 1 (recomendado)**: use sobreposições de rede virtual VMware NSX. Um modelo de VXLAN de amostra é fornecido mediante pedido. Esse VXLAN pode ser usado como ponto de início para construir a rede definida por software (SDN). Para obter mais informações, veja [Configurando sua rede para usar o NSX Edge gerenciado pelo cliente](vc_esg_config.html).
*  **Opção 2**: peça suas próprias sub-redes móveis públicas ou privadas para obter endereços IP. Para distinguir as sub-redes pedidas das sub-redes de gerenciamento, é possível incluir notas em todas as sub-redes que estão sendo pedidas.
