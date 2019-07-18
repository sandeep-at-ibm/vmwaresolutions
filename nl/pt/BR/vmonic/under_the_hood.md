---

copyright:

  years:  2019

lastupdated: "2019-06-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions: tenha uma visão mais detalhada
{: #under_the_hood}

## Implemente e gerencie ambientes virtualizados do VMware
{: #under_the_hood-deploy}

Tenha uma visão mais detalhada da arquitetura do {{site.data.keyword.vmwaresolutions_full}}, uma oferta {{site.data.keyword.cloud_notm}} que fornece implementação e gerenciamento de ambientes virtualizados do VMware. Neste tutorial, é possível ver os componentes da oferta juntos em funcionamento para fornecer e manter o ambiente na nuvem pública.

## Duas empresas, uma solução simplificada
{: #under_the_hood-two-companies}

Já há algum tempo, os usuários implementam ambientes virtualizados do VMware no IBM Public Cloud, por conta própria ou com a ajuda de serviços profissionais. Em fevereiro de 2016, [a IBM e a VMware anunciaram uma parceria](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external} para automatizar o processo de implementação do software e dos ambientes do VMware no {{site.data.keyword.cloud_notm}}. Um dos primeiros resultados dessa parceria foi a capacidade de solicitar diversas implementações e licenças de produtos VMware por meio do console do {{site.data.keyword.vmwaresolutions_short}} e, posteriormente, a oferta do [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external} no {{site.data.keyword.cloud_notm}}. Além disso, a IBM e a VMware trabalharam juntas para produzir uma [prescrição de referência padrão de arquitetura e implementação para o VMware](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external} no IBM Public Cloud.

No outono de 2016, a IBM e a VMware liberaram em conjunto o {{site.data.keyword.vmwaresolutions_short}}. Esse conjunto de ofertas baseia-se nas tecnologias de virtualização do VMware, incluindo computação virtualizada (VMware vSphere), rede (VMware NSX) e, opcionalmente, armazenamento virtualizado (VMware vSAN). Esses ambientes são apropriadamente chamados de data centers definidos por software.

O {{site.data.keyword.vmwaresolutions_short}} baseia-se na tecnologia VMware para simplificar significativamente a implementação e o gerenciamento desses data centers definidos por software no IBM Public Cloud. Usando o {{site.data.keyword.vmwaresolutions_short}}, agora é possível implementar partes da arquitetura de referência padrão no {{site.data.keyword.cloud_notm}} automaticamente , em vez de manualmente. Ambientes que anteriormente levavam semanas para serem implementados e configurados agora podem ser provisionados em questão de horas.

Essa facilidade de implementação permite se concentrar na implementação de soluções no VMware, em vez de criar seu ambiente. Com os ambientes rapidamente à sua disposição, é possível criar soluções de nuvem híbrida que abrangem sua nuvem privada e o IBM Public Cloud, bem como soluções nativas da nuvem no IBM Public Cloud. Combinando diversas implementações, é possível incluir facilmente recursos de recuperação de desastre ou alta disponibilidade em suas soluções.

Agora, obtenha uma visão mais detalhada da arquitetura do {{site.data.keyword.vmwaresolutions_short}}. Você obterá uma compreensão dos diferentes componentes que fazem parte da solução e de como eles trabalham juntos para provisionar e gerenciar seu data center definido por software no {{site.data.keyword.cloud_notm}}. Você também saberá mais sobre a topologia de rede e as diversas opções de conexão com o seu ambiente.

## Conceitos básicos do IBM Cloud for VMware Solutions

Seus data centers definidos por software são provisionados e gerenciados usando o console do [{{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}. Você efetua login no console usando sua conta IBMid.

No catálogo de soluções VMware, é possível provisionar um dos diversos tipos de ambiente de virtualização. A solução de virtualização em destaque é o *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*, que oferece o hypervisor vSphere, o VMware vCenter Server, o VMware NSX e, opcionalmente, o VMware vSAN do VMware. Também é possível provisionar esse ambiente com mais serviços complementares que fornecem backup, recuperação de desastre, migração, segurança, conformidade e serviços de rede.

Antes de solicitar uma instância do vCenter Server, deve-se configurar a chave de API da infraestrutura do {{site.data.keyword.cloud_notm}} no catálogo de soluções do VMware. Para isso, clique no link [Configurações](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external} do menu esquerdo do console e insira seu nome de usuário e chave de API onde for solicitado para as credenciais da infraestrutura do {{site.data.keyword.cloud_notm}}. O sistema verifica se a chave de API e a conta têm permissões e configurações apropriadas para implementar sua instância.

Ao solicitar sua instância do vCenter Server, você primeiro escolhe seu nome e a versão do VMware vSphere. Todas as instâncias do VMware são implementadas com os controladores de domínio do Microsoft Active Directory e, para fins de conexão única, deve-se designar a instância como um site primário ou secundário. Uma instância primária é a primeira ou única instância em seu domínio de conexão única. É possível implementar mais instâncias secundárias e associá-las ao mesmo domínio de conexão única de uma instância primária existente. Em seguida, você escolhe entre trazer suas próprias licenças do VMware ou qual edição da licença alugar do {{site.data.keyword.cloud_notm}}. Finalmente, você escolhe a região e o data center do {{site.data.keyword.cloud_notm}} para sua instância, bem como as características de CPU e memória para os hosts em seu cluster.

Na próxima parte da página do pedido, você insere as características de armazenamento e rede da sua instância. É possível escolher entre os armazenamentos vSAN e NFS para seu cluster, com opções de tamanho e número de discos vSAN Flash e da edição de licença do vSAN ou de tamanho, contagem e desempenho dos volumes de armazenamento NFS. Para a rede, você escolhe o prefixo do nome de seus hosts e o subdomínio e o domínio do cluster. Você tem a opção de implementar os controladores do Active Directory como uma única instância de servidor virtual (VSI) do {{site.data.keyword.cloud_notm}} ou como duas máquinas virtuais em seu cluster para as quais você precisa fornecer licenciamento e ativação.

Na parte inferior da página do pedido do vCenter Server, é possível selecionar dentre diversos serviços complementares que podem ser implementados em sua instância do VMware e que são faturados para sua conta {{site.data.keyword.cloud_notm}}. Alguns serviços exigem configuração adicional, que é especificada como parte do formulário de pedido.

O formulário de pedido calcula e exibe uma estimativa de preço com base em suas seleções. Você tem a oportunidade de revisar essa estimativa, bem como diversos termos e condições antes de fazer seu pedido.

### Opções de implementação
{: #under_the_hood-deploy-options}

O formulário de pedido do vCenter Server apresenta diversas opções de CPU, memória e armazenamento para sua instância. Novas opções são disponibilizadas regularmente, portanto, confira o catálogo do {{site.data.keyword.cloud_notm}} para obter as informações de disponibilidade mais recentes.

O {{site.data.keyword.cloud_notm}} implementa sua instância do vCenter Server usando três VLANs: uma pública e duas privadas. A VLAN pública é conectada a interfaces dual de 10 GbE e é amplamente reservada para ser usada de acordo com seus critérios, para conectividade pública ou tunelamento para suas próprias implementações de carga de trabalho. No entanto, no momento da implementação, um par do NSX Edge Services Gateway é implementado na VLAN pública para permitir que alguns serviços complementares se conectem à rede pública para fins de licenciamento e faturamento. As VLANs privadas são conectadas a interfaces dual de 10 GbE separadas: a primeira VLAN privada é usada para comunicações de gerenciamento e o NSX VTEP; a segunda é usada para o vMotion e para o tráfego de armazenamento NFS.

As instâncias do VMware podem ser provisionadas em 35 {{site.data.keyword.CloudDataCents_notm}} diferentes. O {{site.data.keyword.cloud_notm}} provisiona novos data centers ocasionalmente. Confira o catálogo do {{site.data.keyword.cloud_notm}} para obter a lista mais recente de locais disponíveis.

### Implementação de instância
{: #under_the_hood-inst-deploy}

Ao solicitar uma nova instância do VMware vCenter, você escolhe seu local e especificação. Em seguida, o {{site.data.keyword.vmwaresolutions_short}} usa seu nome de usuário e chave de API selecionados anteriormente do {{site.data.keyword.cloud_notm}} para orquestrar todo o processo de solicitação, instalação e configuração de seu ambiente de virtualização. Isso inclui:

1. Solicitação de VLANs e sub-redes para a rede.
2. Pedindo o  {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}  com o vSphere Hypervisor instalado.
3. Implementação e configuração do VMware vCenter Server com o Platform Services Controller integrado, o VMware NSX Manager, controladores e gateways de serviços do Edge.
4. Solicitação e configuração de seu armazenamento de cluster, incluindo o armazenamento VMware vSAN ou {{site.data.keyword.cloud_notm}} Endurance.
5. Implementação de um componente de gerenciamento da IBM chamado IBM CloudDriver.
6. Implementação e configuração de quaisquer serviços complementares selecionados para sua instância.
7. Validando a instalação e a configuração do ambiente.

Você seleciona o {{site.data.keyword.CloudDataCent_notm}} no qual deseja provisionar sua instância. Se o hardware estiver disponível em seu {{site.data.keyword.CloudDataCent_notm}} selecionado, o processo de provisionamento de instância levará, normalmente, menos de 24 horas.

Uma vez que sua instância tenha sido provisionada, se estiver conectado à sua conta {{site.data.keyword.cloud_notm}} por meio de uma VPN, será possível se conectar ao seu servidor vCenter diretamente do navegador da web de sua estação de trabalho.

Os componentes de sua instância geralmente são acessados ​​pelos seus nomes de host, em vez de pelos endereços IP. Para conectar-se e autenticar-se com o vCenter, é preciso garantir que o nome de host do vCenter e do PSC (Platform Services Controller) possa ser resolvido pela sua estação de trabalho, incluindo-os no arquivo hosts de sua estação de trabalho, conforme mostrado na Listagem 1. É possível localizar o nome de host e o endereço IP no console do {{site.data.keyword.vmwaresolutions_short}}, na guia **Resumo** de sua instância. Também é possível incluir os nomes de host e os endereços IP de seus hosts do vSphere em seu arquivo hosts.

*Listagem 1. Arquivo hosts*

<pre># vCenter do site de Dallas e PSC (Platform Services Controller)
10.208.85.196  vcenter-dallas.dallas.example.com
# Hosts do site de Dallas
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

Depois que sua instância for implementada, será possível gerenciá-la no console. Os recursos de gerenciamento incluem a capacidade de executar cada um dos seguintes procedimentos:

* Implementar e remover nós de seu cluster
* Implementar e remover clusters adicionais no mesmo data center e pod ou em data centers e pods alternativos
* Implementar e remover serviços complementares de sua instância
* Fazer upgrade de determinadas edições de licença para sua instância

O console do {{site.data.keyword.vmwaresolutions_short}} fornece uma visão detalhada de cada uma de suas instâncias do vCenter Server. Para cada instância, a guia **Resumo** inclui um link para o console do vCenter e outros detalhes sobre a instância e os componentes de gerenciamento. A guia **Infraestrutura** mostra detalhes sobre os clusters, os hosts, o armazenamento e a rede da instância e permite incluir ou remover clusters, hosts e armazenamento. Na guia **Atualizar e corrigir**, é possível fazer upgrade de determinadas edições de licença. Na guia **Serviços**, é possível visualizar e gerenciar os serviços complementares implementados em sua instância. A guia **Histórico de implementação** mostra um histórico de todas as ações realizadas em sua instância.

## Componentes do IBM Cloud for VMware Solutions
{: #under_the_hood-comp}

Diversos componentes diferentes trabalham juntos para provisionar e gerenciar seu ambiente. A maioria é implementada em sua conta {{site.data.keyword.cloud_notm}}. Como a solução depende de todos esses componentes trabalhando juntos, não modifique ou cancele nenhum deles em sua conta {{site.data.keyword.cloud_notm}}. A maneira correta de remover uma instância em execução é usando o console, em vez de cancelar os componentes individuais.

Embora esse seja um ambiente de virtualização integrado, o custo de diversos componentes de virtualização (como licenças do VMware), componentes de infraestrutura (servidores bare metal, VLANs, sub-redes e armazenamento) e componentes de gerenciamento é detalhado na conta que você recebe do {{site.data.keyword.cloud_notm}}.

### O console do IBM Cloud for VMware Solutions
{: #under_the_hood-console}

Você efetua login no [console do {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external} para criar e gerenciar suas instâncias. Essa parte da solução é responsável pelo pedido inicial, pelo provisionamento e pelo gerenciamento contínuo do seu ambiente. Suas instâncias implementadas se comunicam com o console por meio da rede do {{site.data.keyword.cloud_notm}} Private.

### O componente IBM CloudBuilder
{: #under_the_hood-ibm-cb}

Quando você provisiona uma nova instância, o console implementa uma instância de servidor virtual (VSI) temporária em sua conta {{site.data.keyword.cloud_notm}}. Esse servidor virtual é conhecido como IBM CloudBuilder. Ele realiza a instalação e a configuração de todos os componentes da instância, além da validação do ambiente. Após a conclusão do provisionamento, o CloudBuilder é excluído.

### O componente IBM CloudDriver
{: #under_the_hood-ibm-cd}

Muito parecido com o CloudBuilder, o IBM CloudDriver é uma instância de servidor virtual (VSI) temporária implementada em sua conta {{site.data.keyword.cloud_notm}} para a execução de operações subsequentes em sua instância. Ele é implementado, conforme necessário, para configurar ou remover hosts, clusters, armazenamento ou serviços de sua instância.

### Componentes do VMware
{: #under_the_hood-vmware-comp}

Para todas as instâncias, o vSphere Hypervisor é instalado nos servidores bare metal. Em seguida, o {{site.data.keyword.cloud_notm}} implementa um vCenter Server Appliance com PSC (Platform Services Controller) integrado, NSX Manager, três controladores NSX e dois pares de gateways de serviços do NSX Edge no cluster de gerenciamento do VMware.

### Componentes adicionais
{: #under_the_hood-add-comp}

Dependendo da sua escolha, uma VSI ou duas máquinas virtuais do Microsoft Windows são implementadas com ou no cluster, como servidores do Active Directory para componentes de gerenciamento. Opcionalmente, é possível incluir seus próprios servidores do Active Directory como origens de identidade adicionais para o acesso de gerenciamento.

Independentemente de como você escolhe fornecer a continuidade de negócios para suas próprias cargas de trabalho, o {{site.data.keyword.cloud_notm}} recomenda fortemente que você faça backup dos componentes de gerenciamento de sua instância. O console do {{site.data.keyword.vmwaresolutions_short}} permite implementar um servidor de backup IBM Spectrum Protect Plus integrado ou um servidor de backup Veeam Backup & Replication com sua instância. Esses serviços de backup podem ser usados como parte de uma [solução de backup completa](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup) para sua instância.

### Licenças
{: #under_the_hood-licenses}

O {{site.data.keyword.cloud_notm}} fornece diversas licenças do VMware (como o vCenter Server e o NSX), que são instaladas em sua instância e faturadas para sua conta {{site.data.keyword.cloud_notm}}.

## Arquitetura de rede do IBM Cloud for VMware Solutions
{: #under_the_hood-network}

Sua instância do vCenter Server se conecta a uma VLAN pública para uso com suas cargas de trabalho implementadas. A VLAN pública é amplamente reservada para ser usada de acordo com seus critérios, mas um par de gateways de serviços do NSX Edge está conectado à ela para permitir que determinados serviços complementares se comuniquem para fins de licenciamento e faturamento. É possível implementar uma instância sem usar a rede pública, no entanto, nem todos os serviços complementares serão suportados e talvez seja necessário fornecer um proxy da web para permitir o uso de alguns desses serviços.

Sua instância do vCenter Server tem duas VLANs privadas truncadas em conjunto na interface da rede privada para seus hypervisors. A primeira VLAN privada é usada para a conectividade de gerenciamento (como comunicações do vCenter com hypervisors) e pelo NSX para o tunelamento de todo o tráfego VXLAN para as cargas de trabalho implementadas. A segunda VLAN privada é usada para o vMotion e o tráfego de armazenamento. O tráfego de armazenamento pode ser o protocolo NFS ou vSAN.

O {{site.data.keyword.cloud_notm}} fornece determinados serviços adicionais nessas VLANs privadas. Seus servidores do Active Directory se comunicam com os servidores DNS do {{site.data.keyword.cloud_notm}} sobre a VLAN de gerenciamento privada. Seus hosts e outros componentes se comunicam com os servidores NTP do {{site.data.keyword.cloud_notm}} sobre a VLAN de gerenciamento privada. O IBM CloudBuilder e o CloudDriver também se comunicam com o console do {{site.data.keyword.vmwaresolutions_short}} sobre essa VLAN. Seus hosts se conectam ao armazenamento do {{site.data.keyword.cloud_notm}} Endurance sobre a VLAN de armazenamento privada.

### Conectando-se à sua instância
{: #under_the_hood-connect-inst}

É possível se conectar às suas instâncias de diversas maneiras. É possível se conectar diretamente a endereços IP privados em sua instância (por exemplo, o vCenter) usando a [VPN do {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/VPN-Access){:external}. Também é possível solicitar [dispositivos de rede do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-appliances){:external} e [firewalls virtuais ou de hardware do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-security), como o FortiGate e o vSRX, para sua conta. O {{site.data.keyword.cloud_notm}} também oferece [links diretos](https://www.ibm.com/cloud/direct-link){:external} entre sua rede e as VLANs na sua conta {{site.data.keyword.cloud_notm}}.

Para acessar suas VMs implementadas, é possível aplicar endereços IP públicos diretamente a elas. No entanto, também é possível usar os recursos de dispositivo de rede e firewall do {{site.data.keyword.cloud_notm}} para configurar um acesso público mais seguro às suas VMs por meio do NAT e do firewall. Além disso, é possível implementar servidores NSX Edge e usá-los para configurar a conectividade de VPN ou NAT com suas VMs.

## Conclusão
{: #under_the_hood-conclusion}

Nesse tutorial, você aprendeu sobre os recursos básicos do {{site.data.keyword.vmwaresolutions_short}} para a implementação e o gerenciamento de ambientes de virtualização do VMware padronizados na nuvem pública. Como esses ambientes podem ser implementados com mais rapidez do que nunca, é possível concentrar seus esforços na implementação de seus aplicativos e soluções neles e na conexão de nuvens para a recuperação de desastre ou a alta disponibilidade.

Exploramos os diversos componentes implementados em sua conta {{site.data.keyword.cloud_notm}}, que aparecem em sua fatura do {{site.data.keyword.cloud_notm}} e trabalham juntos para manter seu ambiente em execução. Finalmente, consideramos a arquitetura de rede da solução e algumas opções para estabelecer a conectividade com o ambiente, seja por meio de diversas opções de conectividade segura para manter as comunicações privadas ou por meio de diversas opções para a conectividade com a Internet pública.

Agora que você sabe tudo o que precisa para começar, siga em frente e implemente hoje seu próximo ambiente de virtualização do VMware no {{site.data.keyword.cloud_notm}}.

## Links relacionados
{: #under_the_hood-related}

* [Iniciar](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Arquitetura do VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
