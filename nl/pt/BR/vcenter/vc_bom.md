---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Lista de materiais do vCenter Server

Revise as informações da Lista de materiais (BOM) para instâncias do VMware vCenter Server.

## BOM de VLANs para instâncias do vCenter Server

A tabela a seguir detalha as informações da BOM para as VLANs do vCenter Server.

Tabela 1. BOM para as VLANs em instâncias do vCenter Server

| VLAN       | Tipo       | Detalhes       |
|:---------- |:---------- |:------------- |
| VLAN1     | Público, primário | Designado aos servidores ESXi físicos para acesso à rede pública. Não usado após a implementação inicial. Disponível para acesso à Internet. |
| VLAN2     | A privado, primário | Designado pelos servidores  {{site.data.keyword.cloud}}  aos servidores ESXi físicos. Usado pela interface de gerenciamento para o tráfego de gerenciamento do VMware vSphere.<br><br>Designado às VMs (máquinas virtuais) que funcionam como componentes de gerenciamento.<br><br>Designado ao VMware NSX VTEP (VXLAN Tunnel Endpoint) |
| VLAN3     | B privado, móvel | Designado ao VMware vSAN, se usado.<br><br>Designado ao VMware NFS, se usado.<br><br>Designado ao VMware vSphere vMotion. |

## BOM do software para instâncias do vCenter Server

A tabela a seguir detalha as informações da BOM para componentes de software do vCenter Server.

Tabela 2. BOM para os componentes de software em instâncias do vCenter Server

| Fabricante  | Componente                      | Versão       |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.5 U1g (ESXi 6.5u1 com o nível da correção ESXi650-201803001 aplicado) |
| VMware       | vCenter Server Appliance        | 6,5 Atualização 1g |
| VMware       | Platform Services Controller    | 6,5 Atualização 1g |
| VMware       | vSAN                            | 6.6.1        |
| VMware       | NSX for vSphere                 | 6.4.1        |
| IBM          | CloudDriver                     | 2.4          |
| Microsoft    | Windows Server Standard Edition | 2012R2       |

**Nota**: VMware vSAN é um componente opcional.

## Definições de configuração avançada para servidores ESXi

Revise a tabela a seguir para obter uma visão geral das definições de configuração avançadas que são aplicadas aos servidores ESXi dependendo se a instância do vCenter Server é implementada na V2.2 ou mais recente ou se tem upgrade feito para a V2.2 ou mais recente de uma V2.1 anterior ou de uma liberação anterior.

As configurações aplicam-se a novas instâncias e novos clusters em novas instâncias V2.2 ou mais recentes. As configurações não se aplicam a novos clusters em instâncias existentes da V2.1 ou anterior ou a instâncias existentes submetidas a upgrade para a V2.2 ou mais recente.

Tabela 3. Definições de configuração avançadas de servidores ESXi para instâncias e clusters do vCenter Server

| Definição de configuração | Se recém-implementado na V2.2 ou mais recente  | Se submetido a upgrade da V2.1 ou anterior |
|:------------- |:------------- |:------------- |
| Máximo de volumes | **MaxVolumes** = 256 | Ambos **/NFS/MaxVolumes** e **/NFS41/MaxVolumes** = 256 |
| Falhas máximas de pulsação | **HeartbeatMaxFailures** = 10 | Não configurado |
| Frequência de pulsação | **HeartbeatFrequency** = 12 | Não configurado |
| Tempo limite de pulsação | **HeartbeatTimeout** = 5 | Não configurado |
| Profundidade máxima da fila | **MaxQueueDepth** = 64 | Não configurado |
| Tamanho da amostra completa da fila | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Limite completo da fila | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| Tamanho do heap TCP/IP | **TcpipHeapSize** = 32 | Não configurado |
| Heap máximo de TCP/IP | **TcpipHeapMax** = 1536 | Não configurado |

**Notas**:
* A configuração **MaxVolumes** é necessária para o serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} porque o serviço pode usar mais que o número padrão de montagens NFS no servidor ESXi.
* Um valor de **Não configurado** para uma definição de configuração indica que a nova configuração não será aplicada automaticamente, porque requer a reinicialização dos servidores ESXi, que poderá ser disruptiva.

  Recomenda-se mudar as definições de configuração **Não configurado** para os novos valores para consistência em todas as instâncias e para permitir suporte adequado para expansão de armazenamento. A IBM planeja testar apenas com essas novas configurações para todos os {{site.data.keyword.vmwaresolutions_short}} V2.2 e liberações mais recentes.

  Para obter mais informações, veja [Aumentando o valor padrão que define o número máximo de montagens NFS em um host ESXi/ESX](https://kb.vmware.com/s/article/2239).

## Definições de configuração do grupo da porta e NSX

Revise a tabela a seguir para obter uma visão geral das definições de configuração do grupo da porta e VMware NSX para instâncias do vCenter Server e as diferenças entre as liberações.

As configurações aplicam-se a novas instâncias e novos clusters em novas instâncias V2.2 ou mais recentes. As configurações não se aplicam a novos clusters em instâncias existentes da V2.1 ou anterior ou a instâncias existentes submetidas a upgrade para a V2.2 ou mais recente.

Tabela 4. Definições de configuração do grupo da porta e NSX para instâncias do vCenter Server

| Definição de configuração | V2.1 ou anterior  | V2.2 ou mais recente |   
|:------------- |:------------- |:------------- |
| Política de equipe de cluster NSX VXLAN | Failover | Balanceamento de carga - SRCID |
| NSX VXLAN cluster VTEP | 1 | 2 |
| Conjunto do ID de segmento para a instância primária | 6000-8000 | 6000-7999 |  
| Conjunto do ID de segmento para instância ou instâncias secundárias subsequentes | 6000-8000 | Intervalo final anterior na configuração de vários sites + 1 para Intervalo final anterior na configuração de vários sites + 2000 |  
| Grupo da porta SDDC-DPortGroup-VSAN (se aplicável) | **Uplinks ativos** configurados como **uplink1** e **Uplinks em espera** configurados como **uplink2** | **Uplinks ativos** configurados como **uplink2** e **Uplinks em espera** configurados como **uplink1** |  
| Grupo da porta SDDC-DPortGroup-Mgmt | **Ligação da porta** configurada como **Ephermeral - sem ligação** e **Balanceamento de carga** configurado como **Rota baseada na porta virtual de origem** | **Ligação da porta** configurada como **Ligação estática** e **Balanceamento de carga** configurado como **Rota baseada na carga NIC física** |  
| Grupo da porta SDDC-DPortGroup-External | **Ligação da porta** configurada como **Ephemeral - sem ligação** | **Ligação da porta** configurada como **Ligação estática** |

## NetworkMTU as definições de configuração

O cluster do vSphere usa dois vSphere Virtual Distributed Switches (VDS), um para conectividade de rede pública e outro para
conectividade de rede privada.

As conexões de rede privada são configuradas para usar a MTU (Unidade Máxima de Transmissão) de Quadros gigantes com o tamanho de 9000, que melhora o desempenho de grandes transferências de dados, como armazenamento e VMware vMotion. Esta é a MTU máxima permitida dentro do VMware e por {{site.data.keyword.cloud_notm}}.

Na V2.1 ou mais recente, as conexões de rede pública usam uma MTU de Ethernet padrão de 1500. Essa configuração de 1500 deve ser mantida; quaisquer mudanças podem causar a fragmentação do pacote pela Internet.

Revise a tabela a seguir para obter uma visão geral das definições de configuração de MTU de rede que são aplicadas ao Distributed Virtual Switch (DVS) público e privado, dependendo se a instância do vCenter Server for implementada na V2.1 ou mais recente.

Tabela 5. Definições de configuração de MTU para instâncias e clusters do vCenter Server dependendo da versão da instância

| VDS | V2.1 ou posterior  | V2.0 ou anterior (ou submetido a upgrade da V2.0 ou anterior) |
|:-------------- |:-------------- |:------------- |
| Comutador público  | 1500 (padrão) | 9000 (Quadros Jumbo) |
| Comutador privado | 9000 (Quadros Jumbo) | 9000 (Quadros Jumbo) |

As configurações aplicam-se a novas instâncias e novos clusters de instâncias implementadas na V2.1 ou mais recente. As configurações também se aplicam a novos clusters em {{site.data.keyword.CloudDataCents_notm}} cruzados de instâncias que foram submetidas a upgrade para a V2.1 ou mais recente.

As configurações não se aplicam a novos clusters no mesmo {{site.data.keyword.CloudDataCent_notm}}, para instâncias existentes da V2.0 ou de instâncias anteriores ou existentes submetidas upgrade para a V2.1 ou mais recente.

Para instâncias que foram implementadas na versão V2.0 ou anterior, é recomendado que você atualize o configuração de MTU do
comutador público para 1500.

### Atualizando a configuração de MTU do comutador público

Para atualizar a configuração de MTU para o comutador público, conclua as seguintes etapas no VMware vSphere Web Client:
1. Clique com o botão direito no VDS e clique em **Editar configurações**.
2. Na **guia Propriedades**, selecione a opção **Avançado**.
3. Certifique-se de que o valor de **MTU máximo** esteja configurado para 1500.

   **Nota**: ao mudar o tamanho do MTU em um vDS, os uplinks conectados (NICs físicos) diminuem e depois aumentam novamente. Como resultado, uma breve interrupção ocorre para as VMs que estão usando o uplink. Portanto, é
recomendável planejar a atualização de configuração do MTU durante o tempo de inatividade planejado.

### Links relacionados

* [Números de compilação e versões do VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Números de compilação e versões do VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Ativando quadros gigantes em comutadores virtuais distribuídos](https://kb.vmware.com/s/article/1038827)
* [Planilha de dados de proteção do VMware vCenter Server on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [Visão geral do vCenter Server](vc_vcenterserveroverview.html)
* [Planejando instâncias do vCenter Server](vc_planning.html)
