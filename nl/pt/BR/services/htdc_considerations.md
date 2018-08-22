---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust DataControl on IBM Cloud Visão Geral

O serviço HyTrust DataControl on {{site.data.keyword.cloud}} oferece criptografia avançada com o gerenciamento de chave integrado para assegurar as cargas de trabalho em todo o seu ciclo de vida. O serviço pode fornecer criptografia no nível do sistema operacional e no nível de dados, o que significa que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho pode ser criptografado e decriptografado.

**Disponibilidade:** esse serviço está disponível somente para instâncias
que estão executando o vSphere 6.5 e que são implementadas na (ou atualizadas para) a V2.3 ou liberações mais recentes.

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

Antes de remover o serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}, assegure-se de que tenha criptografado ou feito backup de todos os discos do DataControl. Depois de remover o serviço, as chaves podem ser excluídas e você pode ser bloqueado de suas VMs.

### Links relacionados

* [Solicitando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gerenciando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
