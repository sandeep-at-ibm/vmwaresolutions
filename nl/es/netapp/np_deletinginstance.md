---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Supresión de instancias de NetApp ONTAP Select
{: #np_deletinginstance}

Si suprime una instancia de NetApp ONTAP Select, los componentes siguientes se publican secuencialmente:
1. Las máquinas virtuales (VM) en clúster desplegadas de NetApp ONTAP Select y la máquina virtual de NetApp ONTAP Select Deploy
2. Cuota de soporte y servicios
3. Licencias del producto VMware
4. Servidores ESXi
5. Subredes
6. VLAN

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación, que suele ser de 30 días, se reclaman las subredes y las VLAN y se completa la supresión de la instancia.

Se le facturará por la instancia suprimida hasta el final del ciclo de facturación.
{:note}

## Procedimiento para suprimir instancias de la página Recursos
{: #np_deletinginstance-procedure1}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de NetApp ONTAP Select**, localice la instancia que desea suprimir.
3. En la columna **Acciones**, pulse el icono Suprimir.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente y su estado sea **Suprimido**, vuelva a pulsar el icono de suprimir en la columna **Acciones**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. En la columna **Acciones**, pulse el icono Suprimir de nuevo.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

## Procedimiento para suprimir instancias de la página de detalles de la instancia
{: #np_deletinginstance-procedure2}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de NetApp ONTAP Select**, pulse la instancia que desea suprimir.
3. Pulse el icono de menú de desbordamiento junto a **Consola de NetApp** y pulse **Suprimir instancia**.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente, los componentes de la instancia se liberarán y el estado de la instancia pasará a ser **Suprimido**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. Pulse el icono de menú de desbordamiento junto a **Consola de vCenter** de nuevo y pulse **Suprimir instancia**.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

## Enlaces relacionados
{: #np_deletinginstance-related}

* [Solicitud de instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [Visualización de instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
