---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud Visão Geral

O serviço HCX on {{site.data.keyword.cloud}} amplia perfeitamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, o que permite que você migre máquinas virtuais (VMs) para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.

Esse serviço está disponível somente para instâncias do VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle que são implementadas na V2.3 e mais recente.
{:note}

É possível fazer upgrade de sua instância do vCenter Server existente para uma instância do vCenter Server with Hybridity Bundle. Para obter mais informações sobre como fazer upgrade de sua instância e implementar o serviço HCX on {{site.data.keyword.cloud_notm}}, consulte [Procedimento para fazer upgrade para a instância do vCenter Server with Hybridity Bundle](../vcenter/vc_applyingupdates.html#procedure-to-upgrade-to-the-vcenter-server-with-hybridity-bundle-instance).

Uma instância do vCenter Server com HCX no {{site.data.keyword.cloud_notm}} é limitada a três conexões simultâneas por meio de sites no local.
{:note}

## Especificações técnicas para HCX on IBM Cloud

Os componentes a seguir são ordenados e incluídos no serviço HCX on {{site.data.keyword.cloud_notm}}.

As instâncias do HCX local incluem apenas licenciamento e ativação.
{:note}

### Um par ativo/passivo de VMware NSX Edge Services Gateways para gerenciamento do HCX

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### HCX Management Appliance-máquina virtual

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: VMDK de 60 GB

Os dispositivos HCX adicionais são implementados durante a configuração, conforme necessário, para conectividade L2, otimização de WAN e conexões de gateway.

### Rede

* Uma sub-rede móvel pública com 16 endereços IP
* Duas sub-redes portáteis privadas com 64 endereços IP
* Oito endereços IP da sub-rede vMotion móvel privada

### Licenças e taxas

* Taxa de licença base: encargo obrigatório para serviço
* Taxa de VM gerenciada: cobrada por VM que é migrada mensalmente

## Considerações ao instalar o HCX on IBM Cloud

Revise as considerações a seguir antes de tentar instalar o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos no número de servidores ESXi

O serviço HCX no {{site.data.keyword.cloud_notm}} não pode ser instalado em uma instância para a qual o cluster padrão tem mais de 51 servidores ESXi. Como o HCX no {{site.data.keyword.cloud_notm}} requer oito endereços IP na sub-rede do vMotion no cluster padrão, se o número de servidores ESXi exceder 51, nenhum endereço IP na sub-rede do vMotion estará disponível para o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos em regras de firewall

Antes de instalar o serviço HCX on {{site.data.keyword.cloud_notm}}, deve-se incluir uma regra de firewall em quaisquer firewalls existentes para permitir todo o tráfego HTTPS de saída para que o dispositivo virtual HCX Manager (HCX Manager) possa se registrar. Após a conclusão da instalação do HCX Manager, você poderá remover a regra de firewall. Além disso, deve-se configurar regras de firewall para permitir que o HCX funcione corretamente. Para obter mais informações, veja *Apêndice A - Requisitos de acesso de porta* em [Arquitetura do HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Considerações ao remover o HCX on IBM Cloud

Revise as considerações a seguir antes de remover o serviço HCX no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que as interconexões e as redes estendidas entre o site de origem no local e os sites de destino do {{site.data.keyword.cloud_notm}} sejam removidas. Para remover as interconexões e as redes estendidas, use a interface com o usuário HCX no VMware vSphere Web Client no local.
* Assegure-se de que os pares de site entre o site de origem no local e os sites de destino do {{site.data.keyword.cloud_notm}} sejam removidos. Para remover os pares de site, use a interface com o usuário HCX no VMware vSphere Web Client no local.
* A remoção do HCX no {{site.data.keyword.cloud_notm}} é automatizada. Os procedimentos a seguir são concluídos para a remoção bem-sucedida desse serviço:
   * A licença do HCX pedida para o HCX Manager do lado da nuvem é desativada.
   * O gerenciador de HCX é excluído.
   * Os endereços IP do vMotion que foram reservados para o HCX são liberados.
   * Se vazios, os conjuntos de recursos relacionados ao HCX são removidos.
   * Se vazias, as pastas relacionadas ao HCX são removidas.
   * Os dispositivos de borda de gerenciamento do HCX são excluídos.

### Links relacionados

* [Solicitando HCX no {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [Gerenciando o HCX no {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glossário de termos do HCX](hcx_glossary.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentação do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
