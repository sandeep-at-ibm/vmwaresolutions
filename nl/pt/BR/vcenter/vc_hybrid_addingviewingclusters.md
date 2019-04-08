---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters}

Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão.

É possível incluir clusters em sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle para expandir a capacidade de cálculo e armazenamento. Em um cluster, gerencie os servidores ESXi para melhor alocação de recurso e alta disponibilidade. Quando não forem mais necessários, exclua os clusters incluídos de sua instância.

## Incluindo clusters em instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding}

O número de clusters que podem ser incluídos em uma instância depende da versão da instância:
* Para instâncias que foram implementadas (ou submetidas a upgrade) na V2.5 e mais recente, o número de clusters, de hosts e de MVs determina o limite máximo para o número de clusters que podem ser incluídos. Deve-se permanecer dentro das diretrizes de dimensionamento do VMware e limites para sua implementação.
* Para instâncias que foram implementadas na V2.3 e mais recente (ou submetidas a upgrade para ela), é possível incluir até 10 clusters.

Para obter mais informações sobre os limites máximos, consulte [Máximos de configuração do VMware](https://configmax.vmware.com/home){:new_window}.

### Configurações do sistema
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

Quando você inclui um cluster para uma instância do vCenter Server with Hybridity Bundle, deve-se especificar as configurações a seguir.

#### Nome do cluster
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

O nome do cluster deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome do cluster deve iniciar e terminar com um caractere alfanumérico.
* O comprimento máximo do nome do cluster é de 30 caracteres.
* O nome do cluster deve ser exclusivo dentro da instância do vCenter Server with Hybridity Bundle.

#### Local do datacenter
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

O local do {{site.data.keyword.CloudDataCent_notm}} do cluster é configurado como o {{site.data.keyword.CloudDataCent_notm}} da instância do vCenter Server por padrão. É possível implementar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente da instância implementada, mas deve-se assegurar que a latência de rede entre os dois {{site.data.keyword.CloudDataCents_notm}} seja menor que 150 ms. Para verificar a latência de rede, use uma ferramenta como o [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Se você implementar o cluster em um pod de infraestrutura diferente do {{site.data.keyword.CloudDataCent_notm}} ou do {{site.data.keyword.cloud_notm}}, mais três VLANs serão pedidas para uso com o {{site.data.keyword.baremetal_short}} pedido.

### Configurações do Bare Metal Server
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

É possível escolher **Skylake** ou **Broadwell**. As opções podem diferir dependendo da versão em que a sua instância foi implementada inicialmente.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

Quando você seleciona **Skylake**, é possível escolher a combinação de CPU e RAM de acordo com suas necessidades.

Tabela 1. Opções para Bare Metal Servers Skylake

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

Quando você seleciona **Broadwell**, é possível escolher a combinação de CPU e RAM de acordo com suas necessidades.

Tabela 2. Opções para Bare Metal Servers Broadwell

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Número de Bare Metal Servers
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

São necessários pelo menos dois {{site.data.keyword.baremetal_short}} para um cluster.

É possível incluir até 59 {{site.data.keyword.baremetal_short}} para um cluster e incluir de 1 a 59 servidores ESXi de cada vez.

Após a implementação, é possível criar até mais quatro clusters. Para o armazenamento VMware vSAN, são necessários quatro servidores para o cluster inicial e para os clusters pós-implementação.

### Configurações do armazenamento vSAN
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

O VMware vSAN 6.6 é incluído no seu pedido de instância do vCenter Server with Hybridity Bundle. Especifique as seguintes opções vSAN:
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade além do limite de oito, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extras para um total de 10 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e maior rendimento de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível apenas para os modelos de CPU Dual Intel Xeon Gold 5120 e Dual Intel Xeon Gold 6140 do Skylake.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.
* **Licença vSAN**: selecione a edição de licença VMware vSAN 6.6 (Advanced ou Enterprise).

### Configurações de licenciamento
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

Licenças fornecidas pela IBM para os seguintes componentes VMware:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Edição Advanced ou Enterprise)

### Configurações da interface de rede
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

As configurações da placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**. Os serviços complementares a seguir requerem NICs públicas e não estão disponíveis com a opção privada:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Resumo do Pedido
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

Com base em sua configuração selecionada para o cluster, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**.

## Procedimento para incluir clusters em instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para visualizar os clusters contidos.

   Assegure-se de que o status da instância seja **Pronto para uso**. Caso contrário, não será possível incluir clusters na instância.
   {:note}

3. Clique em **Infraestrutura** na área de janela de navegação esquerda e clique em **Incluir** no canto superior direito da tabela **CLUSTERS**.
4. Na página **Incluir cluster**, insira o nome do cluster.
5. É possível hospedar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente daquele em que a instância está hospedada. Para isso, em **Bare Metal Server**, marque a caixa de seleção **Selecionar um local diferente** e escolha o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
6. Selecione o **Modelo de CPU**, a quantia de **RAM** e o **Número de Bare Metal Servers** para a configuração do Bare Metal.
7.  Selecione **Armazenamento vSAN** e especifique os tipos de disco para os discos de capacidade e de cache, além do número de discos. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
8. Selecione a edição de licença para VMware vSAN para a configuração de licença.
9. Selecione a configuração de rede de **Rede pública e privada** ou **Somente rede privada**.
10. Na área de janela **Resumo do pedido**, verifique a configuração de cluster antes de incluir o cluster.
   1. Revise as configurações para o cluster.
   2. Revise o custo estimado do cluster. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de incluir o cluster.
   4. Clique em **Provisão**.

### Resultados após a inclusão de clusters em instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding-results}

1. A implementação do cluster é iniciada automaticamente e o status do cluster muda para **Inicializando**. É possível verificar o status da implementação visualizando o histórico de implementação na página **Resumo** da instância.
2. Quando o cluster estiver pronto para usar, seu status mudará para **Pronto para usar**. O cluster recém-incluído é ativado com a Alta disponibilidade (HA) do vSphere e o Distributed Resource Scheduler (DRS) do vSphere.

Não é possível mudar o nome do cluster. Mudar o nome do cluster pode causar falha das operações de inclusão ou remoção de servidores ESXi no cluster.
{:important}

## Procedimento para visualizar clusters em instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para visualizar os clusters contidos.
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
4. Clique em um nome de cluster para visualizar os servidores do ESXi, o armazenamento e os detalhes da interface de rede:

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
  * Interface de rede - Detalhes da VLAN:
    * **Número da VLAN**: o número da VLAN exclusivo.
    * **Descrição**: a descrição da VLAN.
    * **Local**: o local do data center.
    * **Rota primária**: a rota primária da VLAN.
    Clique em **Visualizar recurso** para acessar os detalhes da VLAN.
  * Interface de rede - Detalhes da sub-rede:
    * **Nome**: o nome da sub-rede. Clique no nome para acessar os detalhes da sub-rede.
    * **Tipo**: o tipo de sub-rede: primária ou móvel.
    * **Descrição**: a descrição da sub-rede.
  * Interface de rede - Detalhes do IP:
    * **IP**: o endereço IP.
    * **Status**: o status do endereço IP.
    * **Descrição**: a descrição do endereço IP.

## Excluindo os clusters de instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-deleting}

Talvez você queira excluir um cluster de uma instância no caso de ela não ser mais necessária.

### Antes de excluir
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* É possível excluir um único cluster de cada vez. Para excluir vários clusters, deve-se fazê-lo em sequência; esperar que o cluster anterior seja excluído antes de excluir o próximo.
* Assegure-se de que todos os nós em um cluster estejam ativados e operacionais antes de excluir o cluster.
* Quando você exclui um cluster, todas as MVs (máquinas virtuais) do cluster também são excluídas e não podem ser recuperadas. Se quiser manter as MVs, migre-as para outros clusters.
* O cluster padrão não pode ser excluído.

## Procedimento para excluir clusters de instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja excluir clusters.

   Assegure-se de que a instância esteja no status **Pronta para uso**. Caso contrário, não será possível remover clusters da instância.
   {:note}

3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, localize o cluster que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**.

## Links relacionados
{: #vc_hybrid_addingviewingclusters-related}

* [Visualizando instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
