---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando o HyTrust CloudControl on IBM Cloud
{: #managinghtcc}

Para gerenciar o serviço HyTrust CloudControl on {{site.data.keyword.cloud}} (HTCC), acesse a WebGUI do HTCC por meio do console do {{site.data.keyword.vmwaresolutions_short}} ou acesse o console do HTCC por meio do vSphere Web Client.

## Acessando a WebGUI do HyTrust CloudControl por meio do console do IBM Cloud for VMware Solutions
{: #managinghtcc-accessing-webgui}

Para efetuar login na WebGUI do dispositivo HTCC primário ou secundário, use as credenciais da WebGUI localizadas na página de detalhes do serviço
HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

## Acessando o console do HyTrust CloudControl por meio do vSphere Web Client
{: #managinghtcc-accessing-console}

Para acessar o console do HTCC por meio do vSphere Web Client, use o procedimento a seguir:
1. No vSphere Web Client, localize as máquinas virtuais denominadas **CC1** e **CC2**.
2. Clique com o botão direito em **CC1** ou **CC2** e depois clique em **Abrir console**.
3. Efetue login no console usando as credenciais do console que podem ser localizadas na página de detalhes do serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Ativando o acesso à Internet para as VMs do HyTrust CloudControl
{: #managinghtcc-internet-access}

Para o HTCC 5.5.1 e mais recente, o {{site.data.keyword.vmwaresolutions_short}} fornece suporte de renovação automática para licenças do HyTrust que tenham o recurso Call Home ativado. Para instâncias do vCenter Server que não são somente privadas, o HTCC é implementado com as regras de firewall e SNAT (Conversão de endereço de rede de origem) definidas nos serviços de gerenciamento ESG **mgmt-nsx-edge**.

Essas regras permitem ativar o acesso à Internet para as máquinas virtuais (VMs) do HyTrust. Se o acesso à Internet não estiver ativado, a licença aplicada à sua instalação do HTCC expirará depois de um ano.

Para ambientes do vCenter Server somente privado, o VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** não é incluído; portanto, as regras de firewall e SNAT não estão definidas. Como resultado, a conectividade da Internet não pode ser ativada para instâncias somente privadas e as licenças do HyTrust expiram anualmente.
{:note}

### Procedimento para localizar as regras de firewall e SNAT definidas
{: #managinghtcc-proc-find-firewall}

1. Efetue login no VMware vSphere Web Client (FLEX) e localize o ESG **mgmt-nsx-edge**.
2. Clique em **Página inicial > Rede & Segurança > Bordas NSX**.
3. Clique duas vezes no ESG **mgmt-nsx-edge** e clique na guia **Gerenciar**.
4. Acesse a guia **Firewall** e localize as regras do HyTrust. Anote os endereços IP de origem. Estes são os endereços IP para as VMs do HyTrust.
5. Acesse a guia **NAT** e localize as regras SNAT criadas para as VMs do HyTrust. Os endereços IP de origem corresponderão aos endereços IP que você anotou na etapa anterior.

### Procedimento para ativar a conectividade à Internet para o HTCC
{: #managinghtcc-enable-internet}

Estas etapas a seguir se aplicam para atualizar as configurações de rede do HTCC na máquina virtual (VM) primária, que é usada para os upgrades de licença. Não é necessário atualizar as configurações para a VM secundária.
{:note}

1. Conclua as etapas de 1 a 3 no procedimento anterior.
2. Clique em **Configurações** e, em seguida, clique em **Interfaces**. Anote o endereço IP do uplink privado, que se torna o novo gateway padrão. 
3. Acesse a página de detalhes do serviço HyTrust CloudControl on IBM Cloud, clique em **Visualizar IU da web do HTCC** e efetue login com as credenciais por meio da página de detalhes do serviço.
4. Observe o gateway padrão existente. Por exemplo, para o HTCC 5.5.1, clique em **Configuração > Rede**. Observe o endereço IP do gateway listado, que se torna o gateway para a rota estática.
5. Inclua uma rota estática. Por exemplo, para o HTCC 5.5.1, clique em **Configuração > Rotas estáticas**. Clique em **Incluir**, insira as informações a seguir e clique em **OK**.

  ```
  Network Address: 10.0.0.0
  Mask: 255.0.0.0
  Gateway: IP noted in step 4
  Device: Network 1
  ```

6. Mude o gateway padrão. Por exemplo, para o HTCC 5.5.1, clique em **Configuração > Rede** e substitua o endereço IP no campo **Gateway** por aquele anotado na Etapa 3 e clique em **Salvar**. 

  Assegure-se de configurar a rota estática antes de mudar o gateway padrão, caso contrário, o console da web poderá se tornar inacessível.
  {:important}

  A VM primária agora terá acesso à Internet.

7. Para confirmar que a VM primária tem acesso à Internet, execute um comando `ping` em um endereço IP ou um website público. Para isso, volte para o vCenter e clique com o botão direito em **CC1 > Abrir console**. Efetue login no console usando as credenciais do console por meio da página de detalhes do serviço HyTrust CloudControl on IBM Cloud. Execute um comando `ping`, como `ping www.ibm.com`, e você deverá obter uma resposta imediata. Pressione `Ctrl + C` para finalizar o ping e assegure-se de que a perda do pacote seja de 0%.

## Links relacionados
{: #managinghtcc-related}

* [HyTrust CloudControl no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Website](https://www.hytrust.com/)
