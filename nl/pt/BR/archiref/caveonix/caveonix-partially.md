---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Partidialmente distribuído
{: #caveonix-partially}

Após a conclusão da implementação automatizada, é possível ampliar manualmente aumentando a RAM e o disco na máquina virtual (MV) inicial e incluir três MVs de ampliação. O script de configuração do RiskForesight pode ser executado para permitir e configurar os componentes do aplicativo nas quatro MVs.

Esse modelo de implementação deve atender até 500 Ativos com até 30 dias de indexação de dados.

Selecione os próximos endereços IP disponíveis na sub-rede móvel privada do {{site.data.keyword.cloud}}. Configure nomes FQDN no ADDNS.

O dimensionamento das MVs são como a seguir:

Tabela 1. Parâmetros base

|Parâmetro	|Valor|
|---|---|
|Type	|Base|
|VM qty	|1|
|vCPU	|16|
|RAM	|64 GB|
|Disco	|1000 GB|
|OS	|CentOS 7|
|Componentes do Aplicativo Instalados	|UI, App, Plugins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Remote Collector|

Os detalhes de ampliação da MV são como a seguir:

Tabela 2. Parâmetros de Scale-out

| Parâmetro	| Valor |
|---|---|
| Type	| Scale-out |
| VM qty	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| Disk	| 4 TB |
| OS	| CentOS 7 |
| Componentes do Aplicativo Instalados	| Nós de dados (scale-out) |

Os detalhes da MV do Coletor remoto são mostrados na tabela a seguir.

Tabela 3. Parâmetros do coletor remoto

|Parâmetro	|Valor|
|---|---|
|VM qty	|Conforme requerido|
|vCPU	|8|
|RAM	|8 GB|
|Disk	|1 TB|
|OS	|CentOS 7|
|Componentes do Aplicativo Instalados	|Coletor Remoto|

## Links relacionados
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
