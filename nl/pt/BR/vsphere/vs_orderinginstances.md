---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vSphere order cluster, order vSphere, order vSphere cluster

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo novos clusters do vSphere
{: #vs_orderinginstances}

Para implementar uma plataforma virtualizada VMware altamente customizável, peça um cluster do VMware vSphere no {{site.data.keyword.cloud}}. Use este procedimento para definir um novo cluster do vSphere.

Este procedimento orienta você através da seleção de componentes do VMware, de configurações do Bare Metal Server, configurações de armazenamento e opções de rede do {{site.data.keyword.cloud_notm}}, para criar um novo cluster. Depois de fazer o pedido, a configuração de cluster é capturada para que seja possível voltar e continuar a ajustar a escala do cluster, conforme necessário. Depois que o pedido for concluído, será possível configurar manualmente o cluster do VMware com base em seus requisitos.

## Requisitos
{: #vs_orderinginstances-req}

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Você revisou os requisitos e as considerações em [Requisitos e planejamento para clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Configurações do sistema
{: #vs_orderinginstances-sys-settings}

Deve-se especificar as configurações do sistema a seguir ao solicitar um novo cluster do vSphere.

### Nome do cluster
{: #vs_orderinginstances-cluster-name}

O nome do cluster deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O nome do cluster deve começar com um caractere alfabético minúsculo.
* O nome do cluster deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do nome do cluster é de 10 caracteres.
* O nome do cluster deve ser exclusivo dentro de sua conta.

## Configurações de licenciamento
{: #vs_orderinginstances-licensing-settings}

Selecione os componentes do VMware a serem pedidos com seu cluster e especifique a opção de licenciamento para os componentes.

### Pacotes configuráveis de componentes para usuários do Parceiro de Negócios IBM
{: #vs_orderinginstances-component-bundles-for-bp-users}

Se você for um usuário do Parceiro de Negócios IBM, será possível selecionar um pacote configurável de licença do componente ao pedir um novo cluster do vSphere. Os pacotes configuráveis a seguir estão disponíveis:

| Pacote configurável | Componentes                   |
|:------------------------- |:----------------------- |
| Padrão com Gerenciamento | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Avançado                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Avançado com Rede | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Avançado com Rede e Gerenciamento | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |
{: caption="Tabela 1. Pacotes configuráveis de componentes do Parceiro de Negócios IBM para clusters do vSphere" caption-side="top"}

Também é possível incluir os seguintes componentes do VMware em seu pedido:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

Para usuários do Parceiro de Negócios IBM, a opção Bring Your Own License (BYOL) não está disponível.
{:note}

### Componentes individuais para usuários do Parceiro de Negócios
{: #vs_orderinginstances-individual-components-for-non-bp-users}

Se você não for um Parceiro de Negócios, será possível selecionar os componentes a seguir para seu cluster do vSphere:
* VMware vSphere Enterprise Plus 6.7 U2 ou 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

O componente VMware vSAN não está disponível quando você pede o VMware vSphere Enterprise Plus 6.0. Se você planeja usar sua própria licença para o VMware vSphere Enterprise Plus 6.0, um chamado de infraestrutura do {{site.data.keyword.cloud_notm}} será aberto em seu nome. O chamado solicita que as licenças vSphere do {{site.data.keyword.baremetal_short}} solicitado sejam substituídas por suas licenças fornecidas.
{:note}

### Opções de Licenciamento
{: #vs_orderinginstances-licensing-options}

Você tem as seguintes opções para licenciamento dos componentes do VMware selecionados:
* **incluir a licença com a compra**: neste caso, uma nova licença para o componente do VMware é comprada em seu nome. Uma licença do VMware combinada é gerada para corresponder ao tamanho do cluster do pedido.
* **Eu fornecerei a licença**: neste caso, você usará a sua própria licença para o componente do VMware.

Se você optar por comprar qualquer licença, exceto para o vSphere Enterprise Plus e o vCenter Server, e pedir vários servidores ESXi, um chamado do {{site.data.keyword.cloud_notm}} será aberto automaticamente em seu nome para combinar as chaves de licença. Você é responsável por acompanhar o chamado para assegurar que você use apenas as chaves de licença geradas pela equipe do DevOps.

O uso de chaves de licença individuais junto com as chaves de licença combinadas não atende aos requisitos de pagamento para as licenças que você precisará.
{:important}

## Configurações do Bare Metal Server
{: #vs_orderinginstances-bare-metal-settings}

### Local do data center
{: #vs_orderinginstances-dc-location}

Selecione o {{site.data.keyword.CloudDataCent_notm}} em que o cluster deve ser hospedado.

#### Notas
{: #vs_orderinginstances-notes}

* Se você selecionar um componente vSAN, a lista de locais será filtrada pela disponibilidade do SSD.
* Os Broadwell Bare Metal Servers não estão disponíveis para o local do Data Center **FRA05 - Frankfurt**.
* Os Broadwell Bare Metal Servers certificados pela SAP não estão disponíveis para o local do Data Center **LON05 - Londres**.

### Skylake
{: #vs_orderinginstances-skylake}

Quando você seleciona **Skylake**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades. As opções disponíveis dependem de se você selecionou o componente vSAN do VMware.

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabela 2. Opções para o Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Cascade
{: #vs_orderinginstance-cascade}

Para a configuração **Cascade**, você tem opções para o **Modelo de CPU** e **RAM**.

Os {{site.data.keyword.baremetal_short}} Cascade estão disponíveis somente para instâncias do VMware vSphere Enterprise Plus 6.7 U2.
{:note}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Gold 4210/Total de 20 núcleos, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5218/Total de 32 núcleos, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6248/Total de 40 núcleos, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
{: caption="Tabela 3. Opções para {{site.data.keyword.baremetal_short}} Cascade" caption-side="top"}

### SAP-certificado
{: #vs_orderinginstances-sap}

A guia **Certificado pelo SAP** não estará disponível se você tiver selecionado VMware vSAN anteriormente. Quando você seleciona **Certificado por SAP**, não é possível alterar as configurações de CPU ou RAM.

Com base em seus requisitos, selecione uma configuração do Bare Metal Server:
  * Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 192 GB de RAM
  * Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 384 GB de RAM
  * Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 768 GB de RAM
  * Processador Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM
  * Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/1024 GB de RAM
  * Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/2048 GB de RAM
  * Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/4096 GB de RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

Quando você seleciona **Broadwell**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades. As opções disponíveis dependem de se você selecionou o componente vSAN do VMware.

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabela 4. Opções para {{site.data.keyword.baremetal_short}} Broadwell" caption-side="top"}

### Número de Bare Metal Servers
{: #vs_orderinginstances-bare-metal-number}

O número de servidores ESXi que você deseja incluir no cluster do vSphere. Todos os servidores ESXi possuem a mesma configuração.
* Se você selecionou o componente VMware NSX, um mínimo de três servidores é necessário.
* Se você selecionou o componente VMware vSAN, um mínimo de quatro servidores é necessário.

## Configurações de armazenamento
{: #vs_orderinginstances-storage-settings}

Para pedidos sem vSAN, os servidores ESXi são pedidos com um chassi de 12 discos, com dois discos para o sistema operacional (S.O.) ESXi.

Para pedidos com vSAN, os servidores ESXi são pedidos com um chassi de 12 discos e quatro discos pedidos: dois para o S.O. ESXi e dois reservados para armazenamento em cache. Essas configurações são definidas por padrão e não podem ser mudadas. É possível pedir mais discos de capacidade selecionando **Tipo e tamanho do disco para discos de capacidade do vSAN** e **Número de discos de capacidade do vSAN**.

Se você selecionar o componente VMware vSAN para o cluster, especifique as configurações a seguir.
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade além do limite de oito, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e maior rendimento de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível somente para os modelos de CPU Skylake e Cascade.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.

## Configurações da interface de rede
{: #vs_orderinginstances-network-interface-settings}

Deve-se especificar as configurações de interface de rede a seguir quando solicitar um novo cluster do vSphere.

### Prefixo de nome do host
{: #vs_orderinginstances-host-name-prefix}

O nome do host é usado para todos os pedidos do Bare Metal Server. É recomendável usar o nome do host para todas as máquinas virtuais de gerenciamento, como o vCenter Server e o NSX.

O prefixo de nome do host deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O prefixo do nome do host deve começar com um caractere alfabético minúsculo.
* O prefixo do nome do host deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do prefixo do nome do host é de 10 caracteres.

### Rótulo do subdomínio
{: #vs_orderinginstances-subdomain-label}

O rótulo do subdomínio deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O rótulo do subdomínio deve começar com um caractere alfabético minúsculo.
* O rótulo do subdomínio deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do rótulo do subdomínio é de 10 caracteres.

### Nome de domínio
{: #vs_orderinginstances-domain-name}

O nome de domínio é usado para todos os {{site.data.keyword.baremetal_short}} e deve atender aos seguintes requisitos:
* O nome de domínio deve consistir em duas ou mais sequências separadas por ponto (.)
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* Cada sequência deve começar com um caractere alfabético minúsculo e terminar com um caractere alfabético minúsculo ou numérico.
* A última sequência pode conter somente caracteres alfabéticos minúsculos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.
* O comprimento das outras sequências deve estar no intervalo de 1 a 63 caracteres.
* O comprimento máximo do nome de domínio é de 189 caracteres.

### Rede pública ou privada
{: #vs_orderinginstances-public-private-network}

As configurações de ativação da Placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**.

### VLANs
{: #vs_orderinginstances-vlans}

As configurações de rede se baseiam em sua seleção de **Pedir novas VLANs** ou **Selecionar VLANs existentes**.

#### Pedir novas VLANs
{: #vs_orderinginstances-new-vlans}

Se você estiver pedindo uma rede pública e privada, uma VLAN pública e duas VLANs privadas serão necessárias para o pedido do cluster. As duas VLANs privadas são truncadas em cada Bare Metal Server.

Se você estiver pedindo uma rede privada, somente duas VLANs privadas serão necessárias para o pedido do cluster.

#### Selecionar VLANs existentes
{: #vs_orderinginstances-existing-vlans}

Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

  Ao selecionar para reutilizar VLANs públicas e privadas existentes, especifique as VLANs e as sub-redes:
  * **VLAN pública** é para acesso à rede pública.
  * **Sub-rede primária** é designada a hosts físicos para o acesso à rede pública.
  * **VLAN privada** é para conectividade entre os data centers e os serviços dentro do {{site.data.keyword.cloud_notm}}.
  * **VLAN privada secundária** é para recursos do VMware, como vSAN.
  * **Sub-rede primária privada** é designada a hosts físicos para tráfego de gerenciamento.

##### Importante
{: #vs_orderinginstances-important}

* Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento.
* Assegure-se de que todas as VLANs que você selecionar estejam no mesmo pod. Os servidores ESXi não podem ser provisionados em VLANs de pod misto.

#### Par de HA do FortiGate Physical Appliance série 300
{: #vs_orderinginstances-fortigate-physical-appliance}

É possível também selecionar se deseja incluir o Par de HA do FortiGate Physical Appliance série 300 para assegurar seu ambiente de nuvem. Para obter mais informações, consulte [Visão geral do FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations).

Essa opção está disponível somente para um pedido com uma rede pública e privada.
{:note}

## Resumo do Pedido
{: #vs_orderinginstances-order-summary}

Com base em sua configuração selecionada, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**. Clique em **Detalhes da precificação** para gerar um documento PDF com o resumo de custo dos recursos do {{site.data.keyword.vmwaresolutions_short}}.

Também é possível incluir os recursos provisionados na ferramenta de estimativa do {{site.data.keyword.cloud_notm}}, clicando em **Incluir na estimativa**. Isso é útil se você desejar estimar o custo dos recursos do {{site.data.keyword.vmwaresolutions_short}} selecionados com outros recursos do {{site.data.keyword.cloud_notm}} que você talvez considere comprar.

## Procedimento para pedir clusters do vSphere
{: #vs_orderinginstances-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** da área de janela de navegação esquerda e, em seguida, clique no cartão **VMware vSphere on IBM Cloud** da seção **Data centers virtuais do VMware**.
2. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.  
   Assegure-se de que está na guia **Criar novo** e que **Novo cluster** está exibido na lista **Configurações de cluster**.
3. Insira o nome do cluster.
4. Selecione os componentes do VMware:
  * Se você for um Parceiro de Negócios IBM, selecione um pacote configurável de licença e quaisquer componentes adicionais do VMware disponíveis.
  * Se você for um Parceiro não Comercial, selecione o componente, a edição, se houver alguma, e especifique a opção de licenciamento.
  Quando você escolhe Bring Your Own License (BYOL) para o VMware vSphere Enterprise Plus, um chamado {{site.data.keyword.cloud_notm}} é aberto automaticamente em seu nome para solicitar que as licenças padrão do vSphere no seu {{site.data.keyword.baremetal_short}} pedido sejam substituídas por suas licenças fornecidas.   

    **Importante:** você é responsável por rastrear o chamado para que você substitua a licença do vSphere nos servidores ESXi recém-ordenados. Dessa forma, a infraestrutura do {{site.data.keyword.cloud_notm}} concede o cancelamento do encargo de licença do vSphere da infraestrutura do {{site.data.keyword.cloud_notm}} inicialmente fornecida. Para substituir sua licença ESXi vSphere, veja [Definir Configurações da Licença para um Host ESXi](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:external}.
5. Conclua as configurações do Bare Metal Server:
   1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar o cluster.
   2. Selecione a configuração do Bare Metal Server.
      * Quando você selecionar **Skylake**, **Cascade** ou **Broadwell**, especifique o modelo de CPU e o tamanho de RAM.
      * Quando você selecionar **Certificado pelo SAP**, escolha uma das configurações pré-configuradas.
   3. Especifique o número de Bare Metal Servers.
6. Se você selecionou o componente **VMware vSAN**, conclua a configuração de armazenamento vSAN. Especifique os tipos de disco para os discos de capacidade e de cache, além do número de discos. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
7. Conclua as configurações da interface de rede:
   1. Insira o prefixo de nome do host, o rótulo do subdomínio e o nome de domínio.
   2. Selecione a configuração de rede de **Rede pública e privada** ou **Somente rede privada**.
   3. Selecione a interface de rede que você deseja usar.
    * Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
    * Se você desejar reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e especifique as VLANs e, opcionalmente, as sub-redes.
    4. Se você estiver pedindo VLANS públicas, especifique se deseja aplicar o Par de Alta Disponibilidade do FortiGate Physical Appliance 300 Series para proteger seu ambiente de nuvem.
8. Na área de janela **Resumo**, verifique a configuração de cluster e o custo estimado.
   * Para salvar a configuração como um modelo sem fazer um pedido, clique em **Salvar configuração**.
   * Para fazer o pedido, assegure-se de que a conta a ser cobrada está correta, revise e aceite os termos e, em seguida, clique em **Provisão**.

   Somente os {{site.data.keyword.baremetal_short}} estão instalados. Você é responsável por instalar e configurar vários componentes após a implementação do cluster, como VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

### Resultados depois de pedir clusters do vSphere
{: #vs_orderinginstances-results}

Se você salvou a configuração de cluster como um modelo, obterá uma notificação do console de que a configuração foi salva com êxito e então será possível localizar o modelo na lista **Configurações de cluster**.

Se tiver feito um pedido, a implementação do cluster será iniciada automaticamente e você receberá uma confirmação por e-mail de que o pedido está sendo processado. Quando o cluster estiver pronto para usar, você será notificado por e-mail.

Os clusters do vSphere, ao contrário das instâncias do vCenter Server, não são exibidos na página **Recursos**.
{:note}

## Links relacionados
{: #vs_orderinginstances-related}

* [Pedindo clusters do vSphere com base nas configurações existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Ajustando a escala de clusters existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Ajustando a escala de clusters criados fora do console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
