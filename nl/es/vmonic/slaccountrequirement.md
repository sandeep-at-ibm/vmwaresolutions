---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisitos para la cuenta de infraestructura de IBM Cloud
{: #slaccountrequirement}

Para utilizar {{site.data.keyword.vmwaresolutions_full}} para solicitar instancias, debe tener una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}. El coste de los componentes que se solicitan en las instancias se factura a dicha cuenta de {{site.data.keyword.cloud_notm}}.

## Permisos para la cuenta de infraestructura de IBM Cloud
{: #slaccountrequirement-permissions}

La cuenta de infraestructura de {{site.data.keyword.cloud_notm}} que utilice debe tener ciertos permisos para poder solicitar componentes en sus instancias y realizar operaciones en su nombre. Los requisitos sobre permisos se aplican a todos los tipos de instancias y servicios que solicite desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

Los usuarios autorizados pueden verificar y actualizar los permisos para una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} en el {{site.data.keyword.slportal}}. Para obtener más información, consulte [Edición de los permisos del portal de clientes de un usuario](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}.

Tabla 1. Permisos necesarios para la cuenta de infraestructura de {{site.data.keyword.cloud_notm}}

| Permiso         | Detalles                                 |
|:------------------ |:--------------------------------------- |
| Añadir servidor | Este permiso es necesario para las siguientes operaciones: para solicitar los {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} en los que se ejecuta VMware ESXi y para suministrar los servidores virtuales por hora que se utilizan para las operaciones de configuración, mantenimiento y soporte de la instancia. |
| Cancelar servidor | Este permiso es necesario para liberar y reclamar los {{site.data.keyword.baremetal_short}} en los que ejecuta VMware ESXi. Si suprime su instancia, los componentes solicitados se liberan automáticamente en la secuencia correcta de dependencia. |
| Ver detalles del servidor virtual | Este permiso es necesario para recuperar detalles de suministro del servidor, que se necesitan para la validación de pedidos y para la configuración automática. |
| Añadir almacenamiento | Este permiso es necesario para solicitar almacenamiento de seguridad y almacenamiento compartido para la instancia. |
| Gestionar almacenamiento | Este permiso es necesario para gestionar el almacenamiento de seguridad y el almacenamiento compartido para la instancia. |
| Cortafuegos de hardware | Este permiso es necesario para editar o para ver archivos de registro de cortafuegos para el servicio Fortinet on {{site.data.keyword.cloud_notm}}, si está instalado en su instancia. |
| Añadir sistema con puerto de red pública | Este permiso es necesario para solicitar hardware y VSI (instancias de servidor virtual) con puertos de red pública. |
| Añadir direcciones IP | Este permiso es necesario para solicitar rangos de subredes privadas portátiles en su nombre, lo cual es necesario para gestionar las máquinas virtuales que se ejecutan en un clúster de vSphere. Cuando se añaden más servicios a la instancia, las direcciones IP privadas portátiles se están asignados a asignan a los servidores VMware ESXi para aislar y asignar el ancho de banda. |
| Añadir incidencias | Este permiso es necesario para abrir incidencias de servicio en su nombre. Pueden crearse incidencias para las siguientes operaciones: para iniciar operaciones de restauración y para iniciar procesos de resolución de problemas automáticamente cuando se encuentran problemas. |
| Editar incidencias | Este permiso es necesario para editar las incidencias de servicio creadas en su nombre. |
| Ver incidencias | Este permiso es necesario para supervisar las incidencias de servicio relacionadas con los componentes de su instancia en relación con problemas y retrasos de suministro de la infraestructura de {{site.data.keyword.cloud_notm}}. |
| Ver detalles de hardware | Este permiso es necesario para recuperar detalles de hardware, que se necesitan para la validación de pedidos y para la configuración automática. |
| Rearrancar/Controlar | Este permiso es necesario para apagar el hardware durante el proceso de cancelación de hardware al suprimir una instancia. |
| Ver licencias | Este permiso es necesario para recuperar y validar las licencias que utiliza su instancia. |
| Ver contraseñas | Este permiso es necesario para poder administrar las VSI solicitadas. |
| Gestionar supervisión de servidor | Este permiso no es necesario realizar un pedido, pero sí que se necesita para recuperar y validar el estado de supervisión de los {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} en los que se ejecutan los servidores VMware ESXi en la instancia. |

## VRF con puntos finales de servicio habilitados
{: #slaccountrequirement-vrf-se}

Su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} debe ser una cuenta de direccionamiento virtual y reenvío (VRF) con puntos finales de servicio habilitados. Si su cuenta no es VRF, debe convertirla en una cuenta VRF. Además, debe habilitar su cuenta VRF para el uso de puntos finales de servicio.

Para obtener más información, consulte:
* [Visión general de VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Habilitación de la cuenta para el uso de puntos finales de servicio](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## Fin del soporte para la expansión de VLAN
{: #slaccountrequirement-vlan-eos}

A partir de agosto de 2019, ya no habrá soporte para la expansión de VLAN. Antes de finales de julio de 2019, debe convertir su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} a VRF y habilitar los puntos finales de servicio.
{:important}

## Enlaces relacionados
{: #slaccountrequirement-related}

* [Requisitos para las instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Cuenta de usuario y valores](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [Visión general de VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
