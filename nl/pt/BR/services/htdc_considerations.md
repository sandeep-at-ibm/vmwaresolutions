---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HyTrust DataControl, HTDC, tech specs HTDC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud Visão Geral
{: #htdc_considerations}

O serviço HyTrust DataControl on {{site.data.keyword.cloud}} oferece criptografia avançada com o gerenciamento de chave integrado para assegurar as cargas de trabalho em todo o seu ciclo de vida. O serviço fornece criptografia no nível do sistema operacional e no nível de dados. Isso permite que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho seja criptografado e decriptografado.

Esse serviço está disponível somente para instâncias que estão executando o vSphere 6.5 e são implementadas ou submetidas a upgrade para a V2.3 ou mais recente. A versão atual instalada do HyTrust DataControl é 4.3.2.
{:note}

## Especificações técnicas para o HyTrust DataControl on IBM Cloud
{: #htdc_considerations-specs}

Os componentes a seguir são pedidos e incluídos no serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust DataControl
{: #htdc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: VMDK de 20 GB residente no vSAN em cluster convergido
* Rede: colocada na rede móvel privada suportada por VLAN especificada para gerenciamento

### Alta disponibilidade
{: #htdc_considerations-ha
}
Dois dispositivos DataControl são implementados em uma configuração ativa-ativa.

### Licenças e taxas
{: #htdc_considerations-licenses}

Licença por host: uma licença do HyTrust DataControl é pedida para cada host no ambiente.

## Considerações ao remover o HyTrust DataControl on IBM Cloud
{: #htdc_considerations-remove}

Antes de remover o serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}, desacople todos os clientes do uso do DataControl. Depois de remover o serviço, as chaves poderão ser excluídas e você poderá ser bloqueado de suas MVs.

## Links relacionados
{: #htdc_considerations-related}

* [Solicitando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Gerenciando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Website](https://www.hytrust.com/){:external}
