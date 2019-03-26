---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

#	Upgrades Orquestrados
{: #vum-orchestr-updates}

É possível usar upgrades orquestrados para fazer upgrade do hardware virtual e do VMware Tools de máquinas virtuais no inventário após a atualização dos hosts vSphere ESXi. Depois que os hosts são atualizados, a linha de base de upgrade do VMware Tools é executada primeiro, seguida pela linha de base de upgrade de hardware da máquina virtual. É possível usar upgrades orquestrados em um nível de cluster, pasta ou data center.

O VUM permite executar upgrades orquestrados de hosts e, em seguida, máquinas virtuais usando grupos de linhas de base. É usado um grupo de linhas de base que contém uma única linha de base de upgrade do host e múltiplas linhas de base de correção ou extensão. O VUM primeiro faz upgrade dos hosts e, em seguida, aplica as linhas de base de correção ou extensão. Você executa um upgrade orquestrado de máquinas virtuais usando um grupo de linhas de base da máquina virtual que contém as linhas de base a seguir:
* Upgrade de hardware da MV para corresponder ao host
* Upgrade do VMware Tools para corresponder ao host

Os upgrades orquestrados pelo VUM permitem que você faça upgrade dos objetos de inventário no VCSA em um processo de duas etapas. Primeiramente, os hosts vSphere ESXi são submetidos a upgrade, seguido pelos upgrades de máquina virtual. Esse processo de duas etapas pode ser configurado em um nível do cluster ou é possível configurá-lo no host vSphere ESXi individual ou no nível de máquina virtual para obter controle mais granular.

No upgrade orquestrado, o cluster é corrigido primeiro com relação ao grupo de linhas de base do host, que aplica correções, extensões e upgrades, e uma vez feito upgrade, as máquinas virtuais no cluster são corrigidas com relação ao grupo de linhas de base de upgrade de máquina virtual que contém as linhas de base Upgrade de hardware da MV para corresponder ao host e Upgrade do VMware Tools para corresponder ao host.

Se o grupo de linhas de base também contiver uma linha de base de upgrade, o VUM primeiro fará upgrade dos hosts vSphere ESXi e, em seguida, aplicará as linhas de base de correção ou extensão conforme as correções forem aplicáveis para a versão específica do host. Para as máquinas virtuais, o VMware Tools é atualizado primeiro, seguido pela atualização do hardware virtual.

Portanto, durante o upgrade do VMware Tools, as máquinas virtuais serão ligadas se elas estiverem em um estado desligado ou suspenso, em seguida, o VUM as ligará, executará o upgrade e restaurará o estado de energia original da máquina virtual. Portanto, durante o upgrade de hardware virtual, as MVs deverão estar no estado desligado, se houver máquinas virtuais que estejam ligadas, o VUM as encerrará, fará upgrade do hardware virtual e as ligará novamente.

Por padrão, a correção de hosts vSphere ESXi acontece de maneira sequencial e corrige um host por vez. Quando o processo for concluído para um host, o VUM começará a corrigir o próximo host. Esse padrão pode ser mudado para permitir a correção paralela para que mais de um host possa ser corrigido de cada vez, no entanto, isso será possível somente se você tiver capacidade de failover adequada em seu cluster.

Se os hosts vSphere ESXI forem parte de um cluster vSAN, o processo de correção será sempre sequencial mesmo se você tiver selecionado a correção paralela no assistente de correção, pois somente um host de um cluster vSAN poderá estar no modo de manutenção em qualquer momento. O VUM é inteligente e realiza um cálculo sobre quantos hosts podem ser corrigidos em paralelo sem interromper as configurações do DRS.

Como alternativa, é possível definir o limite para o número de hosts que podem ser corrigidos em paralelo durante o assistente de correção.

O fluxo de trabalho a seguir descreve o processo para executar um upgrade orquestrado:

## Etapa 1
{: #vum-orchestr-updates-step1}

1. Use o vSphere Web Client para efetuar login no VCSA.
2. Selecione **Página inicial** > **Update Manager**, na guia **Objetos**, selecione uma **instância do Update Manager**.
3. Clique na **guia Gerenciar**, em seguida, na **guia Linhas de base do host** e clique em **Novo grupo de linhas de base**.
4. Insira um nome exclusivo para o grupo de linhas de base e clique em **Avançar**.
5. Selecione uma linha de base de upgrade do host para incluí-la no grupo de linhas de base.
6. Opcionalmente, crie uma nova linha de base de upgrade do host clicando em **Criar uma nova linha de base de upgrade do host** na parte inferior da página Upgrades e preencha o assistente de Nova linha de base. Clique em **Avançar**.
7. Selecione as linhas de base de correção que você deseja incluir no grupo de linhas de base.
8. Opcionalmente, crie uma nova linha de base de correção clicando em **Criar uma nova linha de base de correção do host** na parte inferior da página Correções e conclua o assistente de Nova linha de base. Clique em **Avançar**.
9. Selecione as linhas de base de extensão a serem incluídas no grupo de linhas de base.
10. Opcionalmente, crie uma nova linha de base de extensão clicando em **Criar uma nova linha de base de extensão** na parte inferior da página Correções e conclua o assistente de Nova linha de base.
11. Revise a página **Pronto para concluir**, clique em **Concluir** e o grupo de linhas de base do host será exibido na área de janela Grupos de linhas de base.

## Etapa 2
{: #vum-orchestr-updates-step2}

1. Crie um grupo de linhas de base da máquina virtual, contendo a linha de base Upgrade do VMware Tools para corresponder ao host e a linha de base Upgrade de hardware da MV para corresponder ao host, visualização Administração do VUM.
2. Anexe o grupo de linhas de base a um objeto contêiner do vCenter que contenha as máquinas virtuais das quais você deseja fazer upgrade.
3. Varra o objeto contêiner para visualizar o estado de conformidade das máquinas virtuais no contêiner. É possível iniciar a varredura manualmente ou planejar uma tarefa de varredura.
4. Revise os resultados da varredura exibidos na visualização Conformidade do cliente do VUM.
5. Corrija as máquinas virtuais fora de conformidade no objeto contêiner para torná-las compatíveis com o grupo de linhas de base anexado. É possível iniciar a correção manualmente ou planejar uma tarefa de correção.
* Durante um upgrade do VMware Tools, as máquinas virtuais devem ser ligadas. Se uma máquina virtual estiver em um estado desligado ou suspenso antes da correção, o VUM ligará a máquina. Após o upgrade ser concluído, o VUM reiniciará a máquina e restaurará o estado da energia original da máquina virtual.
* Durante um upgrade de hardware da máquina virtual, as máquinas virtuais devem ser encerradas. Depois que a correção é concluída, o VUM restaura o estado da energia original das máquinas virtuais. Se uma máquina virtual estiver ligada, o VUM desligará a máquina, fará upgrade do hardware virtual e, em seguida, ligará a máquina virtual.

Agora é possível usar esses grupos de linha de base nos processos de varredura, revisão, preparação e correção.

## Links relacionados
{: #vum-orchestr-updates-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrações)
