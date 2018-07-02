---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Consideraciones sobre red para instancias de VMware Federal

Revise la siguiente información para obtener detalles sobre las consideraciones y requisitos de red para las instancias de VMware Federal. Asegúrese de cumplir los requisitos para que la instancia funcione correctamente.

## Componentes de red para instancias de VMware Federal

Para revisar los componentes de red que se incluyen en la instancia de VMware Federal, consulte [Componentes de una instancia de vCenter Server para VMware Federal on IBM Cloud](vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud).

## Consideraciones sobre cortafuegos NSX

Si utiliza cortafuegos distribuidos NSX (DFW), revise los siguientes requisitos:
* Debe configurar reglas para todas las comunicaciones procedentes de la máquina virtual (VM) {{site.data.keyword.IBM}} CloudDriver para permitir que todos los protocolos se comuniquen en las direcciones IP `10.0.0.0/8` y `161.26.0.0/16`.
* Debe crear una regla de DFW que permita el tráfico HTTPS entre la VM IBM CloudDriver y cualquier destino.
* La regla de DFW debe ir antes que cualquier otra regla que pueda bloquear el tráfico procedente o dirigido a estas VM.

## Utilización de NSX con máquinas virtuales

Durante el despliegue de la instancia de VMware Federal, VMware NSX se solicita, se adquiere una licencia del mismo, se instala y se configura en la instancia. Además, se configuran NSX Manager, controladores NSX y NSX Transport Zone y cada servidor ESXi se configura con componentes de NSX.

También se despliega una Edge Services Gateway NSX para que la utilizan las VM de carga de trabajo. Para obtener más información, consulte [Configuración de la red para que utilice la ESG NSX gestionada por el cliente con las VM](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Consideraciones al cambiar contraseñas para los componentes de NSX

Revise las siguientes consideraciones antes de cambiar las contraseñas de NSX Manager, controladores NSX y NSX Edges:
* No cambie la contraseña de NSX Manager que encontrará en la página **Resumen** de la instancia en la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Puede cambiar las contraseñas de los controladores NSX. Para ver instrucciones sobre cómo cambiar las contraseñas de los controladores NSX, consulte [Cambio de la contraseña del controlador](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Puede cambiar la contraseña y los valores de SSH de la Edge Services Gateway (ESG) de NSX de VMware gestionada por el cliente. No cambie la contraseña de la Edge Services Gateway (ESG) de NSX de VMware de gestión ni el direccionador lógico distribuido relacionado.

## Enlaces relacionados

* [Visión general de NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Gestión de reglas de NAT](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
