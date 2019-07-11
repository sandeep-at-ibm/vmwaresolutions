---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud Visão Geral
{: #veeam_considerations}

O serviço Veeam no {{site.data.keyword.cloud}} se integra continuamente diretamente com os hypervisors do VMware para ajudar sua empresa a alcançar alta disponibilidade. Esse serviço fornece pontos de recuperação e objetivos de tempo para seus aplicativos e dados. Os pontos de recuperação e os objetivos de tempo podem ser fornecidos em menos de 15 minutos após a conclusão da configuração. Usando esse serviço, você controla o backup e a restauração de todas as máquinas virtuais (MVs) para sua infraestrutura diretamente do console do Veeam.

Esse serviço está disponível somente para instâncias que são implementadas na V1.8 ou mais recente. A versão atual do Veeam instalada é a 9.5u4.
{:note}

## Especificações técnicas para o Veeam on IBM Cloud
{: #veeam_considerations-specs}

Os componentes a seguir são pedidos e incluídos no serviço Veeam no {{site.data.keyword.cloud_notm}}:

### VSIs
{: #veeam_considerations-specs-vsi}

* Single VSI with Veeam Backup and Replication 9.5 OS Add-on e Veeam Availability Suite 9.5
* Windows Server 2016 Standard Edition (64 bits)
* Cores de 4 x 2,0 GHz
* 8 vCPU, 32 GB de RAM
* Uplink de rede privada de 1 Gbps
* Disco de 100 GB (SAN)

### Armazenamento para backups
{: #veeam_considerations-specs-storage}

* Armazenamento iSCSI do Endurance (2.000, 4.000, 8.000 ou 12.000 GB)
* Desempenho do armazenamento (0,25; 2 ou 4 IOPS/GB)

Como parte da instalação e configuração do serviço Veeam, os repositórios a seguir foram criados:
* Para arquivos de backup de configuração do Veeam: um repositório denominado `IC4V Default Config Backup Repository`. O caminho para a pasta na qual os backups do Veeam são armazenados é `<Drive>:\ConfigBackup\`.
* Para ampliação, um repositório denominado `IC4V Scale-Out Repository`. Para obter mais informações, consulte [Incluindo um repositório de ampliação](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo).
* Para backups da Máquina virtual (VM): um repositório denominado ``IC4V Default VM Backup Repository``. O caminho para a pasta na qual os backups da VM são armazenados é ``<Drive>:\VMBackup\`. Esse repositório é incluído como uma extensão em ``IC4V Scale-Out repository`.

### Rede
{: #veeam_considerations-specs-networking}

Um endereço IP privado primário.

### Licenças e taxas
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5 (10, 25, 50, 100 ou 200 licenças da VM)

## Considerações ao instalar o Veeam on IBM Cloud
{: #veeam_considerations-install}

O repositório de armazenamento e o servidor Veeam estão no pod original e no data center. Portanto, o desempenho das operações de backup para clusters remotos pode se deteriorar.

## Considerações ao remover o Veeam on IBM Cloud
{: #veeam_considerations-remove}

A remoção do serviço Veeam on {{site.data.keyword.cloud_notm}} para todos os backups e exclui todos os backups anteriores. O backup das VMs de gerenciamento para e a exclusão de backups anteriores é irreversível. Se as MVs de gerenciamento estiverem corrompidas, elas não poderão ser restauradas.

## Links relacionados
{: #veeam_considerations-related}

* [Pedindo o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Solicitando serviços gerenciados para o Veeam no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Website do Veeam](https://www.veeam.com/){:new_window}
* [Centro de Ajuda do Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
