---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuração e definições para o armazenamento conectado

Esse design suporta a conexão de armazenamento compartilhado somente por meio do NFS v3. O NFS v4 e a v4.1 não são suportados.

O armazenamento conectado para esse design é limitado ao armazenamento do {{site.data.keyword.cloud_notm}} disponível no mesmo {{site.data.keyword.CloudDataCent_notm}} que a solução do vCenter Server. Além disso, todos os discos virtuais armazenados no armazenamento de dados são thin-provisioned por padrão.
{:note}

A arquitetura especifica que os armazenamentos de dados do NFS v3 são conectados usando o nome do DNS do armazenamento do {{site.data.keyword.cloud_notm}} para se conectar ao compartilhamento. O compartilhamento do NFS é conectado a todos os hosts no cluster do vCenter Server e colocado em um cluster de armazenamento de dados com o DRS de armazenamento ativado.

## vSphere Storage Distributed Resource Scheduler (Storage DRS)

Use o Storage DRS para gerenciar os recursos agregados de um cluster de armazenamento de dados. Quando o Storage DRS está ativado, ele fornece recomendações para posicionamento e migração de disco da máquina virtual (MV) para equilibrar o espaço e os recursos de E/S nos armazenamentos de dados no cluster de armazenamento de dados.

Os recursos a seguir estão disponíveis quando o Storage DRS está ativado:
* Balanceamento de carga de espaço entre armazenamentos de dados em um cluster de armazenamento de dados
* Balanceamento de carga de E/S entre armazenamentos de dados dentro de um cluster de armazenamento de dados
* Local inicial para discos virtuais com base no espaço e na carga de trabalho de E/S.

Nesse design, o Storage DRS é ativado com o nível de automação configurado como **Totalmente automatizado**. Como resultado, os arquivos são migrados automaticamente para otimizar o uso do recurso no cluster de dados. Como o cluster é totalmente automatizado, todas as outras opções de Storage DRS são configuradas como **Usar configurações do cluster**.

## Configurações de tempo de execução do Storage DRS para o NFS v3

A agressividade do Storage DRS é determinada ao especificar limites para o espaço usado e a latência de E/S. O Storage DRS coleta informações de uso do recurso para os armazenamentos de dados em um cluster de armazenamento de dados. O vCenter Server usa essas informações para gerar recomendações para o posicionamento de discos virtuais em armazenamentos de dados.

Quando um nível de agressividade baixo é configurado para um cluster de armazenamento de dados, o Storage DRS recomenda migrações de Storage vMotion somente quando necessário. Por exemplo, se a carga de E/S, a utilização de espaço ou seu desequilíbrio é alto, o Storage DRS recomenda uma migração. Se um nível de agressividade alto é configurado para um cluster de armazenamento de dados, o Storage DRS recomenda migrações sempre que o cluster de armazenamento de dados pode se beneficiar do espaço ou do balanceamento de carga de E/S.

As categorias de limite a seguir estão disponíveis no cluster de armazenamento de dados.

* Utilização de espaço: o Storage DRS gera recomendações ou executa migrações quando a porcentagem de utilização de espaço no armazenamento de dados é maior que o limite configurado no vSphere Web Client.
* Latência de E/S: o Storage DRS gera recomendações ou executa migrações quando a latência de E/S do 90º percentil medida ao longo de um dia para o armazenamento de dados é maior que o limite.

Nesse design, as Configurações de tempo de execução do Storage DRS são ativadas e os limites são mantidos em seus respectivos valores padrão. Mude esses valores com base nos requisitos de E/S da carga de trabalho e na sensibilidade de latência.

A tabela a seguir mostra as configurações no VMware vSphere Web Client.

Tabela 1. Configurações de tempo de execução do Storage DRS

| Configuração       | Valor  |
|:--------------- |:------ |
| Ativar métrica de E/S para recomendações do SDRS | Selecionada |
| Espaço Utilizado | Selecionado, configurado como 80% |
| Limite de latência de E/S | 15 ms |

Para obter mais informações sobre como configurar essas definições no vSphere Web Client, consulte [Configurar regras de tempo de execução do Storage DRS no vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

## Controle de E/S de Armazenamento para NFS v3

Quando o SIOC (Storage I/O Control) é ativado no ambiente, ele muda o comprimento da fila de dispositivo da única MV. A mudança para o comprimento da fila de dispositivo reduz a fila de matriz de armazenamento de todas as MVs para um compartilhamento e regulador iguais da fila de armazenamento. O SIOC será encaixado apenas se os recursos forem restritos e a latência de E/S de armazenamento for maior que um limite definido.

Para que o SIOC determine quando um dispositivo de armazenamento está congestionado ou restrito, ele requer um limite definido. A latência de limite de congestionamento é diferente para tipos de armazenamento diferentes. Esse design recomenda e implementa uma latência de limite de 10 milissegundos.

É possível limitar discos virtuais individuais para MVs individuais ou conceder-lhes compartilhamentos diferentes com SIOC. A limitação de discos e a concessão de diferentes compartilhamentos permitem que você corresponda e alinhe o ambiente à carga de trabalho com o número de IOPS do volume de armazenamento de arquivo adquirido. O limite é configurado pelo IOPS e é possível configurar um peso ou compartilhamentos diferentes.

Compartilhamentos de discos virtuais configurados como **Alto** (2.000 compartilhamentos) recebem duas vezes mais E/S do que um disco configurado como **Normal** (1.000 compartilhamentos) e quatro vezes mais do que um configurado como **Baixo** (500 compartilhamentos). **Normal** é o valor padrão para todas as MVs, portanto, será necessário ajustar as configurações **Normal** das MVs que precisarem.

## Armazenamento adicional para NFS v3

Quando surge a necessidade de incluir mais armazenamento no ambiente devido a espaço insuficiente ou latência alta, é possível pedir outro compartilhamento do NFS por meio do console. Depois que o compartilhamento for pedido, anexe a exportação aos hosts ESXi do vSphere no cluster e coloque-a no cluster de armazenamento. Colocar o novo compartilhamento de NFS no cluster de armazenamento dimensiona de forma eficiente e uniforme o armazenamento que está associado ao ambiente sem sobrecarregá-lo com migrações no nível de armazenamento.

## Parâmetros de Configuração Avançados

Esse design inclui parâmetros de configuração avançados que são recomendados pelo {{site.data.keyword.cloud_notm}}. Como resultado, os parâmetros a seguir são configurados em cada host do vSphere ESXi que está conectado ao compartilhamento de NFS do {{site.data.keyword.cloud_notm}}.

Tabela 2. Parâmetros de configuração avançados do NFS

| Parâmetro       | Valor  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MaxQueueDepth | 64 |

### Links relacionados

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
