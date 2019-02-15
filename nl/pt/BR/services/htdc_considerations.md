---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud Visão Geral

O serviço HyTrust DataControl on {{site.data.keyword.cloud}} oferece criptografia avançada com o gerenciamento de chave integrado para assegurar as cargas de trabalho em todo o seu ciclo de vida. O serviço fornece criptografia no nível do sistema operacional e no nível de dados. Isso permite que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho seja criptografado e decriptografado.

Esse serviço está disponível somente para instâncias que estão executando o vSphere 6.5 e são implementadas ou submetidas a upgrade para a V2.3 ou mais recente. A versão atual do HyTrust DataControl que está instalada é 4.2.1.
{:note}

## Especificações técnicas para o HyTrust DataControl on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust DataControl
* CPU: 2 vCPU
* RAM: 8 GB
* Disco: VMDK de 20 GB residente no vSAN em cluster convergido
* Rede: colocada na rede móvel privada suportada por VLAN especificada para gerenciamento

### Alta disponibilidade
Dois dispositivos DataControl são implementados em uma configuração ativa/ativa.

### Licenças e taxas

Licença por host: uma licença do HyTrust DataControl é pedida para cada host no ambiente.

## Considerações ao remover o HyTrust DataControl on IBM Cloud

Antes de remover o serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}, desacople todos os clientes do uso do DataControl. Depois de remover o serviço, as chaves poderão ser excluídas e você poderá ser bloqueado de suas MVs.

### Links relacionados

* [Solicitando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_ordering.html)
* [Gerenciando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managinghtdc.html)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
