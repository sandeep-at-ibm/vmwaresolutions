---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate VA, FortiGate configuration, order FortiGate

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo o FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering}

É possível pedir o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud}} ao pedir uma nova instância com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o FortiGate Virtual Appliance on IBM Cloud para uma nova instância
{: #fortinetvm_ordering-new}

É possível pedir uma nova instância com o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **FortiGate Virtual Appliance on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** da área de janela de navegação esquerda e, em seguida, clique no cartão **FortiGate Virtual Appliance on IBM Cloud** da seção **Serviços do VMware**. Especifique as configurações do serviço e selecione **Incluir na nova instância**.

## Pedindo o FortiGate Virtual Appliance on IBM Cloud para uma instância existente
{: #fortinetvm_ordering-existing}

É possível incluir o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** da área de janela de navegação esquerda e, em seguida, clique no cartão **FortiGate Virtual Appliance on IBM Cloud** da seção **Serviços do VMware**. Especifique as configurações do serviço e selecione **Incluir na instância existente**.

## Pedindo o FortiGate Virtual Appliance on IBM Cloud para instâncias privadas
{: #fortinetvm_ordering-private}

Ao pedir o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} para instâncias não configuradas com interfaces públicas, deve-se fornecer um servidor proxy para concluir a instalação. O servidor proxy HTTP deve ser configurado e disponibilizado por meio do Virtual Routing and Forwarding (VRF) antes que a instalação do Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}} possa ser iniciada.

Para assegurar a operação continuada, o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} deve ter acesso persistente ao servidor de licença do Fortigate por meio da Internet.

## Configuração do serviço FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-config}

Quando você pedir o serviço, forneça as configurações a seguir.

### Conexão de Rede FortiGuard
{: #fortinetvm_ordering-config-network-connect}

Selecione **Rede pública** ou **Rede privada** para o FortiGuard. Se o cluster de destino for configurado com interfaces de rede somente privadas, apenas a opção **Rede privada** estará disponível. Essa seleção determina como o FortiGuard contatará o servidor de licença do Fortinet para ativar a licença e para fazer download de correções de segurança e isso não causará impacto no plano de dados de carga de trabalho.

Se você selecionar **Rede privada**, especifique as configurações a seguir:
* **Endereço IP do proxy**: o endereço IPv4 do servidor.
* **Número da porta do proxy**: o número da porta do servidor proxy, geralmente 8080 ou 3128.
* **Nome do usuário do proxy**: se a autenticação de proxy for requerida, insira o nome do usuário do servidor proxy.
* **Senha de proxy**: se a autenticação de proxy for requerida, insira a senha do servidor proxy.

### Nome
{: #fortinetvm_ordering-config-name}

Insira o nome do serviço.

### Tamanho de implementação
{: #fortinetvm_ordering-config-size}

O {{site.data.keyword.cloud_notm}}  fornece as seguintes opções de tamanho de implementação:
* Pequeno (2 vCPUs / 4 GB de RAM)
* Médio (4 vCPUs / 6 GB de RAM)
* Grande (8 vCPU/12 GB de RAM)

### Modelo de licença
{: #fortinetvm_ordering-config-license}

O modelo de licença para o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}} oferece as seguintes opções:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Esse pacote configurável inclui Inspeção de Pacote Stateful, Proteção de VLAN e Criação de Log Avançado, Regras de Firewall de Ingresso e Egresso, Finalização de VPN SSL/IPSec e suporte 24 x 7.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Esse pacote configurável inclui todos os serviços de firewall padrão, além do serviço Advanced Malware Protection (AMP). Ele inclui Antivírus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Service Protection Service e Content Disarm & Reconstruct. Ele também inclui os serviços Web Filtering, IPS, Antispam, Application Control e FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Esse pacote configurável inclui todos os serviços de firewall padrão e UTM, além dos serviços a seguir:<ul><li>Cloud Access Security Broker (CASB) - esse serviço fornece visibilidade, conformidade, segurança de dados e proteção de ameaça para serviços baseados em nuvem.</li><li>Segurança industrial - esse serviço fornece assinaturas para protocolos ICS/SCADA comuns.</li><li>Classificação de segurança - esse serviço fornece recursos de auditoria para identificar vulnerabilidades críticas e fraquezas de configuração e implementar recomendações de melhor prática.</li></ul></dd>
</dl>

No 3º trimestre de 2018, o Fortinet incluiu três novos serviços (CASB, Segurança Industrial e Classificação de Segurança) em seu pacote configurável Enterprise. Esses serviços estão disponíveis somente no FortiGate 6.0.
{:note}

Não é possível mudar o modelo de licença após a instalação do serviço. Para mudar o modelo de licença, deve-se remover o serviço existente e reinstalar o serviço selecionando uma opção de licença diferente.
{:important}

## Links relacionados
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [Gerenciando o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Website do Fortinet](https://www.fortinet.com/){:external}
* [Biblioteca de documentos do Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:external}
