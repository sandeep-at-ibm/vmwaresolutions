---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# Totalmente distribuído
{: #caveonix-fully}

Máquinas virtuais (MVs) de base e MVs de ampliação adicionais são incluídas de acordo com o número de ativos e requisitos de retenção de dados.

Tabela 1. Interface do usuário base

|Parâmetro	|Valor|
|---|---|
|Type	|Base|
|VM qty	|2|
|vCPU	|2|
|RAM	|6 GB|
|Disk	|60 GB|
|OS	|CentOS 7|
|Componentes do Aplicativo Instalados	|UI|

Tabela 2. Base - aplicativos e plug-ins

|Parâmetro	|Valor|
|---|---|
|Type	|Base|
|VM qty	|2|
|vCPU	|8|
|RAM	|16 GB|
|Disk	|500 GB|
|OS	|CentOS 7|
|Componentes do Aplicativo Instalados	|App, Plug-ins|

Tabela 3. Base-coletor central

|Parâmetro	|Valor |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|500 GB |
|OS	|CentOS 7 |
|Componentes do Aplicativo Instalados	|Coletor Central (Cluster) |

Tabela 4. Base - banco de dados relacional

|Parâmetro	|Valor |
|---|---|
|Type	|Base |
|VM qty	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	C|entOS 7 |
|Componentes do Aplicativo Instalados	|Armazenamento de Dados Relacional (Primário / Secundário) |

Tabela 5. Armazenamento de dados do sistema de mensagens base

|Parâmetro	|Valor |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Componentes do Aplicativo Instalados	|Armazenamento de dados do sistema de mensagens (Cluster) |

Tabela 6. Base - Index Datastore (nós principais)

|Parâmetro	|Valor |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Componentes do Aplicativo Instalados	|Armazenamento de Dados de Índice (Nós principais) |

Tabela 7. Banco de dados - Index Datastore (nós de dados)

|Parâmetro	|Valor |
|---|---|
|Type	|Base |
|VM qty	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|4 TB |
|OS	|CentOS 7 |
|Componentes do Aplicativo Instalados	|Armazenamento de Dados de Índice (Nós de Dados) |

Os detalhes da MV de ampliação são descritos na tabela a seguir.

Tabela 8. Escalar nós de dados

|Parâmetro	|Valor |
|---|---|
|Type	|Scale-out |
|VM qty	28 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|4 TB |
|OS	|CentOS 7 |
|Componentes do Aplicativo Instalados	|Nós de dados (scale-out) |

Os detalhes da MV do Coletor remoto são mostrados na tabela a seguir.

Tabela 9. Coletor remoto

|Parâmetro	|Valor |
|---|---|
|VM qty	|Conforme requerido |
|vCPU	|8 |
|RAM	|8 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Componentes do Aplicativo Instalados	|Coletor Remoto |

## Links Relacionados
{: #caveonix-fully-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
