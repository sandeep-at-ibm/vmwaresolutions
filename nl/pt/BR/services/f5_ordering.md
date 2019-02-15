---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitando F5 no IBM Cloud

É possível pedir o serviço F5 on {{site.data.keyword.cloud}} ao pedir uma nova instância com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o F5 on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o F5 on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **F5 on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **F5 on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o F5 on IBM Cloud para uma instância existente

É possível incluir o serviço F5 on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **F5 on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em instância existente**.

## F5 na configuração do serviço IBM Cloud

Quando você pedir o serviço, forneça as configurações a seguir.

### Conexão de Ativação de Licença F5

Selecione **Rede pública** ou **Rede privada** para ativação de licença. Se o cluster de destino for configurado com interfaces de rede somente privadas, apenas a opção **Rede privada** estará disponível. Essa seleção determina como os servidores virtuais F5 contatarão o servidor de licença F5 e isso não afeta o plano de dados de carga de trabalho.

Se você selecionar **Rede privada**, especifique as configurações a seguir:
* **Endereço IP do proxy**: o endereço IPv4 do servidor.
* **Número da porta do proxy**: o número da porta do servidor proxy, geralmente 8080 ou 3128.

O proxy autenticado não é suportado.
{:note}

### Nome

Insira o nome do serviço.

### Máximo de largura da banda

Especifique o rendimento máximo do dispositivo F5 BIG-IP.

### Modelo de licença

O modelo de licença para o F5 no serviço {{site.data.keyword.cloud_notm}} oferece as seguintes opções:
<dl class="dl">
        <dt class="dt dlterm">Bom</dt>
        <dd class="dd">Essa oferta usa o BIG-IP Local Traffic Manager™ (LTM) VE, operando como uma arquitetura de proxy integral, para fornecer gerenciamento de tráfego local inteligente, visibilidade completa de tráfego SSL e analítica e monitoramento de funcionamento para assegurar que os servidores de aplicativos estejam sempre disponíveis aos seus usuários.</dd>
        <dt class="dt dlterm">Melhor</dt>
        <dd class="dd">Essa oferta é construída sobre os benefícios da opção **Bom**, com a adição de módulos do BIG-IP DNS™, do BIG-IP Advanced Firewall Manager™ (AFM) e do BIG-IP Application Acceleration Manager™ (AAM). Ela fornece serviços de gerenciamento de tráfego global, otimização de desempenho do aplicativo e recursos avançados de mitigação de firewall de rede e Distributed Denial of Service (DDoS).</dd>
        <dt class="dt dlterm">Melhor</dt>
        <dd class="dd">Além das ofertas **Bom** e **Melhor**, o BIG-IP Application Security Manager™ (ASM) fornece proteção de aplicativo abrangente com relação a L7 DDoS, as 10 principais ameaças do Open Web Application Security Project (OWASP) e as vulnerabilidades comuns de aplicativo. O BIG-IP Access Policy Manager™ (APM) oferece aos usuários um acesso seguro e simplificado a aplicativos localizados em qualquer lugar dentro de um ambiente de várias nuvens, incorporando recursos como SSO (Conexão Única) e MFA (Autenticação de Diversos Fatores).</dd>
</dl>

Não é possível mudar o modelo de licença após a instalação do serviço. Para mudar o modelo de licença, deve-se remover o serviço existente e reinstalar o serviço escolhendo um modelo de licença diferente.
{:important}

### Links relacionados

* [F5 no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services/f5_considerations.html)
* [Gerenciando o F5 no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managing_f5.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_addingremovingservices.html)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Guias de Implementação do F5](https://f5.com/solutions/deployment-guides){:new_window}
