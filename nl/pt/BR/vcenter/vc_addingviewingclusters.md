---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server

Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão.

É possível incluir seus próprios clusters em instâncias do VMware vCenter Server para expandir a capacidade de cálculo e armazenamento. Em um cluster, é possível gerenciar servidores ESXi para melhor alocação de recurso e alta disponibilidade. Quando não forem mais necessários, exclua os clusters incluídos de suas instâncias.

**Disponibilidade**: o recurso de exclusão de cluster está disponível somente para instâncias que são implementadas (ou submetidas a upgrade) na V2.3 e mais recente.

## Incluindo clusters para instâncias do vCenter Server

O número de clusters que podem ser incluídos em uma instância depende da versão da instância:
* Para instâncias que foram implementadas (ou submetidas a upgrade) na V2.2 e mais recente, é possível incluir até 10 clusters.
* Para instâncias que foram implementadas na V2.2 ou anterior, é possível incluir até cinco clusters.

### Configurações do sistema

Ao incluir um cluster para uma instância do vCenter Server, deve-se especificar as configurações a seguir.

#### Nome do cluster

O nome do cluster deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome do cluster deve iniciar e terminar com um caractere alfanumérico.
* O número máximo de caracteres é 30.
* O nome do cluster deve ser exclusivo dentro da instância do vCenter Server.

#### Local do datacenter

O local do {{site.data.keyword.CloudDataCent}} do cluster é configurado como o {{site.data.keyword.CloudDataCent_notm}} da instância do vCenter Server por padrão. É possível implementar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente da instância implementada, mas deve-se assegurar que a latência de rede entre os dois {{site.data.keyword.CloudDataCents_notm}} seja menor que 150 ms. Para verificar a latência de rede, é possível usar uma ferramenta, como o [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/).

Se você implementar o cluster em um pod de infraestrutura diferente do {{site.data.keyword.CloudDataCent_notm}} ou do {{site.data.keyword.cloud_notm}}, três VLANs extras serão pedidas para uso com o {{site.data.keyword.baremetal_short}} pedido.

### Configurações do Bare Metal Server

É possível escolher **Pré-configurado** ou **Customizado**.

#### Pré-configurado

Para a configuração **Pré-configurado**, é possível escolher uma **Configuração do Bare Metal Server**, dependendo de seus requisitos:
* Pequeno (Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz/128 GB de RAM/2 discos)
* Médio (Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz/256 GB de RAM/2 discos)
* Grande (Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM/2 discos)

#### Customizado

Para a configuração **Customizado**, você tem um número de opções para o **Modelo de CPU** e **RAM**. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

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

Os clusters requerem pelo menos dois {{site.data.keyword.baremetal_short}}.

Para instâncias do vCenter Server que são implementadas na V2.1 ou mais recente, é possível incluir até 59 {{site.data.keyword.baremetal_short}} para um cluster. É possível incluir de 1 a 59 servidores ESXi de cada vez.

Para instâncias do vCenter Server que foram implementadas na V2.0 ou anterior, é possível incluir até 32 {{site.data.keyword.baremetal_short}} para um cluster. O número do {{site.data.keyword.baremetal_short}} que é possível incluir de cada vez é o seguinte:
* Para as configurações do Bare Metal Server **Pequeno**, **Médio** e **Grande**, é possível incluir de 1 a 10 servidores ESXi de cada vez.
* Para a configuração do Bare Metal Server **Customizado**, é possível incluir de 1 a 20 servidores ESXi de cada vez.

Após a implementação, é possível criar até mais quatro clusters. Se você selecionar a configuração **Customizado** do Bare Metal Server com armazenamento VMware vSAN, serão necessários quatro servidores para o cluster inicial e para os clusters pós-implementação.

### Configurações de armazenamento

As configurações de armazenamento são baseadas em sua seleção de configuração do Bare Metal Server e o tipo de armazenamento.

#### Armazenamento vSAN

Especifique as seguintes opções vSAN:

* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* **Tipo de disco para discos de cache vSAN**: selecione uma opção para os discos de cache necessários.

    **Nota**: se desejar incluir discos de capacidade acima do limite de oito, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e maior rendimento de IOPS. A opção **Intel Optane de alto desempenho** está disponível apenas para os Processadores Dual Intel Xeon Gold 5120 e 6140.
* **Número de discos de cache vSAN**: especifique o número de discos de cache que deseja incluir.
* **Licença do vSAN**: use a licença do VMware fornecida pela IBM para o componente vSAN selecionando **Incluir com a compra** ou Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

Se o seu cluster inicial era um cluster do vSAN, todos os clusters adicionais do vSAN usam a mesma licença do vSAN e têm a mesma configuração que o inicial. Isso também será verdadeiro se qualquer cluster na instância tiver vSAN escolhido para ser implementado nele (inicial ou adicional). A primeira vez que você é solicitado pela licença vSAN (BYOL ou comprada) e a edição. Na próxima vez que você selecionar vSAN para um novo cluster, a licença escolhida inicialmente será reutilizada.

#### Armazenamento NFS

Quando você selecionar **Armazenamento do NFS**, será possível incluir armazenamento compartilhado no nível de arquivo para a sua instância na qual todas as ações usam as mesmas configurações ou será possível especificar definições de configuração diferentes para cada compartilhamento de arquivo. Especifique as seguintes opções NFS:

**Nota:** o número de compartilhamentos de arquivos deve estar no intervalo de 1 a 32.

* **Configurar compartilhamentos individualmente**: selecione para especificar
diferentes definições de configuração para cada compartilhamento de arquivo.
* **Número de compartilhamentos**: quando quiser usar a mesma definição de configuração para cada compartilhamento de arquivo, especifique o número de compartilhamentos de arquivos para o armazenamento compartilhado NFS que quiser incluir.
* **Tamanho**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Desempenho**: selecione o IOPS (operações de entrada/saída por segundo) por GB com base em seus requisitos de carga de trabalho.
* **INCLUIR NFS**: selecione para incluir compartilhamentos de arquivos individuais com definições de configuração diferentes.

Tabela 2. Opções de nível de desempenho do NFS

| Opção        | Detalhes       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Esta opção foi projetada para a maioria de cargas de trabalho de propósito geral. Os aplicativos de exemplo incluem: hospedagem de bancos de dados pequenos, backup de aplicativos da web ou imagens de disco da máquina virtual para um hypervisor. |
  | 4 IOPS/GB | Esta opção foi projetada para cargas de trabalho de maior intensidade que possuem uma alta porcentagem de dados ativos de cada vez. Os aplicativos de exemplo incluem: bancos de dados transacionais. |
  | 10 IOPS/GB | Esta opção foi projetada para os tipos de carga de trabalho mais exigentes, como analítica. Os aplicativos de exemplo incluem: bancos de dados de alta transação e outros bancos de dados sensíveis ao desempenho. Esse nível de desempenho é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo. |

### Configurações de licenciamento

Especifique a opção de licenciamento para o componente VMware vSphere no cluster:
* Para usuários do Parceiro de Negócios, a licença do vSphere (Enterprise Plus edition) é incluída e comprada em seu nome.
* Para usuários não do Parceiro de Negócios, é possível usar as licenças do VMware fornecidas pela IBM para esse componente selecionando **Incluir com a compra** ou usar o Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

### Configurações da interface de rede

As configurações de ativação da Placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**. Os serviços complementares a seguir requerem NICs públicas e não estarão disponíveis se você selecionar a opção privada:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Resumo do Pedido

Com base em sua configuração selecionada para o cluster, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**.

## Procedimento para incluir clusters em instâncias do vCenter Server

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância na qual você deseja incluir clusters.

   **Nota**: assegure-se de que a instância esteja no status **Pronto para usar**. Caso contrário, não será possível incluir clusters na instância.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda e clique em **Incluir** no canto superior direito da tabela **CLUSTERS**.
4. Na página **Incluir cluster**, insira o nome do cluster.
5. Se você desejar hospedar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente daquele no qual a instância está hospedada, sob **Bare Metal Server**, marque a caixa de seleção **Selecionar um local diferente** e escolha o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
6. Conclua a configuração do Bare Metal.
   * Se tiver selecionado **Pré-configurado**, especifique a **Configuração do Bare Metal Server** e o **Número de {{site.data.keyword.baremetal_short}}**. Se estiver planejando usar vSAN como sua solução de armazenamento, serão necessários no mínimo quatro {{site.data.keyword.baremetal_short}}.
   * Se tiver selecionado **Customizado**, especifique o **Modelo de CPU**, a quantia de **RAM** e o **Número de {{site.data.keyword.baremetal_short}}**.
7. Conclua a configuração de armazenamento.
  * Se você selecionar **Armazenamento vSAN**, especifique os tipos de disco para os discos de capacidade e de cache, o número de discos e a edição de licença vSAN. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
  * Se você selecionar **Armazenamento NFS** e quiser incluir e configurar as mesmas configurações para todos os compartilhamentos de arquivo, especifique o **Número de compartilhamentos**, o **Tamanho** e o **Desempenho**.
  * Se você selecionar **Armazenamento NFS** e quiser incluir e configurar compartilhamentos de arquivo individualmente, selecione **Configurar compartilhamentos individualmente**. Em seguida, clique no ícone **+** próximo ao rótulo **Incluir NFS** e selecione o **Tamanho** e o **Desempenho** para cada compartilhamento de arquivo. Deve-se selecionar pelo menos um compartilhamento de arquivo.
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

1. A implementação do cluster é iniciada automaticamente e o status do cluster muda para **Inicializando**. É possível verificar o status da implementação visualizando o histórico de implementação na página **Resumo** da instância.
2. Quando o cluster estiver pronto para usar, seu status mudará para **Pronto para usar**. O cluster recém-incluído é ativado com a Alta disponibilidade (HA) do vSphere e o Distributed Resource Scheduler (DRS) do vSphere.

**Importante**: não é possível mudar o nome do cluster. Mudar o nome do cluster pode causar falha das operações de inclusão ou remoção de servidores ESXi no cluster.

## Visualizando clusters em instâncias do vCenter Server

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique em uma instância para visualizar os clusters contidos.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, visualize o resumo sobre os clusters:
  * **Nome**: o nome do cluster.
  * **Servidores ESXi**: o número de servidores ESXi no cluster.
  * **CPU**: a especificação de CPU dos servidores ESXi no cluster.
  * **Discos vSAN customizados**: o número de discos vSAN no cluster, incluindo o tipo de disco e a capacidade.
  * **Memória**: o tamanho total da memória dos servidores ESXi no cluster.
  * **Local do data center**: o {{site.data.keyword.CloudDataCent_notm}} em que o cluster está hospedado.
  * **Pod**: o pod no qual o cluster é implementado.
  * **Status**: o status do cluster. O status pode ter um dos valores a seguir:
    <dl class="dl">
        <dt class="dt dlterm">Inicialização</dt>
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
4. Clique em um nome de cluster para visualizar os detalhes de servidores ESXi e armazenamento:

  * Detalhes de servidores ESXi:
     * **Nome**: o nome do servidor ESXi está no formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que:

       `host_prefix` é o prefixo de nome do host,

       `n` é a sequência do servidor,

       `subdomain_label` é o rótulo do subdomínio e

       `root_domain` é o nome de domínio raiz.

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
  * Detalhes de armazenamento:
    * **Nome**: o nome do armazenamento de dados.
    * **Tamanho**: a capacidade do armazenamento.
    * **IOPS/GB**: o nível de desempenho do armazenamento.
    * **Protocolo NFS**: a versão NFS do armazenamento.

## Excluindo os clusters de instâncias do vCenter Server

Talvez você queira excluir um cluster de uma instância no caso de ela não ser mais necessária.

### Antes de excluir

* Use este procedimento para excluir clusters de instâncias que são implementadas na V2.3 ou mais recente.
* Para clusters implementados em instâncias V2.2 ou anteriores, deve-se fazer upgrade da instância para a V2.3, no caso de querer excluir os clusters incluídos na instância.
* É possível excluir um único cluster de cada vez. Para excluir mais de um cluster, deve-se fazê-lo em sequência. Espere que o cluster anterior seja excluído antes de excluir o próximo.
* Assegure-se de que todos os nós em um cluster estejam ativados e operacionais antes de excluir o cluster.
* Quando você exclui um cluster, todas as VMs (máquinas virtuais) do cluster também são excluídas e não podem ser recuperadas. Se quiser manter as VMs, migre-as para outros clusters.
* O cluster padrão não pode ser excluído.

## Procedimento para excluir clusters de instâncias do vCenter Server

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja excluir clusters.

   **Nota**: assegure-se de que a instância esteja no status **Pronto para usar**. Caso contrário, não será possível excluir clusters da instância.

3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, localize o cluster que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**.
4. Confirme que você concluiu a migração de máquinas virtuais para outros clusters, se necessário, e que deseja excluir o cluster.

### Links relacionados

* [Visualizando instâncias do vCenter Server](vc_viewinginstances.html)
* [Expandindo e contraindo capacidade para instâncias do vCenter Server](vc_addingremovingservers.html)
