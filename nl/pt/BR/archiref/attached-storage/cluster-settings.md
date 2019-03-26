---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-28"

---

# Configurações do Cluster
{: #cluster-settings}

Antes da adição do armazenamento anexado, a solução vCenter Server não ativou os recursos avançados, como o vSphere Distributed Resource Scheduler (DRS) e o vSphere High Availability (HA). Com a inclusão do dispositivo de armazenamento conectado do NFS, esses recursos são ativados no cluster com as configurações listadas nas seções a seguir.

## Planejador de Recurso Distribuído do vSphere
{: #cluster-settings-vsphere-drs}

Dois recursos principais são ativados quando você ativa o vSphere DRS em um cluster: Balanceamento de carga e Gerenciamento de energia.

### Balanceamento de
{: #cluster-settings-load-balance}

Com o balanceamento de carga, a distribuição e o uso de recursos de CPU e de memória para todos os hosts e máquinas virtuais (MVs) no cluster são monitorados continuamente. O DRS compara essas métricas com um uso de recurso ideal, dados os atributos dos conjuntos de recursos e MVs do cluster e a demanda atual. Em seguida, ele conclui ou recomenda as migrações de MV conforme necessário.

Quando uma MV é ligada pela primeira vez no cluster, o DRS tenta manter o balanceamento de carga adequado, colocando a MV em um host apropriado ou fazendo uma recomendação. As configurações de posicionamento ou de recomendação são configuradas na seção Automação do DRS das configurações de cluster.

Nesse design, o nível de Automação do DRS é configurado como totalmente automatizado, portanto, quando as MVs são ativadas, elas são colocadas automaticamente em hosts com capacidade suficiente. As MVs também são migradas automaticamente de um host para outro para balanceamento de carga do cluster. Além disso, o limite de migração do cluster do DRS é configurado no ponto médio entre conservador e agressivo, de modo que as recomendações de prioridade 1, prioridade 2 e prioridade 3 sejam aplicadas. O vCenter Server fornece pelo menos boas melhorias para o balanceamento de carga do cluster.

A tabela a seguir mostra as configurações para o cluster do vSphere DRS no vSphere Web Client do VMware.

Tabela 1. Configurações de automação do DRS para o cluster do vSphere DRS

| Configuração             | Valor  |
|:------------------- |:------ |
| Ative o vSphere DRS | Selecionada |
| Nível de Automação | Totalmente Automatizado |
| Limite de Migração | Aplicar as recomendações de prioridade 1, prioridade 2 e prioridade 3 |
| Ativar níveis de automação de máquina individuais | Selecionado, configurado como 15 ms |

Para obter mais informações sobre como configurar essas definições no vSphere Web Client, consulte [Configurar um nível de automação customizada para uma máquina virtual no vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

Junto com o nível de automação e o limite de migração do cluster, esse design permite a automação da MV para que seja possível substituir valores por MV individual. Um controle mais granular de MVs permite uma maior priorização do balanceamento de carga de MVs.

### Gerenciamento de energia
{: #cluster-settings-power-mgmt}

Quando o recurso VMware Distributed Power Management está ativado, o DRS compara a capacidade nos níveis de cluster e de host com as demandas das MVs do cluster, incluindo a recente demanda histórica. O recurso de gerenciamento de energia coloca ou recomenda colocar hosts no modo de energia de espera se houver capacidade excessiva suficiente ou ligar os hosts se for necessária a capacidade. Dependendo das recomendações do estado de energia do host resultantes, talvez também seja necessário migrar as MVs dos hosts e para eles.
Nesse design, o gerenciamento de energia está desativado porque não há benefício operacional ou financeiro para ligar e desligar os hosts no cluster.

## Alta Disponibilidade do vSphere
{: #cluster-settings-vsphere-ha}

O vSphere fornece alta disponibilidade para MVs agrupando-as e os hosts em que residem em um cluster. Os hosts no cluster são monitorados e, se ocorrer uma falha, as MVs em um host com falha serão reiniciadas em hosts alternativos.
Nesse design, o vSphere High Availability é ativado com monitoramento do host e monitoramento da MV no cluster.

### Monitoramento do host
{: #cluster-settings-host-monitor}

O monitoramento do host permite que os hosts no cluster troquem pulsações de rede e ativa o vSphere HA ao detectar falhas. Este recurso está ativado nesse design.

### Monitoramento de máquina virtual
{: #cluster-settings-machine-monitor}

O recurso de monitoramento da MV usa as informações de pulsação capturadas pelo VMware Tools como um proxy para disponibilidade do sistema operacional guest. O monitoramento da MV permite que o vSphere HA seja reconfigurado automaticamente ou reinicie as MVs individuais que não têm mais sua capacidade de pulsação. Esse design ativa o monitoramento da MV e do aplicativo.

#### Condições de falha e resposta da MV
{: #cluster-settings-failure-conditions}

As condições de falha definem como as MVs falham e a resposta que é dada a cada falha. Nesse design, a prioridade de reinicialização da MV está configurada como média. Revise esse valor e ajuste as configurações para que a prioridade de reinicialização corresponda à importância da carga de trabalho. Além disso, a resposta para o isolamento do host é configurada como “Desligar e reiniciar MVs” para que as MVs não sejam afetadas por um host isolado no cluster. O restante dos valores para essa configuração é definido como padrão.

A tabela a seguir mostra as configurações para o cluster do vSphere HA no VMware vSphere Web Client.

Tabela 2. Condições de falha e configurações de resposta da MV para o cluster do vSphere HA

| Configuração             | Valor  |
|:------------------- |:------ |
| Prioridade de reinício | Médio |
| Resposta para Isolamento do Host | Desligar e reiniciar MVs |
| Resposta para Armazenamento de dados com Permanent Device Loss (PDL) | Desativado |
| Resposta para Armazenamento de dados com All Paths Down (APD) | Desativado |
| Resposta para recuperação de APD após tempo limite de APD | Desativado |
| Sensibilidade de monitoramento | Customizada |
| Intervalo de falha | 50 s |
| Tempo de atividade mínimo | 90 s |
| Reconfigurações máximas por MV | 10 |
| Janela Tempo Máximo de Reconfigurações | Dentro de 1 h |

Para obter mais informações sobre como configurar essas definições no vSphere Web Client, consulte [Configurar respostas da máquina virtual](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Controle de Admissão
{: #cluster-settings-admin-control}

O vCenter Server usa o controle de admissão para assegurar que recursos suficientes estejam disponíveis em um cluster para fornecer proteção contra failover e assegurar que as reservas de recursos da MV sejam respeitadas. Nesse design, a capacidade de failover é reservada especificando uma porcentagem dos recursos de cluster. A capacidade de failover definida é configurada como 25% de CPU e 25% de memória.

#### Armazenamento do coração de armazenamento de dados
{: #cluster-settings-datastore}

O vSphere HA usa uma pulsação de armazenamento de dados para identificar hosts que falharam e os hosts que residem em uma partição de rede. A pulsação do armazenamento de dados permite que o vSphere HA monitore os hosts quando uma partição de rede de gerenciamento ocorre e continue a responder a falhas que ocorrem. Nesse design, a política de seleção de armazenamento de dados de pulsação é configurada como "Selecionar automaticamente os armazenamentos de dados acessíveis por meio do host".

## Links relacionados
{: #cluster-settings-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
