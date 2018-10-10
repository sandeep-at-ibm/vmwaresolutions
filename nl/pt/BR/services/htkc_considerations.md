---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-11"

---

# Visão geral do HyTrust KeyControl on IBM Cloud

O serviço HyTrust KeyControl on {{site.data.keyword.cloud}} simplifica o gerenciamento de cargas de trabalho criptografadas automatizando e simplificando o ciclo de vida de chaves de criptografia, incluindo o armazenamento de chave, a distribuição de chave, a rotação de chave e a revogação de chave. Usando a criptografia compatível com FIPS 140-2, as empresas podem gerenciar facilmente as chaves de criptografia na escala. 

**Disponibilidade:** esse serviço está disponível somente para instâncias que estão executando o vSphere 6.5 e que são implementadas (ou submetidas a upgrade) na V2.5 e liberações mais recentes.

## Especificações técnicas para o HyTrust KeyControl on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust KeyControl

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: VMDK de 20 GB residente no vSAN em cluster convergido
* Rede: colocada na rede móvel privada suportada por VLAN especificada para gerenciamento

### Alta disponibilidade

Por padrão, dois dispositivos KeyControl são implementados em uma configuração em cluster ativa/ativa.

Opcionalmente, é possível especificar para implementar dois dispositivos KeyControl em uma configuração independente não em cluster.

### Licenças e taxas

É pedida uma licença do HyTrust KeyControl para cada instalação da instância.

## Considerações ao remover o HyTrust KeyControl on IBM Cloud

Antes de remover o serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, assegure-se de que tenha desacoplado todos os clientes do uso do KeyControl. Depois de remover o serviço, as chaves podem ser excluídas e você pode ser bloqueado de suas VMs.

### Links relacionados

* [Pedindo o HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](htkc_ordering.html)
* [Gerenciando o HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](managinghtkc.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
