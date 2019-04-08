---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# Etapa 1 - Planejamento inicial e pré-requisitos
{: #caveonix-step1}

Cada componente do aplicativo Caveonix RiskForesight é fracamente acoplado, mas gerenciado centralmente. Portanto, podem ser implementados em um padrão de implementação de máquina virtual (MV) "tudo em um" ou os componentes do aplicativo podem ter a capacidade aumentada e ser implementados em múltiplas MVs para maior disponibilidade, desempenho e capacidade.

Os padrões de implementação baseiam-se nos requisitos de disponibilidade e no dimensionamento para retenção de dados. Os nós de implementação do RiskForesight podem ser caracterizados como:

-	MVs de base - As MVs de base hospedam os componentes de aplicativo que não são escalados devido à retenção de dados. Esses componentes são: IU do RiskForesight, App do RiskForesight, Plug-ins do RiskForesight, Central Collector, Remote Collector, Index Datastore, Messaging Datastore e Relational Datastore.
-	MVs de ampliação - As MVs de ampliação, o banco de dados e o índice de dados são escalados de acordo com o número de Ativos e a retenção de dados necessária que cria demanda para mais espaço em disco rígido de ampliação e, portanto, mais MVs de ampliação.

Há três modelos de implementação do Caveonix RiskForesight:

-	"Tudo em um" - Uma implementação e uma configuração automatizadas de 1 MV que hospeda todos os componentes do aplicativo:
  - Todos os componentes do aplicativo instalados em uma MV.
  - Coletores remotos podem ser instalados em MVs separadas.
  - Pequenas implementações - até 100 ativos com 7 a 30 dias de indexação.
-	Parcial distribuído - Após a conclusão da implementação automatizada, é possível ampliar manualmente aumentando a RAM e o disco na MV inicial e incluir três MVs de ampliação.
  - IU, App, Plug-ins, Central Collector, Remote Collector, Index Datastore, Messaging Datastore e Relational Datastore implementados em uma MV.
  - Coletores remotos instalados em MVs separadas.
  -	Nós de dados de índice implementados em MVs separadas.
  -	Implementações pequenas a médias - até 500 ativos com 30 dias de indexação.
- Totalmente distribuído - Incluir mais MVs de base e MVs de ampliação de acordo com o número de ativos e requisitos de retenção de dados:
  - Componentes de aplicativo distribuídos em MVs separadas para facilitar o ajuste de escala.
  -	Padrão de implementação necessário, conforme o número de ativos aumenta no intervalo de 500 a 100.000.
  -	Coletores remotos instalados em MVs separadas.
  -	UI em múltiplas MVs.
  -	App e Plugins em múltiplas MVs.
  -	Coletor central configurado em um Cluster.
  -	Relational Datastore implementado em um modelo Primário/Secundário.
  -	Armazenamento de dados do sistema de mensagens implementado em um cluster.
  -	Index Datastore que é implementado com os Nós principal e de dados.
  -	Mais Nós de dados que são usados para Ampliação, conforme o número de ativos aumenta.

Todos os componentes devem ter um FQDN e serem registrados no DNS antes de qualquer implementação da MV. Essa etapa é concluída pela automação do IBM Cloud for VMware Solutions para a implementação inicial "tudo em um", mas é de sua responsabilidade ao fazer o ajuste de escala da implementação.

## Links relacionados
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
