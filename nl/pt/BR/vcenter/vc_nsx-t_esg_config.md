---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configurando sua rede para usar o NSX-T ESG gerenciado pelo cliente com suas VMs
{: #vc_nsx-t_esg_config}

Configure a rede para suas máquinas virtuais para que você possa tirar proveito do VMware NSX-T Edge Services Gateway (ESG) que é implementado em suas instâncias do VMware vCenter Server. Para obter mais informações sobre as medidas de segurança em vigor para ajudar a minimizar o risco de segurança, consulte [Os serviços de gerenciamento do NSX Edge representam um risco de segurança?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

O VMware NSX-T é uma plataforma de virtualização de rede que permite a virtualização de redes isoladas e fornece vários serviços de rede, tais como comutadores, roteamento e firewalls. Para obter mais informações sobre NSX, veja [Visão geral de NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Como parte do processo de pedido para a sua instância do vCenter Server com NSX-T, as ações a seguir são concluídas em seu nome:
* Uma sub-rede privada do cliente é pedida para que seja usada por suas MVs (máquinas virtuais) para acessar a rede privada de infraestrutura do {{site.data.keyword.cloud}}.
* Uma sub-rede pública do cliente é pedida para permitir que suas MVs acessem a Internet.
* O NSX-T é implementado e configurado em sua instância do vCenter Server com NSX-T.
* Um comutador lógico do NSX-T de amostra é implementado para ser usado pelas VMs de carga de trabalho do cliente.
* Um roteador da Camada 1 do NSX-T de amostra é implementado para a potencial comunicação leste-oeste entre as cargas de trabalho locais que estão conectadas às redes da camada 2 (L2).
* Um dispositivo de borda do NSX-T é implementado e configurado para executar a conversão de endereço de rede (NAT) desde o intervalo de endereços IP do
comutador lógico de carga de trabalho até um endereço IP público nas regras NAT.

  A borda do NSX-T não é implementada para instâncias que são apenas privadas.
  {:note}

## Procedimento para configurar as definições de rede para suas MVs
{: #vc_nsx-t_esg_config-procedure-config-networking}

Para aproveitar o NSX-T para suas VMs de carga de trabalho, deve-se definir diversas configurações concluindo as etapas a seguir ao criar suas VMs:

1. Configure o adaptador de rede da MV para o comutador lógico de carga de trabalho:
   1. Na caixa de diálogo **Nova Máquina Virtual**, clique na guia **Customizar Hardware**.
   2. No menu **novo dispositivo**, selecione **Rede** e clique em **Incluir**.
   3. No adaptador de rede recém-incluído, selecione o comutador lógico de sobreposição da carga de trabalho no menu. O nome de exemplo do comutador é **overlay-ls**.

   Assegure-se de não selecionar o comutador **Trânsito de carga de trabalho**.
   {:important}

2. Identifique um endereço IP disponível para a MV:
   *  O endereço IP deve estar no intervalo de `192.168.10.0/24`. Observe que o endereço IP `192.168.10.1` é reservado (veja a **Etapa 3**).
   *  Quando configurar a rede do sistema operacional que é executado na MV, use o endereço IP selecionado e a máscara de rede
   `255.255.255.0`.

   Você é responsável por gerenciar o intervalo de endereços IP para os quais designou suas MVs.
   {:note}

3. Designe o gateway padrão da MV como `192.168.10.1`. Esse é o endereço IP da porta do roteador de downlink no roteador lógico da Camada 1 do cliente e está conectado ao mesmo comutador lógico de sobreposição que as VMs de carga de trabalho.

## Ativando a regra SNAT
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

O NSX-T ativa a regra do SNAT por padrão. Para obter informações sobre a modificação das regras existentes, consulte [Configurar a NAT de origem e de destino em um roteador lógico da camada 0](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}.

## Procedimento para identificar detalhes de sub-redes do cliente
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

Os roteadores lógicos **Customer-T1-LR** e **Customer-T0-LR**, bem como as bordas **cust-nsx-edge0** e **cust-nsx-edge1** são destinados para o seu próprio uso, para que seja possível modificá-lo para definir mais regras de NAT para tráfego de entrada ou de saída. Essas regras devem usar apenas os endereços IP nas sub-redes públicas ou privadas do cliente que são ordenadas em seu nome.

Para identificar os detalhes para as sub-redes do cliente para que seja possível usar os endereços IP pedidos, conclua as etapas a seguir no NSX-T Web Client:

1. Clique na guia **Rede avançada e segurança**.
2. Na área de janela esquerda, clique em **Malha** e, em seguida, na lista suspensa, selecione **Nós**.
3. Na guia, selecione **Nós de transporte de borda**.
4. Clique em uma das bordas do cliente. Por exemplo, **cust-nsx-edge0**. As sub-redes de cliente públicas e privadas são exibidas no campo **Descrição**.

Além disso, é possível localizar mais detalhes sobre as sub-redes do cliente concluindo as etapas a seguir no {{site.data.keyword.slportal}}:

1. Clique em **Rede > Gerenciamento de IP > Subnets**.
2. Clique no menu de filtro e no campo **Sub-rede** insira o identificador conforme visto na descrição de **customer-nsx-edge0** no NSX-T Web Client.
3. Revise as notas que são mostradas para os endereços IP. Essas notas identificam quais das sub-redes e endereços IP são ordenados e usados durante a configuração inicial.

   Não use os endereços IP que são pedidos e usados durante a configuração inicial. No entanto, é possível usar outros endereços IP nessas
   sub-redes de acordo com os seus requisitos. Para configurar regras adicionais de conversão de endereço de rede, veja [Gerenciando regras NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Links relacionados
{: #vc_nsx-t_esg_config-related}

* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Gateway de Serviços de Edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
