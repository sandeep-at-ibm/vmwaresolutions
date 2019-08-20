---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-01"

keywords: troubleshooting, Zerto Virtual Replication, Zerto ESXi server

subcollection: vmware-solutions


---

# No se muestran los dispositivos de réplica virtual de Zerto para los servidores ESXi recién creados
{: #trbl_no_zerto_vra}

## Problema
{: #trbl_no_zerto_vra-problem}

Los dispositivos de réplica virtual (VRA) no se muestran en la consola de réplica virtual de Zerto después de añadir servidores ESXi a una instancia de VMware vCenter Server que tiene instalado el servicio de recuperación tras desastre de Zerto.

## Solución
{: #trbl_no_zerto_vra-resolution}

El servicio de recuperación tras desastre de Zerto solo se instala en el servidor ESXi desde el clúster predeterminado (**cluster1** para las instancias desplegadas en V3.1 o anterior). En los clústeres adicionales del mismo entorno de vCenter Server, no se instala automáticamente el servicio de recuperación tras desastre de Zerto cuando se crea el clúster adicional ni cuando se añade el servidor ESXi a dicho clúster adicional.

En los clústeres adicionales, debe instalar el servicio de recuperación tras desastre de Zerto por separado.

Abra una incidencia de soporte de {{site.data.keyword.cloud}} y trabaje con el equipo de soporte de IBM para obtener las direcciones IP disponibles para poder instalar los VRA desde la consola de Zerto, en lugar de hacerlo desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

Para acceder a la consola de Zerto, pulse la tarjeta de Zerto desde el separador **Servicios** de la instancia y pulse **Ver detalles** y luego **Ver consola de Zerto**.

Para obtener más información sobre cómo ponerse en contacto con el equipo de soporte de IBM, consulte [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-trbl_support#trbl_support).
