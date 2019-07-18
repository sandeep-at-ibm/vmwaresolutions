---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: VMware HCX deployment, HCX configuration, order HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitando VMware HCX on IBM Cloud
{: #hcx_ordering}

É possível pedir o serviço VMware HCX on {{site.data.keyword.cloud}} ao pedir uma nova instância do VMware vCenter Server with Hybridity Bundle com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o VMware HCX on IBM Cloud para uma nova instância
{: #hcx_ordering-new}

Para pedir uma nova instância do VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle com o VMware HCX on {{site.data.keyword.cloud_notm}}, selecione **VMware HCX on IBM Cloud** na seção **Serviços** ao pedir a instância por meio do console do {{site.data.keyword.vmwaresolutions_short}}.


## Pedindo o VMware HCX on IBM Cloud para uma instância existente
{: #hcx_ordering-existing}

Para incluir o serviço VMware HCX on {{site.data.keyword.cloud_notm}} em uma instância existente do VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.

## VMware HCX na configuração do IBM Cloud
{: #hcx_ordering-config}

Para instalar o HCX on {{site.data.keyword.cloud_notm}}, conclua as configurações a seguir:
1. Especifique o **Tipo de interconexão do HCX** selecionando uma das opções a seguir:
  * **Rede pública:** o HCX cria uma conexão criptografada entre sites por meio da rede pública. O registro de licença e a medição são realizados por meio da rede pública.
  * **Interconexão privada:** o HCX cria uma conexão criptografada entre sites por meio da rede privada. O registro de licença e a medição são realizados por meio da rede pública.
  * **Rede privada:** o HCX cria uma conexão criptografada entre sites por meio da rede privada. O registro e a medição da licença são executados na rede privada por meio de proxy HTTP.
3. Se você selecionar **Rede privada**, conclua os seguintes campos:
  * **Endereço de proxy:** o endereço IPv4 do servidor proxy.
  * ** Porta de proxy: **  a porta do servidor proxy. O número da porta é geralmente 8080 ou 3128.
  * **Nome do usuário:** o nome do usuário se a autenticação de proxy for necessária.
  * **Senha:** a senha se a autenticação de proxy for necessária.
  * **Inserir novamente a senha:** insira novamente a senha para a validação de autenticação de proxy.
2. Especifique o **Tipo de certificado de terminal**. Se selecionar **Certificado de autoridade de certificação**, configure as definições a seguir:
  * **Conteúdos do certificado:** insira o conteúdo do certificado de autoridade de certificação.
  * **Chave privada:** insira a chave privada do certificado de autoridade de certificação.
  * (Opcional) **Senha:** insira a senha para a chave privada se ela estiver criptografada.
  * (Opcional) **Inserir a senha novamente:** insira a senha para a chave privada novamente.
  * (Opcional) **Nome do host:** o nome do host a ser mapeado para o nome comum (CN) do certificado de autoridade de certificação. O HCX on {{site.data.keyword.cloud_notm}} requer que o formato do certificado de CA seja aceito pelo NSX Edge. Para obter mais informações sobre os formatos de certificados do NSX Edge, veja [Importando SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Processo de implementação para HCX no IBM Cloud
{: #hcx_ordering-deploy}

A implementação do HCX no {{site.data.keyword.cloud_notm}} é automatizada. Quer você peça uma instância do vCenter Server with Hybridity Bundle com o serviço incluído, quer implemente o serviço posteriormente em sua instância, as etapas a seguir são concluídas pelo processo de automação do {{site.data.keyword.vmwaresolutions_short}}:
1. Três sub-redes são pedidas para o HCX por meio da infraestrutura do {{site.data.keyword.cloud_notm}}:
   * Uma sub-rede móvel privada para gerenciamento do HCX.
   * Uma sub-rede portátil privada para interconexões HCX. Essa sub-rede é usada quando a opção **Rede privada** é selecionada para o **Tipo de interconexão HCX**.
   * Uma sub-rede portátil pública para ativação e manutenção com o VMware. Se a opção **Rede pública** estiver selecionada para o **Tipo de interconexão HCX**, essa sub-rede também será usada para interconexões HCX.

   Os endereços IP nas sub-redes que são pedidos para o HCX são destinados a serem gerenciados pela automação do VMware on {{site.data.keyword.cloud_notm}}. Esses endereços IP não podem ser designados a recursos do VMware, como MVs e NSX Edges, que são criados por você. Se você precisar de endereços IP adicionais para seus artefatos do VMware, deverá pedir suas próprias sub-redes do {{site.data.keyword.cloud_notm}}.
   {:important}
2. Se a **Rede privada** foi selecionada para o **Tipo de interconexão do HCX**, um grupo de portas denominado **SDDC-DPortGroup-HCX-Private** será criado no Distributed Virtual Switch (DVS) privado.
3. Uma chave de ativação do HCX é pedida por meio do VMware.
4. Três conjuntos de recursos e pastas da MV para o HCX são criados, os quais são necessários para as interconexões do
HCX, os componentes do HCX local e os componentes do HCX remoto.
5. Um par de VMware NSX Edge Services Gateways (ESGs) para o tráfego de gerenciamento do HCX é implementado e configurado:
   * As interfaces de uplink públicas e privadas são configuradas usando as sub-redes pedidas.
   * Os ESGs são configurados como um par de dispositivos de borda extragrandes com a Alta Disponibilidade (HA) ativada.
   * As regras de firewall e as regras de conversão de endereço de rede (NAT) são configuradas para permitir o tráfego HTTPS de entrada e de saída para/do HCX Manager.
   * As regras do balanceador de carga e os conjuntos de recursos são configurados. Essas regras e conjuntos de recursos são usados para encaminhar o tráfego de entrada relacionado ao HCX para os dispositivos virtuais apropriados do HCX Manager e do vCenter Server (com o Platform Services Controller integrado).
   * Um certificado SSL para criptografar o tráfego HTTPS de entrada relacionado ao HCX que está chegando por meio de ESGs é aplicado.

   A borda de gerenciamento do HCX é dedicada ao tráfego de gerenciamento do HCX entre os componentes do HCX no local e os componentes do HCX do lado da nuvem. Não modifique o limite de gerenciamento do HCX ou use-o para extensões de rede do HCX. Em vez disso, crie limites separados para extensões de rede. Além disso, usar um firewall ou desativar as comunicações de borda de gerenciamento do HCX para os componentes de gerenciamento privados da IBM ou para a Internet pública pode impactar negativamente a funcionalidade do HCX.
   {:important}

6. O HCX Manager on {{site.data.keyword.cloud_notm}} é implementado, ativado e configurado:
   * O HCX Manager é registrado com o vCenter Server.
   * O HCX Manager, o vCenter Server (com o Platform Services Controller integrado) e o NSX Manager estão configurados.
   * A frota do HCX está configurado.
   * Os contêineres de implementação do HCX locais e remotos são configurados.
7. O nome do host e o endereço IP do HCX Manager está registrado com o servidor DNS do VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Links relacionados
{: #hcx_ordering-related}

* [HCX no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Gerenciando o HCX no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Glossário de termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Documentação do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
