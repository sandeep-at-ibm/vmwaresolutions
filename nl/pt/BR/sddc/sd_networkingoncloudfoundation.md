---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:faq: data-hd-content-type='faq'}

# Considerações de rede para instâncias do Cloud Foundation
{: #sd_networkingoncloudfoundation}

Revise as informações a seguir para obter detalhes sobre as considerações de rede e os requisitos para suas instâncias do Cloud Foundation. Assegure-se de que atenda aos requisitos para que sua instância funcione corretamente.

## Componentes de rede para instâncias do Cloud Foundation
{: #sd_networkingoncloudfoundation-networking-components}
{: faq}

Para revisar os componentes de rede que estão incluídos em sua instância do Cloud Foundation, veja [Especificações técnicas para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances).

## Considerações de firewall
{: #sd_networkingoncloudfoundation-firewall-considerations}

Caso esteja usando firewalls, deve-se configurar regras para todas as comunicações por meio da instância de servidor virtual (VSI) do {{site.data.keyword.IBM}} CloudDriver e das máquinas virtuais (MVs) do SDDC Manager. Essas regras devem permitir que todos os protocolos se comuniquem nos endereços IP `10.0.0.0/8` e `161.26.0.0/16`. Exemplos desses firewalls são os NSX Distributed Firewalls (DFW) ou os firewalls Vyatta.

## Usando o VMware NSX com suas MVs
{: #sd_networkingoncloudfoundation-using-nsx-with-vm}

Durante a implementação de instâncias do Cloud Foundation, o VMware NSX é pedido, instalado, licenciado e configurado em sua instância. Além disso, o NSX Manager, os NSX Controllers e o NSX Transport Zone são configurados e cada servidor ESXi é configurado com os componentes do NSX.

No entanto, se as MVs de carga de trabalho precisarem se comunicar entre si e acessar a Internet, será sua responsabilidade configurar o NSX para uso pelas MVs.

Para obter mais informações sobre como configurar o NSX, consulte os seguintes tópicos:
* Para uma instância primária (única) do Cloud Foundation, veja [Configurando o NSX para MVs de carga de trabalho no VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Para uma instância multissite do Cloud Foundation, veja [Conectar de forma segura suas cargas de trabalho privadas do VMware no {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.

## Considerações ao mudar senhas para componentes NSX
{: #sd_networkingoncloudfoundation-considerations-when-change-nsx-component-password}

Revise as considerações a seguir antes de mudar as senhas para o NSX Manager, NSX Controllers e NSX Edge:
* Não mude a senha do NSX Manager. É possível localizar essa senha na página **Resumo** da instância no console do {{site.data.keyword.vmwaresolutions_short}}.
* É possível mudar senhas dos NSX Controllers. Para obter instruções sobre como mudar senhas dos NSX Controllers, veja [Mudar a senha do controlador](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Não mude a senha para o VMware NSX Edge Services Gateway (ESG) de gerenciamento.

## Links relacionados
{: #sd_networkingoncloudfoundation-related}

* [Visão geral do NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [Gateway de Serviços de Edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Gerenciando regras NAT](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
