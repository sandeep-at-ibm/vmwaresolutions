---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations}

O serviço Caveonix RiskForesight on {{site.data.keyword.cloud}} pode ajudar a gerenciar o risco cibernético e de conformidade com monitoramento proativo e controles de defesa automatizados para proteger contra ameaças e atender às regulamentações da indústria ou do governo.

Esse serviço está disponível apenas para as instâncias do VMware vCenter Server on {{site.data.keyword.cloud_notm}} que são implementadas na V2.9 e nas liberações mais recentes.
{:note}

## Especificações técnicas para o Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-specs}

Os componentes a seguir são pedidos e incluídos no serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}.

### Recursos do vCenter
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* Disco: 80 GB

### Rede
{: #caveonix_considerations-tech-specs-network}

Uma sub-rede privada dedicada com 64 endereços IP é pedida.

### Licenças e taxas
{: #caveonix_considerations-tech-specs-license-fee}

Uma chave de licença do Caveonix RiskForesight é pedida para cada instância do serviço.

## Considerações ao instalar o Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-install}

Antes de instalar o serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, assegure-se de que a CPU e a memória no cluster padrão de sua instância de serviço sejam suficientes para a máquina virtual do Caveonix RiskForesight.

## Considerações ao remover o Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-remove}

Revise as considerações a seguir antes de remover o serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}:
* A remoção do serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} não cancela a licença do Caveonix RiskForesight. Deve-se excluir a licença do Caveonix RiskForesight por meio da tabela **Licenças do Caveonix RiskForesight** na página **Recursos** no console do {{site.data.keyword.vmwaresolutions_short}}.
* Ao remover o serviço, a automação do {{site.data.keyword.vmwaresolutions_short}} exclui apenas a única VM do Caveonix "tudo em um" que foi implementada e a sub-rede privada dedicada que foi pedida para ele. Portanto,
   * Se você escalou a VM do Caveonix em múltiplas VMs, essas VMs adicionais não serão removidas.
   * Se você usou os endereços IP da sub-rede privada dedicada em VMs adicionais, essas VMs deverão ser designadas a novos endereços IP para continuarem a funcionar.
   * Se você excluir a instância A do servidor do vCenter com o serviço do Caveonix RiskForesight no {{site.data.keyword.cloud_notm}} instalado e você usou os endereços IP da sub-rede privada dedicada pedida para o serviço na instância B do servidor do vCenter, a sub-rede privada dedicada será cancelada na exclusão da instância A do servidor vCenter.

## Links relacionados
{: #caveonix_considerations-related}

* [ Pedindo o Caveonix RiskForesight no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [ Gerenciando o Caveonix RiskForesight no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
