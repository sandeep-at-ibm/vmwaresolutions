---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

---

# Glossário de termos do Caveonix
{: #caveonix-terminology}

Este glossário fornece algumas descrições para os termos que estão associados à solução Caveonix RiskForesight:

-	**NIST Special Publication 800-53:** uma Risk Management Framework que trata do controle de segurança.
-	**Security Content Automation Protocol (SCAP):** um método para usar padrões específicos para ativar a avaliação automatizada do gerenciamento de vulnerabilidade, da medição e da conformidade de política de sistemas implementados em uma organização. As listas de verificação padronizam e permitem a automação da ligação entre as configurações de segurança do computador e a estrutura de controles do NIST Special Publication 800-53.
  - O National Vulnerability Database (NVD) é o repositório de conteúdo do governo dos EUA para SCAP.
  -	O SCAP permite que os administradores de segurança varram computadores, software e outros dispositivos com base em uma linha de base de segurança predeterminada para determinar se as correções de configuração e software são implementadas no padrão com o qual estão sendo comparadas.
  Os componentes do SCAP são como a seguir:
  -	Common Vulnerabilities and Exposures (CVE) - Uma lista de vulnerabilidades de segurança cibernética conhecidas publicamente.
  -	Common Configuration Enumeration (CCE) - Uma lista de problemas de configuração do sistema relacionados à segurança.
  -	Common Platform Enumeration (CPE) - Um esquema de nomenclatura estruturado para sistemas de tecnologia da informação, software e pacotes.
  -	Common Weakness Enumeration (CWE) - Uma lista de vulnerabilidades de segurança de software comuns.
  -	Common Vulnerability Scoring System (CVSS) - Fornece uma maneira de capturar as principais características de uma vulnerabilidade e produzir uma pontuação numérica que reflita sua severidade.
  -	Extensible Configuration Checklist Description Format (XCCDF) - Uma linguagem de especificação para gravação de listas de verificação de segurança, avaliações de desempenho e tipos relacionados de documentos. Um documento XCCDF representa uma coleção estruturada de regras de configuração de segurança para algum conjunto de sistemas de destino.
  -	Open Vulnerability and Assessment Language (OVAL) - Uma linguagem usada para codificar detalhes do sistema e uma variedade de repositórios de conteúdo. A linguagem padroniza as três principais etapas do processo de avaliação:
      - Representando informações de configuração de sistemas para teste.
      -	Analisando o sistema (vulnerabilidade, configuração e estado da correção)
      -	Relatando os resultados dessa avaliação.
-	**Security Technical Implementation Guide (STIG):** uma metodologia de segurança cibernética para padronizar protocolos de segurança dentro de redes, servidores, computadores e designs lógicos para aprimorar a segurança geral. Esses guias, quando implementados, aprimoram a segurança de software, hardware, arquiteturas físicas e lógicas para reduzir ainda mais as vulnerabilidades.
-	** Provedor de Serviços: **  A organização de nível superior.
-	**Provedor em nuvem** - Fornece a infraestrutura na qual a nuvem definida pelo software opera. O RiskForesight pode ser configurado para múltiplos Provedores em nuvem.
-	**Organizações:** organizações e suborganizações do locatário do Provedor de serviços. Se o Repositório de ativos for o vCenter, a Lista de organização/locatário deverá ser criada manualmente.
-	**Funções:** funções pré-configuradas e funções criadas pelo Provedor de serviços. As funções pré-configuradas não são editáveis pelo Provedor de serviços.
-	**Usuários da organização:** usuários das Organizações e suborganizações do locatário.
-	**Repositório de ativos:** um ponto de integração que permite que o RiskForesight sincronize o ativo atual na zona de gerenciamento e na zona do cliente do CSP. A versão atual do RiskForesight suporta a sincronização do VMware vCloud Director e dos vCenter Servers. Ele também suporta a coleta de dados do VMware NSX Manager. Os ativos são coletados no Repositório de ativos. O Provedor de serviços designa Ativos que são coletados do vCenter para Organizações e suborganizações do locatário do Provedor de serviços. Um Ativo pode ser designado a somente uma Organização.
-	**Acesso remoto:** fornece credenciais de máquina final para permitir varreduras de monitoramento de vulnerabilidade e conformidade e para coletar logs de eventos do sistema. O provedor de serviços pode apenas ativar o acesso remoto para seus próprios ativos. Os locatários têm controle sobre o acesso remoto de seus Ativos.
-	**Aplicativos e subaplicativos:** uma maneira lógica de agrupar ativos. Aplicativo de exemplo: SAP, Subaplicativos de exemplo: SAP Front End, SAP Middle Tier, SAP Back End.
-	**Locais:** os ativos são agrupados exclusivamente por Local, Provedor em nuvem e Repositório de ativos.
-	**Ambientes:** uma maneira de agrupar Ativos e Aplicativos. A cada ambiente é designado um fator de risco de 1 a 10. Esse fator é aplicado no cálculo de pontuação de risco. O Provedor de Serviços define os Ambientes
-	** Tarefas: **  usadas em RiskForesight para:
  -	Sincronizar periodicamente o Repositório de ativos com o RiskForesight.
  -	Executar Varreduras de Vulnerabilidade e Conformidade do SCAP.
  -	Coletar fluxos de rede e outras informações que usam varreduras do NSX.
  -	Coletar informações sobre o software executado em Ativos monitorados.
  -	Coletar eventos de syslog e do sistema para Ativos.
-	**Tipos de tarefa:** as tarefas a seguir são suportadas:
  -	**Varredura do VMware vCenter:** coleta ativos do vCenter.
	- **Varredura do VMware VCD:** coleta ativos do VCD.
  -	**Varredura do VMware NSX:** coleta informações de rede e fluxo de rede do NSX Manager.
  - **Varredura do SCAP:** esse tipo de varredura é usado para varrer cargas de trabalho para Conformidade e Risco cibernético. Essa varredura é baseada no SCAP (Security Content Automation Protocol). As liberações futuras são planejadas para suportar conteúdo customizado no formato OVAL.
  - **Varredura de software:** essa varredura coleta o inventário de software que está instalado na carga de trabalho de destino sob gerenciamento. Esse inventário fica, então, disponível para procura por meio da opção de procura na barra superior da IU.
  - **LogExtract:** essa varredura suporta a coleção de logs de cargas de trabalho do Windows e do Linux. Isso é usado para propósitos forenses e alimentados por meio de aprendizado de máquina para produzir informações úteis.
  - **Tarefa AMQP:** essa tarefa AMQP é usada para coletar eventos em tempo real do VCD para permitir a sincronização em tempo real. O RiskForesight consome eventos de inclusão, exclusão e atualização de Ativo e atua nesses eventos. Por exemplo, se um novo ativo for incluído e o RiskForesight receber essa notificação por meio do AMQP, ele atualizará imediatamente o banco de dados e iniciará a varredura de Conformidade e de Risco cibernético.
  - **Varredura de infraestrutura do VMware:** essa varredura realiza uma varredura de infraestrutura dos Ativos do VMware.
  -	**Varredura de vulnerabilidade do VMware:** essa varredura realiza uma varredura de Vulnerabilidade dos Ativos do VMware.
-	**Regime de conformidade:** disponível por meio de licença; NIST, NESA, PCI, ISO, HIPAA, GDPR, Customizada, FFIEC, FedRAMP Baixa, FedRAMP Moderada, FedRAMP Alta
-	**Gerente de política:** o Gerente de política entrega a função de criação de política para uma Organização com base na saída de aprendizado de máquina. O Caveonix fornece por padrão três tipos de tarefas de aprendizado de máquina por Organização. Essas tarefas não são editáveis e tarefas adicionais ainda não são suportadas. Atualmente, os tipos suportados de tarefas de aprendizado de máquina são:
  -	Logs de Caveo
  -	Redes Caveo
  -	Varredura do Caveo
-	**Anomalia:** com base nas anomalias localizadas nos dados, podemos configurar as políticas para agir com base nas condições definidas pelo usuário. É possível selecionar o tipo de tarefa e configurar condições booleanas para a pontuação de anomalia e definir a ação quando a condição é verdadeira. Por exemplo:
```
Tarefa: a pontuação de Anomalia de "Logs de Caveo" é > 90, então marque o ativo para quarentena e envie uma Notificação para o Canal slack.`
Tarefa: a pontuação de anomalia da "Caveo Network" é > 95, então coloque o ativo em quarentena e envie uma notificação
por e-mail e uma notificação de IU.
```

## Links relacionados
{: #caveonix-terminology-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
