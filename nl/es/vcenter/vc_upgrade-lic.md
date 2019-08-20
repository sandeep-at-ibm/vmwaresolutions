---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-24"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Actualización de licencias para instancias de vCenter Server
{: #vc_upgrade-lic}

Puede actualizar la licencia de NSX para la instancia V2.1 o posteriores.

## Procedimiento para actualizar la licencia de NSX
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

* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
