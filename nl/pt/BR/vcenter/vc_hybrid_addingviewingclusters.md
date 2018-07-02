---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server with Hybridity Bundle

Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão.

É possível incluir clusters em sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle para expandir a capacidade de cálculo e armazenamento. Em um cluster, é possível gerenciar servidores ESXi para melhor alocação de recurso e alta disponibilidade. Quando não forem mais necessários, será possível excluir os clusters incluídos de sua instância.

## Incluindo clusters em instâncias do vCenter Server with Hybridity Bundle

É possível incluir até 10 clusters em sua instância do vCenter Server with Hybridity Bundle.

### Configurações do sistema

Quando você inclui um cluster para uma instância do vCenter Server with Hybridity Bundle, deve-se especificar as configurações a seguir.

#### Nome do cluster

O nome do cluster deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome do cluster deve iniciar e terminar com um caractere alfanumérico.
* O comprimento máximo do nome do cluster é de 30 caracteres.
* O nome do cluster deve ser exclusivo dentro da instância do vCenter Server with Hybridity Bundle.

#### Local do datacenter

O local do {{site.data.keyword.CloudDataCent}} do cluster é configurado como o {{site.data.keyword.CloudDataCent_notm}} da instância do vCenter Server por padrão. É possível implementar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente da instância implementada, mas deve-se assegurar que a latência de rede entre os dois {{site.data.keyword.CloudDataCents_notm}} seja menor que 150 ms. Para verificar a latência de rede, é possível usar uma ferramenta, como o [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Se você implementar o cluster em um pod de infraestrutura diferente do {{site.data.keyword.CloudDataCent_notm}} ou {{site.data.keyword.cloud_notm}}, três VLANs adicionais serão pedidas para uso com os {{site.data.keyword.baremetal_short}} pedidos.

### Configurações do Bare Metal Server

#### Customizado

Especifique o modelo de CPU e RAM para o Bare Metal Server. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

Tabela 2. Opções para Bare Metal Servers customizados

| Opções de CPU        | Opções de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/total de 16 núcleos, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 96 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Número de Bare Metal Servers

São necessários no mínimo dois {{site.data.keyword.baremetal_short}} para um cluster.

É possível incluir até 59 {{site.data.keyword.baremetal_short}} para um cluster e incluir de 1 a 59 servidores ESXi de cada vez.

Após a implementação, é possível criar até mais quatro clusters. Para armazenamento VMware vSAN, 4 servidores são necessários para o cluster inicial e os clusters de pós-implementação.

### Configurações do armazenamento vSAN

O VMware vSAN 6.6 é incluído no seu pedido de instância do vCenter Server with Hybridity Bundle. Deve-se especificar **Advanced** ou **Enterprise** para a edição de licença.

* **Tipo e tamanho do disco para discos de capacidade vSAN**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Número de discos de capacidade vSAN**: selecione o número de discos para o armazenamento compartilhado vSAN que você deseja incluir. As quantidades de disco devem ser 2, 4, 6 ou 8.
* Selecione a edição de licença VMware vSAN 6.6 (Avançada ou Corporativa).

### Configurações de licenciamento

Licenças do VMware fornecidas pela IBM para o seguinte:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Advanced or Enterprise) 6.3

### Resumo do Pedido

Com base em sua configuração selecionada para o cluster, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**.

## Procedimento para incluir clusters em instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para visualizar os clusters contidos.

   **Nota**: assegure-se de que a instância esteja no status **Pronto para usar**. Caso contrário, não será possível incluir clusters na instância.

3. Clique em **Infraestrutura** na área de janela de navegação esquerda e clique em **Incluir** no canto superior direito da tabela **CLUSTERS**.
4. Na página **Incluir cluster**, insira o nome do cluster.
5. Se você desejar hospedar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente daquele no qual a instância está hospedada, sob **Bare Metal Server**, marque a caixa de seleção **Selecionar um local diferente** e escolha o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
6. Selecione o **Modelo de CPU**, a quantia de **RAM** e o **Número de Bare Metal Servers** para a configuração do Bare Metal.
7.  Selecione **Armazenamento vSAN** e selecione o **Número de discos de capacidade de vSAN** e **Tipo e tamanho do disco para discos de capacidade de vSAN** para a configuração de armazenamento.
8. Selecione a edição de licença para VMware vSAN para a configuração de licença.
9. Na área de janela **Resumo do pedido**, verifique a configuração de cluster antes de incluir o cluster.
   1. Revise as configurações para o cluster.
   2. Revise o custo estimado do cluster. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de incluir o cluster.
   4. Clique em **Provisão**.

### Resultados depois de incluir clusters em instâncias do vCenter Server with Hybridity Bundle

1. A implementação do cluster é iniciada automaticamente e o status do cluster muda para **Inicializando**. É possível verificar o status da implementação visualizando o histórico de implementação na página **Resumo** da instância.
2. Quando o cluster estiver pronto para usar, seu status mudará para **Pronto para usar**. O cluster recém-incluído é ativado com a Alta disponibilidade (HA) do vSphere e o Distributed Resource Scheduler (DRS) do vSphere.

**Importante**: não é possível mudar o nome do cluster. Mudar o nome do cluster pode causar falha das operações de inclusão ou remoção de servidores ESXi no cluster.

## Visualizando clusters em instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
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
4. Clique em um nome de cluster para visualizar os detalhes do servidor ESXi, de armazenamento e de licença:

  **Servidores ESXi**

  * **Nome**: o nome do servidor ESXi está no formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que:

     `host_prefix` é o prefixo de nome do host, `n` é a sequência do servidor, `subdomain_label` é o rótulo do subdomínio e `root_domain` é o nome de domínio raiz.

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

## Excluindo os clusters de instâncias do vCenter Server with Hybridity Bundle

Talvez você queira excluir um cluster de uma instância quando ela não for mais necessária.

### Antes de excluir

* É possível excluir um único cluster de cada vez. Para excluir múltiplos clusters, deve-se fazer isso em sequência, aguardando que o cluster anterior seja excluído antes de tentar excluir o próximo cluster.
* Assegure-se de que todos os nós em um cluster estejam ativados e operacionais antes de excluir o cluster.
* Ao excluir um cluster, todas as VMs (máquinas virtuais) do cluster também serão excluídas e não poderão ser recuperadas. Se quiser manter as VMs, migre-as para outros clusters.
* O cluster padrão não pode ser excluído.

## Procedimento para excluir clusters de instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja excluir clusters.

   **Nota**: assegure-se de que a instância esteja no status **Pronto para usar**. Caso contrário, não será possível remover clusters da instância.

3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, localize o cluster que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**.

## Links relacionados

* [Visualizando instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_viewinginstances.html)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
