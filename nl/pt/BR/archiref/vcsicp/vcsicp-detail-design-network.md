---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Acesso à rede e fluxos

## Acesso ao aplicativo Container-ICP

Há três maneiras principais de obter tráfego externo e acessar seus aplicativos de cluster do Kubernetes:

- NodePort
- LoadBalancer
- Ingresso

### NodePort
As portas de nó são uma maneira simples de expor o acesso externo a uma carga de trabalho para desenvolvimento e testes iniciais, mas não recomendados para produção. Ingress ou balanceador de carga é o caminho recomendado.

### LoadBalancer
Atualmente, a Plataforma ICP suporta um Balanceador de Carga externo para carga de trabalho do aplicativo.

### Ingresso
Um Ingress é uma coleção de regras que permitem que as conexões de entrada atinjam os serviços de cluster. Ele pode ser configurado para fornecer serviços a URLs que podem ser acessadas externamente, ao tráfego de balanceamento de carga, para finalizar o SSL, para oferecer hospedagem virtual baseada em nome e muito mais.  O nó do Proxy na infraestrutura do ICP executa essa função.

## Acesso ao aplicativo Container-IKS
Há três maneiras principais de obter tráfego externo e acessar seus aplicativos de cluster do Kubernetes:

- NodePort
- LoadBalancer
- Ingresso

### NodePort
As portas de nó são uma maneira simples de expor o acesso externo a uma carga de trabalho para desenvolvimento e testes iniciais, mas não recomendados para produção. Ingress ou balanceador de carga é o caminho recomendado.

### LoadBalancer
Cada Cluster do IKS é provisionado com um Application Load Balancer (ALB) público ou privado. O ALB usa um ponto de entrada público ou privado protegido e exclusivo para rotear solicitações recebidas para seus aplicativos.

### Ingresso
Um Ingress é uma coleção de regras que permitem que as conexões de entrada atinjam os serviços de cluster. Ele pode ser configurado para fornecer serviços a URLs que podem ser acessadas externamente, ao tráfego de balanceamento de carga, para finalizar o SSL, para oferecer hospedagem virtual baseada em nome e muito mais.

## Fluxos de tráfego
Os fluxos de tráfego a seguir são descritos:

- Usuário externo na Internet para uma camada da web hospedada em um contêiner no {{site.data.keyword.cloud}} Private (ICP).
- A camada da web hospedada em um contêiner no ICP para a camada de banco de dados hospedada em uma máquina virtual (VM) no VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
- Usuário corporativo no acesso à rede corporativa para uma VM no vCenter Server.

### Usuário externo na Internet para uma camada da web hospedada em um contêiner no ICP

1. O usuário externo faz uma solicitação para a camada da web usando a URL.
2.	O DNS é usado para determinar o endereço IP. Esse endereço IP é um endereço público do {{site.data.keyword.cloud_notm}} em uma sub-rede móvel que é designada à instância do vCenter Server.
3.	A rede pública encaminha automaticamente a solicitação para o host do vSphere ESXi que hospeda o ESG.
4.	O ESG encaminha a solicitação para o endereço IP do cluster interno e o número da porta do ALB ou do Ingress Service. O pacote de IP será encapsulado em um quadro VXLAN se o ESG e o Serviço ALB ou Ingress estiverem em hosts do vSphere ESXi diferentes. Esse endereço IP do cluster interno é acessível somente dentro do cluster.
5.	Dentro do nó do trabalhador, o proxy do kube roteia a solicitação para o serviço ALB ou Ingress.
6.	Se o aplicativo estiver no mesmo nó do trabalhador, o iptables será usado para determinar qual interface interna será usada para encaminhar a solicitação. Se o aplicativo estiver em um nó trabalhador diferente, o Calico vRouter roteará para o nó do trabalhador aplicável, usando encapsulamento IP-in-IP. O pacote IP-in-IP é encapsulado em um quadro VXLAN para transporte para o host do vSphere ESXi em que o nó do trabalhador está localizado.

### Camada da web hospedada em um contêiner no ICP para a camada de banco de dados hospedada em uma VM no vCenter Server

Como as tabelas de rotas no ESG e vRouters são preenchidas depende do método de integração. Veja Integração do ICP e do vCenter Server.

1.	A camada da web em execução em um contêiner no ICP faz uma solicitação para um banco de dados em execução em uma VM na mesma instância do vCenter Server.
2.	O DNS é usado para resolver a solicitação para o endereço IP do banco de dados.
3.	O contêiner envia a solicitação para o Calico vRouter.
4.	O vRouter tem sua tabela de rotas que é preenchida com os intervalos de endereços IP hospedados na instância do vCenter Server.
5.	O vRouter encaminha a solicitação, mas usa SNAT para mudar o endereço IP de origem do endereço IP do pod para o endereço IP do nó do trabalhador.
6.	O nó trabalhador que hospeda o vRouter envia a solicitação para o ESG.
7.	O ESG, em seguida, encaminha para o DLR.
8.	O DLR coloca a solicitação na VXLAN necessária.
9.	A VM do banco de dados recebe a solicitação.

### 	Usuário corporativo no acesso à rede corporativa para uma VM no vCenter Server

1.	Um usuário corporativo conectado à rede interna corporativa faz uma solicitação de um recurso em uma VM hospedada no vCenter Server.
2.	O DNS é usado para determinar o endereço IP da VM. Esse endereço IP está em uma rede que é estendida para o {{site.data.keyword.cloud_notm}}.
3.	O roteador no local direciona o tráfego para o host vSphere que está hospedando o Concentrador L2.
4.	O concentrador L2 encapsula a solicitação em um túnel seguro e a encaminha para o Concentrador L2 remoto hospedado mp {{site.data.keyword.cloud_notm}}, usando o endereço IP da sub-rede móvel privada que é designado ao dispositivo, via roteador no local.
5.	A rota no local verifica sua tabela de roteamento e discerne que o endereço IP para o Concentrador L2 remoto precisa ser enviado para a interface WAN. Ela encaminha ao longo da WAN, por meio do roteador XCR do {{site.data.keyword.cloud_notm}}, via BCR.
6.	O Concentrador L2 recebe a solicitação e a coloca na VXLAN que hospeda a rede estendida.
7.	A VM recebe a solicitação.

## Rede de acesso público
O ICP e o CAM por padrão requerem conectividade de Internet para recuperar imagens do Docker, gráficos Helm, modelos do Terraform e gerenciadores de pacotes do sistema operacional.
Nas liberações mais recentes, agora há suporte para instalações baseadas em proxy para instalações que não estão diretamente conectadas à Internet e têm opções para instalar em um modo off-line.

###	Firewall do NSX
O firewall do ICP NSX Edge é configurado com regras para permitir:
*	Ativar o acesso às redes VXLAN para o acesso público.
*	Ativar o acesso às redes VXLAN para o acesso à rede privada do {{site.data.keyword.cloud_notm}}.
*	Ativar o acesso à rede privada do {{site.data.keyword.cloud_notm}} para as redes VXLAN.

### NSX NAT
O ICP NSX NAT é configurado com os NATs a seguir:
*	SNAT para acesso às redes VXLAN para acesso público.
*	SNAT para acesso às redes VXLAN para acesso à rede privada do {{site.data.keyword.cloud_notm}}.
*	DNAT para o ICP Cluster vIPs.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
