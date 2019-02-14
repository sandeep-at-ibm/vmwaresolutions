---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de clústeres de vSphere en función de configuraciones existentes

Puede solicitar un clúster de VMware vSphere en función de una plantilla de configuración que ha guardado. Siga este procedimiento para definir una nueva configuración de clúster basada en una configuración de clúster existente.

## Requisitos

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud}} en la página **Configuración**. Para obtener más información, consulte [Cuentas de usuario y valores](../vmonic/useraccount.html).
*  Ha revisado los requisitos y las consideraciones del apartado [Requisitos y planificación de clústeres de vSphere](vs_planning.html).
*  Ha creado una plantilla de configuración para reutilizar.

## Procedimiento para solicitar clústeres de vSphere en función de las configuraciones existentes

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** en el panel de navegación izquierdo y pulse **VMware vSphere** en la sección **Centros de datos virtuales**.
2. En la página **VMware vSphere on IBM Cloud**, pulse **Crear**.  
3. Pulse el separador **Crear nuevo** y seleccione una plantilla de configuración de la lista **Configuraciones de clúster**.
4. Escriba un nuevo nombre de clúster.
5. Revise los valores de clúster que se han completado automáticamente y actualice los valores según sus necesidades. Para obtener más información sobre los valores, consulte [Solicitud de clústeres nuevos de vSphere](vs_orderinginstances.html).
6. En el panel **Resumen del pedido**, verifique la configuración de la instancia y el coste estimado.
   * Para guardar la configuración como una plantilla sin realizar un pedido, pulse **Guardar configuración**.
   * Para realizar el pedido, asegúrese de que la cuenta a la que se va a realizar el cobro es correcta; revise y acepte los términos y, a continuación, pulse **Suministro**.

   Solo se instalan los {{site.data.keyword.baremetal_short}}. El usuario es el responsable de instalar y configurar los distintos componentes después del despliegue del clúster, como por ejemplo VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

## Resultados

Si ha guardado la configuración del clúster como una plantilla, recibirá una notificación en la consola que indicará que la configuración se ha guardado. Luego podrá encontrar la plantilla en la lista **Configuraciones de clúster**.

Si ha realizado un pedido, el despliegue del clúster se inicia automáticamente. El usuario recibirá una confirmación por correo electrónico de que el pedido se está procesando. Cuando el clúster esté listo para ser utilizado, también se le notificará por correo electrónico.

A diferencia de las instancias de vCenter Server y Cloud Foundation, los clústeres de vSphere no se muestran en la página **Instancias desplegadas**.
{:note}

### Enlaces relacionados

* [Solicitud de clústeres nuevos de vSphere](vs_orderinginstances.html)
* [Escalado de clústeres existentes de vSphere](vs_scalingexistingclusters.html)
* [Escalado de clústeres creados fuera de la consola](vs_orderingforclustersoutside.html)
