---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aplicación de actualizaciones a instancias de vCenter Server

El proceso de aplicar parches y actualizaciones a instancias de vCenter Server sólo es automático para los componentes de gestión. Las actualizaciones de VMware deben aplicarse manualmente.

## Antes de empezar

Cuando actualice una instancia de vCenter Server a un vCenter Server con la instancia de Hybridity Bundle, primero debe aplicar al menos la actualización de software base de vCenter Server V2.3. Debe hacerlo antes de poder realizar la actualización de la licencia en el paquete híbrido (Hybridity).
{:important}

Los usuarios de Business Partner no tienen la opción de actualizar una instancia de vCenter Server existente a un vCenter Server con la instancia del paquete híbrido (Hybridity).

A partir de la V2.5, las actualizaciones de IBM CloudDriver ya no aparecen listadas porque se han habilitado las actualizaciones automáticas. Las acciones como la adición de un host, la adición de un clúster y la solicitud de un servicio actualizan automáticamente la instancia a la última versión. Para obtener más información sobre las actualizaciones automáticas, consulte la sección *Resiliencia de IBM CloudDriver* en las [Notas del release de V2.5](../vmonic/relnotes_v25.html).
{:note}

Antes de intentar aplicar una actualización, expanda la entrada de la actualización pulsando la flecha hacia abajo y verifique la información siguiente:
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

## Procedimiento para aplicar actualizaciones y parches a las instancias de vCenter Server (V2.1 o posteriores)

Este procedimiento se aplica a las instancias desplegadas en V2.1 o posterior. Para instancias desplegadas en V2.0 y anteriores, debe aplicar las actualizaciones de VMware manualmente.

1. En la consola de {{site.data.keyword.vmwaresolutions_full}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea actualizar.
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación izquierdo para verificar los detalles en la página **Infraestructura**.
   Si no se visualizan los detalles, esto podría indicar un problema de conectividad con la Instancia de servidor virtual (VSI) de IBM CloudDriver, como resultado de una regla de cortafuegos u otro problema de la red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.
4. Pulse **Actualización y parche** en el panel de navegación izquierdo.

   La página **Actualización y parche** de una instancia solo contiene los paquetes para la actualización de los componentes de gestión de IBM y no las actualizaciones de VMware. Las actualizaciones de VMware deben aplicarse manualmente.   {{site.data.keyword.vmwaresolutions_short}} aplica las actualizaciones de VMware para las operaciones siguientes:
   * Cuando se despliega una instancia nueva de vCenter Server.
   * Cuando se añaden nuevos servidores ESXi, los nuevos servidores ESXi se suministran con actualizaciones de VMware, pero los servidores ESXi existentes no se actualizan.
   * Cuando se añaden nuevos clústeres, los nuevos clústeres se suministran con actualizaciones de VMware, pero los clústeres existentes no se actualizan.
   {:note}

5. Para las actualizaciones de licencia de NSX, pulse **Actualizar**. En la ventana **Actualizar edición de licencia de NSX**, seleccione la edición a la que desea actualizar y pulse **Actualizar**. No se permite reducir la edición de la licencia.

   La actualización de licencia sustituye todas las licencias existentes de NSX en la instancia. Es posible que se incurra en cargos adicionales derivados de un solapamiento de licencias antiguas y nuevas si realiza la actualización a mitad del ciclo de facturación. Para evitar estos cargos adicionales, se recomienda actualizar la licencia al final del periodo de facturación.
   {:note}

6. Para actualizaciones de software, pulse la flecha hacia abajo para ampliar la actualización que desea aplicar y luego siga uno de los pasos siguientes:
   *  Para comenzar la actualización de inmediato, pulse el icono de menú de desbordamiento en la columna **Acciones** de la entrada de la actualización y pulse **Actualizar ahora**.
   *  Para planificar una actualización futura, pulse el icono de menú de desbordamiento en la columna **Acciones** de la entrada de la actualización y pulse **Planificar actualización**. Seleccione la fecha, la hora y el huso horario en que desea que comience la actualización. Pulse **Aceptar**.
7. Si está aplicando actualizaciones a instancias de servidores vCenter en una configuración de despliegue de varios sitios, aparecerá una sección llamada **Pasos necesarios para actualizar**. En esta sección se enumeran las operaciones de actualización necesarias para todas las instancias del despliegue de varios sitios. Debe completar los pasos en secuencia pulsando **Aplicar actualización** para cada paso. Debe esperar a que finalice el paso anterior antes de iniciar el paso siguiente.   

## Procedimiento para actualizar a la instancia de vCenter Server con Hybridity Bundle

Durante la actualización de licencia al paquete híbrido (Hybridity), se actualizará automáticamente a la edición VMware NSX Advanced si la instancia de vCenter Server utiliza actualmente la edición Base de VMware NSX.

Si actualiza al paquete híbrido (Hybridity) y la instancia de vCenter Server ya tiene almacenamiento de archivos NFS, no se le cargará el almacenamiento vSAN de VMware. Se le cargará la licencia de vSAN porque se incluye con el paquete híbrido (Hybridity).
{:note}

Siga estos pasos para actualizar una instancia de vCenter Server a vCenter Server con el paquete híbrido (Hybridity).

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea actualizar.
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación izquierdo para verificar los detalles en la página **Infraestructura**.
   Si los detalles no se visualizan, esto podría indicar un problema de conectividad con la VSI de IBM CloudDriver, como resultado de una regla del cortafuegos o de otro problema de red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.
4. Pulse **Actualización y parche** en el panel de navegación izquierdo.
5. Aplique la actualización de licencia del paquete híbrido (Hybridity). En la tabla **Actualizaciones de licencia**, pulse **Actualizar** en la columna **Acción**, revise el coste estimado y pulse **Actualizar**.
6. De forma opcional, despliegue el servicio de VMware HCX on {{site.data.keyword.cloud_notm}}. Cuando el paquete híbrido (Hybridity) esté habilitado en la tabla **Actualizaciones de licencia**, siga estos pasos:
  1. En la tabla **Actualizaciones de licencia**, pulse **Desplegar HCX on {{site.data.keyword.cloud_notm}}** en la columna **Acción**.
  2. Desplácese a la tarjeta **HCX on {{site.data.keyword.cloud_notm}}** y pulse **Seleccionar servicio**.
  3. Desplácese hacia abajo, especifique los valores necesarios para el servicio y pulse **Siguiente**.
  4. Revise los términos que se aplican al servicio, revise el coste estimado y pulse **Realizar el pedido**.

## Resultados

2. Después de aplicar una actualización, aparece un registro en la lista de estado de actualización de software, donde puede ver el progreso detallado y el estado de la actualización. Cuando la actualización finaliza correctamente, aparece un registro en la lista de actualizaciones de software instaladas.

  Para recuperar el estado más reciente de un trabajo de actualización, pulse el icono de renovación de la esquina superior derecha de la página.
  {:tip}

3. Para ver detalles sobre los estados de una actualización, consulte la tabla siguiente.

   Tabla 2. Detalles de los estados de actualización

    <table>
      <tr>
        <th>Estado</th>
        <th>Detalles</th>
      </tr>
      <tr>
        <td>Disponible</td>
        <td>La actualización está lista para se aplicada. No puede seleccionar una actualización disponible hasta que se hayan aplicado sus actualizaciones anteriores.</td>
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

4. Si el proceso de actualización falla en un paso específico, [póngase en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html) para obtener ayuda. Se le informará sobre cómo resolver el problema y se le guiará para que vuelva a intentar la actualización desde el paso que ha dado el error.

### Enlaces relacionados

* [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
