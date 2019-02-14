---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Escalado de clústeres existentes de vSphere

Puede escalar un clúster de VMware vSphere que ha solicitado o guardado en la consola de {{site.data.keyword.vmwaresolutions_full}}. Para ello, añada servidores ESXi o solicite un par de alta disponibilidad de FortiGate 300 Series Security Appliance para el clúster.

## Requisitos

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Cuentas de usuario y valores](../vmonic/useraccount.html).
*  Ha revisado los requisitos y las consideraciones del apartado [Requisitos y planificación de clústeres de vSphere](vs_planning.html).
*  Ha recibido un correo electrónico con la confirmación de que el clúster que desea escalar está listo para que lo utilice.

## Procedimiento para escalar clústeres existentes

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** en el panel de navegación izquierdo y pulse **VMware vSphere** en la sección **Centros de datos virtuales**.
2. En la página **VMware vSphere on IBM Cloud**, pulse **Crear**.  
3. Pulse el separador **Escalar clúster existente** y seleccione el clúster que desea escalar en la lista **Configuraciones de clúster**.
4. Revise los valores de clúster que se han completado automáticamente.
5. En la sección **{{site.data.keyword.baremetal_short}}**, especifique el número de {{site.data.keyword.baremetal_short}} que desea añadir al clúster.
6. Si el clúster no incluye el par de alta disponibilidad de dispositivos de seguridad FortiGate serie 300 en su VLAN pública, puede solicitar el dispositivo. Para ello, marque el recuadro de selección **Incluir con la compra** que hay bajo **FortiGate Physical Appliance 300 Series HA Pair**.
7. En el panel **Resumen del pedido**, verifique la configuración de la instancia y el coste estimado.
   * Para guardar la configuración como una plantilla sin realizar un pedido, pulse **Guardar configuración**.
   * Para realizar el pedido, asegúrese de que la cuenta a la que se va a realizar el cobro es correcta; revise y acepte los términos y, a continuación, pulse **Suministro**.

### Resultados

El escalado de clúster se inicia automáticamente. El usuario recibirá una confirmación por correo electrónico de que el pedido se está procesando. Cuando el clúster esté listo para ser utilizado, se le notificará por correo electrónico.

Si el clúster que está escalando no está listo para que lo utilice, es posible que reciba un mensaje de error.

A diferencia de las instancias de vCenter Server y Cloud Foundation, los clústeres de vSphere no se muestran en la página **Instancias desplegadas**.
{:note}

### Enlaces relacionados

* [Solicitud de clústeres nuevos de vSphere](vs_orderinginstances.html)
* [Solicitud de clústeres de vSphere en función de configuraciones existentes](vs_orderingbasedonexistingconfig.html)
* [Escalado de clústeres creados fuera de la consola](vs_orderingforclustersoutside.html)
