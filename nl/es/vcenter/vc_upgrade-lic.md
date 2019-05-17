---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Actualización de licencias para instancias de vCenter Server
{: #vc_upgrade-lic}

Puede actualizar sus instancias de VMware vCenter Server a vCenter Server con el paquete híbrido (Hybridity) solo si su instancia tiene la versión 2.3 o posterior.

Los usuarios de IBM Business Partner no tiene la opción de actualizar al paquete híbrido (Hybridity).
{:note}

## Antes de actualizar la licencia al paquete híbrido (Hybridity)
{: #vc_upgrade-lic-upgrade-prereq}

Revise las acciones siguientes que se llevan a cabo al actualizar al paquete híbrido (Hybridity):

* Si su instancia de vCenter Server tiene la edición VMware NSX Base instalada, la licencia de NSX se actualizará automáticamente a la edición NSX Advanced.
* Si la instancia de vCenter Server tiene almacenamiento NFS, no se efectuarán cargos por el almacenamiento vSAN de VMware. No obstante, se le cobrará la licencia de vSAN que se incluye con el paquete híbrido (Hybridity).

## Procedimiento para actualizar al paquete híbrido (Hybridity) (instancias V2.3 o posterior)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea actualizar al paquete híbrido (Hybridity).
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación izquierdo para verificar los detalles en la página **Infraestructura**.

   Si los detalles no se visualizan, esto podría indicar un problema de conectividad con la VSI de IBM CloudDriver, como resultado de una regla del cortafuegos o de otro problema de red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.

4. Pulse **Actualización y parche** en el panel de navegación izquierdo.
5. Para aplicar la actualización de la licencia del paquete híbrido (Hybridity), en la tabla
**Actualizaciones de licencia**, pulse **Actualizar** en la columna **Acción**. Revise el coste estimado y pulse **Actualizar**.
6. De forma opcional, puede desplegar el servicio de VMware HCX on {{site.data.keyword.cloud_notm}}. Cuando el paquete híbrido (Hybridity) esté habilitado en la tabla **Actualizaciones de licencia**, siga estos pasos:
  1. En la tabla **Actualizaciones de licencia**, pulse **Desplegar HCX on {{site.data.keyword.cloud_notm}}** en la columna **Acción**.
  2. Desplácese a la tarjeta **HCX on {{site.data.keyword.cloud_notm}}** y pulse **Seleccionar servicio**.
  3. Desplácese hacia abajo, especifique los valores necesarios para el servicio y pulse **Siguiente**.
  4. Revise los términos que se aplican al servicio, revise el coste estimado y pulse **Realizar el pedido**.

## Procedimiento para actualizar la licencia de NSX (instancias V2.1 o posterior)
{: #vc_upgrade-lic-nsx}

Este procedimiento se aplica a las instancias desplegadas en V2.1 o posterior. Para las instancias desplegadas en V2.0 y anteriores, debe actualizar la licencia de NSX manualmente.

Puede actualizar la licencia de NSX para su instancia a una edición posterior. No se admite la degradación de la edición de la licencia.

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea actualizar la licencia de NSX.
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación izquierdo para verificar los detalles en la página **Infraestructura**.

   Si no se visualizan los detalles, esto podría indicar un problema de conectividad con la Instancia de servidor virtual (VSI) de IBM CloudDriver, como resultado de una regla de cortafuegos o un problema de la red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.

4. Pulse **Actualización y parche** en el panel de navegación de la izquierda y pulse
**Actualizar**. En la ventana **Actualizar edición de licencia de NSX**, seleccione la edición a la que desea actualizar y pulse **Actualizar**.

   La actualización de licencia sustituye todas las licencias existentes de NSX en la instancia. Es posible que se incurra en cargos adicionales derivados de un solapamiento de licencias antiguas y nuevas si realiza la actualización a mitad del ciclo de facturación. Para evitar estos cargos adicionales, se recomienda actualizar la licencia al final del periodo de facturación.
   {:note}

## Enlaces relacionados
{: #vc_upgrade-lic-related}

* [Visión general de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
