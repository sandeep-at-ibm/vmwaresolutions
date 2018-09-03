---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Visão geral do VMware vSphere on IBM Cloud

O VMware vSphere on {{site.data.keyword.cloud}} é uma plataforma de ordenação aperfeiçoada e otimizada para VMware. Com essa plataforma, é possível construir seu próprio ambiente VMware hospedado pela IBM customizando e ordenando o hardware compatível com VMware com base em seus componentes selecionados do VMware.

O console do {{site.data.keyword.vmwaresolutions_short}} filtra o hardware automaticamente, com base nos componentes do VMware que você selecionar. Por exemplo, ao criar um novo cluster flash do VMware vSAN, apenas o hardware que é validado com relação ao [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) é apresentado. Além disso, um mínimo de quatro servidores ESXi é necessário.

O VMware vSphere on {{site.data.keyword.cloud_notm}} não automatiza a instalação, a configuração e a ativação dos componentes opcionais do VMware. A plataforma permite o máximo de flexibilidade para projetar e construir seu ambiente VMware hospedado enquanto incorpora o hardware compatível com VMware.

Use essa oferta para criar um novo cluster de servidores ESXi ou ajuste a escala de um cluster existente de servidores ESXi em um {{site.data.keyword.CloudDataCent_notm}}. Dependendo dos componentes do VMware que você selecionar, será possível começar com apenas um servidor ESXi e, em seguida, escalar o cluster posteriormente conforme necessário.

## Especificações técnicas para clusters do VMware vSphere on IBM Cloud

Revise os componentes do VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Nota**: a disponibilidade e a precificação de configurações de hardware padronizadas podem variar com base no {{site.data.keyword.CloudDataCent_notm}} selecionado para implementação.

### Componentes do VMware

Licenças (fornecidas pela IBM ou BYOL) para os seguintes componentes do VMware:
* VMware vSphere Enterprise Plus 6.0u2 ou 6.5u1
* Componentes opcionais do VMware:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced ou Enterprise)
   * VMware vSAN (Advanced ou Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

Um ou mais {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} com seu modelo de CPU selecionado e tamanho de RAM:
* Geração Intel Broadwell de 2 CPUs (Série Intel Xeon E5-2600 v4)
* Geração Intel Skylake de 2 CPUs (série Intel Xeon 4100/5100/6100)

As opções disponíveis dependem de se você selecionou o componente vSAN do VMware.

Além disso, as especificações de disco e rede a seguir:
* Uplinks duais de rede pública e privada de 10 Gbps
* Um controlador de disco RAID

### Redes

* Três VLANs (Virtual LANs): uma VLAN pública e duas VLANs privadas
* (Opcional) Um par de HA de dispositivos do FortiGate Security Appliance

### Armazenamento

Armazenamento customizado pelo usuário para configuração vSAN quando o componente vSAN do VMware é selecionado:
* Opções de disco de armazenamento: SSD SED de 960 GB, SSD SED de 1,9 TB ou SSD SED de 3,8 TB
* Opções de quantidade de discos: 2, 4, 6 ou 8

**Nota:** as unidades SSD (Solid State Disk) de 3,8 TB serão suportadas quando forem disponibilizadas geralmente em um data center.

## Especificações técnicas para nós de expansão de cluster do vSphere

Cada nó de expansão do cluster do vSphere implementará e incorrerá em encargos para os seguintes componentes em sua conta {{site.data.keyword.slportal}}.

### Hardware para nós de expansão

Um Bare Metal Server {{site.data.keyword.cloud_notm}} com a configuração de hardware apresentada em [Especificações técnicas para clusters do VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Rede para nós de expansão

Um Bare Metal Server {{site.data.keyword.cloud_notm}} com a configuração de rede apresentada em [Especificações técnicas para clusters do VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Componentes do VMware para nós de expansão

* Um {{site.data.keyword.cloud_notm}} Bare Metal Server com o VMware vSphere Enterprise Plus 6.0u2 ou 6.5u1  
* Componentes opcionais do VMware apresentados em [Especificações técnicas para clusters do VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

**Importante**: deve-se gerenciar os servidores ESXi, componentes opcionais do VMware e hardware adicional que são pedidos e entregues à sua conta {{site.data.keyword.cloud_notm}} apenas no {{site.data.keyword.slportal}}. Depois de criar um novo cluster no console do {{site.data.keyword.vmwaresolutions_short}}, é possível retornar ao console para escalar o novo cluster usando a configuração salva. Para obter mais informações, consulte [Ajustando a escala de clusters existentes do
vSphere](vs_scalingexistingclusters.html).

### Links relacionados

* [Lista de materiais de software do VMware vSphere](vs_bom.html)
* [Planejando clusters do vSphere](vs_planning.html)
* [Pedindo clusters do vSphere](vs_orderinginstances.html)
* [Ajustando a escala de clusters existentes do vSphere](vs_scalingexistingclusters.html)
