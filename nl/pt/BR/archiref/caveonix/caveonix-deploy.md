---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modelos de implementação para o Caveonix RiskForesight
{: #caveonix-deploy}

Esta seção descreve os modelos de implementação para o Caveonix RiskForesight junto com o processo de instalação para instalar a solução.

Ao selecionar a opção {{site.data.keyword.vmwaresolutions_full}} RiskForesight, você não terá que seguir todas as etapas na implementação, pois as iniciais são automatizadas. No entanto, para obter um entendimento da implementação e da arquitetura completas, e para aqueles que desejam ampliar a solução após a implementação inicial, é necessário um entendimento detalhado.

A instalação do RiskForesight consiste nas etapas de alto nível a seguir:

1. [Planejamento inicial e pré-requisitos](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) - Entender e selecionar uma opção de implementação, configurar o DNS para fornecer a resolução do FQDN/IP para os componentes do aplicativo.
2. [Implementação da máquina virtual](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) - Implementar as MVs por meio de um modelo OVF. A MV instalou nela todos os componentes do aplicativo.
3. [Configuração do aplicativo](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) - Executar o script de configuração do Caveonix que configura o componente de aplicativo em cada uma das MVs.
4. [Configuração do aplicativo](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) - Configurar o Provedor de serviços e um Locatário ou uma Organização para que o aplicativo se torne acessível para os usuários.

A instalação automatizada provisiona uma MV e configura todos os componentes do aplicativo nessa MV.
{:note}

## Dimensionamento de implementação
{: #caveonix-deploy-sizing}

O dimensionamento da implementação é calculado usando os volumes a seguir.

Tabela 1. Volumes

|Tipo de dados	|Volume |
|---|---|
|Varreduras por dia	|1 |
|Dados de varredura (MB)	|20 |
|Dados de Log (MB)	|500 |
|Dados de Fluxo (MB)	|200 |
|Dados do Ativo (MB)	|46 |
|Armazenamento total por ativo por dia (MB)	|766 |
|Multiplicador de Replicação de	|2 |
|Armazenamento de índice total/ativo/dia (MB)	|1532 |

O Multiplicador de replicação de dados é configurado como 2, pois o Armazenamento de índice (Elastic Search) usa por padrão a replicação n + 1 dos índices.
{:note}

O número de MVs de ajuste de escala é calculado do número de Ativos e do número de dias de dados a serem indexados.

Tabela 2. Ajuste de escala de parâmetros da MV

|Número de ativos	|100	|500	|5000 |
|---|---|---|---|
|Dias de Dados	|30	|30	|30 |
|Armazenamento de índice total/ativo/dia (MB)	|1532	|1532	|1532 |
|Total de armazenamento de índice/Ativo/30 dias (TB)	|4	|22	|219 |
|Dados Suportados por Nó de Escalação (TB)	|0	|8	|8 |
|VMs de Escala Necessárias	|0	|3	|27 |

A quantia de armazenamento necessária é calculada como a seguir:

Tabela 3. Parâmetros de armazenamento

|Número de ativos	|100	|500	|5000 |
|---|---|---|---|
|Retenção de Dados de Longo Prazo (Meses)	|8	|8	|8 |
|Armazenamento total por ativo por dia (MB)	|766	|766	|766 |
|Dias de Dados	|30	|30	|30 |
|Retenção de Dados do Termo (TB) do Próximo Prazo	|7	|33	|329 |
|Retenção de Dados de Longo Prazo (TB)	|18	|88	|877 |

De uma perspectiva de dados, os dados são usados como a seguir:

-	Os dados de varredura são usados no Gerenciamento de conformidade
-	Os dados de log são usados no gerenciamento forense
-	Os dados de política e de fluxo são usados no gerenciamento de risco e os dados do fluxo estão disponíveis somente no NSX Manager

O Armazenamento de Dados possui três camadas:

-	Replicado
-	Termo do Near
-	Longo Prazo

A tabela a seguir fornece um resumo das implementações:

Tabela 4. Resumo

|Modelo de implementação	|"tudo em um"	|Parcialmente distribuída	|Totalmente distribuído |
|---|---|---|---|
|Número de Ativos	|100	|500	|5000 |
|Dados on-line gerados em 30 dias (TB)	|4	|22	|219 |
|Retenção de Dados Nearline (90 Dias) (TB)	|7	|33	|329 |
|Retenção de Dados Off-line (8 Meses) (TB)	|18	|88	|877 |
|Total de Retenção de armazenamento de dados (1 ano) (TB)	|28	|142	|1425 |
|MVs de base	|1	|1	|20 |
|Ajuste de escala de MVs	|0	|3	|28 |
|Total de MVs	|1	|4	|48 |

**Notas:**
Ao remover o serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, a automação do {{site.data.keyword.vmwaresolutions_short}} exclui apenas a única VM do Caveonix "tudo em um" que foi implementada e a sub-rede privada dedicada que foi pedida para ele. Portanto,
* Se você escalou a VM do Caveonix em múltiplas VMs, essas VMs adicionais não serão removidas. 
* Se você usou os endereços IP da sub-rede privada dedicada em VMs adicionais, essas VMs deverão ser designadas a novos endereços IP para continuarem a funcionar. 
* Se você excluir a instância A do servidor do vCenter com o serviço do Caveonix RiskForesight no {{site.data.keyword.cloud_notm}} instalado e você usou os endereços IP da sub-rede privada dedicada pedida para o serviço na instância B do servidor do vCenter, a sub-rede privada dedicada será cancelada na exclusão da instância A do servidor vCenter.

## Links relacionados
{: #caveonix-deploy-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
