---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-11"

---

{:faq: data-hd-content-type='faq'}

# Consideraciones sobre red para instancias de vCenter Server con el paquete híbrido (Hybridity)

Revise la siguiente información para obtener detalles sobre las consideraciones y requisitos de red para las instancias de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity). Asegúrese de cumplir los requisitos para que la instancia funcione correctamente.

## Componentes de red para instancias de vCenter Server con el paquete híbrido (Hybridity)
{: faq}

Para revisar los componentes de red que se incluyen en la instancia del vCenter Server con el paquete híbrido (Hybridity), consulte [Especificaciones técnicas para la instancia de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_overview.html#technical-specifications-for-vcenter-server-with-hybridity-bundle-instances).

## Consideraciones sobre cortafuegos

Si utiliza cortafuegos, debe configurar reglas para todas las comunicaciones desde la Instancia de servidor virtual (VSI) de {{site.data.keyword.IBM}} CloudDriver y las máquinas virtuales (VM) de SDDC Manager. Estas reglas deben permitir que todos los protocolos se comuniquen en las direcciones IP `10.0.0.0/8` y `161.26.0.0/16`. Los ejemplos de estos cortafuegos son NSX Distributed Firewalls (DFW) o cortafuegos Vyatta.

## Utilización de NSX con máquinas virtuales

Durante el despliegue de la instancia de vCenter Server, VMware NSX se solicita, se adquiere una licencia del mismo, se instala y se configura en la instancia. Además, se configuran NSX Manager, controladores NSX y NSX Transport Zone y cada servidor ESXi se configura con componentes de NSX.

También se despliega una NSX Edge Services Gateway para que la utilicen las máquinas virtuales (VM) de carga de trabajo. Para obtener más información, consulte [Configuración de la red para que utilice la ESG NSX gestionada por el cliente con las VM](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Consideraciones al cambiar contraseñas para los componentes de NSX

Revise las siguientes consideraciones antes de cambiar las contraseñas de NSX Manager, controladores NSX y NSX Edges:
* No cambie la contraseña de NSX Manager que encontrará en la página **Resumen** de la instancia en la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Puede cambiar las contraseñas de los controladores NSX. Para ver instrucciones sobre cómo cambiar las contraseñas de los controladores NSX, consulte [Cambio de la contraseña del controlador](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Puede cambiar la contraseña y los valores de SSH de la Edge Services Gateway (ESG) de NSX de VMware gestionada por el cliente. No cambie la contraseña de la Edge Services Gateway (ESG) de NSX de VMware de gestión ni el direccionador lógico distribuido relacionado.

### Enlaces relacionados

* [Visión general de NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Gestión de reglas de NAT](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
* [Visión general de VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)
