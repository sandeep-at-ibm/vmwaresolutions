---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Componentes da solução

## Componentes do VCS

Figura 1. Diagrama do ambiente VCS
![Diagrama do ambiente VCS](vcsicp-vcsenv.svg)

### Platform Service Controller

A implementação do VCS usa um único controlador de serviços de plataforma externa instalado em uma sub-rede móvel na VLAN privada associada a máquinas virtuais de gerenciamento. Seu gateway padrão é configurado para o backend customer router (BCR).

### vCenter Server

Como o controlador de serviços de plataforma, o vCenter Server é implementado como um dispositivo. Além disso, o vCenter Server é instalado em uma sub-rede móvel na VLAN privada associada a máquinas virtuais de gerenciamento. Seu gateway padrão é configurado para o endereço IP designado no BCR para essa sub-rede específica.

### Gerenciador NSX

O NSX Manager é implementado no cluster inicial. Além disso, o NSX Manager é designado a um endereço IP suportado pela VLAN por meio do bloco de endereço móvel privado que está designado a componentes de gerenciamento e configurado com os servidores DNS e NTP

### NSX Controllers

A automação do {{site.data.keyword.cloud}} implementa três Controladores NSX dentro do cluster inicial. Os controladores são designados a um endereço IP suportado pela VLAN por meio da sub-rede móvel privada que é designada a componentes de gerenciamento.

### NSX Edge / DLR

Os pares do NSX Edge Services Gateway (ESG) são implementados. Em todos os casos, um par de gateway é usado para o tráfego de saída dos componentes de automação que residem na rede privada. Para o vCenter Server e o ICP, um segundo gateway, conhecido como a borda gerenciada por icp, é implementado e configurado com um uplink para a rede pública e uma interface que é designada à rede privada. Qualquer componente NSX necessário, como o Distributed Logical Router (DLR), os comutadores lógicos e os firewalls, pode ser configurado pelo administrador. O [Guia de rede do vCenter Server](../vcsnsxt/vcsnsxt-intro.html) fornece mais detalhes sobre o design da rede.

A tabela a seguir resume as especificações do ICP ESG/DLR.

Tabela 1. Especificações do ESG do ICP

Atributo  |  Especificação
--|--
Gateway de Serviço de Edge  |  Dispositivo Virtual
Tamanho de borda Grande |   Número de vCPUs 2
Memória	| Disco de 1 GB	| 1000 GB no armazenamento de dados local

Tabela 2. Especificações do DLR do ICP

Atributo  |  Especificação
--|--|
Roteador Lógico Distribuído | 	Dispositivo Virtual
Tamanho de borda	Compacto | Número de vCPUs 1
Memória	| Disco de 512 MB	| 1000 GB no armazenamento de dados local

## Componentes do ICP
O {{site.data.keyword.cloud_notm}} Private é uma plataforma de aplicativo para desenvolvimento e gerenciamento de aplicativos locais e conteinerizados. É um ambiente integrado para gerenciar contêineres, que inclui o orquestrador de contêiner Kubernetes, um repositório de imagem privada, um console de gerenciamento e estruturas de monitoramento.

Figura 2. Implementação do ICP virtual com VCS
![Implementação do ICP virtual com VCS](vcsicp-virtual-icp-deployment-vcs.svg)

###	Nó de Inicialização

Um nó de inicialização ou de autoinicialização (opcional) é usado para executar a instalação, a configuração, o ajuste de escala do nó e as atualizações do cluster. Somente um nó de inicialização é necessário para qualquer cluster. É possível usar um único nó para principal e inicialização.

### Nó Principal

Um nó principal fornece serviços de gerenciamento e controla os nós do trabalhador em um cluster. Nós principais hospedam processos que são responsáveis pela alocação de recurso, manutenção de estado, planejamento e monitoramento. Como um ambiente de alta disponibilidade (HA) contém múltiplos nós principais, se o nó principal inicial falhar, a lógica de failover promoverá automaticamente um nó diferente para a função principal. Os hosts que podem agir como o principal são chamados de candidatos principais.

###	Nó do Trabalhador

Um nó do trabalhador é um nó que fornece um ambiente conteinerizado para executar tarefas. Conforme as demandas aumentam, mais nós do trabalhador podem ser facilmente incluídos em seu cluster para melhorar o desempenho e a eficiência. Um cluster pode conter qualquer número de nós do trabalhador, mas é necessário no mínimo um nó do trabalhador.

### Nó do Proxy

Um nó do proxy é um nó que transmite uma solicitação externa para os serviços criados dentro de seu cluster. Como um ambiente de alta disponibilidade (HA) contém múltiplos nós do proxy, se o nó do proxy principal falhar, a lógica de failover promoverá automaticamente um nó diferente para a função do proxy. Embora seja possível usar um único nó como o principal e o proxy, é melhor usar nós de proxy dedicados para reduzir a carga no nó principal. Um cluster deverá conter pelo menos um nó do proxy se o balanceamento de carga for necessário dentro do cluster.

### Nó de Gerenciamento

Um nó de gerenciamento é um nó opcional que hospeda somente serviços de gerenciamento, como monitoramento, medição e criação de log. Configurando os nós de gerenciamento dedicados, é possível evitar que o nó principal fique sobrecarregado. É possível ativar o nó de gerenciamento apenas durante a instalação do {{site.data.keyword.cloud_notm}} Private.

###	Nó VA

Um nó VA (Vulnerability Advisor) é um nó opcional usado para executar os serviços do Vulnerability Advisor. Os serviços do Vulnerability Advisor são intensivos em recurso. Se você usar o serviço Vulnerability Advisor, especifique um nó VA dedicado.

Especificações da máquina virtual necessárias para uma instância do ICP altamente disponível:

Tabela 3. Especificações da máquina virtual do ICP

Nó | 	Instâncias	| IP	| CPU	| RAM (GB)	| DISCO (GB)
:-----|------------:|:----|----:|----------:|----------:|
Mestrado|	3	| IP (x3) VIP (x1)	| 4	| 64	| 200
Gerenciamento	|3	| IP (x3)	|8	|64	|500
Proxy	| 3	| IP (x3) VIP (x1)	|2	|4	|150
Vulnerability Advisor	|3	| IP (x3)	| 4	| 16	|500
GlusterFS	| 3	| IP (x3)	|8	|16	|150
Trabalhador	| 3-6	| IP (x3)	|4-8	|4	|150

O CAM requer que os nós do trabalhador tenham uma configuração de vCPU e de memória mais alta.

Tabela 4. Especificações da máquina virtual do ICP

Nó | 	Instâncias	| IP	| CPU	| RAM (GB)	| DISCO (GB)
:-----|------------:|:----|----:|----------:|----------:|
trabalhador  |  3 | IP (x3)  |  4-8 |16-20   |  150

## Componentes do CAM

O {{site.data.keyword.cloud_notm}} Automation Manager (CAM) é uma plataforma de gerenciamento de autoatendimento com várias nuvens, executada no ICP, que capacita desenvolvedores e administradores a atender às demandas de negócios.

Figura 3. Referência do componente CAM
![Referência do componente CAM](vcsicp-cam-component-ref.svg)

### Proxy CAM

Fornece um acesso de proxy nginx para o CAM.

### UI do CAM

Os componentes da UI são divididos em múltiplos contêineres: UI de conexões em nuvem, UI de Biblioteca de Modelos e UI de instâncias implementadas.

### API CAM

As APIs do CAM são divididas em múltiplos contêineres.

### Helm

Um contêiner com os binários necessários para implementar gráficos helm em clusters do Kubernetes.

### Terraform

Um contêiner com os binários necessários para implementar recursos do Terraform em múltiplas nuvens.

### Registros

O local para os logs do contêiner.

### Banco de dados do Mongo

O banco de dados Principal para o Aplicativo CAM.

### Redis

O banco de dados Redis é usado para o armazenamento em cache de sessão e os bloqueios no CAM.

### Designer de Modelo

Uma interface gráfica com o usuário para criar modelos do Terraform, com os recursos arrastar e soltar de módulos Terraform.

### Maria DB

O banco de dados para o aplicativo de designer modelo.

### Links relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
