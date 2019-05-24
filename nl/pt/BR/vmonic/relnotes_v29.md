---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas sobre a liberação para a V2.9
{: #relnotes_v29}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vCenter Server on IBM Cloud com NSX-T
{: #relnotes_v29-vcs-nsx-t}

Essa liberação apresenta o VMware vCenter Server on {{site.data.keyword.cloud_notm}} com a oferta NSX-T como um teste de prova de conceito ou de ambiente de simulação. O vCenter Server com NSX-T é uma nuvem hospedada privada que permite fazer um test drive da plataforma de rede de próxima geração do VMware, a NSX-T.

Para obter mais informações, veja os tópicos a seguir:

* [Visão geral do vCenter Server com NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [ Pedindo o vCenter Server com instâncias do NSX-T ](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Fim do suporte para o VMware Cloud Foundation on IBM Cloud
{: #relnotes_v29-vcf-eos}

Para consolidar nossas ofertas para uma melhor experiência de cliente, o {{site.data.keyword.cloud_notm}} não fornecerá mais suporte para o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a partir de 13 de maio de 2019.    
Com o avanço, todos os clientes serão direcionados para o VMware vCenter Server on {{site.data.keyword.cloud_notm}}, que oferece mais flexibilidade em relação às opções de armazenamento e licenciamento.   
Os clientes existentes que usam o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} serão auxiliados a migrar para o VMware vCenter Server on {{site.data.keyword.cloud_notm}} até a data de término de suporte em 13 de maio de 2019.

Após 13 de maio, os recursos de gerenciamento para o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} serão removidos do console do {{site.data.keyword.vmwaresolutions_short}}. As instâncias que não foram migradas para o VMware vCenter Server on {{site.data.keyword.cloud_notm}} podem ser acessadas por meio do console de infraestrutura do IBM Cloud.

Os clientes serão contatados pelo suporte do {{site.data.keyword.cloud_notm}} antes de 25 de março de 2019 para iniciar a migração do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}. Para obter mais informações sobre as opções de migração para clientes existentes, consulte a [ página da wiki do {{site.data.keyword.vmwaresolutions_short}} ](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}.
 
Os clientes podem visualizar sua instância existente do VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} no [console do {{site.data.keyword.vmwaresolutions_short}} ](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted).

## Suporte do VMware vSphere 6.7 Update 1
{: #relnotes_v29-vsphere}

Agora você tem a opção de pedir o VMware vSphere versão 6.7 Atualização 1 com seu VMware vCenter Server, VMware vCenter Server with Hybridity Bundle e VMware vSphere em instâncias do {{site.data.keyword.cloud_notm}}.

Além disso, as instâncias de Single-node Trial for Migration and App Modernization agora são pedidas com o vSphere Enterprise Plus 6.7u1.

O vSphere Enterprise Plus 6.7u1 está disponível para Broadwell e Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} apenas.

Para obter mais informações, consulte as seções _Configurações de licença_ em:

* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Suporte para Interfaces de Programação de Aplicativos
{: #relnotes_v29-api}

Agora, as interfaces de programação de aplicativo (APIs) estão disponíveis para implementação de instâncias, exclusão de instâncias e inclusão e remoção de servidores e clusters ESXi.

A documentação da API de REST também está disponível na seção *Referência* da documentação do usuário. Para obter mais informações, consulte [API do {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/apidocs/vmware-solutions).

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v29-vcs}

Esta liberação aplica os upgrades e melhorias a seguir:

* vSphere ESXi 6.7 Atualização 1 (construção 6.7.0-11675023)
* vSphere ESXi 6.5 Atualização 2 (construção 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1 (construção 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (construção 11197766)
* NSX-T para vSphere 2.4

Para obter mais informações sobre a seleção de seus componentes do VMware, consulte [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Atualizações para data centers
{: #relnotes_v29-dc}

Os novos data centers a seguir estão disponíveis para implementação: **FRA-05 - Frankfurt** e **LON-05 - Londres**. Para obter mais informações, consulte [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).

### Aprimoramentos do servidor ESXi
{: #relnotes_v29-vcs-esxi}

* Agora, o protocolo de shell seguro (SSH) é desativado para servidores ESXi antes da entrega da instância. Se você deseja ativar o SSH, consulte [Ativar SSH por meio do vSphere Web Client](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vcli.getstart.doc%2FGUID-C3A44A30-EEA5-4359-A248-D13927A94CCE.html).
* Iniciando com a liberação V2.9, as operações do servidor ESXi a seguir estão disponíveis:

   * Inclua novos servidores ESXi em um cluster existente enquanto os servidores estiverem no modo de manutenção. As máquinas virtuais não são migradas para os novos servidores até que você as remova do modo de manutenção.
   * Inclua ou remova os servidores ESXi simultaneamente por múltiplos clusters em sua instância.

Para obter mais informações, consulte [Expandindo e contraindo a capacidade para instâncias do servidor do vCenter](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

### Tamanho do armazenamento do Network File System
{: #relnotes_v29-vcs-nfs}

Para pedidos de instância do vCenter Server, agora é possível incluir até 24 TB de armazenamento compartilhado do Network File System (NFS) para os níveis de desempenho de 0,25, 2 e 4 IOPS/GB.

O nível de desempenho de 10 IOPS/GB ainda é limitado a uma capacidade máxima de 4 TB por compartilhamento de arquivo.
{:note}

## Atualizações para serviços complementares
{: #relnotes_v29-services}

### Caveonix RiskForesight no IBM Cloud
{: #relnotes_v29-services-caveonix}

Agora, o serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} está disponível para instâncias do VMware vCenter Server que são implementadas ou atualizadas para a V2.9 ou liberações mais recentes. Esse serviço pode ajudar a gerenciar o risco cibernético e de conformidade com monitoramento proativo e controles de defesa automatizada para proteger contra ameaças e para atender às regulamentações da indústria ou do governo.

É possível pedir instâncias do vCenter Server com o serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} incluído ou incluir posteriormente esse serviço em suas instâncias do vCenter Server existentes na guia **Serviços** na página de detalhes da instância.

Também é possível pedir uma licença independente do Caveonix RiskForesight sem associá-la a nenhuma instância do VMware para licenciamento e ativação de suas cargas de trabalho no local.

Para obter mais informações, veja:
* [ Considerações para o Caveonix RiskForesight no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [ Pedindo o Caveonix RiskForesight no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [ Considerações para licenças do Caveonix ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [ Pedindo licenças do Caveonix ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

Na liberação atual, o F5-BigIP VE V14.1.0.2 é instalado em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no F5-BigIP VE V14.1.0.2, consulte [Nota sobre a liberação: BIG-IP 14.1.0 Novo e instalação](https://techdocs.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

Na liberação atual, o HyTrust CloudControl 5.4.2 é instalado em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no HyTrust CloudControl 5.4.2, consulte [HyTrust CloudControl Notas sobre a liberação da versão 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

Agora, dois novos terminais estão disponíveis em Sydney para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Configuração do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering#kmip_standalone_ordering-config).

(Atualizado em 09 de abril de 2019) Anteriormente, o KMIP for VMware on {{site.data.keyword.cloud_notm}} usava o IBM Key Protect for {{site.data.keyword.cloud_notm}} para criar, criptografar e decriptografar chaves de criptografia. Iniciando com a liberação V2.9, o KMIP for VMware on {{site.data.keyword.cloud_notm}} também pode usar o {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services, um conjunto completo de serviços de criptografia e de gerenciamento de chave, para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Visão geral do KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) e [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started).

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

Na liberação atual, o Veeam Backup and Replication 9.5 Atualização 4 é instalado em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no Veeam 9.5u4, consulte [Informações sobre a liberação para o Veeam Backup and Replication 9.5 Atualização 4](https://www.veeam.com/kb2878){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

Na liberação atual, o Zerto Virtual Replication 6.5 Atualização 3 é instalado em todas as instâncias recém-implementadas. Para obter mais informações sobre os novos recursos no Zerto Virtual Replication 6.5 Atualização 3, consulte [Notas sobre a liberação para o Zerto Virtual Replication V6.5 Atualização 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}.

## Atualizações e aprimoramentos da interface com o usuário
{: #relnotes_v29-ui}

A interface com o usuário é atualizada e fornece os aprimoramentos a seguir:

* Na página **Infraestrutura**, uma nova tabela de **Interface de rede** fornece detalhes de VLAN, sub-rede e endereço IP para o seu cluster.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.
