---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Solicitando F5 no IBM Cloud

É possível pedir o serviço F5 on {{site.data.keyword.cloud}} ao pedir uma nova instância com o BIG-IP Virtual Edition (VE) incluído ou incluindo o BIG-IP VE em sua instância existente.

## Pedindo o F5 on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o F5 on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **F5 on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **F5 on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o F5 on IBM Cloud para uma instância existente

É possível incluir o serviço F5 on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **F5 on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir na instância existente**.

## F5 na configuração do serviço IBM Cloud

Quando você pedir o serviço, forneça as configurações a seguir.

### Nome

Insira o nome do serviço.

### Modelo de licença

O modelo de licença para o F5 no serviço {{site.data.keyword.cloud_notm}} oferece as seguintes opções:
<dl class="dl">
        <dt class="dt dlterm">Bom</dt>
        <dd class="dd">Essa oferta alavanca o BIG-IP Local Traffic Manager™ (LTM) VE, operando como uma arquitetura de proxy integral, para fornecer gerenciamento inteligente de tráfego local, visibilidade completa de tráfego SSL e analítica e monitoramento de funcionamento para assegurar que os servidores de aplicativos estejam sempre disponíveis aos seus usuários.</dd>
        <dt class="dt dlterm">Melhor</dt>
        <dd class="dd">Essa oferta é construída sobre os benefícios da opção **Bom**, com a adição de módulos do BIG-IP DNS™, do BIG-IP Advanced Firewall Manager™ (AFM) e do BIG-IP Application Acceleration Manager™ (AAM). Ela fornece serviços de gerenciamento de tráfego global, otimização de desempenho do aplicativo e recursos avançados de mitigação de firewall de rede e Distributed Denial of Service (DDoS).</dd>
        <dt class="dt dlterm">Melhor</dt>
        <dd class="dd">Além das ofertas **Bom** e **Melhor**, o BIG-IP Application Security Manager™ (ASM) fornece proteção abrangente de aplicativo com relação às 10 principais ameaças e vulnerabilidades comuns de aplicativos do L7 DDoS, Open Web Application Security Project (OWASP). O BIG-IP Access Policy Manager™ (APM) oferece aos usuários um acesso seguro e simplificado a aplicativos localizados em qualquer lugar dentro de um ambiente de várias nuvens, incorporando recursos como SSO (Conexão Única) e MFA (Autenticação de Diversos Fatores).</dd>
</dl>

**Importante:** não é possível mudar o modelo de licença após a instalação do serviço. Para mudar o modelo de licença, deve-se remover o serviço existente e reinstalá-lo usando um modelo de licença diferente.

### Máximo de largura da banda

Especifique o rendimento máximo do dispositivo F5 BIG-IP.

### Links relacionados

* [F5 no {{site.data.keyword.cloud_notm}} visão geral](f5_considerations.html)
* [Gerenciando o F5 no {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Guias de Implementação do F5](https://f5.com/solutions/deployment-guides){:new_window}
