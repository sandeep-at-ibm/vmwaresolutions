---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Implementação de nuvem e do cliente
{: #vcshcx-deployment}

Conforme descrito no início deste documento, uma instalação mínima do HCX
consiste em uma implementação de uma única nuvem e do lado do cliente. O lado do cliente
HCX pode ser instalado em qualquer versão do vSphere suportada pelo HCX, assumindo que
haja conectividade de rede entre os lados do cliente e da nuvem.

## Requisitos
{: #vcshcx-deployment-req}

- HCX Manager - Contagem de 4 CPUs, Memória 12 G, Disco 60 G
- CGW - Contagem de 8 CPUs, Memória 3 G, Disco 2 G
- L2C - Contagem de 8 CPUs, Memória 3 G, Disco 2 G
- WAN Opt - Contagem de 8 CPUs, Memória 14 G, Disco 100 G

## Nuvem
{: #vcshcx-deployment-cloud}

A implementação do HCX do lado da nuvem é manipulada pela automação do {{site.data.keyword.vmwaresolutions_full}}. A configuração padrão usa o grupo de portas
públicas para configurar qualquer conectividade de terminal de componentes de frota. Os
componentes de frota no lado da nuvem são implementados com suas interfaces de
terminal configuradas com endereços IP públicos, uma vez que são dispositivos com segurança
reforçada. É possível implementá-los com a proteção de um firewall. Não é
suportado que os lados do cliente e da nuvem se conectem
entre si por um túnel VPN existente. Se você deseja usar
a rede privada para conectividade de terminal do HCX, é possível pedir o lado da
nuvem do HCX para a implementação da frota de rede privada para uso no link
dedicado, como MPLS.

## Cliente
{: #vcshcx-deployment-client}

O HCX do lado do cliente é implementado pelo usuário e requer permissões de
nível de administrador para o vCenter de origem. A partir dessa gravação, o ova do
gerenciador do lado do cliente do HCX tem aproximadamente 1,7 GB. Ao usar o console do {{site.data.keyword.vmwaresolutions_short}} para pedir
o HCX, é fornecida uma URL com
um link para fazer download da versão do HCX do lado do cliente que corresponde
à versão do HCX implementada no lado da nuvem. Esse link é fornecido na
interface com o usuário (IU) do HCX do gerenciador do lado da nuvem.

Uma chave de registro de uso descartável também é fornecida. Use as etapas a seguir para configurar o registro de uso.

1. Faça download do OVA do cliente HCX (corporativo) por meio do link fornecido na
IU do HCX do lado da nuvem.
    1. Efetue login na IU do HCX do lado da nuvem usando a IU de registro do HCX fornecida pela IBM.
    2. Use o ID e a senha do vCenter da nuvem para efetuar login na IU.
    3. Na guia **Administração**, selecione **solicitar link de download** para fazer download do OVA do lado do cliente. Use uma "caixa de salto", que é local para o vCenter de origem no qual o OVA é implementado, para concluir essa etapa.
2. Efetue login no cliente C++ do vSphere (ou no Web client com o snap-in de integração do cliente em funcionamento) e importe o OVA que usa o assistente de importação do vCenter.
    1. Assegure-se de que a rede na qual o gerenciador do HCX está configurado tenha acesso ao vCenter de origem e à Internet.  
    2. Insira a chave de registro quando solicitado. (Use o Web client se você tiver a configuração de snap-in de ferramentas do cliente.)  
3. Efetue logout e volte para o Web client do vCenter. O ícone de seleção de menu **HCX** é exibido no menu da tela inicial.
4. Para certificados autoassinados, selecione o item de menu HCX para acessar a IU de snap-in do HCX. Selecione a guia  ** Administração ** .
    1. Selecione para importar certificados da URL e tecle a URL de registro do lado da nuvem do HCX fornecida pelo console do {{site.data.keyword.vmwaresolutions_short}} para HCX.
    2. Selecione **Nova parada do site** na área da janela **Paradas do site** na guia **Painel**.
    3. Siga os prompts e forneça a URL de registro do lado da nuvem do HCX e o ID de administrador e a senha do vCenter do lado da nuvem.
    4. Continue seguindo os prompts no assistente de registro do site na configuração dos componentes de Frota, incluindo o Cloud Gateway, o Layer 2 Concentrator e o WAN Optimizer.  

Para o lado do cliente, use o menu **Tarefas** para monitorar a implementação dos componentes de Frota. Para a implementação do lado da nuvem, use o menu **Tarefas** na IU da web do vCenter para a instância específica do vCenter Server.

Se houver uma falha de implementação em
ambos os lados, as implementações do componente de frota serão restauradas e
excluídas. Ao determinar a causa da falha, clique na guia **Interconectar** na IU da web do HCX vCenter no lado do cliente e, em seguida,
selecione **Instalar componentes do HCX** na parte superior da tela.

Após a implementação bem-sucedida de componentes da Frota e depois de vários
minutos, o status do túnel para os componentes CGW e L2C será **Ativo** na guia **Interconexão**.

## Links relacionados
{: #vcshcx-deployment-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
