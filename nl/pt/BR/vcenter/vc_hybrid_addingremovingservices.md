---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle

É possível pedir serviços para a sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, como uma solução de recuperação de desastre. Quando você não precisar mais desses serviços, será possível removê-los de sua instância.

## Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

Os serviços a seguir estão disponíveis para instâncias do vCenter Server with Hybridity Bundle.

Tabela 1. Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

| Nome do Serviço | Disponibilidade | Suporte da instância |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud_notm}}](../services/f5_considerations.html)                                 | Sim | V1.9 e mais recentes |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html)       | Sim | V1.8 e mais recentes |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | Sim | V2.0 e mais recentes |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | Sim | V2.3 e mais recentes |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | Sim | V2.3 e mais recentes |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)         | Sim | V2.2 e mais recentes |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  | Sim | V2.2 e mais recentes |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                           | Sim | V1.8 e mais recentes |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)                        | Sim | V2.3 e mais recentes |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                  | Sim | V1.2 e mais recentes |

## Incluindo serviços em instâncias do vCenter Server with Hybridity Bundle

Para aplicar um serviço à sua instância do vCenter Server with Hybridity Bundle, clique nos links na tabela para revisar as considerações para o serviço, verifique os componentes que estão implementados e siga as instruções nos tópicos de pedido para colocar sua ordem.

### Resultados da instalação de serviço

Quando a instalação do serviço for concluída com êxito, você será notificado por e-mail e o serviço será exibido na guia **Serviços** dos detalhes da instância com o status **Instalado**.

## Visualizando serviços para instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja visualizar serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, clique em um serviço para revisar informações sobre ele, como o status de serviço e outros detalhes.
5. Dependendo do serviço visualizado, é possível acessar os consoles de serviço usando as credenciais fornecidas nos detalhes do serviço e é possível gerenciar o serviço daqui.

## Removendo serviços para instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja remover serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, localize a instância de serviço que você deseja remover e clique no ícone **Excluir**.
5. Na janela **Excluir serviços**, revise as considerações ou os avisos, se houver algum. Selecione **Eu entendo** e clique em **Excluir**.

### Resultados da remoção de serviço

Depois que sua solicitação para remoção do serviço for aceita, o status do serviço mudará para **Removendo**.

Quando a remoção do serviço for concluída com êxito, você será notificado por e-mail e o serviço será removido da página **Serviços** da instância.

**Atenção**: você será cobrado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} pelos serviços removidos.

### Links relacionados

* [Perguntas mais frequentes](../vmonic/faq.html)
