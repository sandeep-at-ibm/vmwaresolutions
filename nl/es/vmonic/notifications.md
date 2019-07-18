---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# Gestión de notificaciones del sistema
{: #notifications}

Puede comprobar las notificaciones sobre el estado del sistema o sobre las operaciones de los usuarios. También puede utilizar la información para investigar problemas que puedan producirse.

## Visualización de notificaciones
{: #notifications-view}

1. En la consola de {{site.data.keyword.vmwaresolutions_full}}, pulse **Notificaciones** en el panel de navegación izquierdo.
2. Vea el resumen sobre todas las notificaciones.

| Columna | Descripción |
|:------ |:----------- |
| Gravedad | La gravedad del suceso que se comunica en la notificación.<br>**Crítico**: un suceso crítico puede afectar a todo el sistema o servicio.<br>**Error**: se produce un suceso de error durante una operación que puede necesitar la intervención del administrador o del usuario.<br>**Aviso**: un componente falla o no funciona correctamente. Sin embargo, la anomalía no interrumpe el proceso en curso del componente.<br>**Informativo**: se ha completado una operación del sistema o de un usuario. Generalmente los siguientes sucesos generan notificaciones informativas:<br>Se ha instalado un servicio.<br>Se ha actualizado un servicio.<br>Se ha eliminado un servicio.<br>Se han vuelto a configurar todos los servicios para los servidores ESXi añadidos.<br>Se han vuelto a configurar todos los servicios para los servidores ESXi eliminados. |
| Tipo | El tipo de componente con el que está relacionado el suceso notificado: instancias de vCenter Server, Servicios, Sistema |
| Recurso | El nombre de la instancia o del servicio que envía la notificación. |
| Descripción | Una breve descripción de la notificación. |
| Fecha | La fecha y hora en que se ha enviado la notificación. |
{: caption="Tabla 1. Historial de notificaciones" caption-side="top"}

3. Pulse la fila de una notificación para ver los detalles de la notificación.

## Filtrado de notificaciones
{: #notifications-filter}

De forma predeterminada, se muestran todas las notificaciones no leídas. Puede filtrar las notificaciones por estado, gravedad y tipo. Para filtrar las notificaciones, marque solo los recuadros de selección de los elementos que desea visualizar en las listas **Estado**, **Gravedad** o **Tipo**.

## Enlaces relacionados
{: #notifications-related}

* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Cuenta de usuario y valores](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
