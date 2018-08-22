---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Supresión de instancias de vCenter Server con el paquete híbrido (Hybridity)

Para liberar los componentes que ha solicitado en una instancia de VMware vCenter Server con el paquete híbrido (Hybridity), suprima la instancia.

Cuando suprima una instancia de vCenter Server con el paquete híbrido (Hybridity), los siguientes componentes se liberarán en esta secuencia:
1. Todos los servicios desplegados
2. Cuota de soporte y servicios
3. Licencias del producto VMware
4. Servidores ESXi
5. Subredes
6. VLAN

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y las VLAN y se completa la supresión de la instancia.

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
3. Pulse el icono de menú de desbordamiento a la derecha de **Consola de vCenter** y pulse **Suprimir instancia**.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente, los componentes de la instancia se liberarán y el estado de la instancia pasará a ser **Suprimido**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. Pulse el icono de menú de desbordamiento a la derecha de **Consola de vCenter** de nuevo y pulse **Suprimir instancia**.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

### Enlaces relacionados

* [Supresión de las instancias de vCenter Server con el paquete híbrido (Hybridity) en una configuración de varios sitios](vc_hybrid_deletinginstance_multi.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_orderinginstance.html)
* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_viewinginstances.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservers.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
