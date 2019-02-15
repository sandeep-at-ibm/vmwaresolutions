---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-19"

---

# Varrendo e revisando

Ao varrer hosts, máquinas virtuais (MVs) e dispositivos virtuais, você os avalia com relação a linhas de base e grupos de linha de base para determinar seu nível de conformidade. Os objetos de Inventário são varridos e os resultados são revisados para determinar como eles obedecem às linhas de base e aos grupos de linhas de base. Os resultados da varredura podem ser filtrados por procura de texto, seleção de grupo, seleção de linha de base e seleção de status de conformidade. É possível iniciar as varreduras a seguir:
*	**Iniciar manualmente uma varredura de hosts vSphere ESXi** - é possível varrer hosts vSphere ESXi no inventário do vSphere com relação a linhas de base e grupos de linhas de base anexados.
*	**Iniciar manualmente uma varredura de máquinas virtuais e dispositivos virtuais** - É possível varrer MVs e dispositivos virtuais no inventário do vSphere com relação a linhas de base e grupos de linha de base anexados.
*	**Iniciar manualmente uma varredura de um objeto contêiner** - Inicie uma varredura simultânea de hosts, MVs e dispositivos virtuais, varrendo um objeto contêiner que é um data center ou uma pasta do data center.
*	**Planejar uma varredura** - É possível configurar o vSphere Web Client para varrer MVs, dispositivos virtuais e hosts ESXi em horários específicos ou em intervalos convenientes para você.

## Iniciando manualmente uma varredura de hosts vSphere ESXi

1. Clique em **Varrer para atualizações**, selecione **Correções e extensões e upgrades**, em seguida, clique em **OK**.
2. Quando a varredura for concluída, selecione **Correções críticas do host**. Na área de janela inferior, revise os detalhes da correção para cada host clicando no número em **Número de correções**. Uma janela mostra as informações de correção.
3. Revise e repita para  ** Correções não Críticas **.

  Os arquivos de log do VUM estão localizados no caminho a seguir: _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

## Iniciando manualmente uma varredura de máquinas virtuais e dispositivos virtuais

É possível varrer MVs e dispositivos virtuais no inventário do vSphere com relação a linhas de base e grupos de linha de base anexados. As MVs e os dispositivos selecionados são varridos com relação a linhas de base anexadas, dependendo das opções selecionadas. Todos os objetos-filhos são varridos, portanto, quanto maior a infraestrutura virtual e quanto mais alto na hierarquia de objeto em que você inicia a varredura, mais tempo a varredura leva e mais precisa é a visualização de conformidade.

1.	Usando o vSphere Web Client, selecione **Página inicial** > **MVs e modelos**.
2.	Clique com o botão direito em uma _máquina virtual_, em um _dispositivo virtual_ ou em uma _pasta de máquinas virtuais e dispositivos_ e clique em **Varrer atualizações**.
3.	Selecione os tipos de atualizações a serem varridas. As opções são _Upgrades do dispositivo virtual, upgrades de hardware da MV_ e _Upgrades das ferramentas do VMware_.
4.	Clique em  ** Varrer **.

##	Iniciando manualmente uma varredura de um objeto de contêiner

Inicie uma varredura simultânea de hosts, MVs e dispositivos virtuais, varrendo um objeto contêiner que é um data center ou uma pasta de data center.
1.	Usando o vSphere Web Client, selecione **Página inicial** > **MVs e modelos**.
2.	Clique com o botão direito em _data center_ ou _pasta do data center_ e clique em **Varrer atualizações**.
3.	Selecione os tipos de atualizações a serem varridas. As opções são _Upgrades do dispositivo virtual, upgrades de hardware da MV_ e _Upgrades das ferramentas do VMware_.
4.	Clique em  ** Varrer **.

##	Planejando uma Varredura

É possível configurar o vSphere Web Client para varrer MVs, dispositivos virtuais e hosts vSphere ESXi em horários específicos ou em intervalos convenientes para você.

1.	Usando o vSphere Web Client, selecione um objeto no inventário. Todos os objetos-filhos do objeto que você seleciona também são varridos.
2.	Selecione a **guia Monitorar** e clique em **Tarefa e eventos**.
3.	Selecione **Tarefas planejadas** e clique em **Planejar uma nova tarefa**.
4.	Selecione **Varrer atualizações** na lista suspensa que aparece. O assistente Varrer para Atualizações é aberto.
5.	Na página Editar configurações, selecione os tipos de atualizações para as quais varrer o objeto de inventário. Deve-se selecionar pelo menos um tipo de varredura. Na página Opções de planejamento, descreva e planeje a tarefa de varredura.
6.	Insira um nome exclusivo e, opcionalmente, uma descrição para a tarefa de varredura. Clique em **Mudar** para configurar a frequência e o horário de início para a tarefa de varredura. Clique em **OK**.
7.	A tarefa de varredura é listada na visualização Tarefas planejadas do vSphere Web Client.

### Links relacionados

* [VMware HCX no	{{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrações)
