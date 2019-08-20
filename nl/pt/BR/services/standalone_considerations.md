---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: VMware HCX standalone, HCX on-premises, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Considerações para instâncias do VMware HCX on IBM Cloud no local
{: #standalone_considerations}

Revise as considerações a seguir antes de instalar ou excluir as instâncias do HCX on {{site.data.keyword.cloud}} que você pediu para uso no local.

Uma instância do vCenter Server com HCX no {{site.data.keyword.cloud_notm}} é limitada a três conexões simultâneas por meio de sites no local.
{:note}

## Considerações antes de instalar as instâncias do HCX on IBM Cloud no local
{: #standalone_considerations-install}

Os componentes do HCX on {{site.data.keyword.cloud_notm}} devem ser instalados no {{site.data.keyword.cloud_notm}} e no ambiente do vSphere no local. Recomenda-se instalar o serviço HCX on {{site.data.keyword.cloud_notm}} em sua instância do vCenter Server no {{site.data.keyword.cloud_notm}} antes de instalar a instância do HCX on {{site.data.keyword.cloud_notm}} no local. Para obter mais informações, consulte [Considerações ao instalar o HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-hcx_considerations#hcx_considerations-install).

### Requisitos de endereço IP
{: #standalone_considerations-ip}

Para a funcionalidade integral do HCX, são necessários pelo menos cinco endereços IP privados que tenham acesso à Internet.

### Processo de implementação para instâncias do HCX on IBM Cloud
{: #standalone_considerations-deploy}

Deve-se concluir as tarefas a seguir para uma instalação bem-sucedida da instância do HCX on {{site.data.keyword.cloud_notm}} no local:
1. No console do {{site.data.keyword.vmwaresolutions_short}}, solicite o HCX no local na instância do {{site.data.keyword.cloud_notm}}. Para obter mais informações, veja [Pedindo instâncias do HCX locais](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
2. Em **Console em Nuvem do HCX**, conclua as etapas a seguir:
    1. Clique na guia **Administração**.
    2. Na guia **Atualizações do Sistema**, clique em **SOLICITAR LINK DE DOWNLOAD**.
    3. Clique em **COPIAR LINK** e, em seguida, use esse link para fazer download do HCX Enterprise Client para um ambiente local com acesso ao ambiente do vSphere local.
3. No VMware vSphere Web Client, implemente o HCX Enterprise Client como um dispositivo virtual do HCX Manager (HCX Manager) em seu ambiente local.

   Deve-se implementar o HCX Manager local em uma rede privada e permitir que ele acesse a rede pública. É possível usar um NSX Edge, Vyatta ou gateways semelhantes para permitir acesso à Internet para o HCX Manager no local. Se os gateways usados para acesso à rede privada e acesso à rede pública forem diferentes, recomenda-se que você use o gateway padrão para permitir o acesso à rede pública e permitir que o **Console do Administrador do HCX Manager** crie uma rota estática para o acesso à rede privada.
   {:note}
4. Após a conclusão da implementação do HCX Manager, use o **Console do Administrador do HCX Manager** para ativar o HCX Manager local. Para obter uma chave de ativação para o HCX Manager no local, peça uma instância do HCX on {{site.data.keyword.cloud_notm}} no local no console do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, veja [Pedindo instâncias do HCX locais](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
5. Se você usou um certificado SSL autoassinado ao pedir o HCX no serviço {{site.data.keyword.cloud_notm}}, deverá importar o certificado para o HCX Manager local concluindo as etapas a seguir:
    1. No **Console do Administrador do HCX Manager** local, clique na guia **Administração**.
    2. Na área de janela de navegação esquerda, clique em **Certificado CA confiável** e, em seguida, clique em **IMPORTAR** à direita.
    3. Clique em **URL** e, em seguida, insira a URL do certificado que você deseja aplicar, que é o **IP de nuvem do HCX** (``https://<cloud-side public IP>``), que é possível localizar na página de detalhes do serviço HCX on {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}.
    4. Clique em **APLICAR**.

Agora, você concluiu a configuração básica do HCX Manager local. É possível continuar para emparelhar o site do HCX on {{site.data.keyword.cloud_notm}} no local com o site do HCX do lado da nuvem.

Para obter mais informações, veja [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}.

## Considerações antes de excluir as instâncias do HCX on IBM Cloud no local
{: #standalone_considerations-delete}

Revise as considerações a seguir antes de excluir uma instância do HCX on {{site.data.keyword.cloud_notm}} que foi pedida para uso no local:
1. No VMware vSphere Web Client, acesse a interface com o usuário do HCX e verifique os itens a seguir:
    1. Assegure-se de que nenhuma operação de migração ou de recuperação de desastre do HCX esteja em execução.
    2. Assegure-se de que todas as redes estendidas sejam removidas.
    3. Assegure-se de que todos os componentes de interconexão com sites em nuvem emparelhados sejam removidos.

   Deve-se concluir todas as etapas anteriores antes de continuar com a próxima etapa. Caso contrário, a licença para a instância do HCX on {{site.data.keyword.cloud_notm}} no local será cancelada. Se a licença for cancelada, as migrações não poderão ser executadas e erros poderão ocorrer para os componentes do HCX.  
   {:important}
2. No console do {{site.data.keyword.vmwaresolutions_short}}, exclua a instância do HCX on {{site.data.keyword.cloud_notm}} no local que foi pedida para obter a chave de ativação para o HCX Manager no local. Assegure-se de que a instância excluída não esteja mais disponível no console antes de passar para a próxima etapa.

   Para obter mais informações, veja [Excluindo instâncias do HCX on {{site.data.keyword.cloud_notm}} no local](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_deletingserviceinstances).
3. No VMware vSphere Web Client, exclua o HCX Manager local.

## Links relacionados
{: #standalone_considerations-related}

* [Visualizando HCX no {{site.data.keyword.cloud_notm}} instâncias](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_viewingserviceinstances)
* [Glossário de termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Documentação do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
