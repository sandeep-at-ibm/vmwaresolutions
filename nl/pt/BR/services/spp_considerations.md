---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do IBM Spectrum Protect Plus on IBM Cloud

O serviço {{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementar o serviço como uma solução independente ou integrá-lo ao ambiente do IBM Spectrum Protect para transferir cópias para armazenamento e controle de dados de longo prazo.

Esse serviço está disponível somente para instâncias que estão executando o vSphere 6.5 e que são implementadas ou submetidas a upgrade para a V2.2 ou mais recente. A versão atual do {{site.data.keyword.IBM}} Spectrum Protect Plus que está instalada é a V10.1.2.
{:note}

## Especificações técnicas para o IBM Spectrum Protect Plus on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}:

### Recursos do vCenter

* MV do servidor executando o servidor IBM Spectrum Protect Plus
   * Sistema operacional Linux 3.10.0-693.11.1.el7.x86_64
   * 4 x 2,0 GHz de núcleos
   * 32 GB de RAM
   * 370 GB de disco
* MV secundária executando o servidor IBM Spectrum Protect Plus vSnap e o proxy VADP
   * Sistema operacional Linux 3.10.0-693.11.1.el7.x86_64
   * CPU e RAM configuradas com base no tamanho do armazenamento selecionado e na orientação de dimensionamento do [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)
   * Disco de 150 GB

### Armazenamento para backups

Armazenamento customizável para backups com as opções a seguir:
* Número de armazenamento de arquivos: 1 - 10
* Cada armazenamento de arquivos de resistência: 500, 1.000, 2.000, 4.000, 8.000 ou 12.000 GB
* Desempenho de armazenamento: 0,25, 2 ou 4 IOPS/GB

Veja a [ferramenta de dimensionamento e blueprint do IBM Spectrum Protect Plus](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) para planejamento e dimensionamento.

### Armazenamento para gerenciamento

Um armazenamento de arquivo de resistência de 2 IOPS/GB, 1000 GB, que hospeda a máquina virtual do IBM Spectrum Protect Plus e que esteja sendo executado na mesma sub-rede que o armazenamento de backup.

### Rede

Dois endereços IP privados portáteis.

### Licenças e taxas

* IBM Spectrum Protect Plus (10 a um máximo de 1000 licenças da MV em incrementos de 10)
* Licença do IBM Spectrum Protect Plus oferecida por meio do console do {{site.data.keyword.vmwaresolutions_short}} (número de MVs em pacotes de 10) ou como BYOL

## Considerações ao instalar o IBM Spectrum Protect Plus on IBM Cloud

Revise as considerações a seguir antes de instalar o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}.

* Assegure-se de que a CPU e a memória no cluster padrão de sua instância sejam suficientes para a máquina virtual do IBM Spectrum Protect Plus.
* Assegure-se de que as montagens NFS disponíveis nos servidores ESXi sejam suficientes com base na versão dos servidores ESXi.

  Instâncias do Cloud Foundation e instâncias do vCenter Server que são implementadas na V2.2
ou em liberações mais recentes (ou que passaram por upgrade para elas) têm uma configuração de parâmetro `NFS.MaxVolumes` no
VMware. Esse parâmetro define o número máximo de montagens do NFS em um servidor ESXi e pode ser configurado para um máximo de 256, que é específico para a versão do servidor ESXi. Para obter mais informações, veja [Aumentando o valor padrão que define o número máximo de montagens NFS em um host ESXi/ESX](https://kb.vmware.com/s/article/2239).

  O serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} pode usar até 11 dos volumes NFS em cada servidor ESXi no cluster padrão de sua instância. Além disso, o serviço cria montagens transientes do NFS para propósitos de backup e restauração. Portanto, deve-se configurar o número de montagens NFS para um mínimo de 64 para assegurar que o serviço possa ser instalado e funcionar corretamente.

## Considerações ao remover o IBM Spectrum Protect Plus on IBM Cloud

Revise as considerações a seguir antes de remover o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que todas as configurações de tarefa de backup sejam removidas juntamente com operações de backup ou restauração ativas.
* Quando você remove o serviço, o armazenamento para o repositório de backup é removido da MV do IBM Spectrum Protect Plus e o pedido de armazenamento é cancelado, o que exclui os dados do repositório de backup permanentemente.
* Quando você remove o serviço, o armazenamento de backup que é pedido para o serviço é removido também. Todos os backups se tornam inacessíveis durante a remoção do serviço.

### Links relacionados

* [Planejamento de serviço preventivo do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gerenciando o IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingspp.html)
* [Solicitando IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/spp_ordering.html)
* [Documentação do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
