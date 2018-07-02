---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Considerações de rede para instâncias do VMware Federal

Revise as informações a seguir para obter detalhes sobre as considerações de rede e os requisitos para suas instâncias do VMware Federal. Assegure-se de que atenda aos requisitos para que sua instância funcione corretamente.

## Componentes de rede para instâncias do VMware Federal

Para revisar os componentes de rede que estão incluídos em sua instância do VMware Federal, veja [Componentes da instância do vCenter Server para o VMware Federal on IBM Cloud](vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud).

## Considerações do NSX Firewall

Se estiver usando NSX Distributed Firewalls (DFW), revise os requisitos a seguir:
* Deve-se configurar regras para todas as comunicações da máquina virtual (VM) do {{site.data.keyword.IBM}} CloudDriver para permitir que todos os protocolos se comuniquem nos endereços IP `10.0.0.0/8` e `161.26.0.0/16`.
* Deve-se criar uma regra de DFW que permita tráfego HTTPS da VM do IBM CloudDriver para qualquer destino.
* A regra de DFW deve vir antes de quaisquer outras regras que bloqueariam o tráfego de ou para essas VMs.

## Usando NSX com suas máquinas virtuais

Durante a implementação da instância do VMware Federal, o VMware NSX é pedido, instalado, licenciado e configurado em sua instância. Além disso, o NSX Manager, os NSX Controllers e o NSX Transport Zone são configurados e cada servidor ESXi é configurado com os componentes do NSX.

Um NSX Edge Services Gateway também é implementado para ser usado por suas VMs de carga de trabalho. Para obter mais informações, veja [Configurando sua rede para usar o NSX ESG gerenciado pelo cliente com suas VMs](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Considerações ao mudar senhas de componentes NSX

Revise as considerações a seguir antes de mudar as senhas para o NSX Manager, o NSX Controllers e o NSX Edges:
* Não mude a senha do NSX Manager, que pode ser localizada na página **Resumo** da instância no console do {{site.data.keyword.vmwaresolutions_short}}.
* É possível mudar senhas dos NSX Controllers. Para obter instruções sobre como mudar senhas dos NSX Controllers, veja [Mudar a senha do controlador](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* É possível mudar a senha e as configurações do SSH para o VMware NSX Edge Services Gateway (ESG) gerenciado pelo cliente. Não mude a senha para o Management VMware NSX Edge Services Gateway (ESG) e o Roteador Lógico Distribuído relacionado.

## Links relacionados

* [Visão geral do NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Gerenciando regras NAT](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
