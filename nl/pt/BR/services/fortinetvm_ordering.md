---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

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
        <dd class="dd">Este pacote inclui Inspeção de Pacote Stateful, Proteção de VLAN e Criação de Log Avançada, Regras de Firewall de Entrada/Saída, Rescisão de VPN SSL/IPSec e suporte contínuo.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Esse pacote configurável inclui todos os serviços de firewall padrão, além de NGFW IPS e filtragem da web, antivírus e antispam, reputação de domínio e de IP e os principais serviços de segurança FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Esse pacote configurável inclui todos os serviços de firewall padrão e UTM além do FortiSandbox Cloud e do Mobile Security.</dd>
</dl>

**Importante**: não é possível mudar o modelo de licença após a instalação do serviço. Para mudar o modelo de licença, deve-se remover o serviço existente e reinstalar o serviço selecionando uma opção de licença diferente.

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
