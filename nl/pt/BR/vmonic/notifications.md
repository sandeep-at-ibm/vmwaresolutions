---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# Gerenciando notificações do sistema
{: #notifications}

É possível verificar notificações para o status do sistema ou operações do usuário. Também é possível usar as informações para investigar problemas que possam ocorrer.

## Visualizando notificações
{: #notifications-view}

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Notificações** na área de janela de navegação esquerda.
2. Visualize o resumo sobre todas as notificações.

| Coluna | Descrição |
|:------ |:----------- |
| Severidade | A severidade do evento que é relatado pela notificação.<br>**Crítico**: um evento crítico pode afetar todo o sistema ou serviço.<br>**Erro**: ocorre um evento de erro durante uma operação que pode precisar de intervenção do administrador ou usuário.<br>**Aviso**: um componente falha ou não está funcionando corretamente. No entanto, a falha não interrompe o processo contínuo do
       componente.<br>**Informativo**: uma operação do sistema ou do usuário é concluída. Geralmente, os eventos a seguir relatam notificações informativas:<br>Um serviço é instalado.<br>Um serviço tem upgrade feito.<br>Um serviço é removido.<br>Todos os serviços são reconfigurados para os servidores ESXi incluídos.<br>Todos os serviços são reconfigurados para os servidores ESXi removidos. |
| Tipo | O tipo de componente ao qual o evento relatado está relacionado: instâncias do vCenter Server, serviços, sistema |
| Recursos | O nome da instância ou do serviço que envia a notificação. |
| Descrição | Uma descrição curta da notificação. |
| Data | A data e hora em que a notificação é enviada. |
{: caption="Tabela 1. Histórico de Notificação" caption-side="top"}

3. Clique em uma linha de notificação para visualizar os detalhes da notificação.

## Filtrando notificações
{: #notifications-filter}

Por padrão, todas as notificações não lidas são exibidas. É possível filtrar as notificações por status, severidade e tipo. Para filtrar as notificações, selecione as caixas de seleção apenas para os itens que você deseja exibir nas listas **Status**, **Gravidade** ou **Tipo**.

## Links relacionados
{: #notifications-related}

* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Conta do usuário e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
