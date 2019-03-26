---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud Visão Geral
{: #addingzertodr}

O serviço Zerto on {{site.data.keyword.cloud}} integra os recursos de replicação e de recuperação de desastre às ofertas de implementação para proteger e recuperar dados no ambiente virtual do VMware no {{site.data.keyword.cloud_notm}}.

Esse serviço está disponível somente para instâncias que são implementadas na V1.2 ou mais recente. A versão atual do Zerto que está instalada é a 6.5, Atualização 3.
{:note}

## Especificações técnicas para Zerto on IBM Cloud
{: #addingzertodr-specs}

Os componentes a seguir são pedidos e incluídos no serviço Zerto on {{site.data.keyword.cloud_notm}}.

Os componentes do Zerto Virtual Replication Appliance (VRA) são implementados apenas no cluster padrão.
{:note}

### VSIs
{: #addingzertodr-specs-vsi}

* Uma Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 núcleos x 2,0 GHz
* RAM de 4 GB
* Windows Server 2016 Standard Edition (64 bits)

### Armazenamento
{: #addingzertodr-specs-storage}

100 GB (SAN) de disco

### Rede
{: #addingzertodr-specs-network}

* Um endereço IP privado primário
* Uplink de rede privada de 1 Gbps

### Licenças e taxas
{: #addingzertodr-specs-licenses}

Zerto Replication V6.5 atualização 3 licença

## Links relacionados
{: #addingzertodr-related}

* [Sobre o {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-prod_overview)
* [Solicitando on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gerenciando o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Solicitando serviços gerenciados para o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Website zerto.com](https://www.zerto.com){:new_window}
* [Documentação técnica do Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
