---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Implementação em uma única
{: #caveonix-allinone}

Uma implementação e uma configuração automatizadas de uma única máquina virtual (MV) que hospeda todos os componentes do aplicativo RiskForesight. Esse modelo de implementação é adequado para pequenas implementações, até 100 ativos com 7 a 30 dias de indexação. Os detalhes da MV "tudo em um" são mostrados na tabela a seguir:

Tabela 1. Parâmetros in-one

|Parâmetro	|Valor|
|---|---|
|Type	|Base|
|VM qty	|1|
|vCPU	|16|
|RAM	|32 GB|
|Disk	|80 GB|
|OS	|CentOS 7|
|Componentes do Aplicativo Instalados|	UI, App, Plugins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Index Datastore, Remote Collector|

Os detalhes adicionais da MV do Remote Collector são mostrados na tabela a seguir.

Tabela 2. Coletor remoto

|Parâmetro	|Valor|
|---|---|
|VM qty	|Conforme requerido|
|vCPU	|8|
|RAM	|8 GB|
|Disk	|1 TB|
|OS	|CentOS 7|
|Componentes do Aplicativo Instalados	|Coletor Remoto|

## Links relacionados
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
