---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-19"

---

# Configurando sua rede para usar o NSX ESG gerenciado pelo cliente com suas VMs

Configure a rede para suas máquinas virtuais para que você possa aproveitar o VMware NSX Edge Services Gateway (ESG) que é implementado em suas instâncias do VMware vCenter Server. Para obter mais informações sobre as medidas de segurança em vigor para ajudar a minimizar o risco de segurança, consulte [Os serviços de gerenciamento do NSX Edge representam um risco de segurança?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX é uma plataforma de virtualização de rede que permite a virtualização de redes isoladas e fornece vários serviços de rede,
como comutadores, roteamento e firewalls. Para obter mais informações sobre NSX, veja [Visão geral de NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Como parte do processo de pedido para sua instância do vCenter Server, as ações a seguir são concluídas em seu nome:
* Uma sub-rede privada do cliente é pedida para que seja usada por suas VMs (máquinas virtuais) para acessar a rede privada de infraestrutura do {{site.data.keyword.cloud}}.
* Uma sub-rede pública do cliente é pedida para permitir que suas VMs acessem a Internet.
* NSX é implementado e configurado em sua instância do vCenter Server.
* Um Comutador Lógico NSX de amostra é implementado para ser usado pelas VMs de carga de trabalho do cliente.
* Um Roteador Lógico Distribuído (DLR) NSX de amostra é implementado para possível comunicação leste-oeste entre as cargas de trabalho locais que estão conectadas a redes de camada 2 (L2).
* Um dispositivo NSX Edge é implementado e configurado para executar a conversão de endereço de rede (NAT) do intervalo de endereços IP do
comutador lógico de carga de trabalho até um endereço IP público nas regras NAT.
* Se você instalou o serviço Veeam on {{site.data.keyword.cloud_notm}}, o NSX Manager será configurado para fazer um backup diário das configurações do NSX. Para obter mais informações, veja [Considerações ao instalar o Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html#considerations-when-installing-veeam-on-ibm-cloud).


## Definindo as configurações de rede para suas VMs

Para aproveitar o NSX para suas VMs de carga de trabalho, deve-se definir várias configurações concluindo as etapas a seguir quando você cria suas VMs:

1. Configure o adaptador de rede da VM para o comutador lógico de carga de trabalho:
   1. Na caixa de diálogo **Nova Máquina Virtual**, clique na guia **Customizar Hardware**.
   2. No menu **novo dispositivo**, selecione **Rede** e clique em **Incluir**.
   3. No adaptador de rede recém-incluído, selecione o comutador lógico de carga de trabalho no menu. Um nome de exemplo do comutador lógico de carga de trabalho
   é **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   **Importante:** assegure-se de não selecionar o comutador **Workload Transit**.

2. Identifique um endereço IP disponível para a VM:
   *  O endereço IP deve estar no intervalo de `192.168.10.0/24`. Observe que o endereço IP `192.168.10.1` é reservado (veja a **Etapa 3**).
   *  Quando configurar a rede do sistema operacional que é executado na VM, use o endereço IP selecionado e a máscara de rede
   `255.255.255.0`.

   **Nota:** você é responsável por gerenciar o intervalo de endereços IP para os quais designou suas VMs.

3. Designe o gateway padrão da VM como `192.168.10.1`. Este é o endereço IP do NSX DLR no mesmo comutador lógico das VMs de carga de trabalho.

## Ativando a regra SNAT

Se você quiser que suas VMs de carga de trabalho tenham acesso de saída para a Internet, deverá ativar a regra SNAT (Source Network Address Translation) associada. Ativar a regra SNAT permite que o acesso à Internet de suas VMs seja convertido em um único endereço IP público. Conclua as seguintes etapas no VMware vSphere Web Client:

1. Clique em **Início > Rede e segurança**.
2. Na área de janela do navegador, clique em **NSX Edges** e dê um clique duplo no limite denominado **customer-nsx-edge**.
3. Clique em **Gerenciamento > NAT** para abrir a guia **NAT**.
4. Selecione a regra SNAT padrão na tabela e clique na marca de seleção verde acima da tabela para ativar a regra.

Para obter mais informações sobre as regras NAT do NSX Edge, veja [Gerenciando regras NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Identificando detalhes de sub-redes do cliente

O limite **customer-nsx-edge** destina-se ao seu próprio uso, então, você pode modificá-lo para definir mais regras NAT para o tráfego de entrada ou de saída. Essas regras devem usar apenas os endereços IP nas sub-redes públicas ou privadas do cliente que são ordenadas em seu nome.

Para identificar os detalhes para as sub-redes do cliente para que seja possível usar os endereços IP pedidos, conclua as etapas a seguir no VMware vSphere Web Client:

1. Clique em **Início > Rede e segurança**.
2. Na área de janela do navegador, clique em **NSX Edges** e dê um clique duplo em **customer-nsx-edge edge**.
3. Na guia **Resumo** para esse limite, revise a descrição do limite, que contém os identificadores de sub-rede para as sub-redes privadas e públicas do cliente.

Além disso, é possível localizar mais detalhes sobre as sub-redes do cliente concluindo as etapas a seguir no {{site.data.keyword.slportal}}:

1. Clique em **Rede > Gerenciamento de IP > Subnets**.
2. Clique no menu de filtro e, no campo Sub-rede, insira o identificador como visto na descrição do limite **customer-nsx-edge** na guia **Resumo** no VMware vSphere Web Client.
3. Revise as notas que são mostradas para os endereços IP. Essas notas identificam quais das sub-redes e endereços IP são ordenados e usados durante a configuração inicial.

   **Aviso:** não use os endereços IP que são ordenados e usados durante a configuração inicial. No entanto, é possível usar outros endereços IP nessas
   sub-redes de acordo com os seus requisitos. Para configurar regras adicionais de conversão de endereço de rede, veja [Gerenciando regras NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

### Links relacionados

* [Resolução de problemas](../vcenter/vcenter_chg_impact.html)
* [Perguntas Mais Frequentes](../vmonic/faq.html)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
