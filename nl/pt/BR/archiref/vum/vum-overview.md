---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Visão geral do VMware Update Manager
{: #vum-overview}

O VMware Update Manager (VUM) usa um processo multiestágio para fazer upgrade de objetos do vSphere e aplicar correções ou extensões. Esse processo permite um procedimento de atualização suave com um mínimo de tempo de inatividade do sistema. Antes de olharmos para este processo, precisamos entender os termos a seguir:
* **Objeto de inventário** - um objeto no vCenter, como uma máquina virtual, dispositivos virtuais ou um host vSphere ESXi.
* **Linha de base** - as linhas de base contêm uma coleção de uma ou mais correções, extensões, service packs, correções de bug ou upgrades e podem ser classificadas como linhas de base de correção, extensão ou upgrade. Há duas classificações de linhas de base: Host e MV/VA e ambas têm linhas de base predefinidas pelo VMware e as Customizadas podem ser incluídas conforme necessário:
  - Linhas de Base de Hosts predefinidas:
    - Correções Críticas do Host
    - Patches de Host Não Crítico

  - Linha de base MVs/VAs predefinida:
    - Upgrade de VA para Mais Recente
    - Upgrade de hardware da MV para corresponder ao host
    - Upgrade do VMware Tools para corresponder ao host

* **Grupo de linhas de base** - um conjunto de linhas de base não conflitantes, que combina diferentes tipos de linhas de base e varre e corrige um objeto de inventário com relação a elas como um todo. Se um grupo de linhas de base contiver linhas de base de upgrade e correção ou extensão, o upgrade será executado primeiro.
* **Varredura** - a varredura é o processo no qual o objeto ou objetos de Inventário são avaliados com relação à linha de base ou ao grupo de linhas de base.
* **Preparação** - a preparação assegura que as correções e extensões sejam transferidas por download para os hosts vSphere ESXi antes da correção e é uma etapa opcional para minimizar o tempo que os hosts estão no modo de manutenção.
* **Correção** - a correção é o processo no qual o VUM aplica correções, extensões e upgrades ao objeto ou objetos de inventário.

Portanto, o processo do VUM é o seguinte:
* Um objeto ou um grupo de objetos de inventário são varridos para conformidade com relação a uma linha de base ou um grupo de linhas de base.
* Após uma revisão, as correções e as extensões podem ser opcionalmente montadas, antes de serem corrigidas.

O download de upgrades, correções de host, extensões e metadados relacionados é um processo automático predefinido que pode ser modificado. Por padrão, em intervalos configuráveis regulares, o VUM contata o VMware ou as origens de terceiros para reunir o seguinte sobre upgrades, correções ou extensões disponíveis:

* Metadados sobre todas as correções do ESXi 5.5 e ESXi 6.x, independentemente de você ter hosts de tais versões em seu ambiente.
* Metadados sobre correções do ESXi 5.5 e do ESXi 6.x e sobre extensões de endereços de URL de fornecedor de terceiros.
* Notificações, alertas e rechamadas de correção para hosts ESXi 5.5 e ESXi 6.x.
* Metadados sobre upgrades para dispositivos virtuais.

O VUM suporta a rechamada de correções para hosts que estão executando o ESXi 5.0 ou mais recente. Uma correção será rechamada se a correção liberada tiver problemas ou potenciais problemas. Depois de varrer os hosts em sua instância do VMware vCenter Server on {{site.data.keyword.cloud}}, o VUM alertará você se a correção rechamada estiver instalada em um determinado host. As correções rechamadas não podem ser instaladas em hosts com o VUM. O VUM também exclui todas as correções rechamadas do repositório de correção. Após uma correção do problema ser liberada, o VUM faz download da nova correção para seu repositório de correções. Se você tiver instalado a correção problemática, o VUM notificará que uma correção foi liberada e solicitará que aplique a nova correção.

A interface do cliente VUM fornece duas visualizações principais:
*	Visualização de Administração
*	Visualização de conformidade

##	Visualização de Administração
{: #vum-overview-admin-view}

A visualização de administração é acessada navegando para **Página inicial** > **Update Manager** e selecionando o endereço IP da instância do Update Manager. Na visualização Administração, é possível executar as tarefas a seguir:
*	Configure as configurações do Update Manager
*	Criar e gerenciar linhas de base e grupos de linhas de base
*	Visualizar eventos do Update Manager
*	Revisar o repositório de correção e os upgrades de dispositivo virtual disponíveis
*	Revisar e Verificar Notificações
*	Importar imagens do ESXi

##	Visualização de conformidade
{: #vum-overview-compliance-view}

A visualização de conformidade de um objeto de inventário selecionado é acessada navegando para **Hosts e clusters** ou **MVs e modelos** e clicando na **guia Update Manager**. Na visualização Conformidade do Update Manager, é possível executar as tarefas a seguir:
*	Visualizar a conformidade e varrer os resultados para cada objeto de inventário selecionado
*	Anexar e remover linhas de base e grupos de linhas de base de um objeto de inventário selecionado
*	Varrer um objeto de inventário selecionado
*	Correções de estágio ou extensões para hosts
*	Remediar um objeto de inventário selecionado

## Links relacionados
{: #vum-overview-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrações)
