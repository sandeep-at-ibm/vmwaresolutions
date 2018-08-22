---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust CloudControl on IBM Cloud Visão Geral

O serviço HyTrust CloudControl on {{site.data.keyword.cloud}} cumpre e controla a conformidade com relação a padrões de segurança e fornece os recursos detalhados de controle de acesso baseado na função (RBAC), aprovação e auditoria. Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilidade:** esse serviço está disponível somente para instâncias
que estão executando o vSphere 6.5 e que são implementadas na (ou atualizadas para) a V2.3 ou liberações mais recentes.

## Especificações técnicas para o HyTrust CloudControl on IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust CloudControl

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: VMDK de 70 GB residente no vSAN em cluster convergido
* Rede: colocada na rede móvel privada suportada por VLAN especificada para gerenciamento

### Alta disponibilidade

Dois dispositivos CloudControl são implementados em uma configuração ativa/passiva.

### Licenças e taxas

Licença por host: uma licença do HyTrust CloudControl é pedida para cada host no ambiente.

## Considerações ao remover o HyTrust CloudControl on IBM Cloud

Antes de remover o serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, certifique-se de
desativar a **Transferência de senha raiz**, se configurada, e de excluir todos os hosts protegidos do
HyTrust CloudControl.

### Links relacionados

* [Solicitando HyTrust CloudControl no {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gerenciando o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
