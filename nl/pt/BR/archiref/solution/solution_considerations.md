---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Considerações pós-implementação para sua instância do VMware

As ofertas {{site.data.keyword.vmwaresolutions_full}}, VMware vCenter Server e VMware Cloud Foundation não são serviços gerenciados. Você é responsável pela configuração, a segurança, o gerenciamento e o monitoramento de todos os componentes de software. Com acesso administrativo completo à solução, você tem grande poder e flexibilidade que requerem conhecimentos técnicos, administrativos e operacionais significativos em vários domínios. O gerenciamento de uma instância do VMware no {{site.data.keyword.cloud_notm}} requer o mesmo planejamento e conhecimento que o planejamento para uma instância no local. As tecnologias definidas por software, como o VMware NSX e o VMware vSAN, simplificam enormemente alguns aspectos do gerenciamento da instância, mas podem requerer novas qualificações e ferramentas para serem gerenciadas e operadas corretamente. A combinação do poder, da velocidade e da confiabilidade da implementação automatizada do VMware do {{site.data.keyword.cloud_notm}} com o planejamento e teste operacionais apropriados assegura uma navegação rápida e bem-sucedida para a nuvem híbrida.

Revise as considerações a seguir para entender suas responsabilidades para gerenciar e operar a instância antes e após sua implementação. 

**Nota:** a lista a seguir não é completa. Para obter mais informações, consulte [Serviços gerenciados pela IBM](../../services/managing_imi.html).

## Acesso à conta do IBM Cloud

Para gerenciar o acesso à conta do {{site.data.keyword.cloud_notm}}, permita que outros membros de sua equipe acessem sua instância no console do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, veja [Convidando usuários para acessar serviços e recursos](../../vmonic/iamuserinvite.html).

## Limitações

Familiarize-se com as seguintes limitações de sua instância:

- [Impactos na mudança de artefatos do vCenter](../../vcenter/vcenter_chg_impact.html)
- [Considerações e limitações da rede](../../vcenter/vc_networkingonvcenterserver.html)
- [Perguntas mais frequentes](../../vmonic/faq.html)

## Design e conectividade da rede

Conclua as etapas a seguir para gerenciar o acesso à rede do {{site.data.keyword.cloud_notm}} e aos componentes de gerenciamento do VMware e para planejar sua topologia de rede do {{site.data.keyword.cloud_notm}}.

- Acesse os terminais de gerenciamento da instância usando a [VPN do {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/vpn-access) ou sua [conexão de link direto do {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/direct-link).
- Conceba uma estratégia para conectividade de rede pública de dentro de sua instância. Suas opções incluem: a amostra do VMware NSX Edge Services Gateway (ESG) do cliente, dispositivos de gateway, como o Vyatta e o FortiGate, além de servidores proxy implementados na rede do {{site.data.keyword.cloud_notm}} ou em sua própria rede acessada por meio do DirectLink.
- Planeje se deve implementar sua carga de trabalho nas VLANs do {{site.data.keyword.cloud_notm}} com [endereços IP móveis do {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/subnets/getting-started.html) ou [em comutadores lógicos NSX (VXLANs) usando seus próprios endereços IP](../nsx/nsx_overview.html). Observe que o uso da rede definida por software (SDN) do NSX oferece a maior flexibilidade para gerenciar e proteger sua rede de carga de trabalho no {{site.data.keyword.cloud_notm}}.
- Use ESGs do NSX, o [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance) e o peer DirectLink para planejar a conectividade para cargas de trabalho (Conversão de endereço de rede, Rede privada virtual, roteamento).
- Se estiver implementando o Cross-vCenter NSX, assegure-se de que os intervalos de ID do segmento local não estejam sendo sobrepostos antes da implementação de cargas de trabalho locais.

## Planejamento e reforço da segurança

Você é responsável por proteger, criptografar e monitorar sua instância e cargas de trabalho do VMware para atender às normas corporativas, industriais e regulamentares. Conclua as etapas a seguir para garantir segurança adequada.

- Mude todas as senhas exibidas no console do {{site.data.keyword.vmwaresolutions_short}} e use seu próprio sistema de gerenciamento de senha. Observe que a IBM retém IDs de usuário distintos necessários para automação e suporte contínuos.
- Revise as políticas de senha, como complexidade e período de expiração, em todos os componentes.
- Revise as configurações de criptografia em todos os componentes.
- Planeje e implemente soluções apropriadas de firewall físico ou virtual, como o NSX Distributed Firewall (DFW), NSX ESGs, o [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html) e o [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance).
- Planeje e implemente soluções apropriadas de balanceamento de carga e segurança do aplicativo, como o [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html).
- Planeje e implemente soluções apropriadas de informações de segurança e gerenciamento de eventos (SIEM), como o [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence).
- Planeje e implemente a varredura de vulnerabilidade apropriada.
- Planeje e implemente o gerenciamento de mudanças, a aprovação, a auditoria e o controle de acesso apropriados para sua instância usando soluções, como o [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html).

## Customização

Conclua as etapas a seguir para customizar a instalação da instância base do VMware para atender aos seus requisitos.

- Use sua própria autoridade de certificação (CA) para gerar certificados para componentes, como o vCenter, o VMware Platform Services Controller (PSC) e o NSX Manager.
- Configure os serviços implementados. Por exemplo:
  - Para o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, configure as definições de integração do AD, de controle de acesso, do Simple Mail Transfer Protocol (SMTP) e as políticas de conformidade.
  - Para o Zerto on {{site.data.keyword.cloud_notm}}, planeje o endereçamento IP e o roteamento das comunicações do Zerto Virtual Replication Appliance (VRA), uma vez que a passagem do network address translator (NAT) não é suportada. Considere o tunelamento ou a reimplementação de seus VRAs para endereçamento e roteamento apropriados.
  - Para serviços de backup, como o Veeam on {{site.data.keyword.cloud_notm}} e o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}, configure sua tarefa de backup, configure opcionalmente o armazenamento adicional e configure os alertas de monitoramento.
  - Para serviços de rede e de segurança, como o F5 on {{site.data.keyword.cloud_notm}} e o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, configure interfaces de rede, certificados, configuração de alta disponibilidade (HA) e regras de acordo com sua topologia de rede e outros requisitos.

## Active Directory

Conclua as etapas a seguir para assegurar configuração e gerenciamento adequados da conexão única (SSO).

- Configure a atualização do servidor Active Directory (AD) e o planejamento de reinicialização.
- Se você tiver escolhido a opção de implementar servidores AD no cluster do vSphere, forneça o licenciamento e a ativação do Microsoft Windows para os servidores, para assegurar conformidade e disponibilidade.
- Estabeleça confiança mútua entre a instância e seu servidor AD no local.
- Integre a VPN do NSX, se aplicável, com a SSO do AD.
- Integre hosts ESXi com a SSO do AD.

## Planejamento de manutenção

Conclua as etapas a seguir para assegurar planejamento adequado para manutenção do software.

- Configure o VMware Update Manager (VUM) por meio de um proxy para obter atualizações do VMware.
- Se aplicável, configure o vSAN por meio de um proxy para manter o banco de dados do vSAN Hardware Compatibility List (HCL).
- Planeje manutenção regular para componentes do VMware não suportados pelo VUM. Por exemplo, VMware vCenter, PSC e NSX.
- Revise a configuração do vSphere Enhanced vMotion Compatibility (EVC). É possível que seu cluster não esteja configurado com o EVC ativado se a versão atual do vSphere não suportar o EVC para o seu nível de hardware.
- Planeje manutenção regular para serviços complementares, como o Veeam on {{site.data.keyword.cloud_notm}}, o Zerto on {{site.data.keyword.cloud_notm}} e o F5 on {{site.data.keyword.cloud_notm}}.

## Monitoramento

Assegure-se de planejar e implementar as soluções a seguir para monitorar sua instância e os componentes da instância.

- Um servidor de criação de log que inclui encaminhamento ou coleta de log para todos os componentes da instância e retenção adequada de log.
- Uma infraestrutura de alerta, incluindo a configuração do servidor SMTP e o gateway de Serviço de mensagens curtas (SMS), conforme necessário.
- Monitoramento proativo de hosts, unidades, software de gerenciamento e rede.
- Monitoramento do vSAN, se aplicável.
- Monitoramento e planejamento de capacidade. É possível [incluir e remover clusters](../../vcenter/vc_addingviewingclusters.html) e [incluir e remover hosts](../../vcenter/vc_addingremovingservers.html) de sua instância do console do {{site.data.keyword.vmwaresolutions_short}}.
- Monitoramento de sua infraestrutura de backup e tarefas de backup.

## Continuidade e disponibilidade de negócios

Sua instância do VMware está em execução nos Bare Metal Servers no {{site.data.keyword.cloud_notm}}. Conclua as etapas a seguir para assegurar-se de fazer planos adequados para alta disponibilidade e continuidade de negócios.

- Revise a configuração do vSphere HA e do vSphere Distributed Resource Scheduler (DRS) com relação a seus requisitos.
- Revise a configuração de controle de E/S da rede e do armazenamento com relação a seus requisitos.
- Configure a ordem de inicialização da máquina com relação a seus requisitos.
- Configure os conjuntos de recursos, conforme necessário, para gerenciamento e carga de trabalho.
- Planeje, implemente e monitore uma solução de backup para [componentes de gerenciamento da instância](solution_backingup.html) e carga de trabalho.
- Planeje a alta disponibilidade do gerenciamento de instância, incluindo a possibilidade de várias instâncias, vários clusters, vCenter HA e PSC HA.
- Planeje a continuidade de negócios para suas cargas de trabalho usando soluções, como o [Zerto Disaster Recovery](../../services/addingzertodr.html), o [backup e a replicação do Veeam](../../services/veeam_considerations.html) e o [IBM Spectrum Protect Plus](../../services/spp_considerations.html).

## Planejamento de armazenamento

Além do planejamento da capacidade, conclua o seguinte para assegurar-se de que sua configuração de armazenamento atenda seus requisitos de desempenho e disponibilidade.

- O desempenho do armazenamento depende de vários fatores, incluindo configuração do RAID e striping de disco; configuração de rede; tamanho do bloco; IOPS (operações de entrada/saída por segundo) configurado para armazenamento conectado à rede; configuração de hardware da VM e método de conexão de armazenamento; métodos de agrupamento e replicação; uso de políticas de armazenamento, como criptografia, deduplicação e compactação. Tempo de planejamento para testar e ajustar sua configuração para atender a suas necessidades de desempenho de armazenamento.
- Revise sua política de armazenamento do vSAN
  - O RAID-1 fornece melhor desempenho e janelas menores de suscetibilidade a falhas sequenciais, como tempo de reconstrução mais curto, do que o RAID-5. No entanto, o RAID-5 tem menos sobrecarga de armazenamento.
  - O RAID-6 fornece proteção contra falhas duplas, mas requer um mínimo de seis hosts em comparação com quatro hosts para o RAID-5.
- Para incluir mais armazenamento no cluster vSAN, deve-se incluir novos hosts no cluster ou incluir o armazenamento NFS do {{site.data.keyword.cloud_notm}} Endurance como alternativa. A inclusão de discos em hosts existentes não é suportada atualmente.
- Se você montar armazenamento NFS adicional do {{site.data.keyword.cloud_notm}} Endurance para seu cluster, assegure-se de seguir a orientação de arquitetura e configurar rotas do host para o armazenamento usando os endereços do grupo de portas `SDDC-DPortGroup-NFS`. Deve-se autorizar esses endereços, em vez dos próprios hosts, para o armazenamento. Para obter mais informações, consulte [Gerenciamento de infraestrutura de armazenamento conectado](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing). Consulte também a orientação do developerWorks mostrando como [incluir mais armazenamento do Endurance no cluster VMware](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/) usando o IBM Spectrum Protect Plus, como um exemplo.

### Links relacionados

* [ Visão geral da solução ](solution_overview.html)
* [ Visão geral do design ](design_overview.html)
* [ Capacidade de Escalação ](solution_scaling.html)

