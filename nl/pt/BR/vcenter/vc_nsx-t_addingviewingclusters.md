---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingviewingcluster}

Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão.

É possível incluir seus próprios clusters em instâncias do VMware vCenter Server com NSX-T para expandir a capacidade de cálculo e armazenamento. Em um cluster, é possível gerenciar servidores ESXi para melhor alocação de recurso e alta disponibilidade. Quando não forem mais necessários, exclua os clusters incluídos de suas instâncias.

## Incluindo clusters para instâncias do vCenter Server
{: #vc_nsx-t_addingviewingclusters-adding}

### Antes de incluir clusters
{: #vc_nsx-t_addingviewingclusters-before-add}

* Sempre que possível, inclua clusters usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, inclua clusters no vCenter Server somente para clusters no local ou clusters que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
* O número de clusters, hosts e máquinas virtuais (VMs) determina o limite máximo para o número de clusters que podem ser incluídos. Deve-se permanecer dentro das diretrizes de dimensionamento do VMware e limites para sua implementação. Para obter mais informações sobre os limites máximos, consulte [Máximos de configuração do VMware](https://configmax.vmware.com/home){:new_window}.

### Configurações do sistema
{: #vc_nsx-t_addingviewingclusters-adding-sys-settings}

Ao incluir um cluster para uma instância do vCenter Server com NSX-T, deve-se especificar as configurações a seguir.

#### Nome do cluster
{: #vc_nsx-t_addingviewingclusters-adding-cluster-name}

O nome do cluster deve atender aos requisitos a seguir:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome do cluster deve iniciar e terminar com um caractere alfanumérico.
* O número máximo de caracteres é 30.
* O nome do cluster deve ser exclusivo dentro da instância do vCenter Server.

#### Local do datacenter
{: #vc_nsx-t_addingviewingclusters-adding-dc-location}

O local do {{site.data.keyword.CloudDataCent}} do cluster é configurado como o {{site.data.keyword.CloudDataCent_notm}} da instância do vCenter Server por padrão. É possível implementar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente da instância implementada, mas deve-se assegurar que a latência de rede entre os dois {{site.data.keyword.CloudDataCents_notm}} seja menor que 150 ms. Para verificar a latência de rede, é possível usar uma ferramenta como [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

Se você implementar o cluster em um pod de infraestrutura diferente do {{site.data.keyword.CloudDataCent_notm}} ou do {{site.data.keyword.cloud_notm}}, três VLANs extras serão pedidas para uso com o {{site.data.keyword.baremetal_short}} pedido.

### Configurações do Bare Metal Server
{: #vc_nsx-t_addingviewingclusters-bare-metal-settings}

É possível escolher **Skylake** ou **Broadwell**.

#### Skylake
{: #vc_nsx-t_addingviewingclusters-adding-skylake}

Para a configuração **Skylake**, você tem opções para o **Modelo de CPU** e **RAM**. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

Tabela 1. Opções para Skylake  {{site.data.keyword.baremetal_short}}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Processador Dual Intel Xeon Silver 4110/total de 16 núcleos, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 5120/total de 28 núcleos, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processador Dual Intel Xeon Gold 6140/Total de 36 núcleos, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell
{: #vc_nsx-t_addingviewingclusters-adding-broadwell}

Para a configuração do **Broadwell**, há várias opções para o **Modelo de CPU** e a **RAM**. As opções disponíveis podem diferir dependendo da versão na qual a sua instância foi inicialmente implementada.

Tabela 2. Opções para Broadwell  {{site.data.keyword.baremetal_short}}

| Opções de modelo da CPU        | Opções de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/total de 40 núcleos, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4/total de 64 núcleos, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Número de Bare Metal Servers
{: #vc_nsx-t_addingviewingclusters-adding-bare-metal-number}

* Todos os servidores que você pede têm a mesma configuração.
* Para armazenamento vSAN, é possível pedir entre 4 e 59 servidores.
* Para armazenamento NFS, é possível pedir entre 2 e 59 servidores. No entanto, para cargas de trabalho de produção, um mínimo de 3 servidores é recomendado. Para obter mais informações, consulte [Uma instância do vCenter Server de dois nós é altamente disponível?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

### Configurações de armazenamento
{: #vc_nsx-t_addingviewingclusters-adding-storage-settings}

As configurações de armazenamento são baseadas em sua seleção de configuração do Bare Metal Server e o tipo de armazenamento.

#### Armazenamento vSAN
{: #vc_nsx-t_addingviewingclusters-adding-vsan-storage}

Especifique as seguintes opções vSAN:
* **Tipo de disco e tamanho para discos de capacidade vSAN**: selecione uma opção para os discos de capacidade necessários.
* **Número de discos de capacidade vSAN**: especifique o número de discos de capacidade que deseja incluir.
* Se você desejar incluir discos de capacidade acima do limite de 10, marque a caixa **Intel Optane de alto desempenho**. Essa opção fornece dois compartimentos de disco de capacidade extra para um total de 12 discos de capacidade e é útil para cargas de trabalho que requerem menos latência e rendimento superior de IOPS.

  A opção **Intel Optane de alto desempenho** está disponível somente para os modelos de CPU Skylake.
  {:note}

* Revise os valores **Tipo de disco para discos de cache vSAN** e **Número de discos de cache vSAN**. Esses valores dependem de a caixa **Intel Optane de alto desempenho** estar ou não marcada.
* **Licença do vSAN**: use a licença do VMware fornecida pela IBM para o componente vSAN selecionando **Incluir com a compra** ou Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

Se o seu cluster inicial era um cluster do vSAN, todos os clusters adicionais do vSAN usam a mesma licença do vSAN e têm a mesma configuração que o inicial. Isso também será verdadeiro se qualquer cluster na instância tiver vSAN escolhido para ser implementado nele (inicial ou adicional). A primeira vez que você é solicitado pela licença vSAN (BYOL ou comprada) e a edição. Na próxima vez que você selecionar vSAN para um novo cluster, a licença escolhida inicialmente será reutilizada.

#### Armazenamento NFS
{: #vc_nsx-t_addingviewingclusters-adding-nfs-storage}

Quando você selecionar **Armazenamento do NFS**, será possível incluir armazenamento compartilhado no nível de arquivo para a sua instância na qual todas as ações usam as mesmas configurações ou será possível especificar definições de configuração diferentes para cada compartilhamento de arquivo. Especifique as seguintes opções NFS:

O número de compartilhamentos de arquivo deve estar no intervalo de 1 a 32.
{:note}

* **Configurar compartilhamentos individualmente**: selecione para especificar
diferentes definições de configuração para cada compartilhamento de arquivo.
* **Número de compartilhamentos**: quando quiser usar a mesma definição de configuração para cada compartilhamento de arquivo, especifique o número de compartilhamentos de arquivos para o armazenamento compartilhado NFS que quiser incluir.
* **Tamanho**: selecione a capacidade que atenda às suas necessidades de armazenamento compartilhado.
* **Desempenho**: selecione o IOPS (operações de entrada/saída por segundo) por GB com base em seus requisitos de carga de trabalho.
* **INCLUIR NFS**: selecione para incluir compartilhamentos de arquivos individuais com definições de configuração diferentes.

Tabela 3. Opções de nível de desempenho do NFS

| Opção        | Detalhes       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Essa opção foi projetada para cargas de trabalho não usadas frequentemente. Os aplicativos de exemplo incluem: dados de área segura, hospedando bancos de dados grandes com dados anteriores ou imagens de disco virtual do sistema de memória virtual como backup. |
  | 2 IOPS/GB | Esta opção foi projetada para a maioria de cargas de trabalho de propósito geral. Os aplicativos de exemplo incluem: hospedando bancos de dados pequenos, fazendo backup de aplicativos da web ou imagens de disco da máquina virtual (MV) para um hypervisor. |
  | 4 IOPS/GB | Esta opção foi projetada para cargas de trabalho de maior intensidade que possuem uma alta porcentagem de dados ativos de cada vez. Os aplicativos de exemplo incluem: bancos de dados transacionais. |
  | 10 IOPS/GB | Esta opção foi projetada para os tipos de carga de trabalho mais exigentes, como analítica. Os aplicativos de exemplo incluem: bancos de dados de alta transação e outros bancos de dados sensíveis ao desempenho. Esse nível de desempenho é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo. |

### Configurações de licenciamento
{: #vc_nsx-t_addingviewingclusters-adding-licensing-settings}

Especifique a opção de licenciamento para o componente VMware vSphere no cluster:
* Para usuários do Parceiro de Negócios, a licença do vSphere (Enterprise Plus edition) é incluída e comprada em seu nome.
* Para usuários não do Parceiro de Negócios, é possível usar as licenças do VMware fornecidas pela IBM para esse componente selecionando **Incluir com a compra** ou usar o Bring Your Own License (BYOL) selecionando **Eu fornecerei** e inserindo sua própria chave de licença.

### Configurações da interface de rede
{: #vc_nsx-t_addingviewingclusters-adding-network-interface-settings}

As configurações de ativação da Placa da interface de rede (NIC) baseiam-se em sua seleção de **Rede pública e privada** ou **Somente rede privada**.

### Resumo do Pedido
{: #vc_nsx-t_addingviewingclusters-adding-order-summary}

Com base em sua configuração selecionada para o cluster, o custo estimado é gerado instantaneamente e exibido na área de janela direita **Resumo do pedido**.

## Procedimento para incluir clusters em instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingviewingclusters-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância na qual você deseja incluir clusters.

   Assegure-se de que a instância esteja no status **Pronta para uso**. Caso contrário, não será possível incluir clusters na instância.
   {:note}
3. Clique em **Infraestrutura** na área de janela de navegação esquerda e clique em **Incluir** no canto superior direito da tabela **CLUSTERS**.
4. Na página **Incluir cluster**, insira o nome do cluster.
5. Se você desejar hospedar o cluster em um {{site.data.keyword.CloudDataCent_notm}} diferente daquele no qual a instância está hospedada, sob **Bare Metal Server**, marque a caixa de seleção **Selecionar um local diferente** e escolha o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.
6. Conclua a configuração do Bare Metal. Especifique o **Modelo de CPU**, a quantia de **RAM** e o **Número de {{site.data.keyword.baremetal_short}}**.
7. Conclua a configuração de armazenamento.
  * Se você selecionar **Armazenamento vSAN**, especifique os tipos de disco para os discos de capacidade e de cache, o número de discos e a edição de licença vSAN. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
  * Se você selecionar **Armazenamento NFS** e desejar incluir e configurar as mesmas definições para todos os compartilhamentos de arquivo, especifique o **Número de compartilhamentos**, o **Desempenho** e o **Tamanho (GB)**.
  * Se você selecionar **Armazenamento NFS** e quiser incluir e configurar compartilhamentos de arquivo individualmente, selecione **Configurar compartilhamentos individualmente**. Em seguida, clique no ícone **+** ao lado do rótulo **Incluir armazenamento compartilhado** e selecione o **Desempenho** e o **Tamanho (GB)** para cada compartilhamento de arquivo. Deve-se selecionar pelo menos um compartilhamento de arquivo.
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

### Resultados depois de incluir clusters nas instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingviewingclusters-adding-results}

1. A implementação do cluster é iniciada automaticamente e o status do cluster muda para **Inicializando**. É possível verificar o status da implementação visualizando o histórico de implementação na página **Resumo** da instância.
2. Quando o cluster estiver pronto para usar, seu status mudará para **Pronto para usar**. O cluster recém-incluído é ativado com a Alta disponibilidade (HA) do vSphere e o Distributed Resource Scheduler (DRS) do vSphere.

Não é possível mudar o nome do cluster. Mudar o nome do cluster pode causar falha das operações de inclusão ou remoção de servidores ESXi no cluster.
{:important}

## Procedimento para visualizar clusters nas instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingviewingclusters-viewing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
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
4. Clique em um nome do cluster para visualizar os detalhes do servidor do ESXi, de armazenamento e de interface de rede:

Tabela 4. Detalhes do servidor ESXi

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome do servidor ESXi está no formato a seguir:<br> `<host_prefix><n>.<subdomain_label>.<root_domain>` <br> em que:<br> `host_prefix` é o prefixo do nome do host<br> `n` é a sequência do servidor<br> `subdomain_label` é o rótulo do subdomínio<br> `root_domain` é o nome do domínio raiz |
| Versão | A versão do servidor ESXi. |
| Credenciais | O nome de usuário e a senha para acessar o servidor ESXi. |
| IP privado | O endereço IP privado do servidor ESXi. |
| Barra de Status | O status do servidor ESXi, que pode ser um dos valores a seguir:<br> **Incluído** o servidor do ESXi foi incluído e está pronto para uso.<br> **Incluindo** o servidor do ESXi está sendo incluído.<br> **Excluindo** o servidor do ESXi está sendo excluído. |

Tabela 5. Detalhes do armazenamento

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome do armazenamento de dados. |
| Tamanho | A capacidade do armazenamento. |
| IOPS/GB | O nível de desempenho do armazenamento. |
| Protocolo do NFS | A versão NFS do armazenamento. |

Tabela 6. Interface de rede - detalhes da VLAN

| Item        | Descrição       |  
|:------------- |:------------- |
| Número da VLAN | O número exclusivo da VLAN.  |
| Descrição | A descrição da VLAN.  |
| Localização | O local do data center. |
| Rota primária | A rota primária da VLAN. |

Clique em **Visualizar recurso** para acessar os detalhes da VLAN.

Tabela 7. Interface de rede - detalhes de sub-rede

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome da sub-rede. Clique no nome para acessar os detalhes da sub-rede. |
| Tipo | O tipo de sub-rede: primária ou móvel. |
| Descrição | A descrição da sub-rede. |

Tabela 8. Interface de rede - detalhes do IP

| Item        | Descrição       |  
|:------------- |:------------- |
| IP | O endereço IP. |
| Barra de Status | O status do endereço IP. |
| Descrição |A descrição do endereço IP.  |

## Excluindo clusters das instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingviewingclusters-deleting}

Talvez você queira excluir um cluster de uma instância no caso de ela não ser mais necessária.

### Antes de excluir
{: #vc_nsx-t_addingviewingclusters-deleting-prereq}

* Sempre que possível, exclua clusters usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, exclua os clusters do vCenter Server somente para clusters no local ou clusters que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
* É possível excluir um único cluster de cada vez. Para excluir mais de um cluster, deve-se fazê-lo em sequência. Espere que o cluster anterior seja excluído antes de excluir o próximo.
* Assegure-se de que todos os nós em um cluster estejam ativados e operacionais antes de excluir o cluster.
* Quando você exclui um cluster, todas as MVs do cluster também são excluídas e elas não podem ser recuperadas. Se quiser manter as MVs, migre-as para outros clusters.
* O cluster padrão não pode ser excluído.

### Procedimento para excluir clusters das instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingviewingclusters-deleting-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja excluir clusters.

   Assegure-se de que a instância esteja no status **Pronta para uso**. Caso contrário, não será possível excluir clusters da instância.
   {:note}

3. Clique em **Infraestrutura** na área de janela de navegação esquerda. Na tabela **CLUSTERS**, localize o cluster que você deseja excluir e clique no ícone **Excluir** na coluna **Ações**.
4. Confirme que você concluiu a migração de MVs para outros clusters, se necessário, e que deseja excluir o cluster.

## Links relacionados
{: #vc_nsx-t_addingviewingclusters-related}

* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Expandindo e contraindo a capacidade para o servidor vCenter com instâncias do NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
