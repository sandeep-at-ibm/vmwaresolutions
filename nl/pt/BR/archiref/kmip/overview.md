---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do KMIP for VMware
{: #kmip-overview}

Essa arquitetura de solução descreve a arquitetura do KMIP on VMware para proteger suas instâncias do VMware on {{site.data.keyword.cloud_notm}}. Muitas opções de criptografia de armazenamento estão disponíveis para proteger a carga de trabalho do VMware. O KMIP for VMware funciona junto com a criptografia vSphere nativa do VMware e a criptografia vSAN para fornecer gerenciamento de criptografia de armazenamento simplificado juntamente com a segurança e a flexibilidade de chaves gerenciadas pelo cliente do {{site.data.keyword.cloud_notm}} Key Protect ou {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services.

Essa solução é considerada como um componente extra e a extensão da oferta do vCenter Server no {{site.data.keyword.cloud_notm}}. Como resultado, esse documento não abrange a configuração existente dessas soluções de base no {{site.data.keyword.cloud_notm}}. Para entender mais sobre a arquitetura da solução de base, consulte a nossa [Arquitetura da solução VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Principais benefícios
{: #kmip-overview-benefits}

Embora muitas soluções de criptografia de armazenamento estejam disponíveis para sua carga de trabalho do VMware, o KMIP for VMware oferece os benefícios a seguir:

* Integração com a criptografia do VMware vSAN e a criptografia do vSphere, ambas implementadas na camada do hypervisor em vez da camada de armazenamento ou da máquina virtual. Essa abordagem permite fácil gerenciamento e transparência para sua solução de armazenamento e aplicativo.
* Servidor de gerenciamento de chave totalmente gerenciado disponível em muitas regiões multizona (MZRs) do {{site.data.keyword.cloud_notm}}.
* A integração de seu cluster VMware com o {{site.data.keyword.cloud_notm}} Key Protect ou {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services fornece a você chaves totalmente gerenciadas pelo cliente que podem ser revogadas a qualquer momento.

## Links relacionados
{: #kmip-overview-related}

* [Design de solução](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [ Implementação e gerenciamento ](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
