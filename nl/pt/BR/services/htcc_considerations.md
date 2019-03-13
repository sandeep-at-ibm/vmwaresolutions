---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud Visão Geral
{: #htcc_considerations}

O serviço HyTrust CloudControl on {{site.data.keyword.cloud}} cumpre e controla a conformidade com relação a padrões de segurança que incluem controle de acesso baseado na função (RBAC), aprovação e auditoria. Quando o serviço é combinado com o HyTrust DataControl, o serviço assegura que as máquinas virtuais e os dados de carga de trabalho não saiam de uma determinada região, cluster ou servidor ESXi dentro do {{site.data.keyword.CloudDataCent_notm}}.

Esse serviço está disponível somente para instâncias que estão executando o vSphere 6.5 e que são implementadas ou submetidas a upgrade para a V2.3 ou mais recente. A versão atual do HyTrust CloudControl que está instalada é 5.4.0.
{:note}

## Especificações técnicas para o HyTrust CloudControl on IBM Cloud
{: #technical-specifications-for-hytrust-cloudcontrol-on-ibm-cloud}

Os componentes a seguir são pedidos e incluídos no serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust CloudControl
{: #htcc_considerations-appliance}

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: VMDK de 70 GB residente no vSAN em cluster convergido
* Rede: colocada na rede móvel privada suportada por VLAN especificada para gerenciamento

### Alta disponibilidade
{: #htcc_considerations-ha}

Dois dispositivos CloudControl são implementados em uma configuração ativa/passiva.

### Licenças e taxas
{: #htcc_considerations-licenses}

Licença por host: uma licença do HyTrust CloudControl é pedida para cada host no ambiente.

## Considerações ao remover o HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-remove}

Antes de remover o serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, certifique-se de
desativar a **Transferência de senha raiz**, se configurada, e de excluir todos os hosts protegidos do
HyTrust CloudControl.

## Links relacionados
{: #htcc_considerations-related}

* [Solicitando HyTrust CloudControl no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Gerenciando o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Website](https://www.hytrust.com/)
