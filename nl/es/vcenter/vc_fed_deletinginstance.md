---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Supresión de instancias de VMware Federal

Para liberar los componentes que ha solicitado en una instancia de VMware Federal, suprima la instancia.

Cuando suprima una instancia de VMware Federal, los siguientes componentes se liberarán en esta secuencia:

1. Cuotas de soporte y servicio
2. Licencias del producto VMware
3. Servidores ESXi
4. Subredes

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y se completa la supresión de la instancia.

**Atención:** Se le facturará por la instancia suprimida hasta el final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}.

## Supresión de instancias de la página Instancias desplegadas

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, busque la instancia que desea suprimir.
3. En la columna **Acciones**, pulse el icono Suprimir.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente, los componentes de la instancia se liberarán y el estado de la instancia pasará a ser **Suprimido**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. En la columna **Acciones**, pulse el icono Suprimir de nuevo.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

## Supresión de instancias de la página de detalles de la instancia

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea suprimir.
3. Pulse el icono de menú de desbordamiento junto a la **consola de vCenter** y pulse **Suprimir instancia**.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente, los componentes de la instancia se liberarán y el estado de la instancia pasará a ser **Suprimido**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. Pulse el icono de menú de desbordamiento junto a **Consola de vCenter** de nuevo y pulse **Suprimir instancia**.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

### Enlaces relacionados

* [Visión general de VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Solicitud de instancias de VMware Federal](vc_fed_orderinginstance.html)
* [Protección de instancias de VMware Federal](vc_fed_securinginstance.html)
* [Visualización de instancias de VMware Federal](vc_fed_viewinginstance.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
