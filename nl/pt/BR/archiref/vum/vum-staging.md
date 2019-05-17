---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-29"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Temporariedade e remediação
{: #vum-staging}

As correções e extensões podem ser opcionalmente montadas antes da correção para assegurar que sejam transferidas por download do VUM para o host do vSphere ESXi sem aplicar as correções ou extensões imediatamente. Durante a correção, o VUM aplica as correções, as extensões e os upgrades aos objetos de inventário. Montar as correções e extensões acelera o processo de correção porque as correções e extensões já estão disponíveis localmente nos hosts.

Se durante o processo de correção qualquer host falhar ao entrar no modo de manutenção, o VUM relatará um erro e o processo de correção parará e falhará. Os hosts vSphere ESXi que já estão corrigidos permanecem no nível atualizado.

Para que o processo de correção funcione normalmente, é aconselhável desativar alguns dos recursos de cluster, como DPM, Controle de Admissão de HA, Tolerância a Falhas, e desconectar quaisquer dispositivos removíveis das máquinas virtuais (MVs) para evitar problemas de DRS enquanto você migra MVs para outros hosts.
Além disso, enquanto você executa o assistente de correção, é possível Gerar relatórios para verificar se não há configurações inconsistentes presentes no nível de host/MV que podem fazer com que o processo de correção falhe.

1. Usando o vSphere Web Client, selecione **Página inicial** > **Hosts e clusters**.
2. Clique com o botão direito em um data center, cluster ou um host e clique em **Montar correções**.
3. Na página Seleção de linha de base do assistente Montar, selecione as linhas de base de correção e extensão a serem montadas.
4. Selecione os hosts em que as correções e extensões são aplicadas e clique em **Avançar**. Se você selecionou para montar correções e extensões em um único host, ele será selecionado por padrão.
5. Opcionalmente, limpe as correções e extensões a serem excluídas da operação de estágio. Para procurar dentro da lista de correções e extensões, insira o texto na caixa de texto na caixa Filtro. Clique em **Avançar**.
6. Revise a página **Pronto para concluir** e clique em **Concluir**.

O número de correções e extensões montadas para o host específico é exibido nas colunas Correções e Extensões na área de janela inferior da guia Update Manager. Depois que uma correção for concluída com êxito, todas as correções e extensões montadas, sejam instaladas ou não durante a correção, serão excluídas do host.
Correção é o processo no qual o VUM aplica correções, extensões e upgrades a hosts vSphere ESXi, MVs ou dispositivos virtuais após uma varredura ser concluída e torna os objetos selecionados compatíveis. É possível corrigir hosts, MVs ou dispositivos virtuais únicos ou em uma pasta, um cluster ou um nível de data center. O VUM suporta a correção para os objetos de inventário a seguir usando correção manual ou correção planejada:
* Hosts ESXi para correções, extensões e correção de upgrade.
* MVs e modelos ativados, suspensos ou desativados para o upgrade de hardware do VMware Tools e da MV.
* Dispositivos virtuais ligados que são criados com o VMware Studio 2.0 e mais recente para o upgrade de dispositivo virtual.

Se a atualização requerer, os hosts serão colocados no modo de manutenção antes da correção. O VCSA migra as MVs para outros hosts da instância do VMware vCenter Server on {{site.data.keyword.cloud}} antes de o host ser colocado no modo de manutenção.

## Para hosts em um cluster vSAN
{: #vum-staging-hosts-vsan}

Esteja ciente do comportamento a seguir para hosts que fazem parte de um cluster vSAN:
* O processo de correção do host pode levar uma quantia extensiva de tempo para ser concluída.
* Por design, somente um host de um cluster VSAN pode estar em um modo de manutenção a qualquer momento.
* O VUM corrige hosts que fazem parte de um cluster VSAN sequencialmente, mesmo se você configura a opção para corrigir os hosts em paralelo.
* Qualquer MV no host que use uma política de armazenamento da MV com uma configuração de 0 para **Número de falhas a serem toleradas**. Nesse caso, o host pode ter atrasos incomuns quando ele entra no modo de manutenção. O atraso ocorre porque o vSAN deve migrar os dados da MV de um disco para outro no cluster de armazenamento de dados do vSAN e isso pode levar muitas horas. É possível trabalhar em torno disso configurando **Número de falhas a serem toleradas** como 1 para a política de armazenamento da MV, que resulta na criação de duas cópias dos arquivos de MV no armazenamento de dados vSAN.
* Qualquer MV no host que use uma política de armazenamento da MV com uma configuração de 1 para **Número de falhas a serem toleradas**. Nesse caso, a MV se torna não redundante quando o host entra no modo de manutenção. Se isso não for aceitável, veja [Redundância de vSAN da máquina virtual](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-vsan-redundancy).

Para corrigir hosts e clusters, siga estas etapas:
1. Use o vSphere Web Client, selecione **Página inicial** > **Hosts e clusters**.
2. No navegador de objeto de inventário, selecione um data center, um cluster ou um host, clique na guia **Update Manager** e clique em **Corrigir**. Se você selecionou um objeto contêiner, todos os hosts sob o objeto selecionado serão corrigidos. O assistente Remediar é aberto.
3. Selecione **Linhas de base de correção** ou **Linhas de base de extensão** dependendo de que tipo de atualização você deseja executar no host. Na página Selecionar linha de base do assistente Corrigir, selecione o **grupo de linhas de base** e as **linhas de base** a serem aplicadas.
4. Selecione os hosts de destino que você deseja corrigir e clique em **Avançar**. Se você escolheu corrigir um único host e não um objeto de contêiner, o host será selecionado por padrão.
5. Opcionalmente, na página **Correções e extensões**, limpe as correções ou extensões específicas para excluí-las do processo de correção e clique em **Avançar**.
6. Opcionalmente, na página **Opções avançadas**, selecione a opção para planejar que a correção seja executada posteriormente e especifique um nome exclusivo e uma descrição opcional para a tarefa. O horário que você configura para a tarefa planejada é o horário no VCSA. Opcionalmente, selecione a opção para ignorar avisos sobre dispositivos não suportados no host ou o armazenamento de dados VMFS não mais suportado para continuar com a correção. Clique em **Avançar**.
7. Na página **Opções de correção** do host, no menu suspenso **Estado de energia da VM**, é possível selecionar a mudança no estado de energia das MVs e dispositivos virtuais que estão em execução nos hosts a serem corrigidos. Um host não pode entrar no modo de manutenção até que as MVs no host sejam desativadas, suspensas ou migradas com vMotion para outros hosts em um cluster do DRS. Algumas atualizações requerem que um host entre no modo de manutenção antes da correção. As MVs e os dispositivos não podem ser executados quando um host está no modo de manutenção. Para reduzir o tempo de inatividade de correção do host em detrimento da disponibilidade da MV, é possível optar por encerrar ou suspender MVs e dispositivos virtuais antes da correção. Em um cluster do DRS, se você não desativar as MVs, a correção demorará mais, mas elas ficarão disponíveis durante todo o processo de correção porque são migradas com vMotion para outros hosts. As seleções são as seguintes:

  * **Desativar máquinas virtuais** - Desative todas as MVs e os dispositivos virtuais antes da correção.
  * **Suspender máquinas virtuais** - Suspenda todas as MVs e dispositivos virtuais em execução antes da correção.
  * **Não mudar o estado de energia da VM** - Deixe as MVs e os dispositivos virtuais em seu estado de energia atual.

8. Opcionalmente, selecione **Desativar quaisquer dispositivos de mídia removível conectados à máquina virtual no host**. O VUM não corrige os hosts nos quais as MVs conectaram unidades de CD, de DVD ou de disquete. Em ambientes em cluster, os dispositivos de mídia conectados poderão evitar o vMotion se o host de destino não tiver um dispositivo idêntico ou uma imagem ISO montada, o que, por sua vez, evita que o host de origem entre no modo de manutenção. Após a correção, o VUM reconectará os dispositivos de mídia removível se eles ainda estiverem disponíveis.
9. Opcionalmente, selecione **Tentar novamente entrar no modo de manutenção no caso de falha**, especifique o número de novas tentativas e especifique o tempo de espera entre as novas tentativas. O VUM aguarda o período de atraso de nova tentativa e tenta novamente colocar o host no modo de manutenção tantas vezes quanto você indicar no campo Número de novas tentativas.

Não há nenhum requisito em uma instância do vCenter Server para marcar a caixa de seleção em Configurações de correção do ESXi para permitir que o Update Manager corrija hosts ESXi inicializados por PXE ativados.
10. Clique em **Avançar**.
11. Se você corrigir hosts em um cluster, edite as opções de correção do cluster. A página **Opções de correção do cluster** está disponível somente quando você corrige clusters. As opções a seguir podem ser selecionadas:
* **Desative o Distributed Power Management (DPM)** se ele estiver ativado para qualquer um dos clusters selecionados - o VUM não corrigirá os clusters com o DPM ativo. O DPM monitora o uso de recurso das MVs em execução no cluster. Se existir excesso de capacidade suficiente, o DPM recomendará a movimentação das MVs para outros hosts no cluster e a colocação do host original no modo de espera para conservar a energia. Colocar hosts no modo de espera pode interromper a correção.
* **Desative o controle de admissão de Alta Disponibilidade** se ele estiver ativado para qualquer um dos clusters selecionados - o VUM não corrigirá os clusters com o controle de admissão de HA ativo. O controle de admissão é uma política usada pelo VMware HA para assegurar a capacidade de failover em um cluster. Se o controle de admissão de HA estiver ativado durante a correção, as MVs de um cluster poderão não ser migradas com vMotion.
* **Desative a tolerância a falhas (FT)** se ela estiver ativada. Isso afeta todas as MVs tolerantes a falhas nos clusters selecionados. Se FT estiver ativado para qualquer uma das MVs em um host, o VUM não corrigirá esse host. Para que a FT seja ativada, os hosts nos quais as MVs primárias e secundárias são executadas devem ter a mesma versão e as mesmas correções instaladas. Se você aplicar correções diferentes a esses hosts, a FT não poderá ser ativada novamente.
* **Ative a correção paralela para os hosts nos clusters selecionados** - corrija os hosts em clusters de uma maneira paralela. Se a configuração não for selecionada, o VUM corrigirá os hosts em um cluster sequencialmente. É possível selecionar uma das opções a seguir para correção paralela:
  - É possível permitir que o VUM avalie continuamente o número máximo de hosts que ele pode corrigir simultaneamente sem interromper as configurações do DRS.
  - É possível especificar um limite do número de hosts corrigidos simultaneamente em cada cluster que você corrigir. Observe, o VUM corrige simultaneamente apenas os hosts nos quais as MVs estão desativadas ou suspensas. É possível optar por desativar ou suspender as MVs no menu Estado de energia da MV na área de janela Opções do modo de manutenção na página Opções de correção do host. Por design, somente um host de um cluster vSAN pode estar em um modo de manutenção a qualquer momento. O VUM corrige hosts que fazem parte de um cluster vSAN sequencialmente, mesmo se você seleciona a opção para corrigi-los em paralelo.
* **Migrar máquinas virtuais desligadas e suspensas para outros hosts no cluster**, se um host precisar entrar no modo de manutenção. O Update Manager migra as MVs suspensas e desativadas de hosts que devem entrar no modo de manutenção para outros hosts no cluster. É possível optar por desativar ou suspender as MVs antes da correção na área de janela **Configurações do modo de manutenção**.
12. Na página Pronto para concluir, é possível, opcionalmente, clicar em **Pré-verificar a correção** para gerar um relatório de opções de correção de cluster e clicar em **OK**. Uma caixa de diálogo Relatório de opções de correção de cluster é aberta. É possível exportar esse relatório ou copiar as entradas para seu próprio registro e clicar e **Avançar**.
13. Revise a página **Pronto para concluir** e clique em **Concluir**.

## Links relacionados
{: #vum-staging-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demonstrações)
