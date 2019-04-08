---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo instâncias do vCenter Server
{: #vc_orderinginstance}

Para implementar uma plataforma virtualizada VMware flexível e customizável que melhor atenda às suas necessidades de carga de trabalho, peça uma instância do VMware vCenter Server. Durante o pedido inicial, também é possível incluir serviços, como o [Zerto on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) para recuperação de desastre.

## Requisitos
{: #vc_orderinginstance-req}

Assegure-se de que tenha concluído as tarefas a seguir:
* Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Você revisou as informações em [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Você revisou o formato de nome da instância e do domínio. O nome do domínio e o rótulo do subdomínio são usados para gerar o nome do usuário e os nomes do servidor da instância.

Tabela 1. Formato de valor para nomes de instância e de domínio

| Nome        | Formato do valor      |
  |:------------|:------------ |
  | Nome de domínio | `<root_domain>` |  
  | Nome do usuário de login do vCenter Server | `<user_id>@<root_domain>` (Usuário do Microsoft Active Directory) ou `administrator@vsphere.local` |
  | FQDN do vCenter Server (com PSC integrado) | ` vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. O comprimento máximo é de 50 caracteres. |
  | Nome do site de Conexão única (SSO) | `<subdomain_label>` |
  | Nome do servidor ESXi totalmente qualificado | `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que `<n>` é a sequência do servidor ESXi. O comprimento máximo é de 50 caracteres. |

Não modifique nenhum valor que seja configurado durante o pedido ou a implementação da instância. Fazer isso pode tornar sua instância inutilizável. Por exemplo, se a rede pública for encerrada, se os servidores e as Virtual Server Instances (VSIs) ficarem atrás de uma provisão intermediária do Vyatta ou se o IBM CloudBuilder VSI parar ou for excluído.
{:important}

## Configurações do sistema
{: #vc_orderinginstance-sys-settings}

Deve-se especificar as seguintes configurações do sistema ao pedir uma instância do vCenter Server.

### Nome da instância
{: #vc_orderinginstance-inst-name}

O nome da instância deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome da instância deve iniciar com um caractere alfabético e terminar com um caractere alfanumérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

### Licenças do VMware vSphere
{: #vc_orderinginstance-vsphere-license}

Selecione se deve-se pedir o vSphere Enterprise Plus 6.7u1 ou o vSphere Enterprise Plus 6.5u2.

O vSphere Enterprise Plus 6.7u1 está disponível para apenas Broadwell e Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.
{:note}

### Principal ou secundário
{: #vc_orderinginstance-primary-secondary}

Selecione se pedirá uma nova instância primária ou uma instância secundária para uma instância primária existente.

## Configurações de licenciamento
{: #vc_orderinginstance-licensing-settings}

Especifique as opções de licenciamento para os seguintes componentes do VMware na instância:
* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 ou 6.7
* NSX Service Providers 6.4 (Edição Base, Advanced ou Enterprise)

Para usuários do Parceiro de Negócios, a licença do vCenter Server (Standard Edition), a licença do vSphere (Enterprise Plus Edition) e a licença do NSX são incluídas e compradas em seu nome. No entanto, deve-se especificar a edição para a licença do NSX.

Para usuários que não são do Parceiros de negócios, é possível usar as licenças do VMware fornecidas pela IBM para esses componentes selecionando **Incluir com a compra** ou é possível usar Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo as suas próprias chaves de licença.

### Notas sobre o licenciamento
{: #vc_orderinginstance-licensing-notes}

* É necessária uma licença com um mínimo de oito CPUs, que é para quatro servidores com duas CPUs por servidor. A opção de licença para cada componente do VMware se aplicará à instância de base e a quaisquer servidores ESXi que forem incluídos na instância posteriormente. Assegure-se de que sua licença suporte futura expansão de capacidade em sua infraestrutura.
* As edições de licença mínimas são indicadas na interface com o usuário. Se diferentes edições de componentes forem suportadas, será possível selecionar a edição desejada. Você é responsável por assegurar que a chave de licença fornecida está correta para cada componente de VMware selecionado.
* Para o vSphere, um encargo de licença é incorrido no momento do pedido, mas esse encargo é creditado em sua conta em seguida.
* Será possível mudar as licenças fornecidas usando o VMware vSphere Web Client depois que a implementação da instância for concluída.
* O suporte para os componentes do VMware para os quais você fornece licenças é oferecido pelo VMware, não pelo Suporte IBM.

## Configurações do Bare Metal Server
{: #vc_orderinginstance-bare-metal-settings}

As configurações de Bare Metal são baseadas em sua seleção de data center e na configuração do servidor bare metal.

### Local do datacenter
{: #vc_orderinginstance-dc-location}

Selecione o {{site.data.keyword.CloudDataCent_notm}} no qual a instância deve ser hospedada.

### Skylake
{: #vc_orderinginstance-skylake}

Quando você seleciona **Skylake**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades.

Tabela 2. Opções para o Skylake {{site.data.keyword.baremetal_short}}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### SAP-certificado
{: #vc_orderinginstance-sap}

Quando você seleciona **Certificado por SAP**, não é possível alterar as configurações de CPU ou RAM.

Com base em seus requisitos, selecione uma configuração do Bare Metal Server:
  * Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 192 GB de RAM
  * Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 384 GB de RAM
  * Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 768 GB de RAM
  * Processador Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM
  * Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/1024 GB de RAM
  * Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/2048 GB de RAM
  * Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/4096 GB de RAM

### Broadwell
{: #vc_orderinginstance-broadwell}

Quando você seleciona **Broadwell**, é possível escolher a combinação de CPU e RAM para o Bare Metal Server, de acordo com suas necessidades.

Tabela 3. Opções para o Broadwell {{site.data.keyword.baremetal_short}}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Número de Bare Metal Servers
{: #vc_orderinginstance-bare-metal-number}

Para o cluster inicial na instância, é possível configurar o número de servidores ESXi no intervalo de 2 a 20. Todos os servidores ESXi compartilham a configuração configurada.

Após a implementação inicial, é possível incluir mais quatro clusters. Se você tiver selecionado a configuração **Skylake** ou **Broadwell** para o VMware vSAN, 4 servidores ESXi serão necessários para os clusters iniciais e pós-implementação. Para obter mais informações sobre o mínimo de servidores ESXi, veja [É uma instância de dois nós do vCenter Server altamente disponível](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

## Configurações de armazenamento
{: #vc_orderinginstance-storage-settings}

As configurações de armazenamento são baseadas em sua seleção de configuração do Bare Metal Server e o tipo de armazenamento.

Para instâncias V2.8 e mais recente, é possível incluir compartilhamentos de armazenamento NFS em um cluster NFS
ou vSAN existente. Para obter mais informações, consulte a seção *Incluindo armazenamento NFS em instâncias do
vCenter Server* em
[Expandindo
e reduzindo capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).
{:note}

### Armazenamento vSAN
{: #vc_orderinginstance-vsan-storage}

O vSAN está disponível somente para a configuração de Bare Metal **Skylake** e **Broadwell**. Especifique as seguintes opções vSAN:
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade além do limite de oito, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e maior rendimento de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível apenas para os modelos de CPU Dual Intel Xeon Gold 5120 e Dual Intel Xeon Gold 6140 do Skylake.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.
* **Licença do vSAN**: use a licença do VMware fornecida pela IBM para o componente vSAN selecionando **Incluir com a compra** ou Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

### Armazenamento NFS
{: #vc_orderinginstance-nfs-storage}

Quando você selecionar **Armazenamento do NFS**, será possível incluir armazenamento compartilhado no nível de arquivo para a sua instância na qual todas as ações usam as mesmas configurações ou será possível especificar definições de configuração diferentes para cada compartilhamento de arquivo. Especifique as seguintes opções NFS:

O número de compartilhamentos de arquivo deve estar no intervalo de 1 a 32.
{:note}

* **Configurar compartilhamentos individualmente**: selecione para especificar
diferentes definições de configuração para cada compartilhamento de arquivo.
* **Número de compartilhamentos**: ao usar a mesma definição de configuração para cada compartilhamento de arquivo, especifique o número de compartilhamentos de arquivos para o armazenamento compartilhado NFS que você deseja incluir.
* **Desempenho**: selecione o IOPS (operações de entrada/saída por segundo) por GB com base em seus requisitos de carga de trabalho.
* **Tamanho (GB)**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Incluir armazenamento compartilhado**: selecione para incluir compartilhamentos de arquivos individuais que usam definições de configuração diferentes.

Tabela 4. Opções de nível de desempenho do NFS

| Opção        | Detalhes       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Essa opção foi projetada para cargas de trabalho não usadas frequentemente. Os aplicativos de exemplo incluem: dados de área segura, hospedando bancos de dados grandes com dados anteriores ou imagens de disco virtual do sistema de memória virtual como backup. |
  | 2 IOPS/GB | Esta opção foi projetada para a maioria de cargas de trabalho de propósito geral. Os aplicativos de exemplo incluem: hospedagem de bancos de dados pequenos, backup de aplicativos da web ou imagens de disco da máquina virtual para um hypervisor. |
  | 4 IOPS/GB | Esta opção foi projetada para cargas de trabalho de maior intensidade que possuem uma alta porcentagem de dados ativos de cada vez. Os aplicativos de exemplo incluem: bancos de dados transacionais. |
  | 10 IOPS/GB | Esta opção foi projetada para os tipos de carga de trabalho mais exigentes, como analítica. Os aplicativos de exemplo incluem: bancos de dados de alta transação e outros bancos de dados sensíveis ao desempenho. Esse nível de desempenho é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo. |

### Discos Locais
{: #vc_orderinginstance-local-disks}

A opção de discos locais está disponível somente para a configuração Bare Metal do processador Quad Intel Xeon E7-8890 v4 **certificado pelo SAP**. Especifique as seguintes opções:
* **Contagem de discos**: selecione o número de discos que você deseja incluir.
* **Tipo de disco**: selecione uma opção para o tipo de disco que você precisa.

## Configurações da interface de rede
{: #vc_orderinginstance-network-interface-settings}

Deve-se especificar as seguintes configurações de interface de rede ao pedir uma instância do vCenter Server.

### Prefixo de nome do host
{: #vc_orderinginstance-host-name-prefix}

O prefixo de nome do host deve atender aos requisitos a seguir:
*  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
*  O prefixo de nome do host deve iniciar e terminar com um caractere alfanumérico.
*  O comprimento máximo do prefixo do nome do host é de 10 caracteres.

### Rótulo do subdomínio
{: #vc_orderinginstance-subdomain-label}

O rótulo do subdomínio deve atender aos requisitos a seguir:
*  Apenas caracteres alfanuméricos e o traço (-) são permitidos.
*  O rótulo do subdomínio deve iniciar com um caractere alfabético e terminar com um caractere alfanumérico.
*  O comprimento máximo do rótulo do subdomínio é de 10 caracteres.
*  O rótulo do subdomínio deve ser exclusivo em sua conta.

### Nome de domínio
{: #vc_orderinginstance-domain-name}

O nome do domínio-raiz deve atender aos requisitos a seguir:
* O nome de domínio deve consistir em duas ou mais sequências separadas por ponto (.)
* A primeira sequência deve começar com um caractere alfabético e terminar com um caractere alfanumérico.
* Todas as sequências, exceto a última, podem conter apenas caracteres alfanuméricos e de traço (-).
* A última sequência pode conter apenas caracteres alfabéticos.
* O comprimento da última sequência deve estar no intervalo de 2 a 24 caracteres.

O comprimento máximo do Nome Completo do Domínio (FQDN) para hosts e MVs é de 50 caracteres. Os nomes de domínio devem ajustar-se a este comprimento máximo.
{:note}

### Rede pública ou privada
{: #vc_orderinginstance-public-private-network}

As configurações de ativação da Placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**. Os serviços complementares a seguir requerem NICs públicas e não estarão disponíveis se você selecionar a opção privada:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLANs
{: #vc_orderinginstance-vlans}

As configurações de rede se baseiam em sua seleção de **Pedir novas VLANs** ou **Selecionar VLANs existentes**.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

#### Pedir novas VLANs
{: #vc_orderinginstance-new-vlans}

Selecione para pedir uma nova VLAN pública e duas novas VLANs privadas.

#### Selecionar VLANs existentes
{: #vc_orderinginstance-existing-vlans}

Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

Ao selecionar para reutilizar VLANs públicas e privadas existentes, especifique as VLANs e as sub-redes:
* **VLAN pública** é para acesso à rede pública.
* **VLAN privada** é para conectividade entre os data centers e os serviços dentro do {{site.data.keyword.cloud_notm}}.
* **VLAN privada secundária** é para recursos do VMware, como vSAN.
* **Sub-rede primária** é designada a hosts físicos para o acesso à rede pública.
* **Sub-rede privada primária** é designada a hosts físicos para o tráfego de gerenciamento.

Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento. Além disso, assegure-se de que todas as VLANs que você selecionar estejam no mesmo pod. Os servidores ESXi não podem ser provisionados em VLANs de pod misto.
{:important}

### Configuração de DNS
{: #vc_orderinginstance-dns-config}

Selecione a configuração do Sistema de Nomes de Domínio (DNS) para sua instância:

* **VSI pública única do Windows para o Active Directory/DNS**: uma VSI única do Microsoft Windows Server para o Microsoft Active Directory (AD), que funciona como o DNS para a instância na qual os hosts e as MVs são registrados, é implementada e pode ser consultada. Essa opção foi implementada por padrão para instâncias da V1.9 e mais recentes.
* **Duas MVs do Windows Server dedicadas, altamente disponíveis no cluster de gerenciamento**: duas MVs do Microsoft Windows são implementadas, ajudando a aprimorar a segurança e a robustez.

Deve-se fornecer duas licenças do Microsoft Windows Server 2012 R2 quando você configura sua instância para usar as duas MVs do Microsoft Windows. Use a licença de edição do Microsoft Windows Server 2012 R2 Standard ou a licença de edição do Microsoft Windows Server 2012 R2 Datacenter, ou ambas.
{:important}

Cada licença pode ser designada apenas a um único servidor físico e abrange até dois processadores físicos. Uma licença da edição Standard pode executar duas MVs virtualizadas do Microsoft Windows por servidor de 2 processadores. Portanto, duas licenças são necessárias, pois duas MVs do Microsoft Windows são implementadas em dois hosts diferentes.

Você tem 30 dias para ativar as MVs.

Para obter mais informações sobre licenciamento do Windows, veja [Documentação do Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Configurações de Serviços
{: #vc_orderinginstance-addon-services}

Ao pedir uma instância do vCenter Server, também é possível pedir serviços complementares. Para obter mais informações sobre os serviços, veja [Serviços disponíveis para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances).

## Resumo do Pedido
{: #vc_orderinginstance-order-summary}

Com base em sua configuração selecionada para os serviços de instância e complemento, o custo estimado é gerado instantaneamente e exibido na seção **Resumo do pedido** na área de janela direita. Clique em **Detalhes da precificação** na parte inferior da área de janela direita para gerar um documento PDF que forneça os detalhes da estimativa.

## Procedimento para pedir instâncias do vCenter Server
{: #vc_orderinginstance-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **vCenter Server** na seção **Data centers virtuais**.
2. Na página **VMware vCenter Server on IBM Cloud**, clique no cartão **vCenter Server** e clique em **Criar**.
3. Na página **vCenter Server**, insira o nome da instância.
5. Selecione a versão do vSphere.
4. Selecione o tipo de instância:
   * Clique em **Instância primária** para implementar uma única instância no ambiente ou para implementar a primeira instância em uma topologia multissite.
   * Clique em **Instância secundária** para conectar a instância a uma instância existente (primária) no ambiente para alta disponibilidade e conclua as etapas a seguir:
     1. Selecione a instância primária à qual deseja que a instância secundária seja conectada.
     2. Para instâncias primárias V2.8 ou mais recente, insira a senha do administrador do vCenter Server para a instância primária.
     3. Para as instâncias primárias V2.5, 2.6 ou 2.7, insira a senha do administrador do PSC para a instância primária.
     4. Para as instâncias primárias V2.4 ou anterior, verifique se o valor pré-preenchido para a senha do administrador do PSC para a instância primária está correto.
6. Conclua as configurações de licença para os componentes da instância.
   *  Para usar licenças fornecidas pela IBM, selecione **Incluir com a compra** e selecione a edição de licença, se necessário.
   *  Para usar sua própria licença, selecione **Eu fornecerei** e insira a chave de licença.
7. Conclua as configurações de Bare Metal Server.
    1. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
    2. Selecione a configuração do Bare Metal Server.
       * Ao selecionar **Skylake** ou **Broadwell**, especifique o modelo de CPU e o tamanho da RAM.
       * Quando você selecionar **Certificado pelo SAP**, escolha uma das configurações pré-configuradas.
    3. Especifique o número de {{site.data.keyword.baremetal_short}}. Se você está planejando usar vSAN como sua solução de armazenamento, no mínimo 4 {{site.data.keyword.baremetal_short}} serão necessários.  
8. Conclua a configuração de armazenamento.
  * Se você selecionar **Armazenamento vSAN**, especifique os tipos de disco para os discos de capacidade e de cache, o número de discos e a edição de licença vSAN. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
  * Se você selecionar **Armazenamento NFS** e desejar incluir e configurar as mesmas definições para todos os compartilhamentos de arquivo, especifique o **Número de compartilhamentos**, o **Desempenho** e o **Tamanho (GB)**.
  * Se você selecionar **Armazenamento NFS** e quiser incluir e configurar compartilhamentos de arquivo individualmente, selecione **Configurar compartilhamentos individualmente**. Em seguida, clique no ícone **+** ao lado do rótulo **Incluir armazenamento compartilhado** e selecione o **Desempenho** e o **Tamanho (GB)** para cada compartilhamento de arquivo. Deve-se selecionar pelo menos um compartilhamento de arquivo.
  * Se você selecionar **Discos locais**, especifique a contagem de discos e o tipo de disco.
9. Conclua as configurações da interface de rede.
   1. Insira o prefixo de nome do host, o rótulo do subdomínio e o nome do domínio-raiz. Para uma instância secundária, o nome de domínio é preenchido automaticamente.
   2. Selecione a configuração de rede de **Rede pública e privada** ou **Somente rede privada**.
   3. Selecione as configurações de VLAN:
      * Se desejar pedir novas VLANs públicas e privadas, clique em **Pedir novas VLANs**.
      * Se quiser reutilizar as VLANs públicas e privadas existentes quando estiverem disponíveis, clique em **Selecionar VLANs existentes** e especifique as VLANs e as sub-redes.
   4. Especifique a configuração do DNS.

10. Selecione os serviços complementares a serem implementados na instância clicando no cartão de serviço correspondente. Se um serviço requerer configuração, conclua as configurações específicas do serviço e clique em **Incluir serviço** no cartão.
Para obter mais informações sobre como fornecer configurações para um serviço, consulte o tópico de pedido de serviço correspondente.

11. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
   1. Revise as configurações para a instância.
   2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de pedir a instância.
   4. Clique em **Provisão**.

## Resultados após o pedido de instâncias do vCenter Server
{: #vc_orderinginstance-results}

A implementação da instância é iniciada automaticamente. Você recebe confirmação de que o pedido está sendo processado e pode verificar o status da implementação visualizando os detalhes da instância.

Quando a instância for implementada com êxito, os componentes que estão descritos em [Especificações técnicas para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs) serão instalados em sua plataforma virtual VMware. Os servidores ESXi pedidos são agrupados como **cluster1** por padrão. Se você pediu serviços complementares, a implementação dos serviços será iniciada após a conclusão de seu pedido.

Quando a instância estiver pronta para usar, seu status mudará para **Pronta para usar** e você receberá uma notificação por e-mail.

Quando você pedir uma instância secundária, o VMware vSphere Web Client da instância primária (vinculado à secundária) poderá ser reiniciado depois que o pedido da instância secundária estiver concluído.

## O que fazer a seguir
{: #vc_orderinginstance-next}

Visualizar e gerenciar a instância do vCenter Server que você pediu.

Deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do
{{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console.
Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.
{:important}

**CUIDADO:** Gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) de fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:
*  Incluindo, modificando, retornando ou removendo componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Desativando componentes
*  Reinício dos serviços

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhados.

## Links relacionados
{: #vc_orderinginstance-related}

* [Inscrevendo-se em uma conta do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Configuração de vários sites para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Excluindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
