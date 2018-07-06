---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust DataControl on IBM Cloud Visão Geral

O serviço HyTrust DataControl on {{site.data.keyword.cloud}} oferece criptografia avançada com o gerenciamento de chave integrado para assegurar as cargas de trabalho em todo o seu ciclo de vida. O serviço pode fornecer criptografia no nível do sistema operacional e no nível de dados, o que significa que qualquer diretório, pasta ou arquivo dentro de uma carga de trabalho pode ser criptografado e decriptografado.

**Disponibilidade:** esse serviço está disponível somente para instâncias
que estão executando o vSphere 6.5 e que são implementadas na (ou atualizadas para) a V2.3 ou liberações mais recentes.

## Componentes do HyTrust DataControl on IBM Cloud

Um par altamente disponível (HA) de dispositivos HyTrust DataControl (HTDC) é implementado no cluster padrão no modo ativo-ativo. Os dispositivos HTDC são licenciados para fornecer a funcionalidade HyTrust KeyControl para suas cargas de trabalho.

Cada par de dispositivos HTDC é implementado na mesma sub-rede móvel que é especificada para as máquinas virtuais (VMs) de gerenciamento, como o NSX Manager, vCenter Server Appliances e Platform Services Controller. Os dispositivos são roteados por meio de backend customer routers (BCRs) do {{site.data.keyword.cloud_notm}} e são designados ao gateway que está associado à sub-rede de VMs de gerenciamento. Além disso, os dispositivos são colocados no armazenamento padrão do cluster padrão.

## Considerações ao remover o HyTrust DataControl on IBM Cloud

Antes de remover o serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}, assegure-se de que tenha criptografado ou feito backup de todos os discos do DataControl. Depois de remover o serviço, as chaves podem ser excluídas e você pode ser bloqueado de suas VMs.

## Links relacionados

* [Solicitando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gerenciando HyTrust DataControl no {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
