---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Eliminación del paquete híbrido (Hybridity) de una instancia de vCenter Server
{: #vc_hybrid_deletingbundle}

Para eliminar la licencia del paquete híbrido (Hybridity) de la instancia de vCenter Server, debe sustituir las claves de licencia de alquiler de VMware NSX y VMware vSAN con las claves de Traiga su propia licencia (BYOL) en el cliente web de VMware vSphere. Además, debe abrir una incidencia de soporte para cancelar los cargos de las licencias de alquiler.

La degradación de la licencia puede hacer que falle la instancia de vCenter Server. Puede optar por degradar una licencia bajo su propio riesgo, pero en primer lugar tenga en cuenta las funciones que no están disponibles cuando degrade. Para obtener más información, consulte [Gráfico de comparación para las ediciones de componentes de VMware](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix).
{:important}

## Consideraciones importantes antes de eliminar el paquete de Hybridity de un entorno de varios sitios
{: #vc_hybrid_deletingbundle-considerations}

Revise las consideraciones siguientes antes de eliminar el paquete de Hybridity de un entorno de varios sitios:

* Debe aplicar las licencias BYOL a todos los despliegues de varios sitios antes de eliminar las licencias de alquiler.
* Debe combinar las licencias de VMware NSX y tener suficiente capacidad que utilizar en todos los despliegues de varios sitios.
* Debe crear una sola incidencia de soporte para eliminar el paquete de Hybridity de todos los despliegues de varios sitios.

Al eliminar el paquete de híbrido de un entorno de varios sitios, se aplican las licencias BYOL. Es su responsabilidad asegurarse de que las ediciones de licencias sean coherentes entre todos los sitios de la configuración de varios sitios.
{:note}

## Antes de eliminar el paquete híbrido (Hybridity)
{: #vc_hybrid_deletingbundle-prereq}

Verifique los siguientes requisitos antes de eliminar el paquete híbrido (Hybridity):

* Tiene una instancia de vCenter Server V2.4 o posterior con el paquete híbrido (Hybridity) habilitado.
* No tiene el servicio de VMware HCX on {{site.data.keyword.cloud_notm}} instalado en la instancia de vCenter Server.
* Tiene acceso al cliente web de VMware vSphere como administrador.
* Si todavía no se ha aplicado, tiene claves BYOL disponibles para aplicar a VMware NSX y a cada clúster VMware vSAN.
* Opcionalmente, y si todavía no se ha aplicado, tiene las claves BYOL disponibles para aplicar a las licencias VMware vCenter Server y VMware vSphere Enterprise Plus.

## Procedimiento para eliminar el paquete híbrido (Hybridity)
{: #vc_hybrid_deletingbundle-procedure}

1. Inicie la sesión como **Administrador** en el cliente web de VMware vSphere en el que desea eliminar el paquete de Hybridity.
2. Pulse **Inicio > Administración > Licencia > Licencias**.
3. Pulse el separador **Activos**.
4. Siga los pasos siguientes para instalar un BYOL de VMware NSX:
   1. Pulse el separador **Soluciones**.
   2. Seleccione NSX for vSphere y pulse **Todas las acciones > Asignar licencia**.
   3. Pulse el icono **Añadir** y escriba la clave de licencia. Pulse **Siguiente**.
   4. Escriba el nombre de la licencia y pulse **Siguiente**. Pulse **Finalizar** para añadir la licencia.
   5. Seleccione la nueva clave de licencia.
   6. Anote las claves de licencia completas para la licencia que se aplica y para la licencia que se ha sustituido.

   Debe tener los detalles de licencia disponibles para utilizarlos más adelante en este procedimiento.
   {:important}
   7. Pulse **Aceptar** para asignar la licencia.
5. Siga los pasos siguientes para instalar un BYOL de VMware vSAN:
   1. Pulse el separador **Clústeres**.
   2. Complete los pasos siguientes para cada clúster vSAN que esté asociado con la instancia de vCenter Server:
    1. Seleccione un clúster vSAN y pulse **Todas las acciones > Asignar licencia**.
    2. Pulse el icono **Añadir** y escriba la clave de licencia. Pulse **Siguiente**.
    3. Escriba el nombre de la licencia y pulse **Siguiente**. Pulse **Finalizar** para añadir la licencia.
    4. Seleccione la nueva clave de licencia.
    5. Anote el nombre de clúster y las claves de licencia completas de la licencia que se aplica y de la licencia que se ha sustituido.

    Debe tener los detalles de licencia disponibles para utilizarlos más adelante en este procedimiento.
    {:important}
    6. Pulse **Aceptar** para asignar la licencia.
6. Opcionalmente, complete los pasos siguientes para instalar un BYOL de VMware vCenter Server:
   1. Pulse el separador **Sistemas de vCenter Server**.
   2. Seleccione vCenter Server y pulse **Todas las acciones > Asignar licencia**.
   3. Pulse el icono **Añadir** y escriba la clave de licencia. Pulse **Siguiente**.
   4. Escriba el nombre de la licencia y pulse **Siguiente**. Pulse **Finalizar** para añadir la licencia.
   5. Seleccione la nueva clave de licencia.
   6. Anote las claves de licencia completas de la licencia que se aplica y de la licencia que se ha sustituido.

   Debe tener los detalles de licencia disponibles para utilizarlos más adelante en este procedimiento.
   {:important}

   7. Pulse **Aceptar** para asignar la licencia.
7. Opcionalmente, complete los pasos siguientes para instalar un BYOL de VMware vSphere Enterprise Plus:
  1. Pulse el separador **Hosts**.
  2. Complete los pasos siguientes para cada clúster que esté asociado con la instancia de vCenter Server o complete para todos los clústeres al mismo tiempo si se aplica la misma licencia a todos los clústeres asociados con el servidor de vCenter:
    1. Seleccione todos los hosts que están asociados al clúster y pulse **Todas las acciones > Asignar licencia**.
    2. Pulse el icono **Añadir** y escriba la clave de licencia. Pulse **Siguiente**.
    3. Escriba el nombre de la licencia y pulse **Siguiente**. Pulse **Finalizar** para añadir la licencia.
    4. Seleccione la nueva clave de licencia.
    5. Anote el nombre de clúster y las claves de licencia completas de la licencia que se aplica y de la licencia que se ha sustituido.

    Debe tener los detalles de licencia disponibles para utilizarlos más adelante en este procedimiento. Si las claves de licencia no son las mismas en todos los clústeres, asegúrese de escribir el nombre del clúster asociado a cada clave de licencia.
    {:important}

    6. Pulse **Aceptar** para asignar la licencia.
8. Elimine las licencias de alquiler.
   1. Pulse el separador **Licencias**.
   2. Seleccione las licencias que ha sustituido en los pasos 4 - 7.
   3. Pulse el icono **Eliminar licencias**.
9. Abra una incidencia de soporte y proporcione la siguiente información para cancelar los cargos de las licencias de alquiler:
  * El nombre de la instancia o instancias de vCenter Server.
  * El ID asociado con la instancia o instancias de vCenter Server.
  * Una lista de las claves de licencia de BYOL que ha instalado en este procedimiento. Cuando sea aplicable, proporcione la instancia y el nombre de clúster con las claves de licencia para los clústeres vSphere y vSAN.
  * Una lista de las claves de licencia de alquiler que ha eliminado en este procedimiento. Cuando sea aplicable, proporcione la instancia y el nombre de clúster con las claves de licencia para los clústeres vSphere y vSAN.

  Los equipos de operaciones y soporte de IBM acceden a la capa de gestión de vCenter de la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) para verificar que se han eliminado las licencias de alquiler antes de cancelar los cargos de licencia de alquiler del paquete híbrido (Hybridity).
  {:note}

## Enlaces relacionados
{: #vc_hybrid_deletingbundle-related}

* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
