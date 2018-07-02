---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Considerações de rede para instâncias do Cloud Foundation

Revise as informações a seguir para obter detalhes sobre as considerações de rede e os requisitos para suas instâncias do Cloud Foundation. Assegure-se de que atenda aos requisitos para que sua instância funcione corretamente.

## Componentes de rede para instâncias do Cloud Foundation

Para revisar os componentes de rede que estão incluídos em sua instância do Cloud Foundation, veja [Componentes de instâncias do Cloud Foundation](sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

## Considerações de firewall

Se estiver usando NSX Distributed Firewalls (DFW), revise os requisitos a seguir:
* Deve-se configurar regras para todas as comunicações do {{site.data.keyword.IBM}} CloudDriver e de máquinas virtuais (VMs) do SDDC Manager para permitir que todos os protocolos se comuniquem nos endereços IP `10.0.0.0/8` e `161.26.0.0/16`.
* Deve-se criar uma regra de DFW que permita tráfego HTTPS da VM do IBM CloudDriver para qualquer destino.
* A regra de DFW deve vir antes de quaisquer outras regras que bloqueariam o tráfego de ou para essas VMs.

## Usando o VMware NSX com suas VMs

Durante a implementação de instâncias do Cloud Foundation, o VMware NSX é pedido, instalado, licenciado e configurado em sua instância. Além disso, o NSX Manager, os NSX Controllers e o NSX Transport Zone são configurados e cada servidor ESXi é configurado com os componentes do NSX.

No entanto, se suas VMs de carga de trabalho precisarem se comunicar umas com as outras e precisarem acessar a Internet, será sua responsabilidade configurar o NSX para ser usado por suas VMs.

Para obter informações sobre como configurar o NSX:
* Para uma instância primária (única) do Cloud Foundation, veja [Configurando o NSX para VMs de carga de trabalho no VMware Cloud Foundation no IBM Cloud](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Para uma instância de vários sites do Cloud Foundation, veja [Conectar com segurança suas cargas de trabalho privadas do VMware no IBM Cloud](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Considerações ao mudar senhas de componentes NSX

Revise as considerações a seguir antes de mudar as senhas para o NSX Manager, NSX Controllers e NSX Edge:
* Não mude a senha do NSX Manager. É possível localizar essa senha na página **Resumo** da instância no console do {{site.data.keyword.vmwaresolutions_short}}.
* É possível mudar senhas dos NSX Controllers. Para obter instruções sobre como mudar senhas dos NSX Controllers, veja [Mudar a senha do controlador](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Não mude a senha para o VMware NSX Edge Services Gateway (ESG) de gerenciamento.

## Links relacionados

* [Visão geral do NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway]( https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Gerenciando regras NAT](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
