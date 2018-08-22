---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Considerações para instâncias do VMware HCX on IBM Cloud no local

Revise as considerações a seguir antes de instalar ou excluir as instâncias do HCX on {{site.data.keyword.cloud}} que você pediu para uso no local.

**Nota:** uma instância do vCenter Server com o HCX no {{site.data.keyword.cloud_notm}} é limitada a três conexões simultâneas por meio de sites no local.

## Considerações ao instalar as instâncias do HCX on IBM Cloud no local

Os componentes do HCX on {{site.data.keyword.cloud_notm}} devem ser instalados no {{site.data.keyword.cloud_notm}} e no ambiente do vSphere no local. É recomendado que você instale o serviço HCX on {{site.data.keyword.cloud_notm}} em sua instância do vCenter Server with Hybridity Bundle on {{site.data.keyword.cloud_notm}} antes de instalar a instância do HCX on {{site.data.keyword.cloud_notm}} no local. Para obter mais informações, veja [Considerações para o HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Requisitos nos endereços IP

Para funcionalidade completa do HCX, você precisa de pelo menos cinco endereços IP privados e deve permitir que eles acessem a Internet.

### Processo de implementação para instâncias do HCX on IBM Cloud

Deve-se concluir as tarefas a seguir para uma instalação bem-sucedida da instância do HCX on {{site.data.keyword.cloud_notm}} no local:
1. No console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
    1. Clique em **Instâncias implementadas** na área de janela de navegação esquerda.
    2. Clique na instância do vCenter Server with Hybridity Bundle com o serviço HCX on {{site.data.keyword.cloud_notm}} instalado. Este é o lado da nuvem ao qual você deseja se conectar do seu ambiente do vSphere local.
    3. Na guia **Serviços**, clique em **Serviços instalados**.
    4. Clique em **na placa do {{site.data.keyword.cloud_notm}}** .
    5. Clique em **Visualizar console em nuvem do HCX** e, em seguida, efetuar login no console usando as credenciais do vCenter Server para visualizar os detalhes do serviço HCX on {{site.data.keyword.cloud_notm}} do lado da nuvem.
2. Em **Console em Nuvem do HCX**, conclua as etapas a seguir:
    1. Clique na guia **Administração**.
    2. Na guia **Atualizações do Sistema**, clique em **SOLICITAR LINK DE DOWNLOAD**.
    3. Clique em **COPIAR LINK** e, em seguida, use esse link para fazer download do HCX Enterprise Client para um ambiente local com acesso ao ambiente do vSphere local.
3. No VMware vSphere Web Client, implemente o HCX Enterprise Client como um dispositivo virtual do HCX Manager (HCX Manager) em seu ambiente local.

   **Nota**: deve-se implementar o HCX Manager local em uma rede privada e permitir que ele acesse a rede pública. É possível usar um NSX Edge, Vyatta ou gateways semelhantes para permitir acesso à Internet ao HCX Manager local. Se os gateways usados para acesso à rede privada e acesso à rede pública forem diferentes, recomenda-se que você use o gateway padrão para permitir o acesso à rede pública e permitir que o **Console do Administrador do HCX Manager** crie uma rota estática para o acesso à rede privada.
4. Após a conclusão da implementação do HCX Manager, use o **Console do Administrador do HCX Manager** para ativar o HCX Manager local. Para obter uma chave de ativação para o HCX Manager no local, peça uma instância do HCX on {{site.data.keyword.cloud_notm}} no local no console do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, veja [Pedindo instâncias do HCX locais](../services/standalone_orderingserviceinstances.html).
5. Se você usou um certificado SSL autoassinado ao pedir o HCX no serviço {{site.data.keyword.cloud_notm}}, deverá importar o certificado para o HCX Manager local concluindo as etapas a seguir:
    1. No **Console do Administrador do HCX Manager** local, clique na guia **Administração**.
    2. Na área de janela de navegação esquerda, clique em **Certificado CA confiável** e, em seguida, clique em **IMPORTAR** à direita.
    3. Clique em **URL** e, em seguida, insira a URL do certificado que deseja aplicar, que é o **HCX Cloud IP** (``https://<cloud-side public IP>``), que pode ser localizado no HCX na página de detalhes do serviço {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}.
    4. Clique em **APLICAR**.

Agora, você concluiu a configuração básica do HCX Manager local. É possível continuar para emparelhar o site do HCX on {{site.data.keyword.cloud_notm}} no local com o site do HCX do lado da nuvem.

Para obter mais informações, veja [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Considerações ao excluir instâncias do HCX on IBM Cloud no local

Revise as considerações a seguir antes de excluir uma instância do HCX on {{site.data.keyword.cloud_notm}} que foi pedida para uso no local:
1. No VMware vSphere Web Client, acesse a interface com o usuário do HCX e, em seguida, verifique os itens a seguir:
    1. Assegure-se de que nenhuma operação de migração ou de recuperação de desastre do HCX esteja em execução.
    2. Assegure-se de que todas as redes estendidas sejam removidas.
    3. Assegure-se de que todos os componentes de interconexão com sites em nuvem emparelhados sejam removidos.

   **Importante**: deve-se concluir todas as considerações antes de continuar com a próxima etapa. Caso contrário, a licença para a instância do HCX on {{site.data.keyword.cloud_notm}} no local é cancelada, razão pela qual migrações não podem ser executadas e erros podem ocorrer nos componentes do HCX.  
2. No console do {{site.data.keyword.vmwaresolutions_short}}, exclua a instância do HCX on {{site.data.keyword.cloud_notm}} no local que foi pedida para obter a chave de ativação para o HCX Manager no local. Assegure-se de que a instância excluída não esteja mais disponível no console antes de passar para a próxima etapa.

   Para obter mais informações, veja [Excluindo instâncias do HCX on {{site.data.keyword.cloud_notm}} no local](../services/standalone_deletingserviceinstances.html).
3. No VMware vSphere Web Client, exclua o HCX Manager local.

### Links relacionados

* [Visualizando HCX no {{site.data.keyword.cloud_notm}} instâncias](../services/standalone_viewingserviceinstances.html)
* [Glossário de termos do HCX](hcx_glossary.html)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
* [Guia do usuário e de instalação do VMware HCX Enterprise](https://hcx.vmware.com/content/docs/vmware-hcx-enterprise-install-guide.pdf){:new_window}
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
