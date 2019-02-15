---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle

É possível pedir serviços para a sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, como uma solução de recuperação de desastre. Quando você não precisar mais desses serviços, será possível removê-los de sua instância.

## Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

Os serviços a seguir estão disponíveis para instâncias do vCenter Server with Hybridity Bundle, juntamente com as versões de serviço instaladas.

Tabela 1. Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

| Nome do Serviço | Versão do serviço atual | Versão da instância |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_considerations.html)                                 | BIG-IP VE v13.1.1.2 | V1.9 e mais recentes |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fsa_considerations.html)       | Série 300 | V1.8 e mais recentes |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_considerations.html) | 6.0.3 | V2.0 e mais recentes |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html)              | 5.4.0 | V2.3 e mais recentes |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html)              | 4.2.1 | V2.3 e mais recentes |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html)              | 4.2 | V2.5 e mais recente |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services/icp_overview.html) | 3.1 | V2.7 e mais recente |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/spp_considerations.html)  | 10.1.2 | V2.2 e mais recentes |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)                  | 2.0  | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/veeam_considerations.html)                           | 9.5u3 | V1.8 e mais recentes |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/hcx_considerations.html)                        | 3.5.1 | V2.3 e mais recentes |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/addingzertodr.html)                                  | 6.0 atualização 3 | V1.2 e mais recentes |

## Procedimento para incluir serviços em instâncias do vCenter Server with Hybridity Bundle

Para aplicar um serviço à instância do vCenter Server with Hybridity Bundle, clique nos links da tabela para revisar as considerações do serviço. Em seguida, verifique os componentes implementados e siga as instruções nos tópicos de solicitação para fazer seu pedido.

### Resultados da instalação de serviço

Quando a instalação do serviço for concluída com êxito, você será notificado por e-mail e o serviço será exibido na guia **Serviços** dos detalhes da instância com o status **Instalado**.

## Procedimento para visualizar serviços para instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja visualizar serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, clique em um serviço para revisar informações sobre ele, como o status de serviço e outros detalhes.
5. Dependendo do serviço visualizado, é possível acessar os consoles de serviço usando as credenciais fornecidas nos detalhes do serviço e é possível gerenciar o serviço daqui.

## Procedimento para remover serviços para instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja remover serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, localize a instância de serviço que você deseja remover e clique no ícone **Excluir**.
5. Na janela **Excluir serviços**, revise as considerações ou os avisos, se houver algum. Selecione **Eu entendo** e clique em **Excluir**.

### Resultados da remoção de serviço

Depois que sua solicitação para remoção do serviço for aceita, o status do serviço mudará para **Removendo**.

Quando a remoção do serviço for concluída com êxito, você será notificado por e-mail e o serviço será removido da página **Serviços** da instância.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para os serviços removidos.
{:note}

### Links relacionados

* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic/faq.html)
