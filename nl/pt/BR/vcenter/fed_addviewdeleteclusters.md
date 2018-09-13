---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-17"

---

# Incluindo, visualizando e excluindo clusters para instâncias do VMware Federal

Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão.

É possível incluir clusters em suas instâncias do VMware Federal para expandir a capacidade de cálculo e armazenamento. Em um cluster, é possível gerenciar servidores ESXi para melhor alocação de recurso e alta disponibilidade. Quando não for mais necessário, será possível excluir os clusters incluídos de suas instâncias.

**Disponibilidade**: o recurso de inclusão e exclusão de clusters está disponível somente para instâncias que foram implementadas na V2.3 e em liberações mais recentes (ou submetidas a upgrade para elas).

## Incluindo clusters para instâncias do VMware Federal

É possível incluir até 10 clusters em uma instância. Ao incluir um cluster para uma instância do VMware Federal, deve-se especificar as configurações a seguir.

### Configurações do sistema

Ao incluir um cluster para uma instância do VMware Federal, deve-se especificar as configurações a seguir.

#### Nome do cluster

O nome do cluster deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome do cluster deve iniciar e terminar com um caractere alfanumérico.
* O comprimento máximo do nome do cluster é de 30 caracteres.
* O nome do cluster deve ser exclusivo dentro da instância do VMware Federal.

#### Local do datacenter

O data center do cluster é configurado para o data center da instância do VMware Federal por padrão.

### Configurações do Bare Metal Server

#### Customizado

Especifique o modelo de CPU e RAM para o Bare Metal Server. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

Tabela 1. Opções para {{site.data.keyword.baremetal_short}}customizado

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Número de Bare Metal Servers

Um mínimo de 2 {{site.data.keyword.baremetal_short}} é necessário para um cluster.

Para instâncias do VMware Federal que são implementadas na V2.3 ou mais recente, é possível incluir até 59 {{site.data.keyword.baremetal_short}} para um cluster e incluir de 1 a 59 servidores ESXi de cada vez.

Após a implementação, é possível criar até mais quatro clusters. Para configurações de armazenamento vSAN, 4 servidores são necessários para o cluster inicial e os clusters de pós-implementação.

### Configurações de armazenamento

As configurações de armazenamento são baseadas em sua seleção de configuração do Bare Metal Server e o tipo de armazenamento.

#### Armazenamento vSAN

Para vSAN, especifique as opções de armazenamento a seguir:

* **Tipo e tamanho do disco para discos de capacidade vSAN**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Número de discos de capacidade vSAN**: selecione o número de discos para o armazenamento compartilhado vSAN que você deseja incluir. As quantidades de disco devem ser 2, 4, 6 ou 8.
* Selecione a edição de licença VMware vSAN 6.6 (Avançada ou Corporativa).

Se o seu cluster inicial era vSAN, todos os clusters vSAN adicionais usarão a mesma licença vSAN e terão a mesma configuração que o cluster vSAN inicial. Isso também será verdadeiro se qualquer cluster na instância tiver vSAN escolhido para ser implementado nele (inicial ou adicional). Na primeira vez, você é solicitado para a licença do vSAN e a edição. Na próxima vez que você selecionar vSAN para um cluster adicional, o que você tiver escolhido inicialmente será reutilizado.

#### Armazenamento NFS

Quando você selecionar **Armazenamento do NFS**, será possível incluir armazenamento compartilhado no nível de arquivo para a sua instância na qual todas as ações usam as mesmas configurações ou será possível especificar definições de configuração diferentes para cada compartilhamento de arquivo. Especifique as seguintes opções NFS:

**Nota:** o número de compartilhamentos de arquivos deve estar no intervalo de 1 a 32.

* **Configurar compartilhamentos individualmente**: selecione para especificar
diferentes definições de configuração para cada compartilhamento de arquivo.
* **Número de compartilhamentos**: ao usar a mesma definição de configuração para cada compartilhamento de arquivo, especifique o número de compartilhamentos de arquivos para o armazenamento compartilhado do NFS que você deseja incluir.
* **Tamanho**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Desempenho**: selecione o IOPS (Input/output Operations Per Second) por GB com base em seus requisitos de carga de trabalho.
* **ADD NFS**: selecione para incluir compartilhamentos de arquivos individuais que usarão definições de configuração diferentes.

Tabela 2. Opções de nível de desempenho do NFS

| Opção        | Detalhes       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Esta opção foi projetada para a maioria de cargas de trabalho de propósito geral. Os aplicativos de exemplo incluem: hospedagem de bancos de dados pequenos, backup de aplicativos da web ou imagens de disco da máquina virtual para um hypervisor. |
  | 4 IOPS/GB | Esta opção foi projetada para cargas de trabalho de maior intensidade que possuem uma alta porcentagem de dados ativos de cada vez. Os aplicativos de exemplo incluem: bancos de dados transacionais. |
  | 10 IOPS/GB | Esta opção foi projetada para os tipos de carga de trabalho mais exigentes, como analítica. Os aplicativos de exemplo incluem: bancos de dados de alta transação e outros bancos de dados sensíveis ao desempenho. Esse nível de desempenho é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo.|

### Configurações de licenciamento

	Licenças do VMware fornecidas pelo {{site.data.keyword.IBM}} para o seguinte:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
  * (Para clusters do vSAN) VMware vSAN Advanced ou Enterprise 6.6

### Resumo do Pedido

Com base em sua configuração selecionada para o cluster, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**.

## Procedimento para incluir clusters em instâncias do VMware Federal

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instância do vCenter Server**, clique na instância na qual você deseja incluir clusters.

   **Nota**: assegure-se de que a instância esteja no status **Pronto para usar**. Caso contrário, não será possível incluir clusters na instância.

3. Clique em **Infraestrutura** na área de janela de navegação esquerda e clique em **Incluir** no canto superior direito da tabela **CLUSTERS**.
4. Na página **Incluir cluster**, insira o nome do cluster.
5. Selecione o **Modelo de CPU**, a quantia de **RAM** e o **Número de Bare Metal Servers** para a configuração do Bare Metal.
6. Conclua a configuração de armazenamento.
  * Quando você selecionar **Armazenamento vSAN**, especifique o **Tipo
e tamanho do disco para discos de capacidade vSAN**, o **Número de discos de
capacidade vSAN** e como a **Licença vSAN** deve ser fornecida.
  * Quando você selecionar **Armazenamento NFS** e desejar incluir e definir as mesmas configurações para todos os compartilhamentos de arquivos, especifique o **Número de compartilhamentos**, o **Tamanho** e o **Desempenho**.
  * Quando você selecionar **Armazenamento NFS** e desejar incluir e configurar compartilhamentos de arquivos individualmente, selecione **Configurar compartilhamentos
individualmente**, em seguida, clique no ícone **+** ao lado do rótulo **Incluir NFS** e selecione o **Tamanho** e o **Desempenho**
para cada compartilhamento de arquivo individual. Deve-se selecionar pelo menos um compartilhamento de arquivo.
7. Selecione a edição de licença para VMware vSAN para a configuração de licença.
8. Na área de janela **Resumo do pedido**, verifique a configuração de cluster antes de incluir o cluster.
   1. Revise as configurações para o cluster.
   2. Revise o custo estimado do cluster. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir seu resumo de pedido, clique no ícone **Imprimir** ou **Download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de incluir o cluster.
   4. Clique em **Provisão**.

## Resultados após a inclusão de clusters em instâncias do VMware Federal

1. A implementação do cluster é iniciada automaticamente e o status do cluster muda para **Inicializando**. É possível verificar o status da implementação visualizando o histórico de implementação na página de resumo da instância.
2. Quando o cluster estiver pronto para usar, seu status mudará para **Pronto para usar**. O cluster recém-incluído é ativado com a Alta disponibilidade (HA) do vSphere e o Distributed Resource Scheduler (DRS) do vSphere.

**Importante**: não é possível mudar o nome do cluster. Mudar o nome do cluster pode causar falha das operações de inclusão ou remoção de servidores ESXi no cluster.

## Visualizando clusters em instâncias do VMware Federal

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique em uma instância para visualizar os clusters contidos.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, visualize o resumo sobre os clusters:
   * **Nome**: o nome do cluster.
   * **ESXi Server**: o número de servidores ESXi no cluster.
   * **CPU**: a especificação de CPU dos servidores ESXi no cluster.
   * **Discos vSAN customizados**: o número de discos vSAN no cluster, incluindo o tipo de disco e a capacidade.
   * **Memória**: o tamanho total da memória dos servidores ESXi no cluster.
   * **Local do data center**: o data center no qual o cluster está hospedado.
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
4. Clique em um nome de cluster para visualizar os detalhes do servidor ESXi, de armazenamento e de licença.

### Servidores ESXi

   * **Nome**: o nome do servidor ESXi está no formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que:

      `host_prefix` é o prefixo do nome do host,
      `n` é a sequência do servidor ESXi,
      `subdomain_label` é o rótulo do subdomínio e
      `root_domain` é o nome do domínio-raiz.

   * **Versão**: a versão do servidor ESXi.
   * **Credenciais**: o nome de usuário e a senha para acessar o servidor ESXi.
   * **IP privado**: o endereço IP privado do servidor ESXi.
   * **Status**: o status do servidor ESXi, que pode ser um dos valores a seguir:
        <dl class="dl">
        <dt class="dt dlterm">Incluído</dt>
        <dd class="dd">O servidor ESXi foi incluído e está pronto para uso. </dd>
        <dt class="dt dlterm">Incluindo</dt>
        <dd class="dd">O servidor ESXi está sendo incluído. </dd>
        <dt class="dt dlterm">Excluindo</dt>
        <dd class="dd">O servidor ESXi está sendo excluído.</dd>
        </dl>

### Armazenamento

   * **Nome**: o nome do armazenamento de dados.
   * **Tamanho**: a capacidade do armazenamento.
   * **IOPS/GB**: o nível de desempenho do armazenamento.
   * **NFS/Portal**: a versão NFS do armazenamento.
   * **Status**: o status do armazenamento, que pode ser um dos valores a seguir:
        <dl class="dl">
        <dt class="dt dlterm">Incluído</dt>
        <dd class="dd">O servidor ESXi foi incluído e está pronto para uso. </dd>
        <dt class="dt dlterm">Incluindo</dt>
        <dd class="dd">O servidor ESXi está sendo incluído. </dd>
        <dt class="dt dlterm">Excluindo</dt>
        <dd class="dd">O servidor ESXi está sendo excluído.</dd>
        </dl>

### Licenças

   * **Licença**: O tipo de licença.
   * **Tipo de pedido**: a licença foi fornecida pela IBM ou fornecida pelo usuário.
   * **Edição de licença**: a versão e edição da licença.
   * **Chave de Licença**: A chave de licença.
   * **Capacidade total (CPU)**: a quantia total de capacidade de CPU para a licença.
   * **Capacidade livre (CPU)**: a quantia de capacidade de CPU livre para a licença.

## Excluindo os clusters de instâncias do VMware Federal

Talvez você queira excluir um cluster de uma instância quando ela não for mais necessária.

**Nota**: use este procedimento para remover clusters de instâncias que são implementadas na (ou submetidas a upgrade para a) V2.3 e liberações mais recentes.

### Antes de excluir

* Use este procedimento para excluir clusters de instâncias implementadas na V2.3 ou liberações mais recentes.
* Para clusters implementados em instâncias da V2.2 ou anteriores, deve-se fazer upgrade da instância para a V2.3 para ser possível excluir os clusters incluídos na instância.
* É possível excluir um único cluster de cada vez. Para excluir múltiplos clusters, deve-se fazer isso em sequência, aguardando que o cluster anterior seja excluído antes de tentar excluir o próximo cluster.
* Assegure-se de que todos os nós em um cluster estejam ativados e operacionais antes de excluir o cluster.
* Ao excluir um cluster, todas as VMs (máquinas virtuais) do cluster também serão excluídas e não poderão ser recuperadas. Se quiser manter as VMs, migre-as para outros clusters.
* O cluster padrão não pode ser excluído.

## Procedimento para excluir clusters de instâncias do VMware Federal

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja excluir clusters.

   **Nota**: assegure-se de que a instância esteja no status **Pronto para usar**. Caso contrário, não será possível excluir clusters da instância.

3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, localize o cluster que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**.

### Links relacionados

* [Visualizando instâncias do VMware Federal](vc_fed_viewinginstance.html)
* [Expandindo e contraindo a capacidade para instâncias do VMware Federal](vc_fed_addingremovingservers.html)
