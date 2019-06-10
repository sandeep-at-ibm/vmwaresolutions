---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Preguntas frecuentes sobre servidores ESXi
{: #faq_esxi}

Encuentre las respuestas a preguntas frecuentes sobre los servidores ESXi que se gestionan en la consola de {{site.data.keyword.vmwaresolutions_full}}.

## ¿Cuántos servidores ESXi puedo añadir a mi instancia?
{: #faq_esxi-instance}
{: faq}

La instancia de vCenter Server le permite expandir el clúster predeterminado para tener hasta 51 servidores ESXi. Cada uno de los clústeres no predeterminados se puede ampliar hasta tener un máximo de 59 servidores ESXi. Dado que puede añadir hasta 10 clústeres a una instancia, cada instancia desplegada puede tener un máximo de 51 + 9x59 = 582 servidores ESXi en todos los clústeres.

## ¿Cuántos servidores ESXi puedo añadir a un clúster?
{: #faq_esxi-cluster}
{: faq}

Para instancias desplegadas en V2.2 y posteriores, puede añadir un máximo de 51 servidores ESXi a un clúster inicial y un máximo de 59 servidores ESXi a clústeres añadidos.

Para instancias desplegadas en V2.1 o anteriores, debe habilitar el soporte de vSAN necesario para aumentar el tamaño del clúster por encima de 32. Siga los pasos siguientes para habilitar el soporte de vSAN necesario:

1. En cada servidor ESXi desplegado, ejecute los mandatos siguientes:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Reinicie cada servidor ESXi. Para obtener más información, consulte [Creación de un clúster vSAN 6.x con un máximo de 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Es posible que tenga que aumentar el tamaño de vCenter Server para dar cabida a las máquinas virtuales añadidas y servidores ESXi.
4. Abra una incidencia de soporte de IBM para indicar que ha aplicado los cambios de vSAN manualmente completando los pasos 1 al 3. En la incidencia, solicite que la instancia actualizada esté habilitada para servidores ESXi más allá de 32.

## ¿Puedo cambiar las direcciones IP y los nombres de los servidores ESXi?
{: #faq_esxi-change-name-ip}
{: faq}

Los nombres de servidor de ESXi y las direcciones IP no se pueden cambiar porque están registrados para la resolución de DNS de Windows. Los cambios podrían dar lugar a errores durante el despliegue o a errores en funciones de vCenter Server.

No utilice la característica **Renombrar dispositivo** en la interfaz de usuario de {{site.data.keyword.cloud_notm}} para cambiar los nombres de servidor de ESXi. Esta función cambia el FQDN del servidor ESXi, pero los registros de vCenter Server y del host de la VSI de Windows serán incorrectos y podrían provocar anomalías.
{:note}

## ¿Puedo inhabilitar el acceso raíz de mis servidores ESXi?
{: #faq_esxi-disable-root}
{: faq}

Se recomienda mantener el acceso raíz habilitado en los servidores ESXi; de lo contrario podrían producirse anomalías en las funciones de {{site.data.keyword.vmwaresolutions_short}}.

Si es necesario, puede inhabilitar el acceso raíz después de que los servidores ESXi alcancen el estado **Listo para su uso** en la consola de {{site.data.keyword.vmwaresolutions_short}}.

Debe volver a habilitar el acceso raíz para las operaciones de automatización posteriores, por ejemplo al añadir o eliminar comparticiones de archivos o al instalar servicios adicionales, como por ejemplo Zerto on {{site.data.keyword.cloud_notm}}.

## ¿Puedo añadir rutas estáticas en mis servidores ESXi para montar el almacenamiento de otras ubicaciones?
{: #faq_esxi-static-routes}
{: faq}

Puede añadir rutas estáticas para el almacenamiento, pero debe hacerlo con extrema precaución. De lo contrario, se podrían desmontar las comparticiones existentes.

No se da soporte a la adición de rutas estáticas para vMotion. Los cambios en la configuración de subred de vMotion podrían provocar anomalías en las funciones de {{site.data.keyword.vmwaresolutions_short}}.
{:note}

## Enlaces relacionados
{: #faq_esxi-related}

* [Ampliación y reducción de la capacidad para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_addingviewingclusters#vc_hybrid_addingviewingclusters)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
