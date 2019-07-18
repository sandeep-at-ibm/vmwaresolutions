---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HTDC WebGUI, HTDC console, enable internet HTDC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando HyTrust DataControl on IBM Cloud
{: #managinghtdc}

Para gerenciar o serviço HyTrust DataControl on {{site.data.keyword.cloud}} (HTDC), acesse a WebGUI por meio do console do {{site.data.keyword.vmwaresolutions_short}} ou acesse o console do HTDC por meio do vSphere Web Client.

## Acessando a WebGUI do HyTrust DataControl por meio do console do IBM Cloud for VMware Solutions
{: #managinghtdc-accessing-webgui}

Para efetuar login na WebGUI do dispositivo HTDC primário ou secundário, use as credenciais da WebGUI localizadas na página de detalhes do serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}.

## Acessando o console do HyTrust DataControl por meio do vSphere Web Client
{: #managinghtdc-accessing-console}

Para acessar o console do HTDC por meio do vSphere Web Client, use o procedimento a seguir:
1. No vSphere Web Client, localize as máquinas virtuais denominadas **KC1** e **KC2**.
2. Clique com o botão direito em **KC1** ou **KC2** e depois clique em **Abrir console**.
3. Efetue login no console usando as credenciais do console que podem ser localizadas na página de detalhes do serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Ativando o acesso à Internet para as VMs do HyTrust DataControl
{: #managinghtdc-internet-access}

Para o HTDC 4.3.2 e mais recente, o {{site.data.keyword.vmwaresolutions_short}} fornece suporte de renovação automática para licenças HyTrust que tenham o recurso Call Home ativado. Para instâncias do vCenter Server que não são somente privadas, o HTDC é implementado com as regras de firewall e SNAT (Conversão de endereço de rede de origem) definidas nos serviços de gerenciamento ESG **mgmt-nsx-edge**.

Essas regras permitem ativar o acesso à Internet para as máquinas virtuais (VMs) do HyTrust. Se o acesso à Internet não estiver ativado, a licença aplicada à sua instalação do HTDC expirará depois de um ano.

Para ambientes do vCenter Server somente privado, o VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** não é incluído; portanto, as regras de firewall e SNAT não estão definidas. Como resultado, a conectividade da Internet não pode ser ativada para instâncias somente privadas e as licenças do HyTrust expiram anualmente.
{:note}

### Procedimento para localizar as regras de firewall e SNAT definidas
{: #managinghtdc-proc-find-firewall}

1. Efetue login no VMware vSphere Web Client (FLEX) e localize o ESG **mgmt-nsx-edge**.
2. Clique em **Página inicial > Rede & Segurança > Bordas NSX**.
3. Clique duas vezes no ESG **mgmt-nsx-edge** e clique na guia **Gerenciar**.
4. Acesse a guia **Firewall** e localize as regras do HyTrust. Anote os endereços IP de origem. Estes são os endereços IP para as VMs do HyTrust.
5. Acesse a guia **NAT** e localize as regras SNAT criadas para as VMs do HyTrust. Os endereços IP de origem corresponderão aos endereços IP que você anotou na etapa anterior.

### Procedimento para ativar a conectividade à Internet para o HTDC
{: #managinghtdc-proc-enable-internet}

1. Conclua as etapas de 1 a 3 no procedimento anterior.
2. Clique em **Configurações** e, em seguida, em **Interfaces**. Anote o endereço IP para o uplink privado. Esse endereço se torna o novo gateway padrão.
3. Clique em **Página inicial > Hosts e Clusters** e localize as VMs do HyTrust. Clique com o botão direito do mouse em uma das VMs e clique em **Abrir console**.
4. Efetue login no console usando as credenciais do console que podem ser localizadas na página de detalhes do serviço HyTrust DataControl on IBM Cloud no console do {{site.data.keyword.vmwaresolutions_short}}.
5. Para obter o endereço IP do gateway padrão atual a partir da VM, clique em **Gerenciar configurações de rede > Mostrar configuração de rede atual**. Anote o endereço IP que está listado para **Gateway**. Esse endereço se torna o gateway usado para a rota estática.
6. Para configurar uma rota estática para a VM, clique em **Gerenciar configurações de rede > Gerenciar rotas estáticas > Incluir rota estática**. Configure **Endereço de rede** para `10.0.0.0/8` e **Gateway** para o endereço IP anotado na etapa anterior.
7. Para configurar o IP do gateway padrão para a VM, clique em **Gerenciar configurações de rede > Mudar a configuração de rede atual**. Se você receber uma mensagem de aviso, clique em **OK** e, em seguida, clique em **Configuração customizada**. Configure o campo **Gateway** para o endereço IP de uplink privado anotado na etapa 2 e clique em **OK**. Aguarde até que a nova configuração de rede esteja instalada e os serviços de rede sejam reiniciados.
8. Se você vir uma mensagem solicitando a reautenticação do HyTrust SecureOS, clique em **OK** e insira o endereço IP da outra VM do HyTrust para esta instalação. Se você for solicitado a informar uma passphrase de 16 caracteres, pressione Enter para retornar ao menu principal. Verifique a configuração de rede atual para assegurar-se de que suas mudanças sejam aplicadas.
9. Para confirmar que a VM tem acesso à Internet, execute ping em um endereço IP público ou website. Clique em **Gerenciar as configurações de rede > Ferramentas de diagnóstico de rede > Testar portas de entrada de outro servidor**. Digite o endereço de um website público, por exemplo, `www.ibm.com`, clique em **OK**, digite `80 443` para as portas (ou quaisquer outras portas que queira testar) e obtenha uma resposta imediata mostrando as portas de entrada com uma mensagem semelhante a `80 (OK) 443 (OK)`.
10. Repita as etapas de 3 a 9 para a outra VM do HyTrust.


## Links relacionados
{: #managinghtdc-related}

* [HyTrust DataControl no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Website](https://www.hytrust.com/){:external}
