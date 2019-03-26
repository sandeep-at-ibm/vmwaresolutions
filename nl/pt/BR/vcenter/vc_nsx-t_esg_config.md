---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

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
* Um roteador lógico distribuído (DLR) do NSX-T de amostra é implementado para uma potencial comunicação leste-oeste entre as cargas de trabalho locais que estão conectadas às redes da camada 2 (L2).
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
   3. No adaptador de rede recém-incluído, selecione o comutador lógico de carga de trabalho no menu. Um nome de exemplo do comutador lógico de carga de trabalho
   é **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   Assegure-se de não selecionar o comutador **Trânsito de carga de trabalho**.
   {:important}

2. Identifique um endereço IP disponível para a MV:
   *  O endereço IP deve estar no intervalo de `192.168.10.0/24`. Observe que o endereço IP `192.168.10.1` é reservado (veja a **Etapa 3**).
   *  Quando configurar a rede do sistema operacional que é executado na MV, use o endereço IP selecionado e a máscara de rede
   `255.255.255.0`.

   Você é responsável por gerenciar o intervalo de endereços IP para os quais designou suas MVs.
   {:note}

3. Designe o gateway padrão da MV como `192.168.10.1`. Este é o endereço IP do NSX DLR no mesmo comutador lógico das MVs de carga de trabalho.

## Procedimento para ativar a regra SNAT
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

Se você quiser que suas MVs de carga de trabalho tenham acesso de saída para a Internet, deverá ativar a regra SNAT (Source Network Address Translation) associada. Ativar a regra SNAT permite que o acesso à Internet de suas MVs seja convertido em um único endereço IP público. Conclua as seguintes etapas no VMware vSphere Web Client:

1. Clique em **Início > Rede e segurança**.
2. Na área de janela do navegador, clique em **NSX Edges** e dê um clique duplo no limite denominado **customer-nsx-edge**.
3. Clique em **Gerenciamento > NAT** para abrir a guia **NAT**.
4. Selecione a regra SNAT padrão na tabela e clique na marca de seleção verde acima da tabela para ativar a regra.

Para obter mais informações sobre as regras de NAT do NSX-T Edge, consulte [Gerenciando regras do NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Procedimento para identificar detalhes de sub-redes do cliente
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

O limite **customer-nsx-edge** destina-se ao seu próprio uso, então, você pode modificá-lo para definir mais regras NAT para o tráfego de entrada ou de saída. Essas regras devem usar apenas os endereços IP nas sub-redes públicas ou privadas do cliente que são ordenadas em seu nome.

Para identificar os detalhes para as sub-redes do cliente para que seja possível usar os endereços IP pedidos, conclua as etapas a seguir no VMware vSphere Web Client:

1. Clique em **Início > Rede e segurança**.
2. Na área de janela do navegador, clique em **Bordas do NSX** e localize **borda customer-nsx-edge** na lista de bordas na área de janela à direita.
3. Na coluna **Descrição**, passe o mouse sobre a descrição de borda para **customer-nsx-edge** para ver os identificadores de sub-rede para as sub-redes do cliente privadas e públicas.

Além disso, é possível localizar mais detalhes sobre as sub-redes do cliente concluindo as etapas a seguir no {{site.data.keyword.slportal}}:

1. Clique em **Rede > Gerenciamento de IP > Subnets**.
2. Clique no menu de filtro e, no campo Sub-rede, insira o identificador como visto na descrição do limite **customer-nsx-edge** na guia **Resumo** no VMware vSphere Web Client.
3. Revise as notas que são mostradas para os endereços IP. Essas notas identificam quais das sub-redes e endereços IP são ordenados e usados durante a configuração inicial.

   Não use os endereços IP que são pedidos e usados durante a configuração inicial. No entanto, é possível usar outros endereços IP nessas
   sub-redes de acordo com os seus requisitos. Para configurar regras adicionais de conversão de endereço de rede, veja [Gerenciando regras NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Links relacionados
{: #vc_nsx-t_esg_config-related}

* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Gateway de Serviços de Edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
