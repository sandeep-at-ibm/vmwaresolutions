---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Protegendo instâncias do VMware Federal

Conclua o procedimento a seguir para proteger sua instância do VMware Federal implementada, ou seja, para remover a conexão de gerenciamento aberta para acesso contínuo à instância.

## Antes de iniciar

Revise as informações a seguir para entender os resultados de proteger sua instância do VMware Federal implementada:

* Registre e salve as credenciais que você pode precisar para o seu ambiente antes de concluir este procedimento. Todas as credenciais para seu ambiente foram apagadas do banco de dados do {{site.data.keyword.vmwaresolutions_full}} e não podem ser recuperadas após a ação segura ser chamada.
* Com exceção de uma exclusão completa da instância, todas as funções de gerenciamento são desativadas após a ação segura ser chamada.
* O VMware NSX Edge Services Gateway (ESG) para o tráfego de gerenciamento HTTPS de saída e a máquina virtual do IBM CloudDriver são excluídos como parte da ação para proteger a instância do VMware Federal implementada.

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a proteger.
3. Clique no ícone de menu overflow à direita do **console do vCenter**.
4. Clique em **Proteger instância**.
5. Clique em **OK** para confirmar que você deseja desconectar a instância da automação.

   **Nota**: antes de concluir esta etapa, assegure-se de que você tenha revisado as informações na seção **Antes de iniciar**.

## Resultados

O status da instância é mudado para **Modificando**.

Quando a instância é protegida com êxito, o status da instância é mudado para **Protegido** e apenas as propriedades da instância e o histórico de implementação estão disponíveis.

### Links relacionados

* [Visão geral do VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Pedindo instâncias do VMware Federal](vc_fed_orderinginstance.html)
* [Visualizando instâncias do VMware Federal](vc_fed_viewinginstance.html)
* [Excluindo instâncias do VMware Federal](vc_fed_deletinginstance.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
