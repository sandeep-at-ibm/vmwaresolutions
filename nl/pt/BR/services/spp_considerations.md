---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Visão geral do IBM Spectrum Protect Plus on IBM Cloud

O serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} fornece uma solução eficiente e escalável para proteção de dados, reutilização de dados e recuperação de dados para ambientes virtuais. É possível implementar o serviço como uma solução independente ou integrá-lo ao seu ambiente do IBM Spectrum Protect Plus para transferir cópias para armazenamento de longo prazo e controle de dados.

**Disponibilidade**: esse serviço está disponível apenas para instâncias que estão em execução no vSphere
6.5 e que sejam implementadas na V2.2 ou em liberações mais recentes (ou que passaram por upgrade para elas).

**Notas:**
* Se você instalar o serviço para instâncias que são implementadas na V2.4 ou em liberações mais recentes, a correção 1 do IBM
Spectrum Protect Plus V10.1.1 estará instalada. O serviço fornece suporte de recuperação para máquinas virtuais (VMs) de gerenciamento automaticamente.
* Se você instalar o serviço para instâncias que são implementadas na V2.3, o IBM Spectrum Protect Plus V10.1.1 será
instalado. O serviço fornece backup para VMs de gerenciamento automaticamente.
* Se você instalar o serviço para instâncias que são implementadas na V2.2, o IBM Spectrum Protect Plus V10.1.0 será instalado. O serviço fornece proteção de dados somente para VMs de carga de trabalho.


## Componentes do IBM Spectrum Protect Plus on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}:

### Recursos do vCenter

* Uma única máquina virtual (VM) executando o servidor IBM Spectrum Protect Plus
* 4 x 2,0 GHz de núcleos
* 32 GB de RAM
* 370 GB de disco

### Armazenamento para backups

Armazenamento customizável para backups com as opções a seguir:
* Número de armazenamento de arquivos: 1, 2, 3 ou 4
* Cada armazenamento de arquivos de resistência: 500, 1.000, 2.000, 4.000, 8.000 ou 12.000 GB
* Desempenho de armazenamento: 0,25, 2 ou 4 IOPS/GB

### Armazenamento para gerenciamento

Um armazenamento de arquivos de resistência (500 GB, 2 IOPS/GB) que hospeda a máquina virtual do IBM Spectrum Protect Plus e em execução na mesma sub-rede que o armazenamento de backup pedido para o serviço.

### Rede

Um endereço IP privado móvel.

### Licenças e taxas

O IBM Spectrum Protect Plus pode ser licenciado no console do {{site.data.keyword.vmwaresolutions_short}} para 10 até um máximo de 1000 VMs em incrementos de 10. Também é possível usar Bring Your Own License (BYOL) e fazer upload do arquivo de licença durante o processo de instalação.

## Considerações ao instalar o IBM Spectrum Protect Plus no IBM Cloud

Revise as considerações a seguir antes de instalar o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}.

* Assegure-se de que a CPU e a memória no cluster padrão de sua instância sejam suficientes para a máquina virtual do IBM Spectrum Protect Plus.
* Assegure-se de que as montagens NFS disponíveis nos servidores ESXi sejam suficientes com base na versão dos servidores ESXi.

  Instâncias do Cloud Foundation e instâncias do vCenter Server que são implementadas na V2.2
ou em liberações mais recentes (ou que passaram por upgrade para elas) têm uma configuração de parâmetro `NFS.MaxVolumes` no
VMware. Este parâmetro define o número máximo de montagens NFS em um servidor ESXi e pode ser configurado para um máximo de 256, que é específico para a versão do servidor ESXi. Para obter mais informações, veja [Aumentando o valor padrão que define o número máximo de montagens NFS em um host ESXi/ESX](https://kb.vmware.com/s/article/2239).

  O serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} pode consumir até cinco dos volumes NFS em cada servidor ESXi no cluster padrão de sua instância. Além disso, o serviço irá criar montagens NFS temporárias para fins de backup e restauração. Portanto, deve-se configurar o número de montagens NFS para um mínimo de 64 para assegurar que o serviço possa ser instalado e funcionar corretamente.

## Considerações ao remover o IBM Spectrum Protect Plus no IBM Cloud

Revise as considerações a seguir antes de remover o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que todas as configurações da tarefa de backup sejam removidas e que não haja nenhuma operação ativa de backup ou restauração.
* Quando você remove o serviço, o armazenamento para o repositório de backup é removido da VM do IBM Spectrum Protect Plus e a ordem de armazenamento é cancelada, o que exclui permanentemente os dados do repositório de backup.
* Quando você remove o serviço, o armazenamento de backup pedido para o serviço também é removido. Portanto, todos os backups se tornam inacessíveis durante a remoção do serviço.

## Links relacionados

* [Planejamento de Serviços Preventivos do IBM Spectrum Protect Plus no IBM Cloud](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gerenciando o IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Solicitando IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentação do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
