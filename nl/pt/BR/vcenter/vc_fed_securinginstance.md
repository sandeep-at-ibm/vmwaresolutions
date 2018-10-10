---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Protegendo instâncias do VMware Federal

Conclua o procedimento a seguir para proteger sua instância do VMware Federal implementada, ou seja, para remover a conexão de gerenciamento aberta para acesso contínuo à instância.

## Antes de iniciar

Revise as informações a seguir para entender os resultados de proteger sua instância do VMware Federal implementada:

* Registre e salve as credenciais que você pode precisar para seu ambiente antes de concluir este procedimento. Todas as credenciais de seu ambiente são apagadas do banco de dados do {{site.data.keyword.vmwaresolutions_full}} e não podem ser recuperadas após o início da ação segura.
* Exceto para uma exclusão completa da instância, todas as outras funções de gerenciamento são desativadas após o início da ação segura.

## Procedimento para proteger instâncias do VMware Federal

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a proteger.
3. Clique no ícone do menu overflow próximo ao **console do vCenter**.
4. Clique em **Proteger instância**.
5. Clique em **OK** para confirmar que você deseja desconectar a instância da automação.

  **Nota**: antes de concluir esta etapa, assegure-se de revisar as informações na seção **Antes de iniciar**.

6. Remova o serviço de gerenciamento público de serviços de gerenciamento VMware NSX Edge Services Gateway (ESG) de seu ambiente e, opcionalmente, remova o ESG gerenciado pelo cliente que é implementado durante a automação.
7. Reconfigure senhas ou chaves de todas as contas usadas pela automação IBM. Para obter mais informações, consulte [Como posso proteger meu ambiente para remover o acesso pela automação e suporte IBM?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)

## Resultados

O status da instância é mudado para **Modificando**.

Quando a instância é protegida com êxito, o status da instância é mudado para **Protegido** e apenas as propriedades da instância e o histórico de implementação estão disponíveis.

### Links relacionados

* [Visão geral do VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Pedindo instâncias do VMware Federal](vc_fed_orderinginstance.html)
* [Visualizando instâncias do VMware Federal](vc_fed_viewinginstance.html)
* [Excluindo instâncias do VMware Federal](vc_fed_deletinginstance.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
