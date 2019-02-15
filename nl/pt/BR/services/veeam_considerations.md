---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud Visão Geral

O serviço Veeam no {{site.data.keyword.cloud}} se integra continuamente diretamente com os hypervisors do VMware para ajudar sua empresa a alcançar alta disponibilidade. Esse serviço fornece pontos de recuperação e objetivos de tempo para seus aplicativos e dados. Os pontos de recuperação e os objetivos de tempo podem ser fornecidos em menos de 15 minutos após a conclusão da configuração. Usando esse serviço, você controla o backup e a restauração de todas as máquinas virtuais (MVs) para sua infraestrutura diretamente do console do Veeam.

Esse serviço está disponível somente para instâncias que são implementadas na V1.8 ou mais recente. A versão atual do Veeam que está instalada é a 9.5u3.
{:note}

## Especificações técnicas para o Veeam on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço Veeam no {{site.data.keyword.cloud_notm}}:

### VSIs

* Única VSI com o complemento de S.O. do Veeam Backup and Replication 9.5
* Windows Server 2016 Standard Edition (64 bits)
* Cores de 4 x 2,0 GHz
* 8 GB de RAM
* Uplink de rede privada de 1 Gbps
* Disco de 100 GB (SAN)

### Armazenamento para backups

* Armazenamento de iSCSI do Endurance (2000, 4000, 8000 ou 12000 GB)
* Desempenho do armazenamento (0,25; 2 ou 4 IOPS/GB)

### Rede

Um endereço IP privado primário.

### Licenças e taxas

Veeam Backup and Replication 9.5 Enterprise Plus (10, 25, 50, 100 ou 200 licenças de MV).

### Gerenciamento

Backups de gerenciamento que são configurados por padrão com até 5 MVs e 2000 GB de armazenamento.

## Considerações ao instalar o Veeam on IBM Cloud

O repositório de armazenamento e o servidor Veeam estão no pod original e no data center. Portanto, o desempenho das operações de backup para clusters remotos pode se deteriorar.

## Considerações ao remover o Veeam on IBM Cloud

A remoção do serviço Veeam on {{site.data.keyword.cloud_notm}} para todos os backups e exclui todos os backups anteriores. Os backups das MVs de gerenciamento param e a exclusão de backups anteriores é irreversível. Se as MVs de gerenciamento estiverem corrompidas, elas não poderão ser restauradas.

### Links relacionados

* [Pedindo o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/veeam_ordering.html)
* [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingveeam.html)
* [Solicitando serviços gerenciados para o Veeam no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managing_veeam_services.html)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Website do Veeam](https://www.veeam.com/){:new_window}
* [Centro de Ajuda do Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
