---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud Visão Geral
{: #hcx_considerations}

O serviço HCX on {{site.data.keyword.cloud}} amplia perfeitamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, o que permite que você migre máquinas virtuais (MVs) para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança. O HCX cria uma camada de abstração que permite a mobilidade de aplicativo e a hibridismo de infraestrutura por meio de redes estendidas com segurança. É possível modernizar de forma simples seu ambiente do VMware do vSphere 5.1 para a versão mais recente do vSphere sem precisar refatorar ou modificar seu aplicativo existente, pois o HCX permite essa transformação contínua. O HCX permite que você traga seus intervalos de sub-rede IP para o {{site.data.keyword.cloud_notm}} assegurando a consistência de IP por meio de uma implementação híbrida, enquanto fornece segurança de alto nível com criptografias de Conjunto B de ponta a ponta.

O HCX on {{site.data.keyword.cloud_notm}} requer que você consuma o NSX Advanced ou Enterprise por meio do {{site.data.keyword.cloud_notm}} ou de uma versão equivalente usando BYOL (Bring Your Own License). Um compromisso de 12 meses é necessário quando você pede o serviço VMware HCX on {{site.data.keyword.cloud_notm}}. Você é cobrado por 12 meses consecutivos após a implementação inicial do HCX. Quaisquer nós adicionais são incluídos dentro da data de expiração de fornecimento inicial. Depois que o compromisso de 12 meses expirar, será possível instalar e desinstalar o serviço HCX on {{site.data.keyword.cloud_notm}} e será possível incluir e remover hosts e clusters sem restrições. Sua conta será então cobrada em uma base mensal e será possível cancelar a qualquer momento.

A data de expiração do compromisso de 12 meses está disponível na página de detalhes do HCX on {{site.data.keyword.cloud_notm}}. Para obter mais informações sobre como visualizar detalhes do serviço, consulte [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

Uma instância do vCenter Server com HCX no {{site.data.keyword.cloud_notm}} é limitada a três conexões simultâneas por meio de sites no local.

O HCX on {{site.data.keyword.cloud_notm}} é suportado nas plataformas a seguir:

* vSphere 5.1 (somente linha de comandos para o vCenter 5.1 usando a API)
* vSphere 5.5 (IU do cliente da web suportado no vCenter 5.5u3 e acima.)
* vSphere 6.0
* vSphere 6.5 (o vDS deve estar em um nível 6.0)
* vSphere 6.7

## Especificações técnicas para HCX on IBM Cloud
{: #hcx_considerations-specs}

Os componentes a seguir são ordenados e incluídos no serviço HCX on {{site.data.keyword.cloud_notm}}.

As instâncias do HCX local incluem apenas licenciamento e ativação.
{:note}

### Um par ativo/passivo de VMware NSX Edge Services Gateways para gerenciamento do HCX
{: #hcx_considerations-nsx}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gerenciamento HCX - máquina virtual
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: VMDK de 60 GB

Os dispositivos HCX adicionais são implementados durante a configuração, conforme necessário, para conectividade L2, otimização de WAN e conexões de gateway.

### Rede
{: #hcx_considerations-networking}

* Uma sub-rede móvel pública com 16 endereços IP
* Duas sub-redes portáteis privadas com 64 endereços IP
* Oito endereços IP da sub-rede vMotion móvel privada

## Considerações ao instalar o HCX on IBM Cloud
{: #hcx_considerations-install}

Revise as considerações a seguir antes de tentar instalar o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos no número de servidores ESXi
{: #hcx_considerations-esxi-servers}

O serviço HCX no {{site.data.keyword.cloud_notm}} não pode ser instalado em uma instância para a qual o cluster padrão tem mais de 51 servidores ESXi. Como o HCX no {{site.data.keyword.cloud_notm}} requer oito endereços IP na sub-rede do vMotion no cluster padrão, se o número de servidores ESXi exceder 51, nenhum endereço IP na sub-rede do vMotion estará disponível para o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos em regras de firewall
{: #hcx_considerations-firewall}

Antes de instalar o serviço HCX on {{site.data.keyword.cloud_notm}}, deve-se incluir uma regra de firewall em quaisquer firewalls existentes para permitir todo o tráfego HTTPS de saída para que o dispositivo virtual HCX Manager (HCX Manager) possa se registrar. Após a conclusão da instalação do HCX Manager, você poderá remover a regra de firewall. Além disso, deve-se configurar regras de firewall para permitir que o HCX funcione corretamente. Para obter mais informações, consulte [Requisitos de acesso à porta do VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req).

## Considerações ao remover o HCX on IBM Cloud
{: #hcx_considerations-delete}

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

## Links relacionados
{: #hcx_considerations-related}

* [Solicitando HCX no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [Gerenciando o HCX no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Demonstração guiada do VMware HCX on IBM Cloud: saiba como migrar uma VM usando o HCX](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [Glossário de termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Documentação do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
