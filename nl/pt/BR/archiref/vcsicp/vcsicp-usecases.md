---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# Casos de uso

## Migração de carga de trabalho para o IBM Cloud
A Acme Skateboards deseja estender de forma contínua seu VMware SDDC no local para uma instância do VCS no IBM Cloud. Ela precisa manter seus negócios em funcionamento e manter seu tempo de inatividade para o mínimo. Reconfigurar seus aplicativos para serem executados na nuvem não é uma solução ideal.

O serviço VMware Hybridity on IBM Cloud permite a criação de conexões contínuas entre o IBM Cloud e um data center virtualizado do VMware no local.

A oferta vCenter Server with Hybridity Bundle do IBM Cloud permite conexões seguras entre o site de origem no local de mesmo nível e o site de destino do IBM Cloud.

Figura 1. VMware Hybridity Services

![VMware Hybrid Cloud Extension Services](vcsicp-hcx.svg)

Isso cria uma interconectividade fracamente acoplada entre o local e o IBM Cloud e permite recursos, como:
- **Interconectividade simples** – as conexões de rede lógica são estabelecidas facilmente sobre qualquer conexão física, incluindo a Internet pública, a VPN privada ou o IBM Cloud Direct Link.
- **Extensão da camada 2** – as redes no local são estendidas para a nuvem, incluindo sub-redes no local e endereçamento IP.
- **Criptografia** – o tráfego de rede é criptografado com segurança entre os sites do mesmo nível.
- **Otimização de rede** – seleciona a melhor conexão e inunda eficientemente a conexão para que o tráfego da rede seja movido o mais rápido possível.
- **Deduplicação de dados** – até 50% de redução no tráfego de rede pode ser alcançado.
- **Roteamento inteligente** – quando uma carga de trabalho é movida, o roteamento de proximidade pode mudar o caminho de rede (isto é, o gateway) para que o tráfego de rede use o gateway do site de destino e não "se prenda" de volta ao site de origem.
- **Migração de tempo de inatividade zero** – uma máquina virtual em execução pode ser movida para (ou voltar de) a nuvem usando o vMotion.
- **Migração planejada** – qualquer número de máquinas virtuais pode ser replicado para o site de destino e, em seguida, ativado nesse site em um tempo designado para substituir os sistemas em execução no site de origem.
- **Migração de políticas de segurança** – se o NSX for usado no local, quaisquer políticas de segurança, firewalls e assim por diante serão movidos juntamente com a carga de trabalho.

Usando essa solução, a Acme Skateboards migrou com êxito suas cargas de trabalho do VMware no local para o IBM Cloud que atendem a seus requisitos de pouco a nenhum tempo de inatividade e nenhuma reconfiguração de aplicativo.

## Implementação de arquitetura híbrida

A Acme Skateboards deseja implementar uma arquitetura híbrida no IBM Cloud que consiste no VCS e no ICP para sua jornada para a modernização de aplicativo. Seus requisitos devem executar seus bancos de dados em máquinas virtuais, os aplicativos e os serviços da web em contêineres e usar um conjunto comum de ferramentas para gerenciamento de rede e segurança.

Figura 2. Aplicativo híbrido Acme Skateboards

![Acme Skateboards Hybrid Application](vcsicp-acme-skateboards-app.svg)

O IBM Cloud for VMware Solutions fornecem automação para implementar componentes de tecnologia do VMware em data centers do IBM Cloud em todo o mundo. A arquitetura consiste em uma única região de nuvem e suporta a capacidade de se estender em mais regiões em nuvem localizadas em outra geografia e/ou em outro pod do IBM Cloud dentro do mesmo data center.

Os produtos IBM Cloud Private (ICP) e Cloud Automation Manager (CAM) são implementados manualmente em sua plataforma de virtualização no local, permitindo o gerenciamento de nuvem por meio da localização no local. Como alternativa, o ICP e o CAM são oferecidos como uma extensão de serviço para uma implementação nova ou existente do VCS, por meio da automação, permitindo o gerenciamento de nuvem do IBM Cloud.

O diagrama abaixo representa o ICP em execução sobre uma instância do VCS. O NSX-V é configurado com um comutador/VXLAN dedicado, um DLR e um ESG especificamente para a rede de sobreposição do ICP, o roteamento é configurado por meio do ESG para acesso à rede subjacente.

Usando a automação do IBM Cloud, a Acme Skateboards pode fornecer uma solução híbrida que abrange o VMware on IBM Cloud para executar suas VMs de banco de dados e o ICP no VMware on IBM Cloud para executar seus apps e serviços da web de front-end em contêineres. O NSX fornece a eles um conjunto comum de ferramentas de gerenciamento para rede e segurança na rede de sobreposição.

Figura 3. VCS com ICP

![VCS com ICP](vcsicp-virtual-icp-deployment-vcs.svg)

### Links relacionados

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
