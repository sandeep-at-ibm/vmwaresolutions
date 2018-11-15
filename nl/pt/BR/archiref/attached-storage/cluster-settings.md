---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Configurações do Cluster

Antes da inclusão do armazenamento conectado, a solução do vCenter Server não ativou recursos avançados, como o vSphere Distributed Resource Scheduler (DRS) e o vSphere High Availability (HA). Com a inclusão do dispositivo de armazenamento conectado do NFS, esses recursos são ativados no cluster com as configurações listadas nas seções a seguir.

## Planejador de Recurso Distribuído do vSphere

Há dois recursos principais que são ativados ao habilitar o vSphere DRS em um cluster: Balanceamento de carga e Gerenciamento de energia.

### Balanceamento de Car

Com o balanceamento de carga, a distribuição e o uso de recursos de CPU e de memória para todos os hosts e máquinas virtuais (VMs) no cluster são monitorados continuamente. O DRS compara essas métricas a uma utilização ideal de recursos, considerando os atributos dos conjuntos de recursos e de VMs do cluster e a demanda atual. Em seguida, ele executa ou recomenda migrações de VM de acordo.

Quando uma VM é ligada pela primeira vez no cluster, o DRS tenta manter um balanceamento de carga adequado, colocando a VM em um host apropriado ou fazendo uma recomendação. As configurações de posicionamento ou de recomendação são configuradas na seção Automação do DRS das configurações de cluster.

Nesse design, o nível de Automação do DRS é configurado como totalmente automatizado, para que, quando as VMs forem ligadas, elas sejam colocadas automaticamente em hosts com capacidade suficiente. As VMs também são migradas automaticamente de um host para outro para balanceamento de carga do cluster. Além disso, o limite de migração do cluster do DRS é configurado no ponto médio entre conservador e agressivo, de modo que as recomendações de prioridade 1, prioridade 2 e prioridade 3 sejam aplicadas. Isso significa que o vCenter Server fornece pelo menos boas melhorias para o balanceamento de carga do cluster.

A tabela a seguir mostra as configurações para o cluster do vSphere DRS no vSphere Web Client do VMware.

Tabela 1. Configurações de automação do DRS para o cluster do vSphere DRS

| Configuração             | Valor  |
|:------------------- |:------ |
| Ative o vSphere DRS | Selecionada |
| Nível de Automação | Totalmente Automatizado |
| Limite de Migração | Aplicar as recomendações de prioridade 1, prioridade 2 e prioridade 3 |
| Ativar níveis de automação de máquina individuais | Selecionado, configurado como 15 ms |

Para obter mais informações sobre como configurar essas definições no vSphere Web Client, consulte [Configurar um nível de automação customizada para uma máquina virtual no vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

Além do nível de automação e do limite de migração do cluster, esse design permite a automação de VMs para que seja possível configurar substituições para VMs individuais. Isso permite um controle mais granular das VMs, permitindo priorizar ainda mais seu balanceamento de carga.

### Gerenciamento de energia

Quando o recurso VMware Distributed Power Management está ativado, o DRS compara a capacidade nos níveis de cluster e de host com as demandas das VMs do cluster, incluindo a recente demanda histórica. Ele colocará (ou recomendará a colocação) os hosts no modo de energia em espera se for detectada capacidade em excesso suficiente ou em ativação de hosts se a capacidade for necessária. Dependendo das recomendações do estado de energia do host resultantes, talvez também seja necessário migrar as VMs dos hosts e para eles.
Nesse design, o gerenciamento de energia está desativado porque não há benefício operacional ou financeiro para ligar e desligar os hosts no cluster.

## Alta Disponibilidade do vSphere

O vSphere fornece alta disponibilidade para VMs agrupando-as e os hosts em que residem em um cluster. Os hosts no cluster são monitorados e, no caso de uma falha, as VMs em um host com falha são reiniciadas em hosts alternativos.
Nesse design, o vSphere High Availability é ativado com monitoramento do host e monitoramento da VM no cluster.

### Monitoramento do host

O monitoramento do host permite que os hosts no cluster troquem pulsações de rede e que o vSphere HA execute uma ação ao detectar falhas. Este recurso está ativado nesse design.

### Monitoramento de máquina virtual

O recurso de monitoramento da VM usa as informações de pulsação capturadas pelo VMware Tools como um proxy para disponibilidade do sistema operacional guest. Isso permite que o vSphere HA reconfigure ou reinicie automaticamente VMs individuais que tenham perdido sua capacidade de pulsação. Esse design ativa o monitoramento da VM e do aplicativo.

#### Condições de falha e resposta da VM

As condições de falha definem como as VMs falham e qual é a resposta dada a cada falha. Nesse design, a prioridade de reinicialização da VM é configurada como média; é altamente recomendável revisar esse valor e ajustar as configurações adequadamente para que a prioridade de reinicialização corresponda à importância da carga de trabalho. Além disso, a resposta para isolamento do host é configurada como "Desligar e reiniciar VMs" para que as VMs não sejam afetadas por um host isolado no cluster. O restante dos valores para essa configuração é definido como padrão.

A tabela a seguir mostra as configurações para o cluster do vSphere HA no VMware vSphere Web Client.

Tabela 2. Condições de falha e configurações de resposta da VM para o cluster do vSphere HA

| Configuração             | Valor  |
|:------------------- |:------ |
| Prioridade de reinício | Médio |
| Resposta para Isolamento do Host | Desligar e reiniciar VMs |
| Resposta para Armazenamento de dados com Permanent Device Loss (PDL) | Desativado |
| Resposta para Armazenamento de dados com All Paths Down (APD) | Desativado |
| Resposta para recuperação de APD após tempo limite de APD | Desativado |
| Sensibilidade de monitoramento | Customizada |
| Intervalo de falha | 50 s |
| Tempo de atividade mínimo | 90 s |
| Reconfigurações máximas por VM | 10 |
| Janela Tempo Máximo de Reconfigurações | Dentro de 1 h |

Para obter mais informações sobre como configurar essas definições no vSphere Web Client, consulte [Configurar respostas da máquina virtual](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Controle de Admissão

O vCenter Server usa o controle de admissão para assegurar que recursos suficientes estejam disponíveis em um cluster para fornecer proteção contra failover e assegurar que as reservas de recursos da VM sejam respeitadas. Nesse design, a capacidade de failover é reservada especificando uma porcentagem dos recursos de cluster. A capacidade de failover definida é configurada como 25% de CPU e 25% de memória.

#### Datastore para pulsação

O vSphere HA usa a pulsação de armazenamento de dados para distinguir entre hosts que falharam e hosts que residem em uma partição da rede. A pulsação de armazenamento de dados permite que o vSphere HA monitore os hosts quando ocorre uma partição da rede de gerenciamento e continue a responder a falhas que ocorrem. Nesse design, a política de seleção de armazenamento de dados de pulsação é configurada como "Selecionar automaticamente os armazenamentos de dados acessíveis por meio do host".

### Links relacionados

* [ Visão geral da solução ](../solution/solution_overview.html)
