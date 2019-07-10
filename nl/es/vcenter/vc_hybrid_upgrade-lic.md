---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: NSX license, upgrade license, Hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Actualización de licencias de NSX para instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_upgrade-lic}

Puede actualizar la licencia de VMware NSX para su instancia a una edición posterior. No se admite la degradación de la edición de la licencia.

## Procedimiento para actualizar la licencia de NSX
{: #vc_hybrid_upgrade-lic-nsx}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea actualizar la licencia de NSX.
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación izquierdo para verificar los detalles en la página **Infraestructura**.

   Si no se visualizan los detalles, esto podría indicar un problema de conectividad con la Instancia de servidor virtual (VSI) de IBM CloudDriver, como resultado de una regla de cortafuegos o un problema de la red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.

4. Pulse **Actualización y parche** en el panel de navegación de la izquierda y pulse
**Actualizar**. En la ventana **Actualizar edición de licencia de NSX**, seleccione la edición a la que desea actualizar y pulse **Actualizar**.

   La actualización de licencia sustituye todas las licencias existentes de NSX en la instancia. Es posible que se incurra en cargos adicionales derivados de un solapamiento de licencias antiguas y nuevas si realiza la actualización a mitad del ciclo de facturación. Para evitar estos cargos adicionales, se recomienda actualizar la licencia al final del periodo de facturación.
   {:note}

## Enlaces relacionados
{: #vc_hybrid_upgrade-lic-related}

* [Visión general de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
