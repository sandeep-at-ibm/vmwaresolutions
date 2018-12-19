---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# Design Detalhado

## Componentes de serviços comuns
Os serviços comuns fornecem os serviços que são usados por outros serviços na plataforma de gerenciamento de nuvem. Os serviços comuns incluem serviços de identidade e acesso, serviços de nome de domínio e serviços NTP.

Figura 1. Serviços comuns do {{site.data.keyword.cloud_notm}} Private (ICP)

![ICP Common Services](vcsicp-icp-commonservices.svg)

### Serviços de identidade e de acesso
Como parte da automação do VMware vCenter Server on {{site.data.keyword.cloud}}, um Microsoft Active Directory (AD) é empregado para Gerenciamento de Identidade. Uma única instância de servidor virtual (VSI) do AD é implementada. O vCenter está configurado para usar a autenticação do AD e é possível configurar o ICP para Autenticação LDAP.

###	Domain Name Services
A implementação do vCenter Server usa as VSIs do AD implementadas como servidores DNS para a instância. Todos os componentes implementados, como vCenter, PSC, NSX e hosts ESXi, são configurados para apontar para AD como seu DNS padrão.

###	Serviços NTP
A implementação do vCenter Server usa os servidores NTP de infraestrutura do {{site.data.keyword.cloud_notm}}. Todos os componentes implementados são configurados para usar esses servidores NTP. Ter todos os componentes dentro do design que usa os mesmos servidores NTP é crítico para que os certificados e a autenticação do AD funcionem corretamente.

## Rede

### Rede NSX-V

O NSX-V foi projetado para que uma única plataforma do gerenciador NSX-V esteja ligada a uma única instância do vCenter Server. Ele fornece serviços de rede para aplicativos que são executados dentro de um ambiente do vSphere.

Usando a rede NSX-V incluída na implementação do VCS, nós podemos implementar o ICP em uma rede de sobreposição VXLAN.

O ICP é implementado com a pilha de rede Calico padrão para Kubernetes, que fornece isolamento de rede dentro de seu cluster.

Figura 2. ICP com rede NSX-V

![ICP with NSX-V Networking](vcsicp-nsxv-networking.svg)

Para obter mais informações, consulte o [Guia de rede do vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

### Rede NSX-T

O NSX-T foi projetado para que uma única plataforma de rede possa se conectar a qualquer tipo de aplicativo, seja baseado em máquina virtual ou em contêiner, em execução dentro ou fora de um ambiente do vSphere.

O ICP fornece uma opção para substituir a rede Calico por uma instância do NSX-T, fornecendo um único local para gerenciar a rede e a segurança.

Figura 3. ICP com rede NSX-T

![ICP with NSX-T Networking](vcsicp-icp-nsxt-networking.svg)

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
