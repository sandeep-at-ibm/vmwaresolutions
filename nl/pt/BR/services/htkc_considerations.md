---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do HyTrust KeyControl on IBM Cloud
{: #hytrust-keycontrol-on-ibm-cloud-overview}

O serviço HyTrust KeyControl on {{site.data.keyword.cloud}} simplifica o gerenciamento de cargas de trabalho criptografadas. Esse serviço automatiza e simplifica o ciclo de vida de chaves de criptografia, inclui o armazenamento de chave, a distribuição de chave, a rotação de chave e a revogação de chave. Usando a criptografia compatível com FIPS 140-2, as empresas podem gerenciar facilmente as chaves de criptografia na escala.

Esse serviço está disponível somente para instâncias que estão executando o vSphere 6.5 e que são implementadas ou submetidas a upgrade para a V2.5 e mais recente. A versão atual do HyTrust KeyControl que está instalada é 4.2.
{:note}

## Especificações técnicas para o HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-specs}

Os componentes a seguir são pedidos e incluídos no serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust KeyControl
{: #htkc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: VMDK de 20 GB residente no vSAN em cluster convergido
* Rede: colocada na rede móvel privada suportada por VLAN especificada para gerenciamento

### Alta disponibilidade
{: #htkc_considerations-ha}

Por padrão, dois dispositivos KeyControl são implementados em uma configuração em cluster ativa/ativa.

Opcionalmente, é possível especificar para implementar dois dispositivos KeyControl em uma configuração independente não em cluster.

### Licenças e taxas
{: #htkc_considerations-licenses}

É pedida uma licença do HyTrust KeyControl para cada instalação da instância.

## Considerações ao remover o HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-remove}

Antes de remover o serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, assegure-se de que tenha desacoplado todos os clientes do uso do KeyControl. Depois de remover o serviço, as chaves poderão ser excluídas e você poderá ser bloqueado de suas MVs.

## Links relacionados
{: #htkc_considerations-related}

* [Pedindo o HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [Gerenciando o HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Website](https://www.hytrust.com/)
