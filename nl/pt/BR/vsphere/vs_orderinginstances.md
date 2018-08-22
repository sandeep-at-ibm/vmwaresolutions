---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

{:tip: .tip}

# Pedindo novos clusters do vSphere

Para implementar uma plataforma virtualizada VMware altamente customizável, peça um cluster do VMware vSphere no {{site.data.keyword.cloud}}. Use este procedimento para definir um novo cluster do VMware vSphere.

Este procedimento guia você pela seleção de componente do VMware, configurações do {{site.data.keyword.cloud_notm}} Bare Metal Server, configurações de armazenamento e opções de rede, para criar um novo cluster. Depois de fazer o pedido, a configuração de cluster é capturada para que seja possível voltar e continuar a ajustar a escala do cluster, conforme necessário. Quando a ordem for concluída, será possível configurar manualmente o cluster do VMware com base em seus requisitos.

## Requisitos

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](../vmonic/useraccount.html).
*  Você revisou os requisitos e as considerações em [Requisitos e planejamento para clusters do vSphere](vs_planning.html).

## Configurações do sistema

Deve-se especificar as configurações do sistema a seguir ao pedir um novo cluster do vSphere.

### Nome do cluster

O nome do cluster deve ser exclusivo dentro de sua conta.

## Configurações de licenciamento

Selecione os componentes do VMware a serem pedidos com seu cluster e especifique a opção de licenciamento para os componentes.

### (Somente para usuários do parceiro de negócios) Pacotes configuráveis de componentes

Se você é um usuário do parceiro de negócios, é possível selecionar um pacote configurável de licença de componente ao pedir um novo cluster do vSphere. Os pacotes configuráveis disponíveis são os seguintes:

Tabela 1. Pacotes configuráveis de componentes do parceiro de negócios para clusters do vSphere

| Pacote configurável | Componentes                   |
|:-------------------------|:-----------------------|
| Padrão com Gerenciamento | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Avançado                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Avançado com Rede | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Avançado com Rede e Gerenciamento | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

É possível também incluir os seguintes componentes adicionais do VMware em seu pedido:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

**Nota:** os usuários de parceiro de negócios não têm a opção de Bring Your Own License (BYOL). A opção **Eu fornecerei a licença** não está disponível ao concluir o seu pedido.

### (Somente para usuários não de parceiro de negócios) Componentes individuais

Se você é um usuário não de parceiro de negócios, é possível selecionar os componentes do VMware a seguir de modo flexível para seu cluster do vSphere:
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

**Nota:** o componente vSAN do VMware não está disponível quando você pede o VMware vSphere Enterprise Plus 6.0. Se você planeja usar sua própria licença para o VMware vSphere Enterprise Plus 6.0, um chamado de infraestrutura do {{site.data.keyword.cloud_notm}} será aberto em seu nome solicitando que as licenças do vSphere do {{site.data.keyword.baremetal_short}} pedido sejam substituídas pelas licenças fornecidas.

### Opções de Licenciamento

Você tem as seguintes opções para licenciamento dos componentes do VMware selecionados:
* **incluir a licença com a compra**: neste caso, uma nova licença para o componente do VMware é comprada em seu nome. Uma licença do VMware combinada é gerada para corresponder ao tamanho do cluster do pedido.
* **Eu fornecerei a licença**: neste caso, você usará sua própria licença para o componente do VMware.

Se você optar por comprar qualquer licença, exceto para o vSphere Enterprise Plus e o vCenter Server, e pedir vários servidores ESXi, um chamado do {{site.data.keyword.cloud_notm}} será aberto automaticamente em seu nome para combinar as chaves de licença. Você é responsável por acompanhar o chamado para assegurar que você use apenas as chaves de licença geradas pela equipe do DevOps.

**Importante**: usar chaves de licença individuais juntamente com as chaves de licença combinadas não atende aos requisitos de pagamento para as licenças que você precisará.

## Configurações do Bare Metal Server

### Local do datacenter

Selecione o {{site.data.keyword.CloudDataCent_notm}} em que o cluster deve ser hospedado.

**Nota:** se você selecionar um componente vSAN, a lista de local será filtrada por disponibilidade SSD.

### Modelo de CPU e RAM

Especifique o modelo de CPU e RAM para o Bare Metal Server.

Tabela 2. Opções para {{site.data.keyword.baremetal_short}} customizados

| Opções de CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

As opções disponíveis dependem de se você selecionou o componente vSAN do VMware.

### Número de Bare Metal Servers

O número de servidores ESXi que você deseja incluir no cluster do vSphere. Todos os servidores ESXi compartilham a mesma configuração.
* Se você selecionou o componente NSX do VMware, um mínimo de 3 servidores será necessário.
* Se você selecionou o componente vSAN do VMware, um mínimo de 4 servidores será necessário.

## Configurações de armazenamento

Para pedidos sem vSAN, os servidores ESXi são pedidos com um chassi de 12 discos, com dois discos para o sistema operacional (S.O.) ESXi.

Para pedidos com vSAN, os servidores ESXi são pedidos com um chassi de 12 discos e quatro discos pedidos: dois para o S.O. ESXi e dois reservados para armazenamento em cache. Essas configurações são definidas por padrão e não podem ser mudadas. É possível pedir mais discos de capacidade selecionando **Tipo e tamanho do disco para discos de capacidade do vSAN** e **Número de discos de capacidade do vSAN**.

Quando você tiver selecionado o componente VMware vSAN para o cluster, especifique as configurações a seguir.

### Tipo e tamanho do disco para discos de capacidade vSAN

Esta opção fica disponível somente ao selecionar o componente VMware vSAN.

Os seguintes tipos de discos estão disponíveis:
* SSD SED de 960 GB
* SSD SED de 1,9 TB
* SSD SED de 3,8 TB (Unidades SSD SED de 3,8 TB são suportadas quando são disponibilizadas geralmente em um data center)

### Número de discos de capacidade vSAN

Esta opção fica disponível somente ao selecionar o componente VMware vSAN. As opções de quantidade de discos incluem 2, 4, 6 e 8.

## Configurações da interface de rede

Deve-se especificar as configurações da interface de rede a seguir ao pedir um novo cluster do vSphere.

### Prefixo de nome do host

O nome do host é usado para todos os pedidos do servidor bare metal. Recomenda-se usar o nome do host para todas as máquinas virtuais de gerenciamento, como vCenter Server, NSX e assim por diante.

O prefixo de nome do host deve atender aos requisitos a seguir:
* O nome deve começar e terminar com um caractere alfanumérico.
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O comprimento máximo é de 10 caracteres.

### Rótulo do subdomínio

O rótulo do subdomínio deve atender aos requisitos a seguir:
*  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
*  O rótulo do subdomínio deve iniciar e terminar com um caractere alfanumérico.
*  O comprimento máximo do rótulo do subdomínio é de 10 caracteres.
*  O rótulo do subdomínio deve ser exclusivo em sua conta.

### Nome de domínio

O nome de domínio é usado para todos os {{site.data.keyword.baremetal_short}} e deve atender aos seguintes requisitos:
* O nome deve consistir em duas ou mais sequências separadas por ponto (.)
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* Cada sequência deve iniciar com um caractere alfabético e terminar com um caractere alfanumérico e a última sequência pode conter apenas caracteres alfabéticos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.
* O comprimento de outras sequências deve estar no intervalo de 1 a 63 caracteres.
* O comprimento máximo do nome de domínio é de 189 caracteres.

### VLANs

As configurações de rede se baseiam em sua seleção de **Pedir novas VLANs** ou **Selecionar VLANs existentes**.

Uma VLAN pública e duas VLANs privadas são necessárias para seu pedido de cluster. As duas VLANs privadas são truncadas em cada Bare Metal Server.

#### Pedir novas VLANs
Selecione para pedir uma nova VLAN pública e duas novas VLANs privadas.

#### Selecionar VLANs existentes  
Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

  Ao selecionar para reutilizar VLANs públicas e privadas existentes, especifique as VLANs e as sub-redes:
  * **VLAN pública** é para acesso à rede pública.
  * **VLAN privada** é para conectividade entre os data centers e os serviços dentro do {{site.data.keyword.cloud_notm}}.
  * **VLAN privada secundária** é para recursos do VMware, como vSAN.
  * **Sub-rede primária** é designada a hosts físicos para o acesso à rede pública.
  * **Sub-rede privada primária** é designada a hosts físicos para o tráfego de gerenciamento.

**Importante:**
* Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento.
* Assegure-se de que todas as VLANs selecionadas estejam no mesmo pod, porque os servidores ESXi não podem ser provisionados em VLANs de pod misto.

#### Par de HA do FortiGate Physical Appliance série 300

É possível também selecionar se deseja incluir o Par de HA do FortiGate Physical Appliance série 300 para assegurar seu ambiente de nuvem. Para obter mais informações, consulte [Visão geral do FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html).

## Resumo do Pedido

Com base em suas configurações, o custo estimado é gerado instantaneamente e exibido na área de janela **Resumo da ordem** à direita. Clique em **Detalhes de precificação** na parte inferior da área de janela para gerar um documento PDF que forneça os detalhes da estimativa.

## Procedimento

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **VMware vSphere** na seção **Data centers virtuais**.
2. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.  
   Assegure-se de que está na guia **Criar novo** e que **Novo cluster** está exibido na lista **Configurações de cluster**.
3. Insira o nome do cluster.
4. Selecione os componentes do VMware:
  * Se você for um usuário de parceiro de negócios, selecione um pacote configurável de licença e quaisquer componentes adicionais do VMware disponíveis.
  * Se você for um usuário não de parceiro de negócios, selecione o componente, a edição, se houver, e especifique a opção de licenciamento.
  Quando você escolhe Bring Your Own License (BYOL) para o VMware vSphere Enterprise Plus, um chamado {{site.data.keyword.cloud_notm}} é aberto automaticamente em seu nome para solicitar que as licenças padrão do vSphere no seu {{site.data.keyword.baremetal_short}} pedido sejam substituídas por suas licenças fornecidas.   

    **Importante:** você é responsável por acompanhar o chamado para assegurar-se de substituir a licença do vSphere nos servidores ESXi recém-pedidos para que a infraestrutura do {{site.data.keyword.cloud_notm}} conceda o cancelamento do encargo de licença do vSphere da infraestrutura do {{site.data.keyword.cloud_notm}} fornecida inicialmente. Para substituir sua licença ESXi vSphere, veja [Definir Configurações da Licença para um Host ESXi](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.

5. Conclua as configurações do Bare Metal Server:
   1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar o cluster.
   2. Selecione o modelo de CPU e o tamanho de RAM.
   3. Especifique o número de Bare Metal Server.
6. Se tiver selecionado o componente **VMware vSAN**, conclua as configurações de armazenamento de vSAN selecionando o **Tipo e tamanho do disco para discos de capacidade de vSAN** e **Número de discos de capacidade de vSAN**.
7. Conclua as configurações da interface de rede:
   1. Insira o prefixo de nome do host, o rótulo do subdomínio e o nome de domínio.
   2. Selecione a interface de rede usar:
    * Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
    * Se você desejar reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e especifique as VLANs e, opcionalmente, as sub-redes.
    3. Especifique se deseja aplicar o Par de HA do FortiGate Physical Appliance série 300 para assegurar seu ambiente de nuvem.  
8. Na área de janela **Resumo**, verifique a configuração de cluster e o custo estimado.
   * Para salvar a configuração como um modelo sem fazer um pedido, clique em **Salvar configuração**.
   * Para fazer o pedido, assegure-se de que a conta a ser cobrada está correta, revise e aceite os termos e, em seguida, clique em **Provisão**.

   **Nota**: Apenas o {{site.data.keyword.baremetal_short}} são instalados. Você é responsável por instalar e configurar vários componentes após a implementação do cluster, como VMware vCenter, VMware NSX, VMware vSAN.

### Resultados

Se você salvou a configuração de cluster como um modelo, obterá uma notificação do console de que a configuração foi salva com êxito e então será possível localizar o modelo na lista **Configurações de cluster**.

Se tiver feito um pedido, a implementação do cluster será iniciada automaticamente e você receberá uma confirmação por e-mail de que o pedido está sendo processado. Quando o cluster estiver pronto para usar, você será notificado por e-mail.

**Nota:** os clusters do vSphere, ao contrário das instâncias do vCenter Server e do Cloud Foundation, não são exibidos na página **Instâncias implementadas**.

### Links relacionados

* [Pedindo clusters do vSphere com base em configurações existentes](vs_orderingbasedonexistingconfig.html)
* [Ajustando a escala de clusters existentes](vs_scalingexistingclusters.html)
* [Ajustando a escala de clusters criados fora do console](vs_orderingforclustersoutside.html)
