---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-05"

---

# Gestión de notificaciones del sistema

Puede comprobar las notificaciones sobre el estado del sistema o sobre las operaciones de los usuarios. También puede utilizar la información para investigar problemas que puedan producirse.

## Visualización de notificaciones

1. En la consola de {{site.data.keyword.vmwaresolutions_full}}, pulse **Notificaciones** en el panel de navegación izquierdo.
2. Vea el resumen sobre todas las notificaciones.

   Tabla 1. Historial de notificaciones

    <table>
      <tr>
        <th>Columna</th>
        <th>Descripción</th>
      </tr>
      <tr>
        <td>Gravedad</td>
        <td>La gravedad del suceso que se comunica en la notificación.
          <dl class="dl">
          <dt class="dt dlterm">Crítico</dt>
          <dd class="dd">Un suceso crítico puede afectar a todo el sistema o servicio.</dd>
          <dt class="dt dlterm">Error</dt>
          <dd class="dd">Se produce un suceso de error durante una operación que puede necesitar la intervención del administrador o del usuario.</dd>
          <dt class="dt dlterm">Aviso</dt>
          <dd class="dd">Un componente falla o no funciona correctamente. Sin embargo, la anomalía no interrumpe el proceso en curso del componente.</dd>
            <dt class="dt dlterm">Informativo</dt>
            <dd class="dd">Se ha completado una operación del sistema o de un usuario. Generalmente los siguientes sucesos generan notificaciones informativas:
              <ul class="ul">
                <li class="li">Se ha instalado un servicio.</li>
                <li class="li">Se ha actualizado un servicio.</li>
                <li class="li">Se ha eliminado un servicio.</li>
                <li class="li">Se han vuelto a configurar todos los servicios para los servidores ESXi añadidos.</li>
                <li class="li">Se han vuelto a configurar todos los servicios para los servidores ESXi eliminados.</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>Tipo</td>
         <td>El tipo de componente con el que está relacionado el suceso notificado:<ul><li>Instancias de vCenter Server</li><li>Instancias de Cloud Foundation</li><li>Servicios</li><li>Sistema</li></ul></td>
       </tr>
       <tr>
         <td>Recurso</td>
         <td>El nombre de la instancia o del servicio que envía la notificación.</td>
       </tr>
       <tr>
         <td>Descripción</td>
         <td>Una breve descripción de la notificación.</td>
       </tr>
       <tr>
         <td>Fecha</td>
         <td>La fecha y hora en que se ha enviado la notificación.</td>
       </tr>
    </table>                                       

3. Pulse la fila de una notificación para ver los detalles de la notificación.

## Filtrado de notificaciones

De forma predeterminada, se muestran todas las notificaciones no leídas. Puede filtrar las notificaciones por estado, gravedad y tipo. Para filtrar las notificaciones, marque solo los recuadros de selección de los elementos que desea visualizar en las listas **Estado**, **Gravedad** o **Tipo**.

### Enlaces relacionados

* [Preguntas frecuentes](faq.html)
* [Cuenta de usuario y valores](useraccount.html)
