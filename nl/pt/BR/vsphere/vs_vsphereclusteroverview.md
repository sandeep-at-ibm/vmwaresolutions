---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do VMware vSphere on IBM Cloud

O VMware vSphere on {{site.data.keyword.cloud}} é uma plataforma de ordenação aperfeiçoada e otimizada para VMware. Com essa plataforma, é possível construir seu próprio ambiente VMware hospedado pela IBM customizando e ordenando o hardware compatível com VMware com base em seus componentes selecionados do VMware.

O console do {{site.data.keyword.vmwaresolutions_short}} filtra o hardware automaticamente, com base nos componentes do VMware que você selecionar. Por exemplo, ao criar um novo cluster flash do VMware vSAN, apenas o hardware que é validado com relação ao [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) é apresentado. Além disso, um mínimo de quatro servidores ESXi é necessário.

O VMware vSphere on {{site.data.keyword.cloud_notm}} não automatiza a instalação, a configuração e a ativação dos componentes opcionais do VMware. A plataforma permite o máximo de flexibilidade para projetar e construir seu ambiente VMware hospedado enquanto incorpora o hardware compatível com VMware.

Use essa oferta para criar um novo cluster de servidores ESXi ou ajuste a escala de um cluster existente de servidores ESXi em um {{site.data.keyword.CloudDataCent_notm}}. Dependendo dos componentes do VMware que você selecionar, será possível começar com apenas um servidor ESXi e, em seguida, escalar o cluster posteriormente conforme necessário.

## Especificações técnicas para clusters do VMware vSphere on IBM Cloud

Revise os componentes do VMware vSphere on {{site.data.keyword.cloud_notm}}.

A disponibilidade e a precificação de configurações padronizadas de hardware podem variar com base no {{site.data.keyword.CloudDataCent_notm}} que é selecionado para implementação.
{:note}

### Componentes do VMware

Selecione licenças (fornecidas pela IBM ou BYOL) para os seguintes componentes do VMware:
* VMware vSphere Enterprise Plus 6.0u2, 6.5u1 ou 6.5u2
* Os componentes do VMware a seguir são opcionais:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced ou Enterprise)
   * VMware vSAN (Advanced ou Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

Selecione um ou mais {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} com seu modelo de CPU e tamanho de RAM selecionados:
* Geração Intel Skylake de 2 CPUs (série Intel Xeon 4100/5100/6100)
* Certificado pela SAP (Série Intel Xeon 6140/E5-2690/E7-8890)
* Geração Intel Broadwell de 2 CPUs (Série Intel Xeon E5-2600/E7-4800)

As opções disponíveis dependem de se você selecionou o componente vSAN do VMware.

Além disso, as especificações de disco e de rede a seguir:
* Uplinks duais de rede pública e privada de 10 Gbps
* Um controlador de disco RAID

### Redes

* Uma VLAN pública de VLAN (Virtual LAN) e duas VLANs privadas
* (Opcional) Um par de HA de dispositivos do FortiGate Security Appliance

### Armazenamento

Armazenamento customizado pelo usuário para configuração vSAN quando o componente vSAN do VMware é selecionado:
* Opções de disco de armazenamento de 960 GB SSD SED, 1,9 TB SSD SED ou 3,8 TB SSD SED
* Opções de quantidade de disco de 2, 4, 6 ou 8

  Além disso, também são pedidos dois discos de cache de 960 GB por host.

  As unidades SSD (Disco de Estado Sólido) de 3,8 TB são suportadas quando são geralmente disponibilizadas em um data center.
  {:note}
* Opção Intel Optane de alto desempenho, que fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade. Essa opção depende do modelo de CPU.

## Especificações técnicas para nós de expansão de cluster do vSphere

Cada nó de expansão de cluster do vSphere é implementado e incorre em encargos para os seguintes componentes em sua conta do {{site.data.keyword.slportal}}.

### Hardware para nós de expansão

Um {{site.data.keyword.cloud_notm}} Bare Metal Server com a configuração de hardware apresentada em
[Especificações técnicas para clusters do VMware vSphere on {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Rede para nós de expansão

Um {{site.data.keyword.cloud_notm}} Bare Metal Server com a configuração de rede apresentada nas
[Especificações
técnicas para clusters do VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Componentes do VMware para nós de expansão

* Um {{site.data.keyword.cloud_notm}} Bare Metal Server com o VMware vSphere Enterprise Plus 6.0u2 ou 6.5u1  
* Componentes opcionais do VMware apresentados nas
[Especificações
técnicas para clusters do VMware vSphere on {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

Deve-se gerenciar os servidores ESXi, os componentes opcionais do VMware e o hardware adicional que são pedidos e entregues à sua conta do {{site.data.keyword.cloud_notm}} somente por meio do {{site.data.keyword.slportal}}. Depois de criar um novo cluster no console do {{site.data.keyword.vmwaresolutions_short}}, é possível retornar para o console e usar as informações salvas para escalar o novo cluster. Para obter mais informações, consulte [Ajustando a escala de clusters existentes do
vSphere](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html).
{:important}

### Links relacionados

* [Lista de materiais de software do VMware vSphere](/docs/services/vmwaresolutions/vsphere/vs_bom.html)
* [Planejando clusters do vSphere](/docs/services/vmwaresolutions/vsphere/vs_planning.html)
* [Pedindo clusters do vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [Ajustando a escala dos clusters do vSphere existentes](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)
