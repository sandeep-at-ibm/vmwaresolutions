---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-29"

---

# Integração
{: #opsmgmt-integration}

Esse tópico destaca a camada de Gerenciamento operacional do design. No entanto, algumas empresas podem desejar integrar essa camada à sua camada de Gerenciamento de serviço. Esta seção fornece orientação sobre essa integração. Neste design, o vROps é o ponto central no qual todos os alertas surgem.

As categorias de integração a seguir são possíveis:
* Direção norte - Integração do vROps com outras ferramentas:
  * Notificação de alertas para o servidor SMTP ou ferramentas como o Slack ou o PagerDuty.
  * Integração de chamados em uma ferramenta de central de serviço, como o ServiceNow.
  * Inicialização dos fluxos de trabalho do vRealize Orchestrator para corrigir um problema descoberto pelo vROps.
* Direção sul - Integração do conjunto de ferramentas de gerenciamento de serviço ou nuvem:
  * O vRealize Automation configura o monitoramento quando uma nova carga de trabalho é incluída.
  * Atualize os objetos do vROps com o enriquecimento de evento de origens externas.

O vROps fornece os seguintes plug-ins de alerta de saída:
* Ação automatizada - ativada por padrão.
* E-mail padrão - usa o Protocolo Simples de Transporte de Correio (SMTP) para enviar por e-mail notificações de alerta do vRealize Operations Manager para os indivíduos interessados.
* Trap SNMP – registra alertas em seu servidor Trap SNMP.
* Notificação de REST - envia alertas do vROps para outro aplicativo ativado para REST no qual você construiu um serviço da web REST para aceitar essas mensagens.
* Arquivo de log - permite que o vROps registre alertas em um arquivo em cada um de seus nós do vRealize Operations Manager. Se você instalou o vRealize Operations Manager como um cluster de diversos nós, cada nó processa e registra os alertas para os objetos que monitora. Cada nó registra os alertas para os objetos que processa.
* Notificação SAM do Smarts - envia notificações de alerta para o EMC Smarts Server Assurance Manager.
* Compartilhamento de rede - envia relatórios para um local compartilhado, suporta o SMB versão 2.0.

Notificações são notificações de alerta que atendem aos critérios de filtro nas regras de notificação antes de serem enviadas na direção norte para sistemas externos. As regras de notificação são configuradas para que os alertas de saída necessários sejam filtrados antes do envio para o sistema externo selecionado. A lista de notificações é usada para gerenciar essas regras.

## Caso de uso de integração
{: #opsmgmt-integration-usecase}

Este caso de uso de exemplo se baseia em uma camada de gerenciamento de serviço genérica existente usada por uma empresa. O cliente provisionou uma instância do vCenter Server com a opção Gerenciamento de operações e deseja integrar essa plataforma à sua plataforma de gerenciamento de serviço. Ele usa um sistema de agregação de evento para integrar os alertas gerados por meio das ferramentas de monitoramento específicas do domínio:

* Uma ferramenta configurada para monitorar o S.O., o middleware e os aplicativos em suas cargas de trabalho do UNIX, Linux e Windows, mas essa ferramenta não monitora os componentes de infraestrutura, como o VMware, os dispositivos de rede ou o armazenamento.
* Um gerenciador de SNMP para receber traps SNMP de sua infraestrutura de rede. Essa ferramenta também coleta métricas de SNMP para ativar alertas de desempenho e capacidade.
* Uma ferramenta de gerenciamento de backup para gerenciar seus backups.
* Ferramentas de gerenciamento de armazenamento para gerenciar suas matrizes de armazenamento.
* Uma ferramenta de disponibilidade que usa ping para testar o acesso dos dispositivos.

Sua camada de gerenciamento de serviço também consiste em:

* Uma ferramenta de capacidade e desempenho do servidor para coletar métricas e fornecer relatórios.
* Um servidor de correção e conformidade para atualizar o S.O., o middleware e os aplicativos e medir a conformidade nessas plataformas.
* Uma ferramenta de chamados usada para gerenciar chamados para incidentes, problemas e mudanças. Essa ferramenta também é o Banco de Dados de Gerenciamento de Configuração (CMDB) da empresa. A ferramenta é capaz de enviar e-mails para as equipes de operações, assim como mensagens SMS.
* Um sistema de criação de log corporativo que captura logs de todos os sistemas e é gerenciado pela equipe de segurança.

Agora que têm o vROps, integrarão essa ferramenta usando a notificação de direção norte por meio do plug-in de Trap SNMP. Para integrar o vROps, os traps enviados pelo vROps precisam ser analisados de maneira que o ambiente de gerenciamento de eventos do cliente possa criar alertas e enriquecê-lo. A equipe da ferramenta de gerenciamento transferiu por download os MIBs do VMware do VMware e os instalou em seu ambiente de gerenciamento de eventos.

O vRLI está configurado para encaminhar todos os eventos para o sistema de criação de log corporativo de acordo com as políticas do cliente.

O cliente deseja usar suas ferramentas de monitoramento de S.O., de middleware e de aplicativo existentes, portanto, usou proxies no {{site.data.keyword.cloud}} para coletar e encaminhar métricas e alertas.

![Diagrama de integração](../../images/opsmgmt-integration.svg "Diagrama de integração")

## Links relacionados
{: #opsmgmt-integration-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
* [API RESTful do vRealize Operations](https://docs.vmware.com/en/vRealize-Operations-Manager/7.0/vrealize-operations-manager-70-api-guide.pdf){:new_window}
* [VMware Code API Explorer](https://code.vmware.com/apis?socv=1&numPerPage=164&sorter=pv){:new_window}
* [Postman Client Collection Tool for vRealize Operations](https://code.vmware.com/samples/4663/postman-client-collection-for-vrealize-operations-rest-apis){:new_window}
* [Blog do VMware PowerCLI](https://blogs.vmware.com/PowerCLI/2016/05/getting-started-with-powercli-for-vrealize-operations-vr-ops.html){:new_window}
* [Shims de webhook](https://blogs.vmware.com/management/2017/01/vrealize-webhooks-infinite-integrations.html){:new_window}
