---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Design de infraestrutura virtual
{: #design_virtualinfrastructure}

A camada de infraestrutura virtual inclui os componentes de software do VMware que virtualizam os recursos de cálculo, armazenamento e rede fornecidos na camada de infraestrutura física: VMware vSphere ESXi, VMware NSX-V ou NSX-T e, opcionalmente, VMware vSAN.

![Infraestrutura virtual](../../images/vcsv4radiagrams-ra-virtinfra.svg "Infraestrutura virtual")

## Design do VMware vSphere
{: #design_virtualinfrastructure-vsphere-design}

A configuração do vSphere ESXi consiste nos aspectos a seguir:
* Configuração de inicialização
* Sincronização de
* Acesso ao host
* Acesso de usuário
* Configuração de DNS

A tabela a seguir descreve as especificações para cada aspecto. Após a configuração e instalação do ESXi, o host é incluído em um VMware vCenter Server e é gerenciado de lá.

Com esse design, é possível acessar os hosts virtuais por meio do Direct Console User Interface (DCUI) e do vSphere Web Client. O Shell Seguro (SSH) e o Shell ESXi são desativados após o fornecimento como uma melhor prática.

Por padrão, os únicos usuários que podem efetuar login diretamente são os usuários _raiz_ e _ibmvmadmin_ para a máquina física do host. O administrador pode incluir usuários do domínio do Microsoft Active Directory (MSAD) para permitir o acesso de usuário ao host. Todos os hosts no design da solução vCenter Server estão configurados para sincronizar com um servidor NTP central.

Tabela 1. Configuração do vSphere ESXi

| Atributo              | Parâmetro de configuração |
|:---------------------- |:----------------------- |
| Local de inicialização ESXi     | Usa discos locais que são configurados no RAID-1 |
| Sincronização de   | Usa  {{site.data.keyword.cloud}}  servidor NTP |
| Acesso ao host            | Suporta DCUI. O SSH e o Shell ESXi são suportados, mas não ativados por padrão |
| Acesso de usuário            | Autenticação local e MSAD |
| Resolução do nome de domínio | Usa o DNS conforme descrito em [Design de serviços comuns](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice). |
| Modo EVC | Skylake (somente para implementações "greenfield" do vSphere 6.7) |

O cluster do vSphere hospeda as máquinas virtuais (VMs) que gerenciam a instância do vCenter Server, bem como recursos de cálculo para cargas de trabalho do usuário.

* Quando uma instância do vCenter Server usa a vSAN, o número mínimo de hosts do ESXi na implementação inicial é 4.
* Quando uma instância do vCenter Server usa o armazenamento de nível de arquivo compartilhado ou de nível de bloco, o número mínimo de hosts do ESXi na implementação inicial é 3.

É possível escalar até um máximo de 59 hosts ESXi durante ou após a implementação inicial.

Para suportar mais cargas de trabalho do usuário, é possível escalar o ambiente da seguinte forma:  
* Implementando mais hosts de cálculo em clusters existentes
* Implementando mais clusters que são gerenciados pelo mesmo vCenter Server Appliance
* Implementando novas instâncias do vCenter Server com o seu próprio vCenter Server Appliance

Para obter mais informações sobre clusters, consulte [executando a arquitetura de solução de clusters do VMware do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf).

## Design do VMware vSAN
{: #design_virtualinfrastructure-vsan-design}

Nesse design, o armazenamento do VMware vSAN é empregado em instâncias do vCenter Server para fornecer armazenamento compartilhado para os hosts do vSphere.

Conforme mostrado na figura a seguir, a vSAN agrega o armazenamento local em múltiplos hosts do ESXi dentro de um cluster do vSphere e gerencia o armazenamento agregado como um único armazenamento de dados da VM. Dentro desse design, os nós de cálculo contêm unidades de disco locais para o Sistema operacional do ESXi (S.O.) e o armazenamento de dados da vSAN. Independentemente de a qual cluster um nó pertence, duas unidades do S.O. estão incluídas em cada nó para abrigar a instalação do ESXi.

![Conceito de vSAN](../../images/vcsv4radiagrams-ra-vsan.svg "O vSAN agrega o armazenamento local em vários hosts ESXi em um cluster do vSphere e gerencia o armazenamento agregado como um único armazenamento de dados da VM")

O vSAN emprega os componentes a seguir:
* O design do vSAN de grupo de dois discos; cada grupo de disco com dois ou mais discos. Uma unidade de SSD ou NVMe do menor tamanho no grupo serve como a camada de cache e os SSDs restantes servem como a camada de capacidade.
* O controlador RAID integrado é configurado em uma matriz RAID-0 para cada unidade, exceto para as duas unidades de S.O.
* Um único armazenamento de dados do vSAN é criado a partir de todo o armazenamento.

Os recursos disponíveis do vSAN dependem da edição de licença que você seleciona ao pedir a instância. Para obter mais informações, veja [Comparação de edição do VMware vSAN](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix#vmware-vsan-edition-comparison).

### Configuração de rede virtual para vSAN
{: #design_virtualinfrastructure-net-setup}

Para esse design, o tráfego do vSAN atravessa entre hosts ESXi em uma VLAN privada dedicada. Os dois adaptadores de rede conectados ao comutador de rede privada são configurados no vSphere como um vSphere Distributed Switch (vDS) com os dois adaptadores de rede como uplinks. Um grupo de portas do kernel do vSAN dedicado que é configurado para a VLAN vSAN reside dentro do vDS. Quadros gigantes (MTU 9000) são ativados para o vDS privado.

O vSAN não carrega o tráfego de balanceamento entre uplinks. Como resultado, um adaptador está ativo enquanto o outro está em espera para suportar a alta disponibilidade (HA). A política de failover de rede para vSAN é configurada como **Failover explícito** entre portas de rede física.

Para obter mais informações sobre conexões do NIC físicas, consulte [Conexões do NIC do host físico](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-host-connect).

### Design de política da vSAN
{: #design_virtualinfrastructure-storage-policy}

Quando o vSAN está ativado e configurado, as políticas de armazenamento são configuradas para definir as características de armazenamento da MV. As características de armazenamento especificam níveis diferentes de serviço para MVs diferentes.

A política de armazenamento padrão nesse design tolera uma única falha. A política padrão é configurada com a codificação de apagamento, com o **Método de tolerância a falhas** configurado como **RAID-5/6 (Codificação de apagamento) - Capacidade** e **Nível primário de falhas** configurado como 1. A configuração do RAID 5 requer um mínimo de quatro hosts.

Como alternativa, é possível escolher a configuração do RAID 6 com o **Método de tolerância a falhas** configurado como **RAID-5/6 (Codificação de apagamento) - Capacidade** e **Nível primário de falhas** configurado como 2. A configuração do RAID 6 requer um mínimo de seis hosts. A **duplicação** e a **compactação** também são ativadas na política de armazenamento padrão.

Uma instância usa a política padrão, a menos que especificado de outra forma por meio do console do vSphere. Quando uma política customizada for configurada, o vSAN garantirá isso quando possível. No entanto, se a política não puder ser garantida, não será possível provisionar uma MV que use a política, a menos que a política esteja ativada para forçar o fornecimento.

As políticas de armazenamento devem ser reaplicadas após a inclusão de novos hosts ESXi ou correção dos hosts ESXi.

### Configurações do vSAN
{: #design_virtualinfrastructure-vsan-sett}

As configurações da vSAN são configuradas com base nas melhores práticas para implementar soluções do VMware no {{site.data.keyword.cloud_notm}}. As configurações de vSAN incluem configurações de SIOC, grupo de portas de configurações de failover explícitas e configurações de cache de disco.
* Configurações de política de cache de SSD: No **Read Ahead**, **Write Through**, **Direct** (NRWTD)
* Configurações de controle de E/S de rede
   * Gerenciamento-20 compartilhamentos
   * Máquina virtual-30 compartilhamentos
   * vMotion-50 compartilhamentos
   * compartilhamentos do vSAN-100
* Portas do kernel vSAN:  ** Failover Explícito **

## Armazenamento conectado ao NFS
{: #design_virtualinfrastructure-nfs-storage}

Ao usar o armazenamento conectado à rede NFS, essa arquitetura prescreve o uso do NFS v3 em vez do NFS v4.1, porque as migrações LIF do servidor NFS podem causar latência excessiva ao usar o NFS v4.1. Cada host do vSphere é conectado ao armazenamento NFS usando seu nome de host.

Um armazenamento de dados NFS de 2 TB é conectado a um cluster para uso por componentes de gerenciamento com uma camada de desempenho de 4 IOPS/GB. Mais armazenamentos de dados podem ser conectados a um cluster para uso de carga de trabalho, em vários tamanhos e camadas de desempenho.

Além disso, essa arquitetura requer que todos os hosts tenham uma rota de sub-rede criada para a sub-rede na qual o armazenamento NFS reside. O propósito dessa rota de sub-rede é direcionar todo o tráfego NFS para usar o grupo da porta, a sub-rede e a VLAN designada para o tráfego NFS por esse design. Se vários armazenamentos de dados NFS estiverem conectados, várias rotas poderão precisar ser configuradas, pois esses armazenamentos de dados talvez estejam localizados em diferentes sub-redes remotas.

As máquinas virtuais de gerenciamento podem ser localizadas em um armazenamento de dados NFS. Isso cria um problema de autoinicialização, pois algumas das máquinas de gerenciamento podem ser responsáveis pelos serviços de DNS, usados para resolver o nome do host do NFS. Portanto, essa arquitetura especifica que pelo menos um dos endereços IP do armazenamento de dados de gerenciamento seja codificado permanentemente em `/etc/hosts` em cada um dos hosts.

## Design do VMware NSX-V
{: #design_virtualinfrastructure-nsx-design}

A virtualização de rede fornece uma sobreposição de rede que existe dentro da camada virtual. A virtualização de rede fornece a arquitetura com recursos, tais como fornecimento rápido, implementação, reconfiguração e destruição de redes virtuais sob demanda. Esse design usa o vDS e o VMware NSX for vSphere para implementar a rede virtual.

Nesse design, o NSX Manager é implementado no cluster inicial. O NSX Manager é designado a um endereço IP suportado pela VLAN por meio bloco de endereço móvel privado, que é designado para componentes de gerenciamento e configurado com os servidores DNS e NTP que são apresentados em [Design de serviços comuns](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice).

A figura a seguir mostra o posicionamento do NSX Manager em relação a outros componentes na arquitetura.

![Visão geral da rede do NSX Manager](../../images/vcsv4radiagrams-ra-vcs-nsx-overview.svg "NSX Manager em relação a outros componentes na arquitetura")

Após a implementação inicial, a automação do {{site.data.keyword.cloud_notm}} implementa três controladores NSX dentro do cluster inicial. Cada um dos controladores é designado a um endereço IP suportado pela VLAN por meio da sub-rede móvel **Privada A** que está designada aos componentes de gerenciamento. Além disso, o design cria regras de antiafinidade VM-VM para separar os controladores entre os hosts no cluster. O cluster inicial deve conter um mínimo de três nós para assegurar alta disponibilidade para os controladores.

Além dos controladores, a automação do {{site.data.keyword.cloud_notm}} prepara os hosts vSphere implementados com o NSX VIBS para permitir o uso de uma rede virtualizada por meio de VXLAN Tunnel Endpoints (VTEPs). Os VTEPs são designados com um endereço IP suportado pela VLAN por meio do intervalo de endereços IP móveis **Privados A** que é especificado para VTEPs conforme listado em [VLANs](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-vlans). O tráfego de VXLAN reside na VLAN não identificada e é designado ao vDS privado.

Em seguida, um conjunto de IDs de segmento é designado e os hosts no cluster são incluídos na zona de transporte. Somente unicast é usado na zona de transporte porque o rastreamento do Internet Group Management Protocol (IGMP) não está configurado dentro do {{site.data.keyword.cloud_notm}}. Duas portas de kernel do VTEP são configuradas por host na mesma sub-rede dedicada do VTEP por melhor prática do VMW.

Depois disso, se a instância tiver interfaces de rede pública, dois pares do NSX Edge Services Gateway serão implementados. Um par de gateway é usado para o tráfego de saída dos componentes de automação que residem na rede privada. Um segundo gateway que é conhecido como a borda gerenciada pelo cliente é implementado e configurado com um uplink para a rede pública e uma interface que é designada para a rede privada. Para obter mais informações sobre os Gateways do NSX Edge Services que são implementados como parte da solução, consulte [Arquitetura da solução do NSX Edge Services Gateway](/docs/services/vmwaresolutions/services?topic=vmware-solutions-nsx_overview#nsx_overview).

Os administradores em nuvem podem configurar quaisquer componentes NSX necessários, como o Distributed Logical Router (DLR), os comutadores lógicos e os firewalls. Os recursos do NSX disponíveis dependem da edição de licença do NSX escolhida ao pedir a instância. Para obter mais informações, veja [Comparação de edição do VMware NSX Edition](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix#vmware-nsx-edition-comparison).

O NSX Manager é instalado com as especificações que estão listadas na tabela a seguir.

Tabela 3. Requisitos do NSX Manager

| Atributo       | Especificação |
|:--------------- |:------------- |
| Gerenciador NSX     | Dispositivo Virtual |
| Número de vCPUs | 4 |
| Memória          | 16 GB |
| Disco            | 60 GB no compartilhamento do NFS de gerenciamento |
| Tipo de disco       | Thin-provisioned |
| Rede         | **Privada A** móvel designada a componentes de gerenciamento |

### Design do comutador distribuído
{: #design_virtualinfrastructure-distr-switch}

O design usa um número mínimo de Comutadores vDS. Os hosts no cluster são conectados às redes pública e privada. Os hosts são configurados com dois comutadores virtuais distribuídos. O uso de dois comutadores segue a prática de rede do {{site.data.keyword.cloud_notm}} que separa as redes pública e privada. O diagrama a seguir mostra o design do vDS.

![Design de comutador distribuído](../../images/vcsv4radiagrams-distributed-switch-design.svg "Design de comutador distribuído")

Conforme mostrado na figura anterior, um vDS é configurado para a conectividade de rede pública (SDDC-Dswitch-Public) e o outro vDS é configurado para conectividade de rede privada (SDDC-Dswitch-Private). A separação de diferentes tipos de tráfego é necessária para reduzir a contenção e a latência e aumentar a segurança.

As VLANs são usadas para segmentar funções de rede física. Esse design usa três VLANs: duas para tráfego de rede privada e uma para tráfego de rede pública. A tabela a seguir mostra a separação de tráfego.

Tabela 4. Mapeamento de VLAN para tipos de tráfego

| VLAN  | Designação | Tipo de tráfego |
|:----- |:----------- |:------------ |
| VLAN 1 | Privada A   | Gerenciamento de ESXi, gerenciamento, VXLAN (VTEP) |
| VLAN 2 | Privada B   | vSAN, NFS e vMotion|
| VLAN 3 | Pública      | Disponível para acesso à Internet |

O tráfego de cargas de trabalho circulará em comutadores lógicos suportados pelo VXLAN.

O cluster do vSphere usa dois vSphere Distributed Switches que são configurados como nas tabelas a seguir. 

Tabela 5. Comutadores distribuídos de cluster convergido

| vSphere Distributed<br>Nome do comutador | Função | Rede<br>Controle de E/S | Balanceamento de Car<br>Modo | NIC Físico<br>Portas | MTU |
|:------------- |:------------- |:------------- |:------------- |:------------- |:------------- |
| SDDC-Dswitch-Privado | Gerenciamento do ESXi, vSAN, vSphere vMotion, terminal de túnel VXLAN, NFS (VTEP) | Ativado | Rota com base em failover explícito (vSAN, vMotion) originando porta virtual (tudo o mais) | 2 | 9.000<br>(Molduras Jumbo) |
| SDDC-Dswitch-Public | Tráfego de gerenciamento externo (norte-sul) | Ativado | Rota com base na porta virtual de origem | 2 | 1.500<br>(padrão) |

Os nomes, o número e a ordenação dos NICs do host podem variar dependendo do {{site.data.keyword.CloudDataCent_notm}} e da seleção de hardware do host.
{:note}

Tabela 6. Definições de configuração de grupo da porta do comutador distribuído do cluster convergido

| Parâmetro          | Configuração       |
|:------------------ |:------------- |
| Balanceamento de     | Rota baseada na porta virtual de origem \* |
| Detecção de Failover | Somente status do link |
| Notificar comutadores    | Ativado |
| Failback           | Não |
| Ordem de Failover     | Uplinks ativos: Uplink1, Uplink2 \* |

\ * O grupo de portas do vSAN usa failover explícito com ativo ou espera porque ele não suporta o balanceamento de carga do tráfego de armazenamento vSAN.
{:note}

Tabela 7. Grupos de portas do comutador virtual de cluster convergido e VLANs, Comutador distribuído **SDDC-Dswitch-Private**

Grupo da porta|Equipe|Uplinks|ID de VLAN
---|---|---|--
SDDC-DPortGroup-Mgmt|Porta virtual de origem|Ativo: 0, 1|VLAN 1
SDDC-DPortGroup-vMotion|Porta virtual de origem|Ativo: 0, 1|VLAN 2
SDDC-DPortGroup-VSAN|Failover explícito|Ativo: 0, Standby: 1|VLAN 2
SDDC-DPortGroup-NFS|Porta virtual de origem|Ativo: 0, 1|VLAN 2
Gerado por NSX|Porta virtual de origem|Ativo: 0, 1|VLAN 1
SDDC-DPortGroup-External|Porta virtual de origem|Ativo: 0, 1|VLAN 3

Tabela 8. Adaptadores do VMkernel do cluster convergido, Comutador distribuído **SDDC-Dswitch-Private**

Propósito|Grupo de portas conectadas|Serviços Ativados|MTU
--|---|---|---|--
Gerenciamento|SDDC-DPortGroup-Mgmt|Tráfego de Gerenciamento|1500 (padrão)
vMotion|SDDC-DPortGroup-vMotion|Tráfego de vMotion|9000
VTEP|Gerado por NSX|-|9000
vSAN|SDDC-DPortGroup-VSAN|vSAN|9000
NAS|SDDC-DPortGroup-NFS|NAS|9000

### Configuração do NSX
{: #design_virtualinfrastructure-nsx-config}

Esse design especifica a configuração de componentes NSX, mas não aplica nenhuma configuração de componente de sobreposição de rede. É possível projetar a sobreposição de rede com base em suas necessidades.

Os aspectos a seguir são pré-configurados:
* Os servidores de gerenciamento e controladores são instalados e integrados à IU da web do vCenter
* Os agentes ESXi são instalados e os endereços IP do VTEP são configurados por host ESXi
* Configuração do VTEP, configuração do controlador e configuração de VXLAN (zona de transporte)
* Dispositivos NSX Edge Services Gateway para uso por componentes de gerenciamento
* Dispositivos do NSX Edge Services Gateway para uso do cliente
* Cargas de trabalho do cliente de trabalho da NSX VXLAN conectadas a um roteador local distribuído (DLR) com uma VXLAN de trânsito entre o DLR e o ESG do cliente.
* Espaço de endereço do RFC 1918 para as VXLANs e espaço de IP móvel privado e público do IBM Cloud para uso como rede de egresso no ESG do cliente.

Os aspectos a seguir não estão configurados:
* Micro segmentação
* Gerenciamento do NSX vinculado para outras instâncias do VMware

![Exemplo de topologia NSX de cliente implementada](../../images/vcsv4radiagrams-ra-vcs-nsx-topology-customer-example.svg "Exemplo de topologia NSX de cliente implementada")

## Conectividade de rede pública

Há vários motivos pelos quais você pode precisar de conectividade de rede pública para sua instância. Isso pode incluir acesso aos serviços de atualização pública ou a outros serviços públicos para sua carga de trabalho, como bancos de dados de localização geográfica ou dados de clima. Seus serviços de gerenciamento de virtualização e complementares também podem requerer ou se beneficiar da conectividade pública. Por exemplo, o vCenter pode atualizar seu banco de dados HCL e obter atualizações do [VMware Update Manager (VUM)](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro) por meio da rede pública. O Zerto, o Veeam, o VMware HCX, o F5 BIG-IP e o FortiGate-VM usam, todos, a conectividade de rede pública para alguma parte de seu licenciamento de produto, ativação ou relatório de uso. Além disso, você pode usar túneis por meio da rede pública para conectividade com o seu data center no local para propósitos de replicação.

Geralmente, essas comunicações são roteadas seletivamente e em NAT para a rede pública por meio do edge services gateway (ESG) de gerenciamento ou do cliente. No entanto, você pode ter mais requisitos de segurança ou pode preferir usar um proxy para simplificar o caminho da comunicação. Além disso, se você implementou sua instância com interfaces públicas desativadas, não será possível usar ESGs para rotear para a rede pública.

Essa arquitetura permite as opções a seguir para roteamento ou proxying de seu tráfego para a rede pública:

Método|Descrição|Limitações
--|--|--
Gateway virtualizado|Implemente um gateway virtualizado (por exemplo, NSX ESG, F5 BIG-IP, FortiGate-VM ou um dispositivo virtual de sua escolha) cruzando as redes privada e pública. Configure o roteamento no sistema de origem (por exemplo, vCenter, Zerto, sua carga de trabalho) para direcionar somente o tráfego de rede pública para o gateway e configure o gateway de acordo com suas necessidades.|Aplicável somente a instâncias com interfaces públicas ativadas. Essa configuração permite os padrões de tráfego de saída e de entrada.
Gateway virtualizado com proxy|Implemente um gateway virtualizado como acima. Atrás desse gateway, [implemente um servidor proxy](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config) e configure seus serviços e aplicativos para se conectar à rede pública por meio desse proxy.|Aplicável somente a instâncias com interfaces públicas ativadas. Os padrões de tráfego de saída podem usar o proxy, mas os padrões de tráfego de entrada devem ser gerenciados no gateway.
Gateway de hardware|Implemente um [dispositivo de gateway de hardware](https://cloud.ibm.com/catalog/infrastructure/gateway-appliance) em sua VLAN de gerenciamento. Configure o gateway para a saída NAT para a rede pública de acordo com suas necessidades.|Aplicável a todas as instâncias, com ou sem interfaces públicas ativadas. Essa configuração permite os padrões de tráfego de saída e de entrada.
Gateway de hardware com proxy|Implemente um dispositivo de gateway como acima. Atrás desse gateway, [implemente um servidor proxy](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config) e configure seus serviços e aplicativos para se conectar à rede pública por meio desse proxy.|Aplicável a todas as instâncias, com ou sem interfaces públicas ativadas. Os padrões de tráfego de saída podem usar o proxy, mas os padrões de tráfego de entrada devem ser gerenciados pelo gateway.
Balanceador de carga|O IBM Cloud oferece vários [serviços do balanceador de carga](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group) que podem ser usados para fornecer acesso à rede de entrada para seus aplicativos.|Aplicável a todas as instâncias, mas limitado a padrões de tráfego de entrada.

## Links relacionados
{: #design_virtualinfrastructure-related}

* [ {{site.data.keyword.cloud_notm}}  executando a arquitetura de solução de clusters VMware ](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf)
* [ Arquitetura da solução do NSX Edge Services Gateway ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-nsx_overview#nsx_overview)
