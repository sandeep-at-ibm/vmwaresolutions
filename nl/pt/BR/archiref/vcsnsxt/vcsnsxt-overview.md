---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Visão geral da arquitetura

Esta seção fornece mais detalhes sobre a arquitetura de rede que é usada nesta arquitetura de referência. Ela consiste nas seções a seguir:
* **Visão geral do VCS** - essa seção descreve os destaques da plataforma VCS.
* **Visão geral da rede** - essas seções fornecem informações sobre os componentes de rede que são usados nesta arquitetura de referência:
  - **Rede do IBM Cloud** - o {{site.data.keyword.cloud}} fornece a rede física e é totalmente gerenciado pelo {{site.data.keyword.cloud_notm}}. Essa rede tem algumas características chave que precisam ser entendidas para entender os fluxos de rede entre no local e fora do local e entre cargas de trabalho que são hospedadas em serviços diferentes.
  - **NSX-V** - a rede VCS é construída sobre a rede {{site.data.keyword.cloud_notm}} com uma sobreposição fornecida pelo VMware NSX-V. Essa sobreposição segmenta o tráfego da rede subjacente do {{site.data.keyword.cloud_notm}} permitindo maior controle e configurabilidade, incluindo BYOIP.
  - **IBM Kubernetes Service** - o IKS usa o Calico como seu plug-in da Interface de Rede do Contêiner.
  - **IBM Cloud Private** - o ICP usa o Calico como seu plug-in da Interface de Rede do Contêiner.

* **Integração** – essa seção descreve a arquitetura dos componentes de rede para permitir os fluxos e o endereçamento de tráfego de rede necessários:
  - Alocação de endereço IP
  - Fluxos de tráfego de rede

## Visão geral do VCS

O VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle (VCS) é uma nuvem particular host que ajuda a ampliar de forma rápida e fácil sua infraestrutura no local para a nuvem para hibridismo de infraestrutura seguro e contínuo e a verdadeira mobilidade de aplicativo.

O VCS Hybridity Bundle é implementado sobre um mínimo de quatro {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, oferece armazenamento dedicado por meio de uma rede de área de armazenamento virtual (VSAN) e inclui a implementação e a configuração automáticas de uma infraestrutura de rede definida por software (NSX-V) fácil de gerenciar. O VCS Hybridity Bundle é uma arquitetura de referência implementada por meio de automação, que assegura consistência, desempenho e conformidade. Em muitos casos, o ambiente inteiro pode ser provisionado em menos de um dia e a infraestrutura bare metal pode escalar de forma rápida e elástica a capacidade de cálculo e armazenamento para cima e para baixo, conforme necessário.

Muitas opções estão disponíveis para aprimorar e ampliar o VCS Hybridity Bundle. As ofertas de serviços do {{site.data.keyword.cloud_notm}} não incluem apenas opções de armazenamento e várias opções de conectividade WAN públicas e privadas, mas também abrangem áreas de segurança da plataforma, segurança de rede, balanceamento de carga de tráfego para backup e recuperação de desastre.

Os serviços de segurança da plataforma incluem o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, que fornece suporte automatizado de segurança e conformidade, permitindo uma melhor visibilidade e controle sobre seu ambiente de nuvem e administradores. O HyTrust DataControl on {{site.data.keyword.cloud_notm}} fornece proteção de dados com criptografia poderosa e gerenciamento de chave escalável para proteger suas cargas de trabalho em seus ciclos de vida. O {{site.data.keyword.cloud_notm}} Secure Virtualization simplifica a conformidade e protege seus dados com políticas geofencing e de criptografia e controles de acesso baseados em função, enquanto o KMIP for VMware on {{site.data.keyword.cloud_notm}}, uma oferta de gerenciamento de ciclo de vida de chave de criptografia, gerencia as chaves de criptografia usadas pelos serviços do {{site.data.keyword.cloud_notm}} ou aplicativos integrados do cliente.

As opções de segurança de rede são o FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} que provisiona um par altamente disponível de dispositivos FortiGate Security Appliance para analisar o tráfego de rede e proteger sua infraestrutura virtual e o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, que implementa um par de alta disponibilidade VMs do FortiGate no {{site.data.keyword.cloud_notm}} para reduzir o risco implementando controles de segurança crítica dentro de sua infraestrutura virtual. Ofertas de segurança de rede adicionais estão em desenvolvimento.

A oferta de serviço de balanceador de carga de rede F5 on {{site.data.keyword.cloud_notm}} otimiza o desempenho e assegura a disponibilidade e a segurança de seus aplicativos mais críticos com o conjunto F5 BIG-IP.

As ofertas de backup e recuperação de desastre da IBM, do Veeam e do Zerto entregam tranquilidade e continuidade operacional caso ocorra um desastre. O IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} é uma solução de proteção de dados e de disponibilidade para ambientes virtuais. O Veeam on {{site.data.keyword.cloud_notm}} ativa a disponibilidade para o Always-On Enterprise™ com backup, recuperação e replicação integrado no {{site.data.keyword.cloud_notm}}. O Zerto on {{site.data.keyword.cloud_notm}} fornece aos clientes locais e do {{site.data.keyword.cloud_notm}} uma solução de Recuperação de desastre segura, flexível e escalável.

O {{site.data.keyword.cloud_notm}} VCS Hybridity Bundle não é um serviço gerenciado, embora seja possível incluir o IBM Managed Services para transferir as operações e manutenção diárias das camadas de virtualização, Guest do S.O. ou aplicativo. A equipe do {{site.data.keyword.cloud_notm}} Professional Services também está disponível para ajudá-lo a acelerar sua jornada para a nuvem com serviços de migração, implementação, planejamento e onboarding.

As opções de integração da plataforma do VCS Hybridity Bundle não estão limitadas a opções disponíveis do VMware, como vRealize Suite ou vSphere with Operations Management, mas abrangem múltiplas ofertas de serviços do {{site.data.keyword.cloud_notm}}, como [vCenter Server e IBM Kubernetes](../vcsiks/vcsiks-intro.html) e [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html), que usam o Terraform de software livre para gerenciar e entregar infraestrutura como código.

O portfólio extensivo de serviços e as opções de integração de multioferta disponíveis para o VCS Hybridity Bundle entregam uma plataforma realmente híbrida que torna possível o Hybridity como um Serviço.

### Links Relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
