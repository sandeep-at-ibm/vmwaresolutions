---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Implementação do cliente HCX
{: #hcxclient-vcs-client-deployment}

Uma instalação mínima do HCX consiste em uma única implementação de nuvem e do lado do cliente.

O lado do cliente
HCX pode ser instalado em qualquer versão do vSphere suportada pelo HCX, assumindo que
haja conectividade de rede entre os lados do cliente e da nuvem.

## Requisitos
{: #hcxclient-vcs-client-deployment-req}

| Componente | Contagem de CPU | Memória (GB) | Disco (GB) |
|--------|--------|---------|-------|
| Gerenciador de HCX | 4 | 12 G |  60 G |
| HCX Interconnect (HCX-IX) | 4 | 3G |  2G |
| HCX Network Extension (HCX-NE) | 4 | 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) | 8 | 14 G |  100 G |

## Licenciamento do cliente
{: #hcxclient-vcs-client-deployment-licensing}

HCX é um serviço. O HCX é licenciado por site e por máquina virtual (MV) gerenciada por meio de
servidores de licenciamento mantidos pelo VMware. A nuvem do HCX e as instâncias do lado do
cliente requerem comunicação com o site de registro do VMware
em todo o seu ciclo de vida.
- O tráfego na 80 e na 443 deve ser permitido para
`https://connect.hybridity.vmware.com`
- Uma chave de registro de uso único é fornecida pelo console do {{site.data.keyword.vmwaresolutions_full}} para a instalação do lado do cliente. É necessária uma chave para
cada instalação do HCX do lado do cliente.

### Procedimento para pedir licenças do HCX no local
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Role para a tabela **Licenças do HCX no local** e clique em **Provisionar nova**.
3. Especifique o nome da licença.
4. Clique no link ou nos links dos termos que se aplicam a seu pedido e assegure-se de que você concorda com esses termos antes de pedir a licença.
5. Clique em **Provisão**.

## Requisitos de endereço IP
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

Para implementar o HCX, o número adequado de endereços IP deve estar disponível no local e no
IBM Cloud de destino.

* Endereço do vMotion
  Manter uma rede separada para o vMotion é uma prática comum no data center no local. O Cloud Gateway deve ter acesso à rede vMotion. Se não tiver, um endereço IP extra será necessário para se comunicar com a rede vMotion.

* No local
  * Um endereço IP para o dispositivo HCX Manager.
  * Um para cada InterConnect Appliance, inclua um se houver uma rede vMotion separada.
  * Um para cada Network Extension padrão

* IBM Cloud
  * Dois endereços IP por dispositivo HCX Manager conectado ao IBM Cloud. Os endereços podem ser usados para se conectar à Internet ou a uma ou mais linhas do Direct Connect.
  * Inclua um se houver uma conexão de rede vMotion separada.

## Download do OVA do lado do cliente
{: #hcxclient-vcs-client-deployment-client-ova}

O HCX do lado do cliente é implementado pelo usuário e requer permissões de nível de administrador para o vCenter de origem. A partir dessa gravação, o ova do
gerenciador do lado do cliente do HCX tem aproximadamente 1,7 GB. Ao usar o console do {{site.data.keyword.vmwaresolutions_short}} para pedir
o HCX, é fornecida uma URL com
um link para fazer download da versão do HCX do lado do cliente que corresponde
à versão do HCX implementada no lado da nuvem. Esse link é fornecido na interface com o usuário (IU) do HCX Manager do lado da nuvem.

Uma chave de registro de uso descartável também é fornecida. Use as etapas a seguir para configurar o registro de uso.

1. Faça download do OVA do cliente HCX (corporativo) por meio do link fornecido na
IU do HCX do lado da nuvem.
    1. Efetue login na IU do HCX do lado da nuvem usando a IU de registro do HCX fornecida pela IBM.
    2. Use o ID e a senha do vCenter da nuvem para efetuar login na IU.
    3. Na guia **Administração**, selecione **solicitar link de download** para fazer download do OVA do lado do cliente. Use uma "caixa de salto", que é local para o vCenter de origem no qual o OVA é implementado, para concluir essa etapa.

## Instalando e configurando o HCX na origem
{: #hcxclient-vcs-client-deployment-install-cfg-src}

A instalação no local requer a implementação do dispositivo de gerenciamento HCX e seu registro com o ambiente do vCenter.

### Instalando o HCX Manager Appliance
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

Instale o dispositivo HCX Manager no vCenter no local.
1. Efetue login no **Meu VMware** e faça download do arquivo OVA do Hybrid Cloud Services na página de download do produto.
2. Abra um navegador e efetue login no vSphere Web Client. Visualize a guia  ** Página inicial ** .
3. Na lista **Árvores de inventários**, clique em **Host e clusters**.
4. Expanda a hierarquia para mostrar os data centers.
5. Clique com o botão direito no data center de destino e selecione **Implementar modelo OVF** no menu. Pode levar alguns segundos para que o item de menu **Implementar modelo OVF** apareça.
6. Escolha  ** Implementar modelo OVF **.
  1. Selecione **Arquivo local** e clique em **Procurar** para localizar o arquivo OVA transferido por download para o computador. Clique em **Avançar**.
  2. Na página **Revisar detalhes**, marque a caixa ** Aceitar opções de configuração extras** e clique em **Avançar**.
  3. Na página **Aceitar EULAs**, role para baixo para revisar o contrato de licença do usuário do VMware. Clique em  ** Aceitar **  e em  ** Avançar **.
  4. Na página **Selecionar nome e pasta**, edite o nome, se necessário, e selecione o local para o Hybrid Cloud Services. Clique em **Avançar**.
  5. Na página **Selecionar um recurso**, selecione o local de instalação.
  6. Na página **Selecionar armazenamento**, selecione o armazenamento para o Hybrid Cloud Services e clique em **Avançar**. Na lista **Selecionar formato de disco virtual**, é possível selecionar **thin provisioning** ou **thick provisioning**.
  7. Na página **Configurar redes**, mapeie o adaptador Hybrid Cloud Services para uma rede de host escolhida na lista **Destino**.
7. Na página **Modelo customizado**, insira os valores específicos para o ambiente:
  * Para as senhas, o nome do usuário padrão para a interface da linha de comandos (CLI) e a interface com o usuário da web é **admin**. O usuário e a senha **admin** para efetuar login na interface com o usuário da web são necessários, assim como uma conta do usuário **raiz** que tenha uma senha que possa ser configurada.
  * Insira e insira novamente a senha de usuário **admin** da CLI.
  * Insira e insira novamente a senha de usuário **raiz**. No futuro, se a ajuda for necessária do VMware Global Support Services (GSS), essa senha poderá ter que ser compartilhada para que eles possam solucionar problemas do sistema.
  * Para as propriedades de rede, insira o nome do host para a MV do HCX Manager. Insira o endereço IPv4 da rede, o prefixo IPv4 (o CIDR) e o gateway padrão. A tabela a seguir mostra os valores de amostra:

Tabela 1. Valores de amostra para propriedades de rede

| Campo                    | Valor           |
|--------------------------|-----------------|
| Hostname                 | HCM_1           |
| Endereço IPv4 da Rede 1   | 192.168.200.101 |
| Prefixo IPv4 da Rede 1    | 24              |
| Gateway IPv4 padrão     | 192.168.200.1   |
| Endereço IPv6 da Rede 1   |                 |
| Prefixo de 1 IPv6 de Rede    |                 |

8. Revise a página de ligações do vService. Clique em  ** Avançar **  para continuar.
9. Na página **Pronto para concluir**, siga estas etapas:
  * Marque a caixa **Ligar após a implementação**.
  * Revise as configurações do Hybrid Cloud Services e clique em **Concluir**. Pode levar vários minutos para que o dispositivo do Hybrid Cloud Services seja ligado.
  * Para verificar o status, acesse a página inicial do vSphere Web Client e, na guia **Página inicial**, acesse **Inventários** e clique em **Hosts e clusters**. Expanda a hierarquia do data center e clique na máquina virtual do serviço Hybrid Cloud Services para exibir um resumo na área de janela central.
  * Visualize a guia **Resumo**. O console lê **Ligado** e o ícone **Reproduzir** está verde.
10. O HCX Manager está ligado e pronto para ser registrado com o vCenter no local.

## Configuração inicial do HCX Manager Appliance
{: #hcxclient-vcs-client-deployment-inital-config}

1. Assegure-se de que o dispositivo virtual Hybrid Cloud Service tenha acesso de saída para `https://connect.hcx.vmware.com`
2. Efetue login na interface do administrador do dispositivo virtual Hybrid Cloud Services `https://<IP>:9443` com **administrador**
3. Forneça a chave de licença coletada em Pré-requisitos do lado do cliente.
4. Local do Data center do HCX Cloud
    - Insira a cidade mais próxima do Data center no qual a instância do HCX Cloud reside. Se a cidade não estiver presente, selecione a cidade principal mais próxima.
5. Forneça o nome do sistema

## Importar o certificado do vSphere Server
{: #hcxclient-vcs-client-deployment-import-cert}

1. Efetue login na interface do administrador do HCX Manager `https://<IP>:9443`
2. Selecione a guia **Administração** em **Certificado** -> **Certificado de autoridade de certificação confiável**
3. Importe o website do vSphere Server
   1. Selecione para importar certificados da URL e da chave na URL de registro do lado da nuvem do HCX.
     * São Paulo: `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## Procedimento para registrar o HCX Manager com o vCenter/SSO/NSX
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. Efetue login no dispositivo virtual de serviço Hybrid Cloud Services.
2. Na área de janela **Painel**, conclua as etapas a seguir:
  1. Na área de janela esquerda, em **Configurar sistemas**, selecione vCenter.
  2. Clique em **Incluir vCenter** na parte superior direita.
  3. Insira o endereço IP do vCenter Server no formato `https://vCenter-host-name` ou `https://vCenter-IP-address`. Por exemplo, `https://My-vCenter` ou `https://10.108.26.211`
  4. Insira o nome do usuário e a senha do vCenter Server. A conta que é usada deve ter a função de Administrador do vCenter.
  5. Clique em **OK**. Não reinicie quando a mensagem _Você precisa reiniciar o app_ for exibida.
3. Configure o serviço de SSO/consulta.
  6. Clique na guia  ** Gerenciar ** .
  7. Clique em **Editar** ao lado da caixa de texto **URL de serviço de consulta**.
  8. Insira o terminal em serviço de rede de consulta no formato a seguir:
    * Para o vCenter Server 6.5 `https://psc/`
  9.  Forneça detalhes do NSX, se necessário.
  10. Clique em **OK**. Não reinicie quando uma mensagem para reiniciar o mecanismo da web for exibida.
4. Clique na guia **Resumo** e localize a seção **Componentes de gerenciamento de hibridismo**. Pare e inicie o mecanismo de aplicativo e o mecanismo da web.
5. Para finalizar o registro, efetue logout do vSphere Web Client. Efetue login novamente no vSphere Web Client e verifique se a Guia HCX está presente.

## Resultados
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

Observe o ícone **Nuvem híbrida** existente e o item de menu **Hybrid Cloud Services** à esquerda. O registro do Hybrid Cloud Services atualiza esses rótulos. No inventário, o rótulo do ícone se torna **Hybrid Cloud Services**.

## Links relacionados
{: #hcxclient-vcs-client-deployment-related}

* [Glossário de componentes e termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparando o ambiente de instalação](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Entrelaçamento de serviços HCX no local](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrações de nuvem híbrida do VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitorando parâmetros e componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolução de problemas do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
