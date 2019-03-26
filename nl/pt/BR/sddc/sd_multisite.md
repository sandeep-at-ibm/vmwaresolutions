---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuração de vários sites para instâncias do Cloud Foundation
{: #sd_multisite}

O {{site.data.keyword.vmwaresolutions_full}} permite que as instâncias sejam implementadas em locais diferentes e fiquem funcionais em pouco tempo.

## Notas
{: #sd_multisite-notes}

* Não é possível vincular entre as instâncias do VMware Cloud Foundation e do VMware vCenter Server em uma configuração de vários sites.
* Não é possível vincular instâncias que são implementadas na V2.0 a instâncias de liberações anteriores (mesmo que elas tenham sido atualizadas para a V2.0).

## Componentes de implementação de vários sites
{: #sd_multisite-deployment-components}

Uma implementação de vários sites consiste nos componentes a seguir.

* **Instância primária**: a instância primária do VMware Cloud Foundation tem a seguinte configuração:
  *  Domínio-raiz do Microsoft Active Directory (AD) e DNS (Sistema de Nomes de Domínio)
  *  Subdomínio do Cloud Foundation
  *  Domínio SSO (Conexão Única)
  *  Nome do site SSO
* **Instância ou instâncias secundárias**: uma ou mais instâncias secundárias do Cloud Foundation, vinculadas à instância primária, com a seguinte configuração:
   *  Nome do site SSO
   *  Subdomínio do DNS que é vinculado ao domínio-raiz na instância primária
   *  A replicação do DNS e do AD é configurada entre as máquinas virtuais do AD nas instâncias primárias e secundárias
   *  PSC (Platform Services Controller) implementado e configurado para replicar com o PSC na instância primária
   *  O VMware vCenter nas instâncias secundárias é configurado com o Modo vinculado aprimorado para o vCenter na instância primária

## Implementação de vários sites do Cloud Foundation
{: #sd_multisite-deployment}

O recurso de configuração de vários sites usa uma topologia de hub e spoke com um site primário e um máximo de sete sites secundários. Uma única camada de sites é suportada, ou seja, não é possível configurar sites subsequentes vinculados a outros sites secundários. É possível ter um total de 128 servidores ESXi em uma configuração de vários sites em todas as instâncias.

Se a sua configuração requerer uma implementação de vários sites com mais de 128 servidores ESXi, entre em contato com o Suporte IBM para obter assistência. Para obter mais informações, veja [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).
{:note}

O gráfico a seguir descreve a visão geral da implementação de vários sites do Cloud Foundation.

Figura 1. Implementação de vários sites do Cloud Foundation

![Implementação multissite do Cloud Foundation](multisite-hub-spoke.svg "Implementação multissite do Cloud Foundation")

O modelo contém as camadas a seguir:

* **Instância primária**: em uma configuração de multisite, a primeira instância foi definida como primária durante o processo de pedido da instância.
* **Instâncias secundárias**: em uma configuração multisite, as instâncias que são anexadas à instância primária foram definidas como secundárias durante o processo de pedido.

É possível ter um máximo de 8 instâncias (1 primária e 7 secundárias) que serão implementadas em uma configuração de vários sites.

A exclusão de instâncias do Cloud Foundation que fazem parte de uma configuração multisite requer planejamento especial. Para obter mais informações, veja [Excluindo instâncias do Cloud Foundation em uma configuração de vários sites](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi).
{:note}

## Links relacionados
{: #sd_multisite-related}

* [Designar função principal ao NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [Configurando gerenciadores NSX secundários](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [Trusts do Active Directory suportados com Conexão única do VMware vCenter](https://kb.vmware.com/kb/2064250){:new_window}
* [Conectar com segurança suas cargas de trabalho privadas do VMware no {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}
