---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# Introdução
{: #opsprocs-intro}

Muitas organizações de TI documentem seus procedimentos operacionais em um runbook. Um runbook é um conjunto de documentos, referências e procedimentos padronizados que explicam tarefas comuns e recorrentes de TI. A equipe de TI consulta o runbook para realizar o trabalho de maneira ideal. Os runbooks melhoram a eficiência organizacional por meio da padronização e auxiliam na integração mais efetiva de funcionários. Há geralmente dois tipos de runbook:

1. Documentação geral usada para capturar procedimentos, guias e tarefas. Tendem a ser gerais por natureza e se referem à documentação existente fornecida pelos fornecedores.
2. Documentação especializada escrita para a empresa. Essa documentação é específica para um sistema, aplicativo ou conjunto de aplicativos e não é coberta pela documentação dos fornecedores. Ao realizar sua documentação especializada, aconselhamos a seguinte estrutura:

 * Visão geral - Uma visão geral do serviço com seções que descrevem:
    * Qual é o serviço e por que ele é necessário para a empresa?
    * Quem são os principais contatos para o serviço?
    * Para quem relatar problemas com o serviço?
 * Construção - Essa seção está focada principalmente nas equipes de desenvolvimento, nos principais componentes de software do serviço e na maneira como o serviço será construído. Informações sobre produtos de software, locais de OVAs, mídia de distribuição ou o local do código-fonte. As etapas necessárias para empacotar ou distribuir a liberação. Ela inclui quaisquer instruções de introdução necessárias para um novo desenvolvedor.
 * Implementação - Essa seção está focada principalmente na equipe de operações e na implementação do software. Ela inclui detalhes da infraestrutura de hardware e virtualizada e da construção das máquinas virtuais (VMs), incluindo vCPU, requisitos de RAM e de disco, versão e configuração do sistema operacional e qual middleware ou pacote instalar.
 * Procedimentos - Instruções detalhadas para tarefas comuns, como inclusão, mudança e exclusão, problemas comuns e suas soluções e aviso de resolução de problemas.
 * Resolução de problemas - Uma lista de alertas comuns do sistema de monitoramento, incluindo tarefas passo a passo para esses alertas e orientação genérica sobre a resolução de problemas do serviço.
 * Planos e procedimentos de recuperação de desastre - Detalhes sobre como recuperar o serviço em outro local devido a um desastre no local primário.
 * Acordo de nível de serviço - Os parâmetros de serviço acordados, como acordos de nível operacional, indicadores de ponto principais, objetivos de disponibilidade, objetivos do ponto de recuperação e objetivo de tempo de recuperação.

A maioria das organizações de TI tem diversos runbooks que atuam como seus manuais de referência. Esta série de documentações foi projetada para uso como um runbook geral para sua organização, consumindo instâncias do vCenter Server. Embora o conteúdo de cada runbook seja específico para as necessidades da organização, a metodologia de criação de runbook é bastante padrão por meio de dois estágios:

1. O primeiro estágio é decidir quais procedimentos precisam ser documentados e, quando listados, documentar cada um com detalhes suficientes.
2. O segundo estágio é contínuo e consiste em manter, atualizar e corrigir esses procedimentos, incluindo novos e retirando os que não são mais necessários.

O {{site.data.keyword.vmwaresolutions_full}} permite utilizar as qualificações, os conjuntos de ferramentas e os runbooks locais existentes da sua equipe para gerenciar suas instâncias no {{site.data.keyword.cloud_notm}}. No entanto, criamos a documentação geral a seguir para capturar procedimentos, guias e tarefas comuns:

* Tarefas de configuração - Essas tarefas são atividades comuns que os administradores de sistemas precisam executar para customizar o ambiente às necessidades da empresa e responder a solicitações de serviço, como a inclusão de novas VMs e o aumento da capacidade. Essas tarefas são agrupadas na estrutura a seguir:
 * Orientação genérica
 * Procedimentos de VM
 * Procedimentos do vCenter
 * Procedimentos de host do vSphere ESXi
 * Procedimentos de armazenamento
 * Procedimentos de rede
* Alarmes - O vSphere inclui um subsistema de eventos e alarmes que rastreia eventos que ocorrem no ambiente do vSphere e disponibiliza essas informações no vCenter. Essa seção descreve esse subsistema e como ativar e usar os alarmes em sua empresa.
* Verificações diárias proativas - Essas verificações permitem que os administradores do sistema mantenham o ambiente funcional. Quando realizadas diariamente, evitam que muitos problemas comuns relacionados à capacidade e ao desempenho impactem suas cargas de trabalho.
* Resolução de problemas - Mesmo realizando verificações diárias proativas, problemas que afetam suas cargas de trabalho podem ocorrer, portanto, é necessário corrigir o problema subjacente o mais rápido possível. Esses guias de resolução de problemas e alguns cenários de resolução de problemas comuns ajudam os administradores de sistema a identificar e corrigir esses problemas rapidamente.
* Conformidade - O guia de conformidade fornece alguns insights sobre a manutenção da conformidade do ambiente com relação a um regime de conformidade regulamentar ou melhor prática do mercado. O foco desse guia está no guia de reforço do VMware, que é uma variedade de listas documentadas de melhores práticas para um ambiente do VMware.

Muitas das tarefas acima são automatizadas no Operations Management on {{site.data.keyword.cloud_notm}}, e, para as tarefas que não são, esse conjunto de ferramentas facilita muito os processos manuais para os administradores de sistemas. É necessário monitorar os principais componentes do ambiente do VMware e isso é realizado no Operations Management on {{site.data.keyword.cloud_notm}} conforme a seguir:

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

É possível que você tenha um conjunto de ferramentas corporativo local que possa ser utilizado para monitorar e gerenciar sua instância do vCenter Server. A Tabela 1 descreve os principais componentes do ambiente do vCenter Server, por que eles precisam ser monitorados e como isso é feito por meio do Operations Management on {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte a documentação da arquitetura de referência.

Tabela 1. Principais componentes do ambiente do vCenter Server

| Componente | Por que | Monitorado por  |
|---|---|---|
| vCenter | O vCenter é o componente de gerenciamento de infraestrutura que gerencia os hosts do vSphere e construções virtualizadas, como clusters. O vSAN é monitorado por meio do vCenter. A rede do vSphere, como os comutadores distribuídos e os grupos de portas, é monitorada por meio do vCenter. | O vRealize Operations Manager (vROps) e o VMware SDDC Health Management Pack. O vRealize Log Insights (vRLI) coleta os dados de log do vCenter, que são compreendidos pelo Content Pack for vSphere que envia alertas para o vROPs. |
| Hosts do vSphere | Os hosts do vSphere fornecem a CPU virtualizada, a RAM e a rede às VMs de cálculo. | vROps via vCenter. O vRLI coleta os dados de log |
| vSAN | O vSAN fornece um armazenamento de dados consolidando o armazenamento nos hosts para uso pelas VMs. Os problemas que afetam a capacidade e o desempenho têm efeito sobre os aplicativos em execução nessas VMs. |O vROps e o Management Pack for vSAN fornecem painéis adicionais para auxiliar no monitoramento do vSAN. As Verificações de Funcionamento do vCenter vSAN são coletadas por meio do vROps. O vRLI coleta os dados de log do vCenter. |
| NSX | O NSX fornece os componentes de rede virtualizados que são utilizados pelas VMs de cálculo, portanto, quaisquer falhas da rede podem impactar os aplicativos em execução nessas VMs. | O vROps e o vROps Management Pack for VMware NSX fornecem visibilidade sobre a topologia de rede. O vRLI coleta os dados de log dos componentes do NSX, como Controladores, ESG e comutadores lógicos. O vRealize Network Insight (vRNI) fornece uma resolução de problemas de rede detalhada. |

Além do monitoramento, o Operations Management on {{site.data.keyword.cloud_notm}} fornece assistência com configuração, conformidade e muitas outras tarefas proativas detalhadas nessa documentação.


## Links relacionados
{: #opsprocs-intro-links}

* [Monitoramento do vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [Guia de reforço de segurança do VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Gerenciamento de operações no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
