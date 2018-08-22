---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Lista de materiais do Cloud Foundation

Revise as informações da Lista de Materiais (BOM) para instâncias do VMware Cloud Foundation.

## BOM de VLANs para instâncias do Cloud Foundation

A tabela a seguir detalha as informações da BOM para as VLANs do Cloud Foundation.

Tabela 1. BOM para as VLANs em instâncias do Cloud Foundation

| VLAN      | Tipo      | Detalhes      |
|:----------|:----------|:-------------|
| VLAN1     | Público, primário | Designado aos servidores ESXi físicos para acesso à rede pública. Não usado após a implementação inicial. Disponível para acesso à Internet. |
| VLAN2     | A privado, primário | Designado pelos servidores  {{site.data.keyword.cloud}}  aos servidores ESXi físicos. Usado pela interface de gerenciamento para o tráfego de gerenciamento do VMware vSphere.<br><br>Designado às VMs (máquinas virtuais) que funcionam como componentes de gerenciamento.<br><br>Designado ao VMware NSX VTEP (VXLAN Tunnel Endpoint) |
| VLAN3     | B privado, móvel | Designado ao VMware vSAN, se usado.<br><br>Designado ao VMware NFS, se usado.<br><br>Designado ao VMware vSphere vMotion. |

## BOM de software para instâncias do Cloud Foundation

A tabela a seguir detalha as informações da BOM para componentes de software do Cloud Foundation.

Tabela 2. BOM para os componentes de software em instâncias do Cloud Foundation

| Fabricante | Componente                                | Versão      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 U1g (ESXi 6.5u1 com o nível da correção ESXi650-201803001 aplicado) |
| VMware       | vCenter Server Appliance                 | 6,5 Atualização 1g |
| VMware       | Platform Services Controller             | 6,5 Atualização 1g |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.3.5        |
| VMware       | SDDC Manager                             | 2.4          |
| IBM          | CloudDriver                              | 2.4          |
| Microsoft    | Windows Server Standard Edition (64 bits) | 2012R2       |

## Definições de configuração avançada para servidores ESXi

Revise a tabela a seguir para obter uma visão geral das definições de configuração avançadas que são aplicadas aos servidores ESXi dependendo se a instância do Cloud Foundation é implementada na V2.2 ou mais recente ou se é atualizada para a V2.2 ou mais recente de uma V2.1 anterior ou de uma liberação anterior.

Tabela 3. Definições de configuração avançada de servidores ESXi para instâncias e clusters do Cloud Foundation

| Definição de configuração | Se recém-implementado na V2.2 ou mais recente  | Se submetido a upgrade da V2.1 ou anterior |   
|:------------- |:------------- |:------------- |
| Tamanho do heap TCP/IP | **TcpipHeapSize** = 32 | Não configurado |
| Heap máximo de TCP/IP | **TcpipHeapMax** = 1536 | Não configurado |  
| Máximo de volumes | **MaxVolumes** = 256 | Ambos **/NFS/MaxVolumes** e **/NFS41/MaxVolumes** = 256 |  
| Falhas máximas de pulsação | **HeartbeatMaxFailures** = 10 | Não configurado |  
| Frequência de pulsação | **HeartbeatFrequency** = 12 | Não configurado |  
| Tempo limite de pulsação | **HeartbeatTimeout** = 5 | Não configurado |
| Profundidade máxima da fila | **MaxQueueDepth** = 64 | Não configurado |
| Tamanho da amostra completa da fila | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Limite completo da fila | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

**Notas**:
* A configuração **MaxVolumes** é necessária para o serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} porque o serviço pode usar mais que o número padrão de montagens NFS no servidor ESXi.
* Um valor de **Não configurado** para uma definição de configuração indica que a nova configuração não será aplicada automaticamente, porque requer a reinicialização dos servidores ESXi, que poderá ser disruptiva.

  Recomenda-se mudar as definições de configuração **Não configurado** para os novos valores para consistência em todas as instâncias e para permitir suporte adequado para expansão de armazenamento. A IBM planeja testar apenas com essas novas configurações para todos os {{site.data.keyword.vmwaresolutions_short}} V2.2 e liberações mais recentes.

  Para obter mais informações, veja [Aumentando o valor padrão que define o número máximo de montagens NFS em um host ESXi/ESX](https://kb.vmware.com/s/article/2239).

### Links relacionados

* [Números de compilação e versões do VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Números de compilação e versões do VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Planilha de dados de proteção do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Visão geral do Cloud Foundation](sd_cloudfoundationoverview.html)
* [Planejando instâncias do Cloud Foundation](sd_planning.html)
