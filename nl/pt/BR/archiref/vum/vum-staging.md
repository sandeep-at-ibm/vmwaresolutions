---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Temporariedade e remediação

As correções e extensões podem ser opcionalmente montadas antes da correção para assegurar que sejam transferidas por download do VUM para o host do vSphere ESXi sem aplicar as correções ou extensões imediatamente. Durante a correção, o VUM aplica as correções, as extensões e os upgrades aos objetos de inventário. Montar as correções e extensões acelera o processo de correção porque as correções e extensões já estão disponíveis localmente nos hosts.

Se, durante o processo de correção, qualquer host falhar ao entrar no modo de manutenção, o VUM relatará um erro e o processo de correção parará e falhará. Os hosts do vSphere ESXi que já foram corrigidos permanecem no nível atualizado.

Para que o processo de correção funcione sem problemas, é aconselhável desativar alguns dos recursos de cluster, como DPM, Controle de Admissão de HA, Tolerância a Falhas, bem como desconectar quaisquer dispositivos removíveis das máquinas virtuais para que o DRS não enfrente nenhum problema ao migrar VMs para outros hosts.
Além disso, ao executar o assistente de correção, é possível Gerar relatórios para verificar se não existem configurações inconsistentes presentes no nível de host/VM que possam fazer o processo de correção falhar.

1.	Usando o vSphere Web Client, selecione **Página inicial** > **Hosts e clusters**.
2.	Clique com o botão direito em um data center, cluster ou um host e clique em **Montar correções**.
3.	Na página Seleção de linha de base do assistente Montar, selecione as linhas de base de correção e extensão a serem montadas.
4.	Selecione os hosts em que as correções e extensões serão aplicadas e clique em **Avançar**. Se você selecionou para montar correções e extensões em um único host, ele será selecionado por padrão.
5.	Opcionalmente, cancele a seleção de correções e extensões para excluir da operação de montagem. Para procurar dentro da lista de correções e extensões, insira o texto na caixa de texto na caixa Filtro. Clique em **Avançar**.
6.	Revise a página Pronto para concluir e clique em **Concluir**.

O número de correções e extensões montadas para o host específico é exibido nas colunas Correções e Extensões na área de janela inferior da guia Update Manager. Depois que uma correção for concluída com êxito, todas as correções e extensões montadas, sejam instaladas ou não durante a correção, serão excluídas do host.
A correção é o processo no qual o VUM aplica correções, extensões e upgrades a hosts do vSphere ESXi, máquinas virtuais ou dispositivos virtuais após uma varredura ser concluída e torna os objetos selecionados compatíveis. É possível corrigir hosts únicos, máquinas virtuais ou dispositivos virtuais ou em uma pasta, um cluster ou um nível de data center. O VUM suporta a correção para os objetos de inventário a seguir usando correção manual ou correção planejada:
*	Hosts ESXi para correções, extensões e correção de upgrade.
*	Máquinas virtuais ligadas, suspensas ou desligadas e modelos para o VMware Tools e o upgrade de hardware de máquina virtual.
*	Dispositivos virtuais ligados que são criados com o VMware Studio 2.0 e mais recente para o upgrade de dispositivo virtual.

Se a atualização requerer, os hosts serão colocados no modo de manutenção antes da correção. O VCSA migra as máquinas virtuais para outros hosts dentro da instância do VCS antes que o host seja colocado no modo de manutenção.

## Para hosts em um cluster vSAN
Esteja ciente do comportamento a seguir para hosts que fazem parte de um cluster vSAN:
* O processo de correção do host pode levar uma quantia extensiva de tempo para ser concluída.
* Por design, somente um host de um cluster VSAN pode estar em um modo de manutenção a qualquer momento.
* O VUM corrige hosts que fazem parte de um cluster VSAN sequencialmente, mesmo se você configura a opção para corrigir os hosts em paralelo.
* Para qualquer máquina virtual no host que use uma política de armazenamento de VM com uma configuração para "Número de falhas a serem toleradas=0", o host pode ter atrasos incomuns ao entrar no modo de manutenção. O atraso ocorre porque o vSAN deve migrar os dados de máquina virtual de um disco para outro no cluster de armazenamento de dados vSAN e isso pode levar muitas horas. Uma solução alternativa é configurar o "Número de falhas a serem toleradas=1" para a política de armazenamento de VM, que resulta na criação de duas cópias dos arquivos de máquina virtual no armazenamento de dados vSAN.
* Para qualquer máquina virtual no host que use uma política de armazenamento de VM com uma configuração para "Número de falhas a serem toleradas=1", a VM se tornará não redundante quando o host entrar no modo de manutenção. Se isso não for aceitável, veja [Redundância de vSAN da máquina virtual](vum-vsan-redundancy.html).

Para corrigir hosts e clusters, siga estas etapas:
1.	Use o vSphere Web Client, selecione **Página inicial** > **Hosts e clusters**.
2.	No navegador de objeto de inventário, selecione um data center, um cluster ou um host, clique na guia **Update Manager** e clique em **Corrigir**. Se você selecionou um objeto contêiner, todos os hosts sob o objeto selecionado serão corrigidos. O assistente Remediar é aberto.
3.	Selecione **Linhas de base de correção** ou **Linhas de base de extensão** dependendo de que tipo de atualização você deseja executar no host. Na página Selecionar linha de base do assistente Corrigir, selecione o **grupo de linhas de base** e as **linhas de base** a serem aplicadas.
4.	Selecione os hosts de destino que você deseja corrigir e clique em **Avançar**. Se você escolheu corrigir um único host e não um objeto contêiner, o host será selecionado por padrão.
5.	Opcionalmente, na página **Correções e extensões**, cancele a seleção de correções ou extensões específicas para excluí-las do processo de correção e clique em **Avançar**.
6.	Opcionalmente, na página **Opções avançadas**, selecione a opção para planejar que a correção seja executada posteriormente e especifique um nome exclusivo e uma descrição opcional para a tarefa. O horário que você configura para a tarefa planejada é o horário no VCSA. Opcionalmente, selecione a opção para ignorar avisos sobre dispositivos não suportados no host ou o armazenamento de dados VMFS não mais suportado para continuar com a correção. Clique em **Avançar**.
7.	Na página **Opções de correção** do host, no menu suspenso **Estado da energia da VM**, é possível selecionar a mudança no estado da energia das máquinas virtuais e dispositivos virtuais que estão em execução nos hosts a serem corrigidos. Um host não pode entrar no modo de manutenção até que as máquinas virtuais no host sejam desligadas, suspensas ou migradas com o vMotion para outros hosts em um cluster DRS. Algumas atualizações requerem que um host entre no modo de manutenção antes da correção. As máquinas virtuais e os dispositivos não podem ser executados quando um host está no modo de manutenção. Para reduzir o tempo de inatividade de correção do host em detrimento da disponibilidade de máquina virtual, é possível escolher encerrar ou suspender máquinas virtuais e dispositivos virtuais antes da correção. Em um cluster DRS, se você não desligar as máquinas virtuais, a correção demorará mais, mas as máquinas virtuais estarão disponíveis durante todo o processo de correção porque elas são migradas com o vMotion para outros hosts. As seleções são as seguintes:

  - **Desligar máquinas virtuais** - desligue todas as máquinas virtuais e dispositivos virtuais antes da correção.
  - **Suspender máquinas virtuais** - suspenda todas as máquinas virtuais e dispositivos virtuais em execução antes da correção.
  - **Não mudar o estado da energia da VM** - deixe as máquinas virtuais e os dispositivos virtuais em seu estado da energia atual.

8.	Opcionalmente, selecione **Desativar quaisquer dispositivos de mídia removível conectados à máquina virtual no host**. O VUM não corrige hosts nos quais as máquinas virtuais têm unidades de CD, DVD ou disquete conectadas. Em ambientes em cluster, os dispositivos de mídia conectados poderão evitar o vMotion se o host de destino não tiver um dispositivo idêntico ou uma imagem ISO montada, o que, por sua vez, evita que o host de origem entre no modo de manutenção. Após a correção, o VUM reconectará os dispositivos de mídia removível se eles ainda estiverem disponíveis.
9.	Opcionalmente, selecione **Tentar novamente entrar no modo de manutenção no caso de falha**, especifique o número de novas tentativas e especifique o tempo de espera entre as novas tentativas. O VUM aguarda o período de atraso de nova tentativa e tenta novamente colocar o host no modo de manutenção tantas vezes quanto você indicar no campo Número de novas tentativas.
10.	Não há nenhum requisito em uma instância do VCS para marcar a caixa de seleção sob Configurações de correção do ESXi para permitir que o Update Manager corrija hosts ESXi inicializados pelo PXE ligados.
11.	Clique em **Avançar**.
12.	Se você corrigir hosts em um cluster, edite as opções de correção do cluster. A página **Opções de correção do cluster** está disponível somente quando você corrige clusters. As opções a seguir podem ser selecionadas:

*	**Desative o Distributed Power Management (DPM)** se ele estiver ativado para qualquer um dos clusters selecionados - o VUM não corrigirá os clusters com o DPM ativo. O DPM monitora o uso de recursos das máquinas virtuais em execução no cluster. Caso exista excesso de capacidade suficiente, o DPM recomenda mover as máquinas virtuais para outros hosts no cluster e colocar o host original no modo de espera para conservar a energia. Colocar hosts no modo de espera pode interromper a correção.
*	**Desative o controle de admissão de Alta Disponibilidade** se ele estiver ativado para qualquer um dos clusters selecionados - o VUM não corrigirá os clusters com o controle de admissão de HA ativo. O controle de admissão é uma política usada pelo VMware HA para assegurar a capacidade de failover em um cluster. Se o controle de admissão de HA estiver ativado durante a correção, as máquinas virtuais dentro de um cluster poderão não migrar com o vMotion.
*	**Desative a tolerância a falhas (FT)** se ela estiver ativada. Isso afeta todas as máquinas virtuais tolerantes a falhas nos clusters selecionados - se a FT estiver ativada para qualquer uma das máquinas virtuais em um host, o VUM não corrigirá esse host. Para que a FT seja ativada, os hosts nos quais as máquinas virtuais Primárias e Secundárias são executadas devem ser da mesma versão e devem ter as mesmas correções instaladas. Se você aplicar correções diferentes a esses hosts, a FT não poderá ser ativada novamente.
*	**Ative a correção paralela para os hosts nos clusters selecionados** - corrija os hosts em clusters de uma maneira paralela. Se a configuração não for selecionada, o VUM corrigirá os hosts em um cluster sequencialmente. É possível selecionar uma das opções a seguir para correção paralela:
    - É possível permitir que o VUM avalie continuamente o número máximo de hosts que ele pode corrigir simultaneamente sem interromper as configurações do DRS.
    - É possível especificar um limite do número de hosts corrigidos simultaneamente em cada cluster que você corrigir. Nota, o VUM corrige simultaneamente somente os hosts nos quais as máquinas virtuais são desligadas ou suspensas. É possível escolher desligar ou suspender as máquinas virtuais por meio do menu Estado da energia da VM na área de janela Opções do modo de manutenção na página Opções de correção do host. Por design, somente um host de um cluster vSAN pode estar em um modo de manutenção a qualquer momento. O VUM corrige hosts que fazem parte de um cluster vSAN sequencialmente, mesmo se você seleciona a opção para corrigi-los em paralelo.
*	**Migrar máquinas virtuais desligadas e suspensas para outros hosts no cluster**, se um host precisar entrar no modo de manutenção. O Update Manager migra as máquinas virtuais suspensas e desligadas de hosts que devem entrar no modo de manutenção para outros hosts no cluster. É possível escolher desligar ou suspender as máquinas virtuais antes da correção na área de janela **Configurações do modo de manutenção**.
13.	Na página Pronto para concluir, é possível, opcionalmente, clicar em **Pré-verificar a correção** para gerar um relatório de opções de correção de cluster e clicar em **OK**. Uma caixa de diálogo Relatório de opções de correção de cluster é aberta. É possível exportar esse relatório ou copiar as entradas para seu próprio registro e clicar e **Avançar**.
14.	Revise a página Pronto para concluir e clique em **Concluir**.

### Links relacionados

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções VMware no IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
