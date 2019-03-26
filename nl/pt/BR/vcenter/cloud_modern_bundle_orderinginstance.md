---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo, visualizando e excluindo instâncias do Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_orderinginstance}

Revise os requisitos de planejamento antes de pedir uma instância do Single-node Trial for Migration and App Modernization.

## Requisitos e planejamento para pedir instâncias de Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_orderinginstance-req}

Assegure-se de que você confirme os requisitos a seguir e conclua as tarefas a seguir.

### Pré-requisitos para Instâncias do HCX no local
{: #cloud_modern_bundle_orderinginstance-hcx-req}

* Requer o VMware vSphere e o vCenter 5.5 ou superior.
* O ambiente do vSphere deve ter comutadores distribuídos para as MVs que serão migradas para o {{site.data.keyword.cloud_notm}}.
* O dispositivo virtual HCX Manager deve estar apto a ser implementado em uma rede privada no ambiente no local e deve ter permissão para acessar a Internet pública.

### Conta de infraestrutura do IBM Cloud
{: #cloud_modern_bundle_orderinginstance-account-req}

* Para usar {{site.data.keyword.vmwaresolutions_short}} para pedir instâncias, deve-se ter uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer). O custo dos componentes que são pedidos em suas instâncias é faturado para aquela conta {{site.data.keyword.cloud_notm}}.
*  Configure as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Configurações** na área de janela de navegação esquerda.

### Requisitos de nome da instância
{: #cloud_modern_bundle_orderinginstance-inst-name-req}

Revise os requisitos de nome da instância:
* Apenas caracteres alfanuméricos e o traço (-) são permitidos.
* O nome da instância deve iniciar com um caractere alfabético e terminar com um caractere alfanumérico.
* O comprimento máximo do nome da instância é de 10 caracteres.
* O nome da instância deve ser exclusivo dentro de sua conta.

## Procedimento para pedir instâncias do Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_orderinginstance-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação esquerda e, em seguida, clique em **Single-node Trial for Migration and App Modernization** na seção **Datacenters virtuais**.
2. Na página **Single-node Trial for Migration and App Modernization**, clique em **Continuar**.
3. Conclua as etapas para solicitar uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} ou forneça o **Nome do usuário** e a **Chave de API** existentes e clique em **Recuperar**.

 Esta seção estará oculta se a chave de API existir.
 {:note}
4. Insira o nome da instância.
5. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.  

 Por padrão, o DAL09  {{site.data.keyword.CloudDataCent_notm}}  é pré-selecionado. Selecione um local do  {{site.data.keyword.CloudDataCent_notm}}  diferente, se necessário.
 {:note}
6. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
   1. Revise as configurações para a instância.
   2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de pedir a instância.
   4. Clique em **Provisão**.

### Resultados
{: #cloud_modern_bundle_orderinginstance-results}

A implementação da instância é iniciada automaticamente e o HCX no local na chave de ativação de serviço do {{site.data.keyword.cloud_notm}} é pedido.

#### Processo de implementação para HCX no IBM Cloud
{: #cloud_modern_bundle_orderinginstance-hcx-deploy-process}

A implementação do HCX no {{site.data.keyword.cloud_notm}} é automatizada. As etapas a seguir são concluídas pelo processo de automação do {{site.data.keyword.vmwaresolutions_short}}:
1. Três sub-redes são pedidas para o HCX por meio da infraestrutura do {{site.data.keyword.cloud_notm}}:
   * Duas sub-redes móveis privadas para gerenciamento do HCX.
   * Uma sub-rede portátil pública para ativação e manutenção com o VMware. Essa sub-rede também é usada para interconexões de HCX.

   Os endereços IP nas sub-redes que são pedidos para o HCX são destinados a serem gerenciados pela automação do VMware on {{site.data.keyword.cloud_notm}}. Esses endereços IP não podem ser designados a recursos do VMware, como MVs e NSX Edges, que são criados por você. Se você precisa de mais endereços IP para seus artefatos do VMware, deve-se pedir suas próprias sub-redes por meio do {{site.data.keyword.cloud_notm}}.
   {:important}
3. Três conjuntos de recursos e pastas da MV para o HCX são criados, os quais são necessários para as interconexões do
HCX, os componentes do HCX local e os componentes do HCX remoto.
4. Um par de VMware NSX Edge Services Gateways (ESGs) para o tráfego de gerenciamento do HCX é implementado e configurado:
   * As interfaces de uplink públicas e privadas são configuradas usando as sub-redes pedidas.
   * Os ESGs são configurados como um par de dispositivos de borda extragrandes com a Alta Disponibilidade (HA) ativada.
   * As regras de firewall e as regras de conversão de endereço de rede (NAT) são configuradas para permitir o tráfego HTTPS de entrada e de saída para/do HCX Manager.
   * As regras do balanceador de carga e os conjuntos de recursos são configurados. Essas regras e conjuntos de recursos são usados para encaminhar o tráfego de entrada relacionado ao HCX para os dispositivos virtuais apropriados do HCX Manager e do vCenter Server (com o Platform Services Controller integrado).
   * Um certificado SSL para criptografar o tráfego HTTPS de entrada relacionado ao HCX que está chegando por meio de ESGs é aplicado.

   A borda de gerenciamento do HCX é dedicada ao tráfego de gerenciamento do HCX entre os componentes do HCX no local e os componentes do HCX do lado da nuvem. Não modifique o limite de gerenciamento do HCX ou use-o para extensões de rede do HCX. Em vez disso, crie limites separados para extensões de rede. Além disso, o uso de um firewall ou a desativação das comunicações de borda de gerenciamento do HCX para os componentes de gerenciamento privado da IBM ou a Internet pública pode causar impacto negativamente na funcionalidade do HCX.
   {:important}

5. O HCX Manager on {{site.data.keyword.cloud_notm}} é implementado, ativado e configurado:
   * O HCX Manager é registrado com o vCenter Server.
   * O HCX Manager, o vCenter Server (com o Platform Services Controller integrado) e o NSX Manager estão configurados.
   * A frota do HCX está configurado.
   * Os contêineres de implementação do HCX locais e remotos são configurados.
6. O nome do host e o endereço IP do HCX Manager está registrado com o servidor DNS do VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualizando detalhes da instância
{: #cloud_modern_bundle_orderinginstance-view-inst-details}

É possível verificar o status da implementação visualizando os detalhes da instância. Clique em **Recursos** na área de janela de navegação esquerda e localize a tabela **Instâncias do servidor do vCenter** ou **Instâncias do HCX no local** para visualizar informações sobre as instâncias que você pediu.

Quando a instância é implementada com êxito, os componentes que são descritos nas seções *Especificações técnicas* deste tópico são instalados em sua plataforma virtual VMware e a chave de ativação do serviço HCX on {{site.data.keyword.cloud_notm}} no local é listada na tabela **Instâncias do HCX no local**.

O status da instância muda para **Pronto para uso** e você recebe uma notificação por e-mail.

### O que fazer a seguir
{: #cloud_modern_bundle_orderinginstance-next}

Instale o HCX Enterprise Manager local e configure a conexão com a instância do HCX on {{site.data.keyword.cloud_notm}}.

1. Localize a chave de ativação no local na página **Recursos**.
  1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
  2. Na tabela **Instâncias do vCenter Server**, revise a coluna **Tipo** para localizar a instância do Single-node Trial for Migration and App Modernization e anote o nome da instância.
  3. Role para a tabela **Instâncias do HCX no local** e revise a coluna **Nome** para localizar a instância que tem o mesmo nome que a instância de nó único que você pediu com o sufixo *-OnPrem*.
  4. Anote a chave no campo **Chave de ativação**.
2. Obtenha o HCX Enterprise Manager Open Virtual Appliance (OVA) local por meio do console do HCX on {{site.data.keyword.cloud_notm}} HCX Manager.
  1. Conecte-se ao HCX Cloud Console.
    1. Na tabela **Instâncias do vCenter Server**, clique na instância do Single-node Trial for Migration and App Modernization para visualizar os detalhes da instância.
    2. Em **Informações de acesso**, localize e anote as credenciais do vCenter.
    3. Clique em **Serviços** na área de janela de navegação esquerda.
    4. Na página **Serviços**, clique em **HCX on IBM Cloud**.
    5. Na página de detalhes **HCX on IBM Cloud**, localize e anote o **IP do HCX Cloud**.
    6. Assegure-se de que esteja conectado à VPN para acessar sua rede privada do {{site.data.keyword.cloud_notm}}.
    7. Clique em **Visualizar HCX Cloud Console**.
  2. Em **Console em Nuvem do HCX**, conclua as etapas a seguir:
      1. Clique na guia **Administração**.
      2. Na guia **Atualizações do Sistema**, clique em **SOLICITAR LINK DE DOWNLOAD**.
      3. Clique em **COPIAR LINK** e, em seguida, use esse link para fazer download do HCX Enterprise Client para um ambiente local com acesso ao ambiente do vSphere local.
3. No VMware vSphere Web Client, implemente o HCX Enterprise Client como um dispositivo virtual do HCX Manager (HCX Manager) em seu ambiente local. Para obter mais informações, consulte [Instalando o HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    Deve-se implementar o HCX Manager local em uma rede privada e permitir que ele acesse a rede pública. É possível usar um NSX Edge, Vyatta ou gateways semelhantes para permitir acesso à Internet para o HCX Manager no local. Se os gateways usados para acesso à rede privada e acesso à rede pública forem diferentes, recomenda-se que você use o gateway padrão para permitir o acesso à rede pública e permitir que o **Console do Administrador do HCX Manager** crie uma rota estática para o acesso à rede privada.  
    {:note}
4. Use a chave de ativação no local anotada na etapa 1 para ativar a MV do HCX Enterprise Manager local.
  1. Efetue login na sua MV do HCX Enterprise Manager no local usando as credenciais que são especificadas ao implementar o OVA.
  2. Insira a chave de ativação quando solicitada.

  Para obter mais informações, consulte [Ativação e configuração inicial do HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. Um certificado SSL autoassinado foi gerado pelo serviço HCX on {{site.data.keyword.cloud_notm}}. Deve-se importar o certificado para o HCX Manager local concluindo as etapas a seguir:
    1. No **Console do Administrador do HCX Manager** local, clique na guia **Administração**.
    2. Na área de janela de navegação esquerda, clique em **Certificado CA confiável** e, em seguida, clique em **IMPORTAR** à direita.
    3. Clique em **URL** e, em seguida, insira a URL do certificado que você deseja aplicar. Este é o **IP de nuvem do HCX** (``https://<cloud-side public IP>``) que pode ser localizado na página de detalhes do serviço HCX on {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}.
    4. Clique em **APLICAR**.
6. Continue a configuração inicial e construa a interconexão. Para obter mais informações, consulte [Instalando e configurando o VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Amplie as redes no VMware HCX do local para o {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Ampliando redes com o VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migre as MVs entre o local e o {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Migrando máquinas virtuais com o VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

Deve-se gerenciar os componentes de infraestrutura do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do {{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console.
Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console e poderão tornar seu ambiente instável.
{:important}

## Procedimento para excluir instâncias do Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_orderinginstance-deleting-procedure}

Quando você exclui uma instância do Single-node Trial for Migration and App Modernization, os componentes a seguir são liberados sequencialmente:

1. Todos os serviços implementados
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e as VLANs não podem ser excluídas até que os servidores do ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}}, o que acontece no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}. No final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e VLANs são excluídas e a exclusão da instância é concluída.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para a instância excluída.
{:note}

Conclua as etapas a seguir para excluir uma instância do Single-node Trial for Migration and App Modernization:

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, localize a instância a ser excluída.
3. Na coluna **Ações**, clique no ícone Excluir.
   O status da instância é mudado para **Excluindo**. Quando a instância for excluída com êxito, seus componentes serão liberados e seu status mudará para **Excluído**.
4. Se desejar remover o registro da instância do console do {{site.data.keyword.vmwaresolutions_short}}, conclua as etapas a seguir:
   1. Na coluna **Ações**, clique no ícone Excluir novamente.
   2. Na janela **Excluir instância**, clique em **OK**.

## Links relacionados
{: #cloud_modern_bundle_orderinginstance-related}

* [Guia do vCenter Server e do IBM Cloud Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Abra um chamado para o IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=en_US)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Obtendo o HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
