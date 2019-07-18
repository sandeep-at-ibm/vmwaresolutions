---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do Zerto on IBM Cloud
{: #addingzertodr}

O serviço Zerto on {{site.data.keyword.cloud}} integra os recursos de replicação e de recuperação de desastre às ofertas de implementação para proteger e recuperar dados no ambiente virtual do VMware no {{site.data.keyword.cloud_notm}}.

## Antes de iniciar
{: #addingzertodr-req}

* Assegure-se de que sua conta do {{site.data.keyword.cloud_notm}} seja uma conta faturável e que esteja vinculada à conta de infraestrutura do {{site.data.keyword.cloud_notm}} em que sua instância está implementada. Para obter mais informações, consulte [Faturamento para replicação do Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).
* Esse serviço está disponível somente para instâncias que são implementadas na V1.2 ou mais recente. A versão atual do Zerto que está instalada é 6.5 atualização 3.

## Especificações técnicas para Zerto on IBM Cloud
{: #addingzertodr-specs}

Os componentes a seguir são pedidos e incluídos no serviço Zerto on {{site.data.keyword.cloud_notm}}.

Os componentes do Zerto Virtual Replication Appliance (VRA) são implementados apenas no cluster padrão.
{:note}

### Virtual Service Instances
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

* VSI
  * Um endereço IP privado primário
  * Uplink de rede privada de 1 Gbps
* Dispositivos de replicação virtual (VRAs)
  * Uma sub-rede móvel privada para implementação do VRA

### Licenças e taxas
{: #addingzertodr-specs-licenses}

Licença do Zerto Replication V6.5 atualização 3

## Links relacionados
{: #addingzertodr-related}

* [Solicitando on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gerenciando o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Serviços gerenciados para o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Website zerto.com](https://www.zerto.com){: external}
* [Documentação técnica do Zerto](https://www.zerto.com/myzerto/technical-documentation/){: external}
