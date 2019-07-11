---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# Etapa 4-Configuração do aplicativo
{: #caveonix-step4}

Depois que as máquinas virtuais (MVs) são implementadas e os componentes do aplicativo são instalados, a solução Caveonix RiskForesight fica disponível para ser configurada para o Provedor de serviços e o primeiro Locatário ou a primeira Organização.

O Provedor de serviços é a organização de nível superior e há um ou mais Locatários/Organização atendidos por ele. O Provedor de serviços designa Ativos que são coletados do vCenter para o Locatário ou para as Organizações, que então os designam a Aplicativos ou Subaplicativos. Esses Aplicativos estão, então, sujeitos a um regime de conformidade.

Esta etapa é concluída inicialmente pela automação do IBM Cloud for VMware Solutions que usa informações fornecidas pelo cliente durante o processo de pedido e informações padrão. O processo de configuração pode ser iniciado pelo cliente, após a implementação, para modificar o Provedor de serviços ou a Organização do locatário como uma pós-instalação necessária.

A configuração do Provedor de serviços tem oito subetapas:
-	Etapa 1: Detalhe da organização - Inclua os detalhes da organização pai para o seu provedor de serviço de nuvem. Essa organização pode ter múltiplos locais físicos e múltiplos data centers. As organizações para seus locatários e suborganizações de seu provedor de serviços são incluídas posteriormente.
-	Etapa 2: Locais – Mapeie a infraestrutura em "Locais” do RiskForesight. Os recursos são agrupados por local, provedor de nuvem e repositório de ativos.
-	Etapa 3: Ambientes-Opcional. Ambientes são uma maneira de agrupar ativos. Por exemplo, DevOps, Site Site, Produção.
-	Etapa 4: Provedor em nuvem - Incluir os "provedores" que fornecem a infraestrutura em que seu aplicativo é executado.
-	Etapa 5: Repositórios de ativos - Um Repositório de ativos associa um conjunto de ativos a uma Organização, um Provedor em nuvem e um Local.
-	Etapa 6: Organizações - Criar suborganização para suas próprias operações e organizações adicionais - uma para cada um dos locatários do provedor de serviços. Cada locatário deve passar por seu próprio processo de configuração - incluindo a criação de suas próprias suborganizações.
-	Etapa 7: Usuários da organização - Criar e designar Usuários a Organizações e Suborganizações do Locatário do Provedor de serviços.
-	Etapa 8: Planejador de tarefas - Configurar tarefas para: Sincronizar com o Repositório de ativos, Executar varreduras de Vulnerabilidade e Conformidade do SCAP, Coletar fluxos de rede do NSX, Coletar informações sobre o software que está em execução em Ativos monitorados, Coletar logs do sistema e eventos do sistema para Ativos.

A Configuração do locatário ou da Organização tem sete subetapas:

-	Etapa 1: Organização - Incluir detalhes para sua organização primária. Também é possível criar sub-organizações. Use as organizações para segmentar seus usuários ou como uma das maneiras de agrupar seus ativos. É possível criar mais organizações com uma de suas organizações existentes como mãe. Ao criar uma nova organização, é possível selecionar o "Valor do impacto nos negócios", que é usado para gerar pontuações de risco cibernético.
-	Etapa 2: Ativos da organização - Novos ativos/cargas de trabalho são agrupados automaticamente por local, provedor em nuvem e repositório de ativos. Os Ativos podem ser designados a apenas uma organização de cada vez. O Provedor de serviços precisa designar ativos a uma organização.
-	Etapa 3: Associar ambiente e local - Opcional. Os ambientes são definidos pelo Provedor de serviços.
-	Etapas 4 e 5: Criar Subaplicativos ou Aplicativos - usado para agrupar ativos em locais e organizações e ver seus fluxos e políticas associados. Criar aplicativos que correspondam aos serviços de negócios e de TI. Por exemplo, Aplicativo=SAP, Subaplicativos=Front-end do SAP, Camada do meio do SAP e Back-end do SAP. O valor do impacto nos negócios corresponde a um Aplicativo; os regimes de conformidade aplicam-se a um aplicativo.
-	Etapa 6: Acesso remoto - o Acesso remoto é necessário para executar varreduras em ativos, pode ser uma conta de serviço padrão ou uma conta específica do ativo.
-	Etapa 7: Planejador de tarefas - Planejar varreduras para execução em uma base periódica. Os tipos de tarefas incluem: Vulnerabilidade de varredura do SCAP, XCCDF de varredura do SCAP, Varredura de fluxo do NSX, Varredura de software, Varredura de extração de log.

As informações a seguir são coletadas do usuário no momento do pedido e são usadas para a configuração do aplicativo.

Tabela 1. Informações coletadas do usuário

|Estágio de Configuração |Parâmetro |
|---|---|
|Repositórios de Organização / Ativo  |Nome da Organização |
|Organização |Número de Telefone |
|Organização |E-mail |
|Repositórios de Organização / Ativo |Linha 1 de Endereço |
|Provedor em Nuvem / Repositórios de Recursos |Nome |
|Provedor em nuvem |Descrição |
|Provedor em nuvem |E-mail do POC |
|Provedor em nuvem |Tipo|
|Provedor em nuvem |Nome do POC |
|Provedor em nuvem |Telefone POC |

As informações padrão a seguir são usadas na configuração do aplicativo.

Tabela 2. Informações padrão usadas na configuração do aplicativo

|Estágio de Configuração |Parâmetro |
|---|---|
|Ambiente |O nome do ambiente é configurado como "Inicial"|
|Ambiente | O Score está configurado como 5|
|Repositório de Recursos | Dois Repositórios de ativos são configurados: vCenter e NSX Manager. URL do host configurada como `https://vCenter_fqdn` e `https://*NSX Manager_fqdn` |
|Repositório de Recursos |Dois Repositórios de ativos são configurados: vCenter e NSX Manager. Ambos usam o mesmo nome de usuário. O nome do usuário é configurado como o nome do usuário administrador do vCenter|
|Repositório de Recursos |Dois repositórios de ativos são configurados: vCenter e NSX Manager. Ambos usam a mesma senha. A senha é configurada como a senha do administrador do vCenter
|Repositório de Recursos |Dois repositórios de ativos são configurados: vCenter e NSX Manager. Ambos usam a mesma senha. O tipo é configurado como vCenter para um repositório e NSX para o outro
|Tarefa |Quatro tarefas são configuradas: Varredura de ativo, Fluxos de NSX, Varredura da infraestrutura do VMware e
Vulnerabilidade do VMware. O ScanName é configurado como DC1AssetScan, NSXFlows, VMWInfraScan, VMWVulnScan |
|Tarefa |Quatro tarefas são configuradas: Varredura de ativo, Fluxos de NSX, Varredura da infraestrutura do VMware e
Vulnerabilidade do VMware. O tipo é configurado como vCenter, NSX, VMWareInfrastructureScan, VMWareVulnerabilityScan |
|Tarefa |O planejamento é configurado como Por hora para DC1AssetScan e Diário para os outros |

## Links relacionados
{: #caveonix-step4-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
