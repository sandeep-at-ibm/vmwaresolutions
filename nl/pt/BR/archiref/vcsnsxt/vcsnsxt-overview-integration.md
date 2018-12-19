---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# Integração, endereçamento IP e fluxos de rede

## Integração do ICP e VCS

O {{site.data.keyword.cloud}} Private está instalado em várias máquinas virtuais em uma instância do VCS. Dentro da instância do VCS, a instância do ICP é implementada com um NSX Edge Services Gateway (ESG) e um Distributed Logical Router (DLR) dedicados e usa uma VXLAN.

O ESG é configurado com uma regra SNAT para permitir o tráfego de saída, permitindo a conectividade da Internet para fazer download dos pré-requisitos do ICP e a conectividade com o GitHub e o Docker. Um servidor proxy da web pode ser usado para fornecer a conectividade da Internet, se desejado. O ESG é configurado com conectividade privada para acessar serviços DNS e NTP. O ESG também é configurado com uma regra DNAT para ativar os vIPs Principal e Proxy do ICP a serem acessados por meio da rede {{site.data.keyword.cloud_notm}} 10.x.

## Integração do IKS e VCS

Atualmente, há os cenários a seguir para integrar a rede IKS e VCS:
- **VLAN comum** - isso requer que os nós do trabalhador do IKS sejam implementados na mesma VLAN que a instância do VCS. Isso permite que um ESG seja um peer do BGP para os nós do trabalhador.
- **VPN strongSwan** - esse cenário usa o IKS padrão para a solução de conectividade corporativa. Um contêiner strongSwan fornece um gateway VPN para o cluster que encaminha pacotes para redes remotas por meio de um túnel IPSec para o gateway remoto. Esse gateway remoto é um ESG na instância do VCS. Nos gateways, as rotas são configuradas enviando todos os intervalos de IP do cluster e do serviço para o contêiner do strongSwan e todos os endereços BYOIP do VCS para o ESG. Os endereços IP de destino dos gateways são o endereço IP móvel privado do serviço de balanceador de carga que é designado ao contêiner do strongSwan e ao endereço IP móvel privado do ESG.
- **Rotas estáticas e NAT**.
- **Peering do BGP** - o peering do BGP não é uma oferta padrão no {{site.data.keyword.cloud_notm}} e deve ser solicitado e aprovado. Uma vez ativado, o peer do BGP permite que o Calico vRouters e o ESG anunciem rotas para o BCR.

## Integração do IKS e ICP

A integração do IKS e ICP usa a conectividade de VPN strongSwan com um contêiner do strongSwan no ICP e IKS.

## Alocação de endereço IP

De uma perspectiva administrativa, a arquitetura de referência tem os intervalos de rede conceitual a seguir:
-	**Rede de pod do IKS** - todos os pods que são implementados em um nó trabalhador são designados a um endereço IP privado no intervalo 172.30.0.0/16 e são roteados somente entre os nós do trabalhador. Para evitar conflitos, não use esse intervalo de IPs em quaisquer nós que se comunicam com os nós do trabalhador. Os nós do trabalhador e os pods podem se comunicar com segurança na rede privada usando endereços IP privados. No entanto, quando um pod trava ou um nó do trabalhador precisa ser recriado, um novo endereço IP privado
é designado.
-	**Rede de serviço do IKS** - o IKS usa 172.21.0.0/16 para endereços de serviço dentro do cluster. Há dois outros intervalos de endereços IP:
    - Pública – Uma sub-rede móvel pública com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}. Esse intervalo de endereços IP é usado para expor apps à Internet via serviços ALB ou Ingress.
    - Privada – Uma sub-rede móvel privada com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}. Esse intervalo de endereços IP é usado para expor apps à rede privada via serviços ALB ou Ingress.
- **Rede de nós do trabalhador do IKS** - há dois intervalos de endereço IP de rede do nó trabalhador:
    - Pública – Uma sub-rede primária pública com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}.
    - Privada – Uma sub-rede primária privada com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}.
-	**Rede de host do VCS** - há dois intervalos de endereço IP de rede de host do VCS:
    - Pública – Uma sub-rede primária pública com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}.
    - Privada – Uma sub-rede primária privada com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}.
-	**Rede de ESG do VCS** - há dois intervalos de endereço IP de rede ESG do VCS
    - Pública – Uma sub-rede móvel pública com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}.
    - Privada – Uma sub-rede móvel privada com um intervalo de endereços IP fornecido pelo {{site.data.keyword.cloud_notm}}.
-	**Rede de VMs do VCS** - um intervalo de endereço IP corporativo que usa um intervalo BYOIP que não colide com nenhuma sub-rede fornecida pelo {{site.data.keyword.cloud_notm}}.
-	**Rede de pod do ICP ** - um intervalo de endereço IP corporativo que usa um intervalo BYOIP que não colide com nenhuma sub-rede fornecida pelo {{site.data.keyword.cloud_notm}}. Os intervalos de endereços IP de pod e de serviço podem ser configurados no cluster/config.yaml.
-	**Rede de serviço do ICP** - um intervalo de endereço IP corporativo que usa um intervalo BYOIP que não colide com nenhuma sub-rede fornecida pelo {{site.data.keyword.cloud_notm}}. Os intervalos de endereços IP de pod e de serviço podem ser configurados no cluster/config.yaml.
-	**Rede de nós do trabalhador do ICP** - um intervalo de endereço IP corporativo que usa um intervalo BYOIP que não colide com nenhuma sub-rede fornecida pelo {{site.data.keyword.cloud_notm}}.

## Fluxos de tráfego de rede

Os fluxos de tráfego a seguir são descritos:
-	Usuário externo na Internet para uma camada da web hospedada em um contêiner no IKS.
-	Usuário externo na Internet para uma camada da web hospedada em um contêiner no ICP.
-	Camada da web hospedada em um contêiner no IKS para a camada de banco de dados hospedada em uma VM no VCS.
-	A camada da web hospedada em um contêiner no ICP para a camada de banco de dados hospedada em uma VM no VCS.
-	Usuário corporativo no acesso à rede corporativa para uma VM no VCS.

### Usuário externo na Internet para uma camada da web hospedada em um contêiner no IKS

1.	O usuário externo faz uma solicitação para a camada da web usando a URL.
2.	O DNS é usado para determinar o endereço IP. Esse endereço IP é um endereço público do {{site.data.keyword.cloud_notm}} em uma sub-rede móvel que foi designada ao Serviço ALB ou Ingress.
3.	A rede pública encaminhará automaticamente a solicitação para o nó do trabalhador que hospeda o Serviço ALB ou Ingress.
4.	O nó do trabalhador encaminhará a solicitação para o endereço IP do cluster interno e o número da porta do Serviço ALB ou Ingress. Esse endereço IP do cluster interno é acessível somente dentro do cluster.
5.	Dentro do nó do trabalhador, o proxy do kube roteia a solicitação para o serviço ALB ou Ingress.
6.	Se o aplicativo estiver no mesmo nó do trabalhador, o iptables será usado para determinar qual interface interna é usada para encaminhar a solicitação. Se o aplicativo estiver em um nó trabalhador diferente, o Calico vRouter roteará para o nó do trabalhador aplicável usando o encapsulamento IP-in-IP somente se o nó do trabalhador estiver em uma sub-rede diferente.

### Usuário externo na Internet para uma camada da web hospedada em um contêiner no ICP

1.	O usuário externo faz uma solicitação para a camada da web usando a URL.
2.	O DNS é usado para determinar o endereço IP. Esse endereço IP será um endereço público do {{site.data.keyword.cloud_notm}} em uma sub-rede móvel que foi designada à Instância do VCS.
3.	A rede pública encaminhará automaticamente a solicitação para o host vSphere ESXi que hospeda o ESG.
4.	O ESG encaminhará a solicitação para o endereço IP do cluster interno e o número da porta do serviço ALB ou Ingress. O pacote IP será encapsulado em um quadro VXLAN se o ESG e o serviço ALB ou Ingress estiverem em hosts vSphere ESXi diferentes. Esse endereço IP do cluster interno é acessível somente dentro do cluster.
5.	Dentro do nó do trabalhador, o proxy do kube roteia a solicitação para o serviço ALB ou Ingress.
6.	Se o aplicativo estiver no mesmo nó do trabalhador, o iptables será usado para determinar qual interface interna será usada para encaminhar a solicitação. Se o aplicativo estiver em um nó trabalhador diferente, o Calico vRouter roteará para o nó do trabalhador aplicável usando encapsulamento IP-in-IP. O pacote IP-in-IP será encapsulado em um quadro VXLAN para transporte para o host vSphere ESXi no qual o nó do trabalhador está localizado.

### Camada da web hospedada em um contêiner no IKS para a camada de banco de dados hospedada em uma VM no VCS

Como as tabelas de rotas no ESG e vRouters são preenchidas depende do método de integração. Veja Integração do IKS e VCS.
1.	A camada da web em execução em um contêiner no IKS faz uma solicitação para um banco de dados em execução em uma VM na instância do VCS.
2.	O DNS é usado para resolver a solicitação para o endereço IP do banco de dados.
3.	O contêiner envia a solicitação para o Calico vRouter.
4.	O vRouter tem sua tabela de rotas preenchida com os intervalos de endereços IP hospedados na instância do VCS.
5.	O vRouter encaminha a solicitação, mas usa SNAT para mudar o endereço IP de origem do endereço IP do pod para o endereço IP do nó do trabalhador.
6.	O nó trabalhador que hospeda o vRouter envia a solicitação para o BCR.
7.	O BCR encaminha a solicitação para o ESG.
8.	O ESG, em seguida, encaminha para o DLR.
9.	O DLR coloca a solicitação na VXLAN necessária.
10.	A VM do banco de dados recebe a solicitação.

### Camada da web hospedada em um contêiner no ICP para a camada de banco de dados hospedada em uma VM no VCS

Como as tabelas de rotas no ESG e vRouters são preenchidas depende do método de integração. Consulte o ICP e o VCS Integration.
1.	A camada da web em execução em um contêiner no ICP faz uma solicitação para um banco de dados em execução em uma VM na mesma instância do VCS.
2.	O DNS é usado para resolver a solicitação para o endereço IP do banco de dados.
3.	O contêiner envia a solicitação para o Calico vRouter.
4.	O vRouter tem sua tabela de rotas preenchida com os intervalos de endereços IP hospedados na instância do VCS.
5.	O vRouter encaminha a solicitação, mas usa SNAT para mudar o endereço IP de origem do endereço IP do pod para o endereço IP do nó do trabalhador.
6.	O nó do trabalhador que hospeda o vRouter envia a solicitação para o ESG.
7.	O ESG, em seguida, encaminha para o DLR.
8.	O DLR coloca a solicitação na VXLAN necessária.
9.	A VM do banco de dados recebe a solicitação.

### Usuário corporativo no acesso à rede corporativa para uma VM em VCS

1.	Um usuário corporativo conectado à rede interna corporativa faz uma solicitação de um recurso que está localizado em uma VM hospedada no VCS.
2.	O DNS é usado para determinar o endereço IP da VM. Esse endereço IP está em uma rede que foi estendida para o {{site.data.keyword.cloud_notm}}.
3.	O roteador no local direciona o tráfego para o host vSphere que está hospedando o Concentrador L2.
4.	O concentrador L2 encapsula a solicitação em um túnel seguro e a encaminha para o Concentrador L2 remoto hospedado no {{site.data.keyword.cloud_notm}} usando o endereço IP da sub-rede móvel privada designado ao dispositivo, por meio do roteador local.
5.	A rota local verifica sua tabela de roteamento e discerne que o endereço IP para o Concentrador L2 remoto precisa ser enviado para a interface WAN e encaminha pela WAN, por meio do roteador XCR do {{site.data.keyword.cloud_notm}}, via BCR.
6.	O Concentrador L2 recebe a solicitação e a coloca na VXLAN que hospeda a rede estendida.
7.	A VM recebe a solicitação.

### Mais recursos

* [Rede do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [White Paper do contêiner](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (download de PDF)
* [Blog do VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Planilha de dados do VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Máximo de configuração do NSX for vSphere 6.4.3](https://configmax.vmware.com/guest)
* [Documentação da plataforma {{site.data.keyword.cloud_notm}}](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [Serviço {{site.data.keyword.cloud_notm}} Kubernetes](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Projeto Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
