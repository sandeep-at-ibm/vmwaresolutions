---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

# Configuração inicial
{: #vum-init-config}

A automação IC4VS configura o VCSA com um gateway padrão configurado para o {{site.data.keyword.cloud}} Backend Customer Router (BCR). No entanto, não há rota para a Internet por meio do BCR. A rota padrão para a Internet por meio da instância do VMware vCenter Server on {{site.data.keyword.cloud_notm}} é via ESG de Gerenciamento. Como não é aconselhável mudar a configuração do VCSA ou do ESG de Gerenciamento, uma implementação do servidor proxy na sub-rede do cliente é recomendada para ativar o VUM.

Essa abordagem significa que você não precisa reconfigurar o VCSA ou o ESG de Gerenciamento, no entanto, uma pequena máquina virtual (MV) ou um dispositivo deve ser instalado. Um servidor proxy é um sistema que fica entre dois dispositivos de terminal e age como um dispositivo intermediário. Neste caso, ele fica entre o VUM e os servidores de atualização no VMware.

Quando um VUM solicita um recurso do servidor de atualização no VMware, a solicitação é enviada para o servidor proxy primeiro e o servidor proxy, em seguida, envia a solicitação para o servidor de atualização. Depois que o recurso é obtido pelo servidor proxy, ele o envia para o VUM. Um servidor proxy pode ser usado para facilitar a segurança, os controles administrativos e os serviços de armazenamento em cache.

Este documento descreve o uso de um servidor proxy com base no CentOS e no Squid. O Squid Proxy é um proxy de armazenamento em cache de software livre para a web e suporta muitos protocolos que incluem HTTP e HTTPS. Vários proxies baseados em MV e baseado em dispositivo estão disponíveis e deve-se selecionar o apropriado com base nos requisitos de sua empresa e instalar e configurar seguindo a orientação do fornecedor. Os clientes que optam por usar uma implementação do CentOS/Squid devem continuar com o processo a seguir.

* Fazer download do ISO do CentOS em um servidor de salto
* Criar uma Biblioteca do vCenter
* Fazer upload do ISO para a Biblioteca vCenter
* Criar uma MV, instalar e configurar o CentOS e instalar o Squid

Antes de poder iniciar essa tarefa, é necessário coletar informações para preencher a Tabela 1. Revise os valores sugeridos e assegure-se de que eles sejam apropriados para sua empresa. Essa configuração é baseada em um pequeno proxy apenas para o VUM que usa o CentOS-Minimal e o Squid.

Tabela 1. Valores de implementação

| Parâmetro | Valores sugeridos | Notas |
|:--------- |:-------------- |:------ |
| CPU do proxy | 1 vCPU | O Squid não tem requisitos mínimos |
| RAM de proxy | 2 GB | O Squid não tem requisitos mínimos |
| Disco de proxy | 25 | O GB Squid não possui requisitos mínimos |
| Hostname | Proxy01 | |
| Endereço | IP de proxy | Um endereço IP sobressalente deve ser usado por meio do Cliente, a sub-rede móvel privada designada durante o processo de fornecimento. Somente dois endereços IP teriam sido reservados nessa sub-rede; um para o BCR e o outro para o customer-esg
| Máscara de | 255.255.255.192 | |
| Gateway| customer-nsx-ip private uplink ip | Essa é a configuração de gateway padrão para o servidor proxy, que é o endereço IP do uplink privado de customer-nsx-edge. O endereço IP pode ser localizado revisando a guia **Configurações** para o **customer-nsx-edge**. |
| Servidor DNS | IP do AD/DNS | Esse endereço IP pode ser localizado na página da instância no console do {{site.data.keyword.vmwaresolutions_short}}, na página **Recursos**. |
| IP do BCR | bcr ip | Esse é o endereço IP do {{site.data.keyword.cloud_notm}} Backend Customer Router e é o gateway para 10.0.0.0/8 e 161.26.0.0/16. Esse endereço é usado em uma rota estática no servidor proxy para que ele possa atingir o VCSA e o servidor AD/DNS. |

## Configurando o NSX
{: #vum-init-config-config-nsx}

As configurações de firewall do ESG do Cliente NSX e da NAT são necessárias para ativar o tráfego do servidor proxy.

### Firewall
{: #vum-init-config-firewall}

1. Acesse  ** Home **  >  ** Networking & Security **.
2. Selecione **NSX Edges**, customer-nsx-edge e, em seguida, **Firewall**.
3. Clique no símbolo **+** e inclua uma regra de firewall.
4. Forneça os parâmetros necessários conforme observado na tabela a seguir. A nova regra de firewall deve vir antes da última regra, a regra de Negação padrão.

Tabela 2. Regra de firewall

| Parâmetro | Valores sugeridos |
|:--------- |:-------------- |
| Nome | Proxy01 de saída |
| Tipo | User |
| Origem | IP do servidor proxy |
| Destino | qualquer |
| Serviço | Eco do HTTP/HTTPS/ICMP |
| Ação | Aceitar |

Após os parâmetros serem fornecidos, clique em **Publicar mudanças**.

### Instalando e configurando um servidor proxy
{: #vum-init-config-inst-cfg-proxy}

O processo a seguir implementa uma MV para hospedar o CentOS e o Squid da Biblioteca de Conteúdo e consiste nas etapas a seguir. Presume-se que você tenha uma VSI do Windows provisionada para uso como um jumpbox e que esteja usando o Remote Desktop Protocol para se conectar à interface pública da VSI:

* Fazer download do arquivo CentOS-Minimal ISO
* Configurar uma Biblioteca de Conteúdo do vCenter e preencher com o arquivo ISO do CentOS
* Configurar a MV do Proxy, instalar o CentOS e o Squid

### Fazendo download do arquivo CentOS-Minimal ISO
{: #vum-init-config-downloading-centos}

Usando um navegador em seu servidor de salto, faça download do arquivo ISO do CentOS-Minimal por meio do [CentOS](https://www.centos.org/download/). Observe que o {{site.data.keyword.cloud_notm}} mantém um espelho de muitas distribuições Linux populares. Esse espelho está disponível somente na rede privada e os ISOs do CentOS estão disponíveis no endereço a seguir: `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Configurando uma biblioteca de conteúdo e preenchendo-a com o arquivo ISO do CentOS
{: #vum-init-config-config-conent-library}

Crie uma biblioteca de conteúdo do vCenter local. A biblioteca é acessível somente na instância do vCenter Server na qual ela é criada. Preencha a biblioteca com modelos e ISOs necessários para implementar MVs.

1. Por meio do vSphere Web Client, navegue para **Página inicial** > **Biblioteca de conteúdo** > **Objetos** > **Criar uma nova biblioteca de conteúdo** > **Criar biblioteca inscrita no vCenter**.
2. Insira um nome para a biblioteca de conteúdo, por exemplo, ISO, e, na caixa de texto Notas, insira uma descrição para a biblioteca e clique em **Avançar**.
3. Selecione **Biblioteca de conteúdo local** e clique em **Avançar**.
4. Selecione um armazenamento de dados e, em seguida, clique em um armazenamento de dados adequado, por exemplo, vsanDatastore.
5. Revise as informações na página **Pronto para concluir** e clique em **Concluir**.

### Configurando a MV do proxy, instalar o CentOS e o Squid
{: #vum-init-config-config-proxy}

Esta atividade tem as tarefas a seguir:

*	Criar uma nova MV
*	Instalar o CentOS
*	Instalar o Squid

#### Criar uma nova MV
{: #vum-init-config-create-new-vm}

Esta tarefa cria uma nova MV pronta para uso como o servidor proxy. As configurações da Tabela 1 Valores de implementação devem ser usadas para preencher a configuração.

1.	Por meio do vSphere Web Client, navegue para **Página inicial** > **MVs e modelos**.
2.	Na área de janela do Navegador, clique em **datacenter1** e, em seguida, clique com o botão direito e selecione **Nova máquina virtual** > **Nova máquina virtual**.
3.	Selecione **Criar uma nova máquina virtual** e, em seguida, clique em **Avançar**.
4.	Insira um Nome para a MV, por exemplo, Proxy01, e selecione **datacenter1**, em seguida, clique em **Avançar**.
5.	Selecione  ** cluster1 **  e, em seguida, clique em  ** Avançar **.
6.	Selecione um armazenamento de dados apropriado, por exemplo, vsanDatastore, e clique em **Avançar** e em **Avançar** novamente.
7.	Em **Família de S.O. guest**, selecione **Linux** e, em **Versão do S.O. guest**, selecione **CentOS 7 (64 bits)** e clique em **Avançar**.
8.	Configure **CPU como 1**, **Memória como 2048 MB** e **Novo disco rígido como 25 GB**. Selecione **Arquivo ISO de Biblioteca de Conteúdo** e, em seguida, **CentOS-7-x86_64-Minimal**, clique em **OK** e marque a caixa **Conectado**.
9.	Na caixa Novo dispositivo, selecione **Rede** e, em seguida, clique em **Incluir**.
10.	Selecione a rede **SDDC-DPortGroup-Mgmt** e assegure-se de que a caixa de seleção Conectar esteja marcada, clique em **Avançar**.
11.	Revise e clique em **Concluir**.

#### Instalar o CentOS
{: #vum-init-config-install-centos}

Esta tarefa instala e configura a MV recém-criada pronta para a instalação do Squid

1.	Na área de janela do Navegador do vSphere Web Client, selecione a **VM** recém-criada, Proxy01, em seguida, selecione a **Guia Resumo**.
2.	Clique em **"Reproduzir"** para ligar a MV.
3.	A MV é ligada e inicializada por meio do ISO do CentOS 7. Inicie um **Console remoto ou console da web** para a MV. Deve-se instalar o Console Remoto e o sistema que está executando o navegador da web deve resolver os hosts vSphere ESXi por nome.
4.	Na tela Bem-vindo ao CentOS 7, selecione seu idioma necessário e clique em **Continuar**.
5.	Na tela **LOCALIZAÇÃO**, clique em **DATE E HORA** e selecione seu fuso horário, em seguida, clique em **Pronto**.
6.	Na tela **LOCALIZAÇÃO**, clique em **TECLADO** para mudar do padrão, se necessário, em seguida, pressione **Pronto**.
7.	Na tela **LOCALIZAÇÃO**, clique em **DESTINO DE INSTALAÇÃO**, clique no **Ícone de disco virtual do VMware** e, em seguida, clique em **Pronto**.
8.	Na tela **LOCALIZAÇÃO**, clique em **REDE E NOME DO HOST**, mude o nome do Host para o nome do host escolhido, por exemplo, Proxy01.
9.	Clique em  ** Configurar ** e, em seguida, em  ** Configurações de IPv4 **. Na caixa  ** Método ** , selecione  ** Manual **.
10.	Usando o botão **Incluir**, insira _Máscara de rede do endereço_ e _Gateway_ da _Tabela 1 - Valores de implementação_.
11.	Insira o _Endereço IP do servidor DNS_ da Tabela 1 - Valores de implementação.
12.	Clique no botão **Rotas** e inclua as rotas estáticas a seguir, _10.0.0.0/8 e 161.26.0.0/16_ com um endereço IP de gateway do _Endereço IP do BCR_ da Tabela 1 Valores de implementação, como o gateway. Essa rota estática permite que o servidor proxy atinja o servidor DNS.
13.	Clique em **Salvar** e, em seguida, assegure-se de que a interface Ethernet esteja Ligada e mostrada como conectada. Clique em **Pronto** e em **Iniciar instalação**.
14.	Conforme a instalação continua, configure uma senha raiz e configure um usuário.
15.	Quando a instalação estiver concluída, efetue login como o usuário e, em seguida, insira o comando _ping vmware.com_. O nome é resolvido para um endereço IP e você recebe uma resposta. Se você não obtiver respostas, verifique os endereços IP, as regras de firewall e as configurações de NAT.

#### Instalar e configurar o Squid
{: #vum-init-config-install-cfg-squid}

O Squid não tem nenhum requisito mínimo de hardware, mas a quantia de RAM pode variar de acordo com os usuários que estão acessando a Internet por meio de seu proxy e os objetos que são armazenados no cache. Como o servidor proxy é acessado somente pelo VUM e o cache não está ativado, somente uma MV pequena está configurada.

1. Usando o Console da Web ou o Console Remoto por meio do vSphere Web Client, efetue login no servidor proxy como o usuário e, em seguida, `su` para raiz.
2. Antes de instalar quaisquer pacotes, deve-se usar o comando a seguir para atualizar o sistema e os pacotes:
   `yum -y update`

3. Para instalar o Squid, é necessário instalar o repositório EPEL para o sistema, pois o Squid não está disponível no repositório yum padrão. Execute o comando a seguir para instalar o repositório EPEL:
  `yum -y install epel-release`

4. Atualize e limpe usando os comandos a seguir:

  `yum -y update`
  `yum clean all`

5. O Squid é instalado usando o comando a seguir: `yum -y install squid`.
6. Depois de instalado, inicie o Squid imediatamente usando o comando a seguir: `systemctl start squid`.
7. Execute o comando a seguir para iniciar automaticamente o Squid no tempo de inicialização: `systemctl enable squid`.
8. Execute o comando a seguir para assegurar-se de que o Squid esteja em execução: `systemctl status squid`.
9. O firewall CentOS precisa permitir acesso à porta do Squid, TCP 3128, usando o comando a seguir: `firewall-cmd –add-port=3128/tcp –permanent`.
10.	Para salvar a regra e reiniciar o serviço, use o comando a seguir: `firewall-cmd –reload`.

## A configuração inicial do VUM
{: #vum-init-config-init-setup-vum}

Configure o VUM para usar o servidor proxy para acessar os repositórios na Internet.
1. Usando o vSphere Web Client, navegue para **Página inicial** > **Update Manager**. Clique em seu vCenter Server.
2. Selecione a **guia Gerenciar** e clique no botão **Configurações**.
3. Selecione **Configurações de download** e, em seguida, em _Configurações de proxy_, clique em **Editar**.
4. Marque a caixa **Usar proxy** e insira o _Endereço IP do servidor proxy_ e a _porta 3128_, clique em **OK**. O Status de conectividade muda para _Validando_ e, em seguida, para _Conectado_.
5. Clique em  ** Fazer Download Agora **. Na área de janela _Tarefas recentes_, você deverá ver essa atividade concluída.

## Links relacionados
{: #vum-init-config-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrações)
