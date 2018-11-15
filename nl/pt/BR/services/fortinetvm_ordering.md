---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo o FortiGate Virtual Appliance on IBM Cloud

É possível pedir o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud}} ao pedir uma nova instância com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o FortiGate Virtual Appliance on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **FortiGate Virtual Appliance on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **FortiGate Virtual Appliance on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o FortiGate Virtual Appliance on IBM Cloud para uma instância existente

É possível incluir o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **FortiGate Virtual Appliance on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir na instância existente**.

## Configuração do serviço FortiGate Virtual Appliance on IBM Cloud

Quando você pedir o serviço, forneça as configurações a seguir.

### Conexão de Rede FortiGuard

Selecione **Rede pública** ou **Rede privada** para o FortiGuard. Se o cluster de destino for configurado com interfaces de rede somente privadas, apenas a opção **Rede privada** estará disponível. Essa seleção determina como o FortiGuard contatará o servidor de licença do Fortinet para ativar a licença e para fazer download das correções de segurança e isso não afetará o plano de dados de carga de trabalho.

Se você selecionar **Rede privada**, especifique as configurações a seguir:
* **Endereço IP do proxy**: o endereço IPv4 do servidor.
* **Número da porta do proxy**: o número da porta do servidor proxy, geralmente 8080 ou 3128.
* **Nome do usuário do proxy**: se a autenticação de proxy for requerida, insira o nome do usuário do servidor proxy.
* **Senha de proxy**: se a autenticação de proxy for requerida, insira a senha do servidor proxy.

### Nome

Insira o nome do serviço.

### Tamanho de implementação

O {{site.data.keyword.cloud_notm}}  fornece as seguintes opções de tamanho de implementação:
* Pequeno (2 vCPUs / 4 GB de RAM)
* Médio (4 vCPUs / 6 GB de RAM)
* Grande (8 vCPU/12 GB de RAM)

### Modelo de licença

O modelo de licença para o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}} oferece as seguintes opções:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Esse pacote configurável inclui Inspeção de Pacote Stateful, Proteção de VLAN e Criação de Log Avançado, Regras de Firewall de Ingresso e Egresso, Finalização de VPN SSL/IPSec e suporte 24 x 7.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Esse pacote configurável inclui todos os serviços de firewall padrão além do serviço Advanced Malware Protection (AMP) (incluindo Antivírus, Serviço de IP/Domínio do Botnet, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service e Content Disarm e Reconstruct), assim como os serviços de Filtragem da Web, IPS, Antispam, Controle do Aplicativo e FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Esse pacote configurável inclui todos os serviços de firewall padrão e UTM, além dos serviços a seguir:<ul><li>Cloud Access Security Broker (CASB): esse serviço fornece visibilidade, conformidade, segurança de dados e proteção de ameaça para serviços baseados em nuvem.</li><li>Segurança Industrial: esse serviço fornece assinaturas para protocolos ICS/SCADA comuns.</li><li>Classificação de segurança: esse serviço fornece recursos de auditoria para identificar vulnerabilidades críticas e pontos fracos de configuração e implementar recomendações de melhor prática.</li></ul></dd>
</dl>

No 3º trimestre de 2018, o Fortinet incluiu três novos serviços (CASB, Segurança Industrial e Classificação de Segurança) em seu pacote configurável Enterprise. Esses serviços estão disponíveis somente no FortiGate 6.0.
{:note}

Não é possível mudar o modelo de licença após a instalação do serviço. Para mudar o modelo de licença, deve-se remover o serviço existente e reinstalar o serviço selecionando uma opção de licença diferente.
{:important}

### Links relacionados

* [FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}} visão geral](fortinetvm_considerations.html)
* [Gerenciando o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Website do Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos do Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
