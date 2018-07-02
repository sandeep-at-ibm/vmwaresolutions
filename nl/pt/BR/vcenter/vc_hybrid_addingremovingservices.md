---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle

É possível pedir serviços para a sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, como uma solução de recuperação de desastre. Quando você não precisar mais desses serviços, será possível removê-los de sua instância.

## Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

Os serviços a seguir estão disponíveis para instâncias do vCenter Server with Hybridity Bundle.

Tabela 1. Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

| Nome do Serviço                                                                           | Disponibilidade |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)                                 | Sim              |
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)       | Sim              |
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html) | Sim              |
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)              | Sim              |
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)              | Sim              |
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)         | Sim              |
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)                  | Sim              |
| [Veeam on IBM Cloud](../services/veeam_considerations.html)                           | Sim              |
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                         | Sim              |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                  | Sim              |


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

## Links relacionados

* [Perguntas mais frequentes](../vmonic/faq.html)
