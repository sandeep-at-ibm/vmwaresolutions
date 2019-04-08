---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Escalado de clústeres creados fuera de la consola
{: #vs_orderingforclustersoutside}

Puede utilizar la oferta de VMware vSphere para escalar los clústeres existentes de vSphere que se han creado fuera de la consola de {{site.data.keyword.vmwaresolutions_full}}. Para escalar un clúster de vSphere que se ha creado fuera de la consola, vuelva a crear el clúster con los mismos valores con la consola y luego escale el clúster.

## Requisitos
{: #vs_orderingforclustersoutside-req}

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Ha revisado los requisitos y las consideraciones del apartado [Requisitos y planificación para VMware vSphere en {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Procedimiento para escalar clústeres creados fuera de la consola
{: #vs_orderingforclustersoutside-procedure}

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** en el panel de navegación izquierdo y pulse **VMware vSphere** en la sección **Centros de datos virtuales**.
2. En la página **VMware vSphere on IBM Cloud**, pulse **Crear**.  
   Asegúrese de que está en el separador **Crear nuevo** y de que se muestra **Nuevo clúster** en la lista **Configuraciones de clúster**.
3. Cree un clúster con los mismos valores que el clúster existente que se ha creado fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).  
   Para la interfaz de red, para escalar un clúster que se ha creado fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} debe seleccionar las VLAN existentes para el clúster.
   {:note}
4. En el panel **Resumen del pedido**, verifique la configuración del clúster y pulse **Guardar configuración**.   
5. Luego pulse **Cómo comenzar** en la tarjeta de **VMware vSphere on IBM Cloud**.
6. En la página **VMware vSphere on IBM Cloud**, pulse **Crear**.
7. Pulse el separador **Escalar existente**. En la lista **Configuraciones de clúster**, seleccione el clúster que ha creado recientemente.
8. En la sección **{{site.data.keyword.baremetal_short}}**, especifique el número de {{site.data.keyword.baremetal_short}} que desea añadir al clúster.
9. Si el clúster no incluye el par de alta disponibilidad de dispositivos de seguridad FortiGate serie 300 en su VLAN pública, puede solicitar seleccionando **Incluir con la compra** bajo **Par de alta disponibilidad de dispositivos físicos FortiGate serie 300**.
10. En el panel **Resumen del pedido**, verifique la configuración de la instancia y el coste estimado, asegúrese de que la cuenta a la que se va a realizar el cobro es correcta, revise y acepte los términos y, a continuación, pulse **Suministro**.

## Resultados
{: #vs_orderingforclustersoutside-results}

El despliegue del clúster se inicia automáticamente y el usuario recibe una confirmación por correo electrónico de que el pedido se está procesando. Cuando el clúster esté listo para ser utilizado, se le notificará por correo electrónico.

Los clústeres de vSphere no se muestran en la página **Recursos**, junto con las instancias de vCenter Server y de Cloud Foundation.
{:note}

## Enlaces relacionados
{: #vs_orderingforclustersoutside-related}

* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Solicitud de clústeres de vSphere en función de configuraciones existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Escalado de clústeres existentes de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
