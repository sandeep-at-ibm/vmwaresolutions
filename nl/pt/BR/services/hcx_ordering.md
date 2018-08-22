---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Solicitando VMware HCX on IBM Cloud

É possível pedir o serviço VMware HCX on {{site.data.keyword.cloud}} ao pedir uma nova instância do VMware vCenter Server with Hybridity Bundle com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o VMware HCX on IBM Cloud para uma nova instância

Para pedir uma nova instância do VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle com o VMware HCX on {{site.data.keyword.cloud_notm}}, selecione **VMware HCX on IBM Cloud** na seção **Serviços** ao pedir a instância por meio do console do {{site.data.keyword.vmwaresolutions_short}}.


## Pedindo o VMware HCX on IBM Cloud para uma instância existente

Para incluir o serviço VMware HCX on {{site.data.keyword.cloud_notm}} em uma instância existente do VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.

## VMware HCX na configuração do IBM Cloud

Para instalar o HCX on {{site.data.keyword.cloud_notm}}, conclua as configurações a seguir:
1. Especifique o **Tipo de interconexão do HCX** selecionando uma das opções a seguir:
  * **Rede pública**: o HCX cria uma conexão criptografada entre sites na rede pública.
  * **Rede privada**: o HCX cria uma conexão criptografada entre sites na rede privada.
2. Especifique o **Tipo de certificado de terminal**. Se selecionar **Certificado de autoridade de certificação**, configure as definições a seguir:
  * **Conteúdo do certificado**: insira o conteúdo do certificado de autoridade de certificação.
  * **Chave privada**: insira a chave privada do certificado de autoridade de certificação.
  * (Opcional) **Senha**: insira a senha para a chave privada se ela estiver criptografada.
  * (Opcional) **Inserir a senha novamente**: insira a senha para a chave privada novamente.
  * (Opcional) **Nome do host**: o nome do host a ser mapeado para o nome comum (CN) do certificado de CA. O HCX on {{site.data.keyword.cloud_notm}} requer que o formato do certificado de CA seja aceito pelo NSX Edge. Para obter mais informações sobre os formatos de certificados do NSX Edge, veja [Importando SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Processo de implementação para HCX no IBM Cloud

A implementação do HCX no {{site.data.keyword.cloud_notm}} é automatizada. Quer você peça uma instância do vCenter Server with Hybridity Bundle com o serviço incluído, quer implemente o serviço posteriormente em sua instância, as etapas a seguir são concluídas pelo processo de automação do {{site.data.keyword.vmwaresolutions_short}}:
1. Três sub-redes são pedidas para o HCX por meio da infraestrutura do {{site.data.keyword.cloud_notm}}:
   * Uma sub-rede móvel privada para gerenciamento do HCX.
   * Uma sub-rede móvel privada para interconexões do HCX se **Rede privada** é selecionado para **Tipo de interconexão do HCX**.
   * Uma sub-rede móvel pública para interconexões do HCX se **Rede pública** é selecionado para **Tipo de interconexão do HCX**. Essa sub-rede também é usada para ativação e manutenção com o VMware.

   **Importante:** os endereços IP nas sub-redes ordenados para HCX devem ser gerenciados pelo VMware na automação do {{site.data.keyword.cloud_notm}}. Esses endereços IP não podem ser designados a recursos do VMware, como VMs e NSX Edges, que são criados por você. Se você precisar de endereços IP adicionais para seus artefatos do VMware, deverá pedir suas próprias sub-redes do {{site.data.keyword.cloud_notm}}.
2. Se a **Rede privada** foi selecionada para o **Tipo de interconexão HCX**, um
grupo da porta denominado **SDDC-DPortGroup-HCX-Private** é criado no comutador virtual distribuído (DVS) privado.
3. Uma chave de ativação do HCX é pedida por meio do VMware.
4. Três conjuntos de recursos e pastas da VM para o HCX são criados, os quais são necessários para as interconexões do
HCX, os componentes do HCX local e os componentes do HCX remoto.
5. Um par de VMware NSX Edge Services Gateways (ESGs) para o tráfego de gerenciamento do HCX é implementado e configurado:
   * As interfaces de uplink públicas e privadas são configuradas usando as sub-redes pedidas.
   * Os ESGs são configurados como um par de dispositivos de borda extragrandes com a Alta Disponibilidade (HA) ativada.
   * As regras de firewall e as regras de conversão de endereço de rede (NAT) são configuradas para permitir o tráfego HTTPS de entrada e de saída para/do HCX Manager.
   * As regras do balanceador de carga e os conjuntos de recursos são configurados. Essas regras são conjuntos de recursos usados para encaminhar o tráfego de entrada relacionado ao HCX para os dispositivos virtuais apropriados do HCX Manager, vCenter Server e Platform Services Controller (PSC).
   * Um certificado SSL para criptografar o tráfego HTTPS de entrada relacionado ao HCX que passa pelos ESGs é aplicado.

   **Importante**: o limite de gerenciamento do HCX é dedicado ao tráfego de gerenciamento do HCX entre os componentes do HCX no local e os componentes do HCX na nuvem. Não modifique o limite de gerenciamento do HCX ou use-o para extensões de rede do HCX. Em vez disso, crie limites separados para extensões de rede. Além disso, observe que usar um firewall ou desativar as comunicações de limite de gerenciamento do HCX para os componentes de gerenciamento IBM privados ou Internet pública pode afetar negativamente a funcionalidade do HCX.

6. O HCX Manager on {{site.data.keyword.cloud_notm}} é implementado, ativado e configurado:
   * O HCX Manager é registrado com o vCenter Server.
   * O HCX Manager, vCenter Server, PSC e NSX Manager são configurados.
   * A frota do HCX está configurado.
   * Os contêineres de implementação do HCX locais e remotos são configurados.
7. O nome do host e o endereço IP do HCX Manager está registrado com o servidor DNS do VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

### Links relacionados

* [HCX no {{site.data.keyword.cloud_notm}} visão geral](hcx_considerations.html)
* [Gerenciando o HCX no {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Glossário de termos do HCX](hcx_glossary.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
