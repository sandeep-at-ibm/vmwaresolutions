---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementação e gerenciamento do KMIP for VMware
{: #kmip-implementation}

## Conectando o servidor de gerenciamento de chaves
{: #kmip-implementation-connecting-kms}

Para ativar a criptografia do vSphere ou a criptografia do vSAN usando o KMIP for VMware on {{site.data.keyword.cloud_notm}}, é necessário concluir as tarefas a seguir:

1. [ Ative sua conta para os terminais de serviço ](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started).
2. Crie uma instância do [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial).
3. Crie um customer root key (CRK) dentro do IBM Key Protect.
4. Crie um [ID do serviço e uma chave de API](/docs/iam?topic=iam-serviceidapikeys) do Identity and Access Management (IAM) para uso com o KMIP for VMware. Conceda a esse ID do serviço o acesso de visualizador de plataforma e o acesso de gravação de serviço para sua instância do Key Protect.
5. Crie uma instância do [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering) por meio do catálogo do {{site.data.keyword.cloud_notm}}.
6. No VMware vCenter, crie um cluster do key management server (KMS) com dois servidores, um para cada terminal do KMIP for VMware em sua região escolhida.
7. Selecione um dos métodos do VMware para gerar ou instalar um certificado de cliente KMS no vCenter.
8. Exporte a versão pública do certificado e configure-a como um certificado de cliente permitido em sua instância do KMIP for VMware.

## Ativando a Crip
{: #kmip-implementation-enable-encrypt}

Para usar a criptografia do vSAN, edite as configurações gerais do vSAN em seu cluster do vCenter e marque a caixa de seleção de criptografia.

A verificação de funcionamento do vSAN pode emitir avisos periódicos de que ele não é capaz de se conectar ao cluster do KMS por meio de um ou mais de seus hosts vSphere. Esses avisos ocorrem porque a conexão de verificação de funcionamento do vSAN atinge o tempo limite muito rapidamente. É possível ignorar esses avisos. Para obter mais informações, consulte [o vSAN KMS Health Check falha intermitentemente com o erro de tempo limite de handshake SSL](https://kb.vmware.com/s/article/67115){:new_window}.
{:note}

Para usar a criptografia do vSphere, edite suas políticas de armazenamento da máquina virtual para requerer criptografia de disco.

## Rotação de chave
{: #kmip-implementation-key-rotation}

[Gire sua customer root key (CRK) do Key Protect](/docs/services/key-protect?topic=key-protect-key-rotation#key-rotation) usando o console ou a API do {{site.data.keyword.cloud_notm}}.

Para criptografia do VMware vSAN, gire suas chaves de criptografia de chaves (KEKs) do VMware e, opcionalmente, data&ndash;encrypting keys (DEKs) por meio das configurações gerais do vSAN em seu cluster do vCenter.

Para a criptografia do VMware vSphere, gire as KEKs e DEKs do VMware (opcionalmente) usando o comando PowerShell **Set-VMEncryptionKey**.

## Revocação de chave
{: #kmip-implementation-key-revocation}

É possível revogar todas as chaves em uso pelo KMIP for VMware excluindo sua CRK escolhida do Key Protect.

Quando as chaves são revogadas, todos os dados protegidos por essas chaves e por sua instância do KMIP for VMware são fragmentados criptograficamente por esse método. O VMware preserva algumas chaves enquanto um host ESXi está ligado, portanto, é necessário reiniciar o cluster do vSphere para assegurar que todos os dados criptografados não estejam mais em uso.
{:important}

O KMIP for VMware armazena KEKs individuais agrupadas em sua instância do Key Protect usando nomes que estão associados aos IDs de chave que são conhecidos para o VMware. É possível excluir chaves individuais para revogar a criptografia de discos ou unidades individuais.

O VMware não exclui chaves do KMS quando uma MV com discos criptografados é removida do inventário. Isso é para permitir a recuperação dessa MV por meio do backup ou se ela for restaurada para o inventário. Se você desejar recuperar essas chaves e invalidar criptograficamente todos os backups, será necessário excluir as chaves do Key Protect depois de excluir suas MVs.
{:note}

## Links relacionados
{: #kmip-implementation-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [Design de solução](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
