---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# Introdução aos procedimentos operacionais
{: #opsprocs-intro}

Muitas organizações de TI documentem seus procedimentos operacionais em um runbook. Um runbook é um conjunto de documentos, referências e procedimentos padronizados que explicam tarefas comuns e recorrentes de TI. A equipe de TI consulta o runbook para realizar o trabalho de maneira ideal. Os Runbooks melhoram a eficiência organizacional por meio da padronização e ajudam na integração mais eficaz dos funcionários. Há geralmente dois tipos de runbook:

1. Documentação geral usada para capturar procedimentos, guias e tarefas. Tendem a ser gerais por natureza e se referem à documentação existente fornecida pelos fornecedores.
2. Documentação especializada escrita para a empresa. Essa documentação é específica para um sistema, um aplicativo ou um conjunto de aplicativos e não é coberta pela documentação dos fornecedores. Ao documentar sua documentação especializada, a estrutura a seguir é recomendada:

 * Visão geral - Uma visão geral do serviço com seções que descrevem:
    * Qual é o serviço e por que ele é necessário para a empresa?
    * Quem são os principais contatos para o serviço?
    * Para quem relatar problemas com o serviço?
 * Construção - Essa seção se concentra nas equipes de desenvolvimento e nos principais componentes de software do serviço e como o serviço é construído. Informações sobre produtos de software, locais de OVAs, mídia de distribuição ou o local do código-fonte. As etapas necessárias para empacotar ou distribuir a liberação. Ela inclui quaisquer instruções de introdução necessárias para um novo desenvolvedor.
 * Implementação - Essa seção se concentra na equipe de operações e em como implementar o software. Inclui detalhes do hardware e da infraestrutura virtualizada e como construir as máquinas virtuais (VMs), incluindo: requisitos de vCPU, de RAM e de disco, versão e configuração do S.O., qual middleware ou pacotes instalar.
 * Procedimentos - Instruções passo a passo para tarefas comuns, como: incluir, mudar e excluir, problemas comuns e suas soluções, conselho de resolução de problemas.
 * Resolução de problemas - Uma lista de alertas comuns do sistema de monitoramento, incluindo tarefas passo a passo para esses alertas e orientação genérica sobre a resolução de problemas do serviço.
 * Planos e procedimentos de recuperação de desastre - Detalhes sobre como recuperar o serviço em outro local devido a um desastre no local primário.
 * Acordo de nível de serviço - Os parâmetros de serviço acordados, como acordos de nível operacional, indicadores de ponto principais, objetivos de disponibilidade, objetivos do ponto de recuperação e objetivo de tempo de recuperação.

A maioria das organizações de TI tem diversos runbooks que atuam como seus manuais de referência. Esta série de documentações foi projetada para uso como um runbook geral para sua organização, consumindo instâncias do vCenter Server. Embora o conteúdo de cada runbook seja específico para as necessidades da organização, a metodologia de criação de runbook é bastante padrão por meio de dois estágios:

1. O primeiro estágio é decidir quais procedimentos precisam ser documentados e, quando listados, documentar cada um com detalhes suficientes.
2. O segundo estágio é contínuo e consiste em manter, atualizar e corrigir esses procedimentos, incluindo novos procedimentos e retirando procedimentos que não são mais necessários.

O {{site.data.keyword.vmwaresolutions_full}} permite que você use qualificações, conjuntos de ferramentas e runbooks existentes da equipe que você tem no local para gerenciar suas instâncias no {{site.data.keyword.cloud_notm}}.

A lista a seguir contém os procedimentos, guias e tarefas mais comuns:
* Tarefas de configuração - Essas tarefas são atividades comuns que os administradores de sistema precisam executar para customizar o ambiente de acordo com as necessidades da empresa e responder a solicitações de serviço, como: incluir novas VMs e aumentar a capacidade. Essas tarefas são agrupadas na estrutura a seguir:
 * Orientação genérica
 * Procedimentos de VM
 * Procedimentos do vCenter
 * Procedimentos de host do vSphere ESXi
 * Procedimentos de armazenamento
 * Procedimentos de rede
* Alarmes - O vSphere inclui um subsistema de eventos e alarmes que rastreia eventos que ocorrem no ambiente do vSphere e disponibiliza essas informações no vCenter. Essa seção descreve esse subsistema e como ativar e usar os alarmes em sua empresa.
* Verificações diárias proativas - Essas verificações permitem que os administradores do sistema mantenham o ambiente funcional. Quando realizada diariamente, ela deve evitar muitos problemas comuns relacionados à capacidade e ao desempenho de afetar suas cargas de trabalho.
* Resolução de problemas - Mesmo ao realizar verificações diárias proativas, ocorrem problemas que afetam suas cargas de trabalho. Portanto, é necessário corrigir o problema subjacente o mais rápido possível. Esses guias de resolução de problemas e alguns cenários de resolução de problemas comuns ajudam os administradores de sistema a identificar e corrigir esses problemas rapidamente.
* Conformidade - O guia de conformidade fornece alguns insights sobre a manutenção da conformidade do ambiente com relação a um regime de conformidade regulamentar ou melhor prática do mercado. O foco desse guia está no guia de reforço do VMware, que é uma variedade de listas documentadas de melhores práticas para um ambiente do VMware.

Muitas das tarefas anteriores são automatizadas no Operations Management on {{site.data.keyword.cloud_notm}} e, para as tarefas que não são, essas ferramentas tornam os processos manuais mais fáceis para os administradores de sistema. É necessário monitorar os principais componentes do ambiente do VMware e isso é realizado no Operations Management on {{site.data.keyword.cloud_notm}} conforme a seguir:

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

É possível ter ferramentas corporativas em vigor que podem ser usadas para monitorar e gerenciar a instância do vCenter Server. A Tabela 1 descreve os principais componentes do ambiente do vCenter Server, por que precisam ser monitorados e como são monitorados usando o Operations Management on {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte a documentação da arquitetura de referência.

Tabela 1. Principais componentes do ambiente do vCenter Server

| Componente | Por que | Monitorado por  |
|---|---|---|
| vCenter | O vCenter é o componente de gerenciamento de infraestrutura que gerencia os hosts do vSphere e construções virtualizadas, como clusters. O vSAN é monitorado por meio do vCenter. A rede do vSphere, como os comutadores distribuídos e os grupos de portas, é monitorada por meio do vCenter. | O vRealize Operations Manager (vROps) e o VMware SDDC Health Management Pack. O vRealize Log Insights (vRLI) coleta os dados de log do vCenter, que são compreendidos pelo Content Pack for vSphere que envia alertas para o vROPs. |
| Hosts do vSphere | Os hosts do vSphere fornecem CPU virtualizada, RAM e rede para as VMs de cálculo. | vROps via vCenter. O vRLI coleta os dados de log |
| vSAN | O vSAN fornece um armazenamento de dados consolidando o armazenamento nos hosts para uso pelas VMs. Os problemas que afetam a capacidade e o desempenho têm efeito sobre os aplicativos em execução nessas VMs. |O vROps e o Management Pack for vSAN fornecem painéis adicionais para auxiliar no monitoramento do vSAN. As Verificações de Funcionamento do vCenter vSAN são coletadas por meio do vROps. O vRLI coleta os dados de log do vCenter. |
| NSX | O NSX fornece os componentes de rede virtualizados usados pelas VMs de cálculo; quaisquer falhas da rede podem afetar os aplicativos em execução nessas VMs. | O vROps e o vROps Management Pack for VMware NSX fornecem visibilidade sobre a topologia de rede. O vRLI coleta os dados do log por meio dos componentes NSX, como Controladores, ESG e comutadores lógicos. O vRealize Network Insight (vRNI) fornece uma resolução de problemas de rede detalhada. |

Além do monitoramento, o Operations Management on {{site.data.keyword.cloud_notm}} ajuda com a configuração, a conformidade e muitas das tarefas proativas detalhadas nesta documentação.


## Links relacionados
{: #opsprocs-intro-links}

* [Monitoramento do vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [Guia de reforço de segurança do VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Gerenciamento de operações no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
