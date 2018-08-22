---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-17"

---

# Preguntas frecuentes sobre servidores ESXi

Encuentre las respuestas a preguntas frecuentes sobre los servidores ESXi que se gestionan en la consola de {{site.data.keyword.vmwaresolutions_full}}.

## ¿Cuántos servidores ESXi puedo añadir a mi instancia?

* Para instancias de vCenter Server, puede expandir el clúster predeterminado para tener hasta 51 servidores ESXi. Cada uno de los clústeres no predeterminados se puede ampliar hasta tener un máximo de 59 servidores ESXi. Dado que puede añadir hasta 10 clústeres a una instancia, cada instancia desplegada puede tener un máximo de 51 + 9x59 = 582 servidores ESXi en todos los clústeres.
* Para instancias de Cloud Foundation, la configuración estándar tiene cuatro servidores ESXi. Puede añadir un máximo de 28 servidores (hasta un total de 32 servidores). Para las instancias de Cloud Foundation de una configuración de varios sitios, puede tener un máximo de 128 servidores ESXi en todas las instancias.

  **Nota**: si la configuración de Cloud Foundation requiere un despliegue de varios sitios con más de 128 servidores ESXi, [póngase en contacto con el equipo de soporte de IBM](trbl_support.html) para obtener ayuda.

## ¿Cuántos servidores ESXi puedo añadir a un clúster?

Para V2.2 y releases posteriores, puede añadir un máximo de 51 servidores ESXi a un clúster inicial y un máximo de 59 servidores ESXi a clústeres adicionales.

Para instancias desplegadas en V2.1 o releases anteriores, debe habilitar el soporte de vSAN necesario para aumentar el tamaño del clúster por encima de 32. Siga los pasos siguientes para habilitar el soporte de vSAN necesario:

1. En cada servidor ESXi desplegado, ejecute los mandatos siguientes:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Reinicie cada servidor ESXi. Para obtener más información, consulte [Creación de un clúster vSAN 6.x con un máximo de 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Tenga en cuenta que es posible que tenga que aumentar el tamaño de vCenter Server para dar cabida a las nuevas máquinas virtuales y servidores ESXi.
4. Abra una incidencia de soporte de IBM en la que indique que ha aplicado manualmente los cambios de vSAN completando los pasos 1 a 3 y que desea habilitar su instancia actualizada para servidores ESXi adicionales por encima de 32.

## ¿Puedo cambiar las direcciones IP y los nombres de los servidores ESXi?

Las direcciones IP y los nombres de los servidores ESXi no se pueden cambiar, porque están registrados para la resolución de DNS de Windows. Los cambios podrían dar lugar a errores durante el despliegue o a errores en funciones de vCenter Server.

**Nota**: No utilice la característica **Renombrar dispositivo** en la interfaz de usuario de {{site.data.keyword.cloud_notm}} para cambiar los nombres de servidor de ESXi. Esta función cambiaría el FQDN del servidor ESXi, pero los registros de vCenter Center y del host de la VSI de Windows serían incorrectos y podrían provocar anomalías.

## ¿Puedo inhabilitar el acceso raíz de mis servidores ESXi?

Se recomienda mantener el acceso raíz habilitado en los servidores ESXi; de lo contrario podrían producirse anomalías en la funcionalidad de {{site.data.keyword.vmwaresolutions_short}}.

Si es absolutamente necesario, puede inhabilitar el acceso raíz después de que los servidores ESXi alcancen el estado **Listo para su uso** en la consola de {{site.data.keyword.vmwaresolutions_short}}.

Debe volver a habilitar el acceso raíz para las operaciones de automatización posteriores, por ejemplo al añadir o eliminar comparticiones de archivos o al instalar servicios adicionales, como por ejemplo Zerto on {{site.data.keyword.cloud_notm}}.

## ¿Puedo añadir rutas estáticas en mis servidores ESXi para montar el almacenamiento de otras ubicaciones?

Se pueden añadir rutas estáticas para almacenamiento, pero las operaciones deben realizarse con sumo cuidado. De lo contrario, se podrían desmontar las comparticiones existentes.

**Nota**: no se da soporte a la adición de rutas estáticas para vMotion. Los cambios en la configuración de subred de vMotion podrían provocar anomalías en la funcionalidad de {{site.data.keyword.vmwaresolutions_short}}.

### Enlaces relacionados

* [Ampliación y reducción de la capacidad para instancias de vCenter Server](../vcenter/vc_addingremovingservers.html)
* [Ampliación y reducción de la capacidad para instancias de Cloud Foundation](../sddc/sd_addingremovingservers.html)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](../vcenter/vc_addingviewingclusters.html)
* [Adición, visualización y supresión de clústeres para instancias de Cloud Foundation](../sddc/sd_addingviewingclusters.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](trbl_support.html)
