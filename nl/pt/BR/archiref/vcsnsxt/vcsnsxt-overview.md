---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Visão geral da arquitetura geral
{: #vcsnsxt-overview}

As informações a seguir fornecem mais detalhes sobre a arquitetura de rede que é usada nesta arquitetura de referência. Ela consiste nas seções a seguir:
* **Visão geral do VMware vCenter Server on {{site.data.keyword.cloud}}** - descreve os destaques da plataforma vCenter Server.
* **Visão geral de rede** - fornece informações sobre os componentes de rede que são usados nesta arquitetura de referência:
  - **Rede do {{site.data.keyword.cloud_notm}}** - o {{site.data.keyword.cloud_notm}} fornece a rede física e ela é totalmente gerenciada pelo {{site.data.keyword.cloud_notm}}. Revise as características chave de rede do {{site.data.keyword.cloud_notm}} para entender os fluxos de rede entre no local e fora do local e entre cargas de trabalho que estão hospedadas em serviços diferentes.
  - **NSX-V** - a rede do vCenter Server é construída na rede do {{site.data.keyword.cloud_notm}} com uma sobreposição fornecida pelo VMware NSX-V. Essa sobreposição segmenta o tráfego da rede subjacente do {{site.data.keyword.cloud_notm}} que permite maior controle e configurabilidade, incluindo Bring Your Own IP (BYOIP).
  - **{{site.data.keyword.containerlong_notm}}** - o {{site.data.keyword.containerlong_notm}} usa o Calico como seu plug-in Container Network Interface.
  - **{{site.data.keyword.icpfull_notm}}** - o {{site.data.keyword.icpfull_notm}} usa o Calico como seu plug-in Container Network Interface.

* **Integração** - descreve a arquitetura dos componentes de rede para permitir os fluxos de tráfego de rede e o endereçamento necessários:
  - Alocação de endereço IP
  - Fluxos de tráfego de rede

## Visão geral do vCenter Server
{: #vcsnsxt-overview-vcs-ovw}

O VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle é uma nuvem particular hospedada que ajuda a ampliar de maneira rápida e fácil sua infraestrutura local para a nuvem para um hibridismo de infraestrutura seguro e perfeito e uma verdadeira mobilidade de aplicativo.

O vCenter Server Hybridity Bundle é implementado em um mínimo de quatro {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, oferece armazenamento dedicado por meio de uma rede de área de armazenamento virtual (VSAN) e inclui a implementação e a configuração automáticas de uma infraestrutura de rede definida por software (NSX-V) fácil de gerenciar. O vCenter Server Hybridity Bundle é uma arquitetura de referência implementada por meio de automação, assegurando consistência, desempenho e conformidade. Em muitos casos, é possível provisionar o ambiente inteiro em menos de um dia e a infraestrutura bare metal pode aumentar ou reduzir de forma rápida e elástica a capacidade de cálculo e armazenamento conforme necessário.

Há muitas opções disponíveis para aprimorar e ampliar o vCenter Server Hybridity Bundle. As ofertas de serviços do {{site.data.keyword.cloud_notm}} não incluem apenas opções de armazenamento e várias opções de conectividade WAN públicas e privadas, mas também abrangem áreas da segurança da plataforma, segurança de rede, balanceamento de carga de tráfego para backup e recuperação de desastre.

Os serviços de segurança da plataforma incluem o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, que fornece suporte automatizado de segurança e conformidade, permitindo uma melhor visibilidade e controle sobre seu ambiente de nuvem e administradores. O HyTrust DataControl on {{site.data.keyword.cloud_notm}} fornece proteção de dados com criptografia poderosa e gerenciamento de chave escalável para proteger suas cargas de trabalho em seus ciclos de vida. O {{site.data.keyword.cloud_notm}} Secure Virtualization simplifica a conformidade e protege seus dados com políticas geofencing e de criptografia e controles de acesso baseados em função, enquanto o KMIP for VMware on {{site.data.keyword.cloud_notm}}, uma oferta de gerenciamento de ciclo de vida de chave de criptografia, gerencia as chaves de criptografia usadas pelos serviços do {{site.data.keyword.cloud_notm}} ou aplicativos integrados do cliente.

As opções de segurança de rede são o FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} que provisiona um par altamente disponível de dispositivos FortiGate Security Appliance para analisar o tráfego de rede e proteger sua infraestrutura virtual e o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, que implementa um par de alta disponibilidade MVs do FortiGate no {{site.data.keyword.cloud_notm}} para reduzir o risco implementando controles de segurança crítica dentro de sua infraestrutura virtual. Mais ofertas de segurança de Rede estão em desenvolvimento.

A oferta de serviço de balanceador de carga de rede F5 on {{site.data.keyword.cloud_notm}} otimiza o desempenho e assegura a disponibilidade e a segurança de seus aplicativos mais críticos com o conjunto F5 BIG-IP.

As ofertas de backup e recuperação de desastre da IBM, do Veeam e do Zerto entregam tranquilidade e continuidade operacional caso ocorra um desastre. O IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} é uma solução de proteção de dados e de disponibilidade para ambientes virtuais. O Veeam on {{site.data.keyword.cloud_notm}} permite a disponibilidade para o Always-On Enterprise™ com backup integrado, recuperação e replicação no {{site.data.keyword.cloud_notm}}. O Zerto on {{site.data.keyword.cloud_notm}} fornece aos clientes locais e do {{site.data.keyword.cloud_notm}} uma solução de Recuperação de desastre segura, flexível e escalável.

O vCenter Server Hybridity Bundle não é um serviço gerenciado, embora seja possível incluir o IBM Managed Services para transferir as operações e manutenção diárias das camadas de virtualização, guest do S.O. ou aplicativo. A equipe do {{site.data.keyword.cloud_notm}} Professional Services também está disponível para ajudá-lo a acelerar sua jornada para a nuvem com serviços de migração, implementação, planejamento e onboarding.

As opções de integração de plataforma do vCenter Server Hybridity Bundle não estão limitadas a opções disponíveis do VMware, como o vRealize Suite ou o vSphere with Operations Management, mas abrangem múltiplas ofertas de serviço do {{site.data.keyword.cloud_notm}}, como o [vCenter Server, o {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro), o [vCenter Server e o {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro), que usam o Terraform de software livre para gerenciar e entregar a infraestrutura como código.

O extenso portfólio de serviços e as opções de integração de múltiplas ofertas disponíveis para o vCenter Server Hybridity Bundle entregam uma plataforma realmente híbrida que torna possível o Hibridismo como um Serviço.

## Links relacionados
{: #vcsnsxt-overview-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
