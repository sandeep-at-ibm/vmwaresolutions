---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aplicación de actualizaciones de componentes de gestión de IBM a instancias de vCenter Server
{: #vc_applyingupdates}

El procedimiento de esta sección se aplica para actualizar componentes de gestión de IBM para instancias desplegadas en los releases de V2.1 a V2.4.

Para las instancias desplegadas en (o actualizadas a) V2.5 o posterior, las actualizaciones y parches para los componentes de gestión de IBM se aplican automáticamente, según sea necesario.

Para instancias desplegadas en V2.0 y anteriores, debe aplicar las actualizaciones manualmente.

Además, tenga en cuenta el comportamiento siguiente cuando termine determinadas operaciones en la instancia:
* Al solicitar nuevos servicios, la instancia se actualiza a la versión más reciente.
* Al añadir clústeres nuevos, se suministran estos clústeres con los componentes más recientes de VMware, pero los clústeres existentes no.
* Al añadir nuevos servidores ESXi, se suministran estos servidores ESXi con los componentes más recientes de VMware, pero los servidores ESXi existentes no.

{{site.data.keyword.vmwaresolutions_short}} no ofrece soporte para aplicar actualizaciones y parches para componentes de VMware. Debe supervisar y aplicar estas actualizaciones usted mismo.
{:important}

## Antes de aplicar actualizaciones de componentes de gestión de IBM
{: #vc_applyingupdates-prereq}

Expanda la entrada de actualización pulsando la flecha hacia abajo y verifique la información siguiente:
* La versión de la actualización. Debe aplicar las actualizaciones en secuencia cronológica, es decir, desde la primera hasta la más reciente. Asegúrese de haber aplicado todas las actualizaciones anteriores antes de aplicar la más reciente. Por ejemplo, debe aplicar la actualización V2.3 antes de intentar aplicar la actualización V2.4.
* Si se requiere tiempo de inactividad.
* El tiempo total estimado para completar la actualización.
* El impacto de la actualización sobre el entorno virtual VMware. En la Tabla 1 se muestra cómo afectan al sistema distintos niveles de impacto.
* Los detalles de la actualización.

Tabla 1. Niveles de actualización e impacto

<table>
  <tr>
    <th>Nivel de actualización</th>
    <th>Impacto</th>
  </tr>
  <tr>
    <td>Bajo</td>
    <td>Esta actualización no afecta a ningún sistema. No es necesario que la aplique durante un tiempo de inactividad planificado.</td>
  </tr>
  <tr>
    <td>Medio</td>
  <td>Esta actualización puede afectar a algunos sistemas. Se recomienda aplicarla durante un tiempo de inactividad planificado.</td>
  </tr>
    <tr>
    <td>Grave</td>
  <td>Esta actualización afecta a algunos o a todos los sistemas. Debe aplicarla durante un tiempo de inactividad planificado.</td>
  </tr>
</table>

## Procedimiento para aplicar actualizaciones de componentes de gestión de IBM (instancias de V2.1 a V2.4)
{: #vc_applyingupdates-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea actualizar.
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación izquierdo para verificar los detalles en la página **Infraestructura**.

   Si no se visualizan los detalles, esto podría indicar un problema de conectividad con la Instancia de servidor virtual (VSI) de IBM CloudDriver, como resultado de una regla de cortafuegos o un problema de la red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.

4. Pulse **Actualización y parche** en el panel de navegación de la izquierda y pulse la flecha hacia abajo para expandir la actualización de gestión de IBM que desee aplicar y, a continuación, realice uno de los pasos siguientes:
   * Para comenzar la actualización de inmediato, pulse el icono de menú de desbordamiento en la columna **Acciones** de la entrada de la actualización y pulse **Actualizar ahora**.
   * Para planificar una actualización futura, pulse el icono de menú de desbordamiento en la columna **Acciones** de la entrada de la actualización y pulse **Planificar actualización**. Seleccione la fecha, la hora y el huso horario en que desea que comience la actualización. Pulse **Aceptar**.
5. Si está aplicando actualizaciones a instancias que tienen una configuración de despliegue de varios sitios, aparecerá una sección llamada **Pasos necesarios para actualizar**. En esta sección se enumeran las operaciones de actualización necesarias para todas las instancias del despliegue de varios sitios. Debe completar los pasos en secuencia pulsando **Aplicar actualización** para cada paso. Debe esperar a que finalice el paso anterior antes de iniciar el paso siguiente.

## Resultados después de aplicar actualizaciones de componentes de gestión de IBM
{: #vc_applyingupdates-results}

1. Después de aplicar una actualización, aparece un registro en la lista de estado de actualización de software, donde puede ver el progreso detallado y el estado de la actualización. Cuando la actualización finaliza correctamente, aparece un registro en la lista de actualizaciones de software instaladas.

  Para recuperar el estado más reciente de un trabajo de actualización, pulse el icono de renovación de la esquina superior derecha de la página.
  {:tip}

2. Para ver detalles sobre los estados de una actualización, consulte la tabla siguiente.

   Tabla 2. Detalles de los estados de actualización

    <table>
      <tr>
        <th>Estado</th>
        <th>Detalles</th>
      </tr>
      <tr>
        <td>Disponible</td>
        <td>La actualización está lista para ser aplicarse. No puede seleccionar una actualización disponible hasta que se hayan aplicado sus actualizaciones anteriores.</td>
      </tr>
      <tr>
        <td>En curso</td>
      <td>El trabajo de actualización se ha iniciado pero todavía no ha finalizado. No puede aplicar ninguna otra actualización hasta que finalice el trabajo de actualización actual. </td>
      </tr>
        <tr>
        <td>Instalado</td>
      <td>El trabajo de actualización ha finalizado. El componente correspondiente de la plataforma VMware se ha actualizado.</td>
      </tr>
        <tr>
        <td>Fallido</td>
      <td>El trabajo de actualización ha fallado. La consola muestra un error correspondiente a la anomalía de actualización. Revise el error y solucione el problema antes de aplicar la actualización.</td>
      </tr>
          <tr>
        <td>Planificado</td>
      <td>El trabajo de actualización está planificado para un momento posterior. El trabajo de actualización se inicia automáticamente en el momento planificado.</td>
      </tr>
          <tr>
        <td>Desconocido</td>
      <td>No se puede obtener el estado del trabajo de actualización. Póngase en contacto con el servicio de soporte de IBM para obtener ayuda.</td>
      </tr>
    </table>

3. Si el proceso de actualización falla en un paso específico, [póngase en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obtener ayuda. Obtendrá información sobre cómo resolver el problema e instrucciones para aplicar las actualizaciones y parches desde el paso que ha fallado.

## Enlaces relacionados
{: #vc_applyingupdates-related}

* [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Actualización de licencias para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
