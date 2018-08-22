---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Visão geral do IBM Spectrum Protect Plus on IBM Cloud

O serviço {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementar o serviço como uma solução independente ou integrá-lo ao ambiente do IBM Spectrum Protect para transferir cópias para armazenamento e controle de dados de longo prazo.

**Disponibilidade**: esse serviço está disponível apenas para instâncias que estão em execução no vSphere
6.5 e que sejam implementadas na V2.2 ou em liberações mais recentes (ou que passaram por upgrade para elas).

**Notas:**
* Se você instalar o serviço para instâncias que são implementadas na V2.4 ou em liberações mais recentes, a correção 1 do IBM
Spectrum Protect Plus V10.1.1 estará instalada.
* Se você instalar o serviço para instâncias que são implementadas na V2.3, o IBM Spectrum Protect Plus V10.1.1 será
instalado.
* Se você instalar o serviço para instâncias que são implementadas na V2.2, o IBM Spectrum Protect Plus V10.1.0 será instalado.


## Especificações técnicas para o IBM Spectrum Protect Plus on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}:

### Recursos do vCenter

* VM do servidor executando o servidor IBM Spectrum Protect Plus
   * OS: Linux 3.10.0-693.11.1.el7.x86_64
   * 4 x 2,0 GHz de núcleos
   * 32 GB de RAM
   * 370 GB de disco
* VM secundária executando o servidor IBM Spectrum Protect Plus vSnap e o proxy VADP
   * OS: Linux 3.10.0-693.11.1.el7.x86_64
   * CPU e RAM configuradas com base no tamanho do armazenamento selecionado e na orientação de dimensionamento do [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/homelang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)
   * Disco de 150 GB

### Armazenamento para backups

Armazenamento customizável para backups com as opções a seguir:
* Número de armazenamento de arquivos: 1 - 10
* Cada armazenamento de arquivos de resistência: 500, 1.000, 2.000, 4.000, 8.000 ou 12.000 GB
* Desempenho de armazenamento: 0,25, 2 ou 4 IOPS/GB

Veja a [ferramenta de dimensionamento e blueprint do IBM Spectrum Protect Plus](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) para planejamento e dimensionamento.

### Armazenamento para gerenciamento

Um armazenamento de arquivos de resistência de 1000 GB, 2 IOPS/GB, hospedando a máquina virtual do IBM Spectrum Protect Plus e em execução na mesma sub-rede que o armazenamento de backup.

### Rede

Dois endereços IP privados portáteis.

### Licenças e taxas

* IBM Spectrum Protect Plus (10 a um máximo de 1000 licenças da VM em incrementos de 10)
* Licença do IBM Spectrum Protect Plus oferecida por meio do console do {{site.data.keyword.vmwaresolutions_short}} (número de VMs em pacotes de 10) ou como BYOL

## Considerações ao instalar o IBM Spectrum Protect Plus no IBM Cloud

Revise as considerações a seguir antes de instalar o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}.

* Assegure-se de que a CPU e a memória no cluster padrão de sua instância sejam suficientes para a máquina virtual do IBM Spectrum Protect Plus.
* Assegure-se de que as montagens NFS disponíveis nos servidores ESXi sejam suficientes com base na versão dos servidores ESXi.

  Instâncias do Cloud Foundation e instâncias do vCenter Server que são implementadas na V2.2
ou em liberações mais recentes (ou que passaram por upgrade para elas) têm uma configuração de parâmetro `NFS.MaxVolumes` no
VMware. Este parâmetro define o número máximo de montagens NFS em um servidor ESXi e pode ser configurado para um máximo de 256, que é específico para a versão do servidor ESXi. Para obter mais informações, veja [Aumentando o valor padrão que define o número máximo de montagens NFS em um host ESXi/ESX](https://kb.vmware.com/s/article/2239).

  O serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} pode consumir até onze dos volumes NFS em cada servidor ESXi no cluster padrão de sua instância. Além disso, o serviço irá criar montagens NFS temporárias para fins de backup e restauração. Portanto, deve-se configurar o número de montagens NFS para um mínimo de 64 para assegurar que o serviço possa ser instalado e funcionar corretamente.

## Considerações ao remover o IBM Spectrum Protect Plus no IBM Cloud

Revise as considerações a seguir antes de remover o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que todas as configurações da tarefa de backup sejam removidas e que não haja nenhuma operação ativa de backup ou restauração.
* Quando você remove o serviço, o armazenamento para o repositório de backup é removido da VM do IBM Spectrum Protect Plus e a ordem de armazenamento é cancelada, o que exclui permanentemente os dados do repositório de backup.
* Quando você remove o serviço, o armazenamento de backup pedido para o serviço também é removido. Portanto, todos os backups se tornam inacessíveis durante a remoção do serviço.

### Links relacionados

* [Planejamento de serviço preventivo do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gerenciando o IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Solicitando IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentação do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
