---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vCenter Server add cluster, view cluster vCenter Server, delete cluster vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server
{: #vc_addingviewingclusters}

É possível incluir seus próprios clusters em instâncias do VMware vCenter Server para expandir a capacidade de cálculo e armazenamento. Em um cluster, é possível gerenciar servidores ESXi para melhor alocação de recurso e alta disponibilidade. Quando não forem mais necessários, exclua os clusters incluídos de suas instâncias.

O recurso de exclusão de cluster está disponível somente para instâncias que são implementadas na (ou submetidas a upgrade para a) V2.3 e mais recente.
{:note}

## Incluindo clusters para instâncias do vCenter Server
{: #vc_addingviewingclusters-adding}

### Antes de incluir clusters
{: #vc_addingviewingclusters-before-add}

* Sempre que possível, inclua clusters usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, inclua clusters no vCenter Server somente para clusters no local ou clusters que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
* Para instâncias que foram implementadas (ou submetidas a upgrade) na V2.5 e mais recente, o número de clusters, de hosts e de MVs determina o limite máximo para o número de clusters que podem ser incluídos. Deve-se permanecer dentro das diretrizes de dimensionamento do VMware e limites para sua implementação. Para obter mais informações sobre os limites máximos, consulte [Máximos de configuração do VMware](https://configmax.vmware.com/home){:external}.
* Para instâncias que foram implementadas em (ou submetidas a upgrade para) V2.2, 2.3 ou 2.4, é possível incluir até 10 clusters.
* Para instâncias que foram implementadas na V2.1 ou anterior, é possível incluir até cinco clusters.

### Configurações do sistema
{: #vc_addingviewingclusters-adding-sys-settings}

Ao incluir um cluster para uma instância do vCenter Server, deve-se especificar as configurações a seguir.

#### Nome do cluster
{: #vc_addingviewingclusters-adding-cluster-name}

O nome do cluster deve atender aos requisitos a seguir:
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O nome do cluster deve começar com um caractere alfabético minúsculo.
* O nome do cluster deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do nome do cluster é de 30 caracteres.
* O nome do cluster deve ser exclusivo dentro da instância do vCenter Server.

#### Local do data center
{: #vc_addingviewingclusters-adding-dc-location}

O local do {{site.data.keyword.CloudDataCent}} do cluster é configurado como o {{site.data.keyword.CloudDataCent_notm}} da instância do vCenter Server por padrão. É possível implementar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente da instância implementada, mas deve-se assegurar que a latência de rede entre os dois {{site.data.keyword.CloudDataCents_notm}} seja menor que 150 ms. Para verificar a latência de rede, é possível usar uma ferramenta como [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

Se você implementar o cluster em um pod de infraestrutura diferente do {{site.data.keyword.CloudDataCent_notm}} ou do {{site.data.keyword.cloud_notm}}, três VLANs extras serão pedidas para uso com o {{site.data.keyword.baremetal_short}} pedido.

### Configurações do Bare Metal Server
{: #vc_addingviewingclusters-bare-metal-settings}

É possível escolher **Skylake**, **Cascade**, **Certificado pelo SAP** ou **Broadwell**. As opções podem diferir dependendo da versão em que a sua instância foi implementada inicialmente.

#### Skylake
{: #vc_addingviewingclusters-adding-skylake}

Para a configuração **Skylake**, você tem opções para o **Modelo de CPU** e **RAM**. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabela 1. Opções para Skylake  {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Cascade
{: #vc_addingviewingclusters-adding-cascade}

Para a configuração **Cascade**, você tem opções para o **Modelo de CPU** e **RAM**.

Os {{site.data.keyword.baremetal_short}} Cascade estão disponíveis somente para instâncias do VMware vSphere Enterprise Plus 6.7 U2.
{:note}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Gold 4210/Total de 20 núcleos, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5218/Total de 32 núcleos, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6248/Total de 40 núcleos, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
{: caption="Tabela 2. Opções para {{site.data.keyword.baremetal_short}} Cascade" caption-side="top"}

#### SAP-certificado
{: #vc_addingviewingclusters-adding-sap}

Quando você seleciona **Certificado por SAP**, não é possível alterar as configurações de CPU ou RAM.

Com base em seus requisitos, selecione uma configuração do Bare Metal Server:
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 192 GB de RAM
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 384 GB de RAM
* Processador Dual Intel Xeon Gold 6140 / total de 36 núcleos, 2.3 GHz / 768 GB de RAM
* Processador Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM
* Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/1024 GB de RAM
* Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/2048 GB de RAM
* Processador Quad Intel Xeon E7-8890 v4/total de 96 núcleos, 2.2 GHz/4096 GB de RAM

#### Broadwell
{: #vc_addingviewingclusters-adding-broadwell}

Para a configuração do **Broadwell**, há várias opções para o **Modelo de CPU** e a **RAM**. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabela 3. Opções para o Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Número de Bare Metal Servers
{: #vc_addingviewingclusters-adding-bare-metal-number}

* Todos os servidores que você pede têm a mesma configuração.
* Para armazenamento vSAN, é possível pedir entre 4 e 59 servidores.
* Para armazenamento NFS, é possível pedir entre 2 e 59 servidores. No entanto, para cargas de trabalho de produção, um mínimo de 3 servidores é recomendado. Para obter mais informações, consulte [Uma instância do vCenter Server de dois nós é altamente disponível?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

### Configurações de armazenamento
{: #vc_addingviewingclusters-adding-storage-settings}

As configurações de armazenamento são baseadas em sua seleção de configuração do Bare Metal Server e o tipo de armazenamento.

#### Armazenamento vSAN
{: #vc_addingviewingclusters-adding-vsan-storage}

Especifique as seguintes opções vSAN:
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade acima do limite de 10, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extra para um total de 12 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e rendimento superior de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível somente para os modelos de CPU Skylake e Cascade.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.
* **Licença do vSAN**: use a licença do VMware fornecida pela IBM para o componente vSAN selecionando **Incluir com a compra** ou Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

Se o seu cluster inicial era um cluster do vSAN, todos os clusters adicionais do vSAN usam a mesma licença do vSAN e têm a mesma configuração que o inicial. Isso também será verdadeiro se qualquer cluster na instância tiver vSAN escolhido para ser implementado nele (inicial ou adicional). A primeira vez que você é solicitado pela licença vSAN (BYOL ou comprada) e a edição. Na próxima vez que você selecionar vSAN para um novo cluster, a licença escolhida inicialmente será reutilizada.

#### Armazenamento NFS
{: #vc_addingviewingclusters-adding-nfs-storage}

Quando você selecionar **Armazenamento do NFS**, será possível incluir armazenamento compartilhado no nível de arquivo para a sua instância na qual todas as ações usam as mesmas configurações ou será possível especificar definições de configuração diferentes para cada compartilhamento de arquivo. Especifique as seguintes opções NFS:

O número de compartilhamentos de arquivo deve estar no intervalo de 1 a 32.
{:note}

* **Configurar compartilhamentos individualmente**: selecione para especificar
diferentes definições de configuração para cada compartilhamento de arquivo.
* **Número de compartilhamentos**: quando quiser usar a mesma definição de configuração para cada compartilhamento de arquivo, especifique o número de compartilhamentos de arquivos para o armazenamento compartilhado NFS que quiser incluir.
* **Tamanho**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Desempenho**: selecione o IOPS (operações de entrada/saída por segundo) por GB com base em seus requisitos de carga de trabalho.
* **INCLUIR NFS**: selecione para incluir compartilhamentos de arquivos individuais com definições de configuração diferentes.

Detalhes do nível de desempenho:

| Opção        | Detalhes       |
|:------------- |:------------- |
| 0,25 IOPS/GB | Essa opção foi projetada para cargas de trabalho não usadas frequentemente. Os aplicativos de exemplo incluem: dados de área segura, hospedando bancos de dados grandes com dados anteriores ou imagens de disco virtual do sistema de memória virtual como backup. |
| 2 IOPS/GB | Esta opção foi projetada para a maioria de cargas de trabalho de propósito geral. Os aplicativos de exemplo incluem: hospedando bancos de dados pequenos, fazendo backup de aplicativos da web ou imagens de disco da máquina virtual (MV) para um hypervisor. |
| 4 IOPS/GB | Esta opção foi projetada para cargas de trabalho de maior intensidade que possuem uma alta porcentagem de dados ativos de cada vez. Os aplicativos de exemplo incluem: bancos de dados transacionais. |
| 10 IOPS/GB | Esta opção foi projetada para os tipos de carga de trabalho mais exigentes, como analítica. Os aplicativos de exemplo incluem: bancos de dados de alta transação e outros bancos de dados sensíveis ao desempenho. Esse nível de desempenho é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo. |
{: caption="Tabela 4. Opções de nível de desempenho do NFS" caption-side="top"}

### Discos Locais
{: #vc_addingviewingclusters-adding-local-disks}

A opção de discos locais está disponível somente para a configuração Bare Metal do processador Quad Intel Xeon E7-8890 v4 **certificado pelo SAP**. Especifique as seguintes opções:
* **Contagem de discos**: selecione o número de discos que você deseja incluir.
* **Tipo de disco**: selecione uma opção para o tipo de disco que você precisa.

### Configurações de licenciamento
{: #vc_addingviewingclusters-adding-licensing-settings}

Especifique a opção de licenciamento para o componente VMware vSphere no cluster:
* Para usuários do Parceiro de Negócios, a licença do vSphere (Enterprise Plus edition) é incluída e comprada em seu nome.
* Para usuários não do Parceiro de Negócios, é possível usar as licenças do VMware fornecidas pela IBM para esse componente selecionando **Incluir com a compra** ou usar o Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

### Configurações da interface de rede
{: #vc_addingviewingclusters-adding-network-interface-settings}

Quando você inclui um cluster para uma instância do vCenter Server, deve-se especificar as configurações de interface de rede a seguir.

#### Rede pública ou privada

As configurações de ativação da Placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**. Os serviços complementares a seguir requerem NICs públicas e não estarão disponíveis se você selecionar a opção privada:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

#### VLANs
{: #vc_orderinginstance-vlans}

As configurações de rede se baseiam em sua seleção de **Pedir novas VLANs** ou **Selecionar VLANs existentes**.

São necessárias uma VLAN pública e duas VLANs privadas para o seu pedido de instância. As duas VLANs privadas são truncadas em cada Bare Metal Server.

##### Pedir novas VLANs
{: #vc_orderinginstance-new-vlans}

Selecione para pedir uma nova VLAN pública e duas novas VLANs privadas.

##### Selecionar VLANs existentes
{: #vc_orderinginstance-existing-vlans}

Dependendo do {{site.data.keyword.CloudDataCent_notm}} selecionado, VLANs públicas e privadas existentes podem estar disponíveis.

Ao selecionar para reutilizar VLANs públicas e privadas existentes, especifique as VLANs e as sub-redes:
* **VLAN pública** é para acesso à rede pública.
* **VLAN privada** é para conectividade entre os data centers e os serviços dentro do {{site.data.keyword.cloud_notm}}.
* **VLAN privada secundária** é para recursos do VMware, como vSAN.
* **Sub-rede primária** é designada a hosts físicos para o acesso à rede pública.
* **Sub-rede privada primária** é designada a hosts físicos para o tráfego de gerenciamento.

Assegure-se de que a configuração de firewall nas VLANs selecionadas não bloqueie o tráfego de dados de gerenciamento. Além disso, assegure-se de que todas as VLANs selecionadas estejam no mesmo pod. Os servidores ESXi não podem ser provisionados em VLANs de pod misto.
{:important}

### Resumo do Pedido
{: #vc_addingviewingclusters-adding-order-summary}

Com base em sua configuração selecionada para o cluster, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**. Clique em **Detalhes da precificação** para gerar um documento PDF com o resumo de custo dos recursos do {{site.data.keyword.vmwaresolutions_short}}.

Também é possível incluir os recursos provisionados na ferramenta de estimativa do {{site.data.keyword.cloud_notm}}, clicando em **Incluir na estimativa**. Isso é útil se você desejar estimar o custo dos recursos do {{site.data.keyword.vmwaresolutions_short}} selecionados com outros recursos do {{site.data.keyword.cloud_notm}} que você talvez considere comprar.

## Procedimento para incluir clusters em instâncias do vCenter Server
{: #vc_addingviewingclusters-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância na qual você deseja incluir clusters.

   Assegure-se de que a instância esteja no status **Pronta para uso**. Caso contrário, não será possível incluir clusters na instância.
   {:note}
3. Clique em **Infraestrutura** na área de janela de navegação esquerda e clique em **Incluir** no canto superior direito da tabela **CLUSTERS**.
4. Na página **Incluir cluster**, insira o nome do cluster.
5. Se você desejar hospedar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente daquele no qual a instância está hospedada, sob **Bare Metal Server**, marque a caixa de seleção **Selecionar um local diferente** e escolha o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
6. Conclua a configuração do Bare Metal.
   * Se você selecionou **Skylake**, **Cascade** ou **Broadwell**, especifique o **Modelo de CPU**, a quantia de **RAM** e o **Número de {{site.data.keyword.baremetal_short}}**.
   * Se você selecionou **Certificado pelo SAP**, especifique o modelo de CPU.
7. Conclua a configuração de armazenamento.
  * Se você selecionar **Armazenamento vSAN**, especifique os tipos de disco para os discos de capacidade e de cache, o número de discos e a edição de licença vSAN. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
  * Se você selecionar **Armazenamento NFS** e desejar incluir e configurar as mesmas definições para todos os compartilhamentos de arquivo, especifique o **Número de compartilhamentos**, o **Desempenho** e o **Tamanho (GB)**.
  * Se você selecionar **Armazenamento NFS** e quiser incluir e configurar compartilhamentos de arquivo individualmente, selecione **Configurar compartilhamentos individualmente**. Em seguida, clique no ícone **+** ao lado do rótulo **Incluir armazenamento compartilhado** e selecione o **Desempenho** e o **Tamanho (GB)** para cada compartilhamento de arquivo. Deve-se selecionar pelo menos um compartilhamento de arquivo.
  * Se você selecionar **Discos locais**, especifique a contagem de discos e o tipo de disco.
8. Conclua as configurações da interface de rede.
8. Especifique como a chave de licença do vSphere é fornecida:
  * Para usuários do Parceiro de Negócios, a licença do vSphere (Enterprise Plus edition) é incluída e comprada em seu nome.
  * Para usuários que não são Parceiros de Negócios, é possível selecionar uma das seguintes opções:
      * Se você deseja que novas licenças sejam compradas em seu nome, selecione **Incluir com a compra** para o componente.
      * Se quiser usar sua própria licença VMware para o componente, selecione **Eu fornecerei** e insira sua chave de licença.
9. Selecione a configuração de rede de **Rede pública e privada** ou **Somente rede privada**.
10. Na área de janela **Resumo do pedido**, verifique a configuração de cluster antes de incluir o cluster.
   1. Revise as configurações para o cluster.
   2. Revise o custo estimado do cluster. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de incluir o cluster.
   4. Clique em **Provisão**.

### Resultados após a inclusão de clusters em instâncias do vCenter Server
{: #vc_addingviewingclusters-adding-results}

1. A implementação do cluster é iniciada automaticamente e o status do cluster muda para **Inicializando**. É possível verificar o status da implementação visualizando o histórico de implementação na página **Resumo** da instância.
2. Quando o cluster estiver pronto para usar, seu status mudará para **Pronto para usar**. O cluster recém-incluído é ativado com a Alta disponibilidade (HA) do vSphere e o Distributed Resource Scheduler (DRS) do vSphere.

Não é possível mudar o nome do cluster. Mudar o nome do cluster pode causar falha das operações de inclusão ou remoção de servidores ESXi no cluster.
{:important}

## Procedimento para visualizar clusters em instâncias do vCenter Server
{: #vc_addingviewingclusters-viewing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique em uma instância para visualizar os clusters contidos.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, visualize o resumo sobre os clusters:
  * **Nome**: o nome do cluster.
  * **Servidores ESXi**: o número de servidores ESXi no cluster.
  * **Armazenamento**: o tipo de armazenamento usado pelo cluster.
  * **Local do data center**: o {{site.data.keyword.CloudDataCent_notm}} em que o cluster está hospedado.
  * **Pod**: o pod no qual o cluster é implementado.
  * **Status**: o status do cluster. O status pode ter um dos valores a seguir:
    <dl class="dl">
        <dt class="dt dlterm">Inicializando</dt>
        <dd class="dd">O cluster está sendo criado e configurado.</dd>
        <dt class="dt dlterm">Modificando</dt>
        <dd class="dd">O cluster está sendo modificado.</dd>
        <dt class="dt dlterm">Pronto para usar</dt>
        <dd class="dd">O cluster está pronto para uso.</dd>
        <dt class="dt dlterm">Excluindo</dt>
        <dd class="dd">O cluster está sendo excluído.</dd>
        <dt class="dt dlterm">Excluído</dt>
        <dd class="dd">O cluster é excluído.</dd>
    </dl>
  * **Ações**: clique no ícone **Excluir** para excluir o cluster.
4. Clique no nome de um cluster para visualizar os detalhes de interface de rede, armazenamento e servidor do ESXi.

Visualize detalhes do servidor ESXi:

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome do servidor ESXi está no formato a seguir: `<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>`, em que `n` é a sequência do servidor ESXi. |
| Versão | A versão do servidor ESXi. |
| Credenciais | O nome de usuário e a senha para acessar o servidor ESXi. |
| IP privado | O endereço IP privado do servidor ESXi. |
| Barra de Status | O status do servidor ESXi, que pode ser um dos valores a seguir:<br> **Incluído** o servidor do ESXi foi incluído e está pronto para uso.<br> **Incluindo** o servidor do ESXi está sendo incluído.<br> **Excluindo** o servidor do ESXi está sendo excluído. |
{: caption="Tabela 5. Detalhes do servidor ESXi" caption-side="top"}

Expanda o servidor ESXi para obter detalhes adicionais:

| Item        | Descrição       |  
|:------------- |:------------- |
| CPU | A especificação de CPU dos servidores ESXi no cluster. |
| Memória | O tamanho da memória total dos servidores ESXi no cluster. |
| Discos vSAN customizados | O número de discos vSAN no cluster, incluindo o tipo e a capacidade dos discos. |
| Discos de cache vSAN | O tipo e o número de discos de cache vSAN. |
| Rede |As configurações de ativação da placa da interface de rede (NIC) de Rede Pública e Privada ou Somente Rede Privada. |
{: caption="Tabela 6. Detalhes adicionais do servidor ESXi" caption-side="top"}

Visualizar os detalhes de armazenamento:

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome do armazenamento de dados. |
| Tamanho | A capacidade do armazenamento. |
| IOPS/GB | O nível de desempenho do armazenamento. |
| Protocolo do NFS | A versão NFS do armazenamento. |
{: caption="Tabela 7. Detalhes do armazenamento" caption-side="top"}

Visualizar os detalhes da interface de rede:

| Item        | Descrição       |  
|:------------- |:------------- |
| Número da VLAN | O número exclusivo da VLAN.  |
| Descrição | A descrição da VLAN.  |
| Localização | O local do data center. |
| Rota primária | A rota primária da VLAN. |
{: caption="Tabela 8. Interface de rede - Detalhes da VLAN" caption-side="top"}

Clique em **Visualizar recurso** para acessar os detalhes da VLAN.

Visualizar os detalhes da sub-rede:

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome da sub-rede. Clique no nome para acessar os detalhes da sub-rede. |
| Tipo | O tipo de sub-rede: primária ou móvel. |
| Descrição | A descrição da sub-rede. |
{: caption="Tabela 9. Interface de rede - Detalhes da sub-rede" caption-side="top"}

Visualizar os detalhes do IP:

| Item        | Descrição       |  
|:------------- |:------------- |
| IP | O endereço IP. |
| Barra de Status | O status do endereço IP. |
| Descrição |A descrição do endereço IP.  |
{: caption="Tabela 10. Interface de rede - Detalhes do IP" caption-side="top"}

## Excluindo os clusters de instâncias do vCenter Server
{: #vc_addingviewingclusters-deleting}

Talvez você queira excluir um cluster de uma instância no caso de ela não ser mais necessária.

### Antes de excluir clusters
{: #vc_addingviewingclusters-deleting-prereq}

* Use este procedimento para excluir clusters de instâncias que são implementadas na V2.3 ou mais recente.
* Para clusters implementados em instâncias V2.2 ou anteriores, deve-se fazer upgrade da instância para a V2.3, no caso de querer excluir os clusters incluídos na instância.
* Sempre que possível, exclua clusters usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, exclua os clusters do vCenter Server somente para clusters no local ou clusters que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
* É possível excluir um único cluster de cada vez. Para excluir mais de um cluster, deve-se fazê-lo em sequência. Espere que o cluster anterior seja excluído antes de excluir o próximo.
* Assegure-se de que todos os nós em um cluster estejam ativados e operacionais antes de excluir o cluster.
* Quando você exclui um cluster, todas as MVs do cluster também são excluídas e elas não podem ser recuperadas. Se quiser manter as MVs, migre-as para outros clusters.
* O cluster padrão não pode ser excluído.

Um compromisso de 12 meses é necessário quando você pede o serviço VMware HCX on {{site.data.keyword.cloud_notm}}. Sua conta continuará a ser cobrada pelos componentes do HCX se você excluir um cluster antes do término do período de compromisso de 12 meses. A data de expiração do compromisso de 12 meses está disponível na página de detalhes do HCX on {{site.data.keyword.cloud_notm}}. Para obter mais informações sobre como visualizar detalhes do serviço, consulte [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:important}

### Procedimento para excluir clusters de instâncias do vCenter Server
{: #vc_addingviewingclusters-deleting-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja excluir clusters.

   Assegure-se de que a instância esteja no status **Pronta para uso**. Caso contrário, não será possível excluir clusters da instância.
   {:note}

3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, localize o cluster que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**.
4. Confirme que você concluiu a migração de MVs para outros clusters, se necessário, e que deseja excluir o cluster.

## Links relacionados
{: #vc_addingviewingclusters-related}

* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
