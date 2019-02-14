---

copyright:

  years:  2016, 2019

lastupdated: "2017-08-16"

---

# Alertas y avisos del estado de SAN virtual

## Problema
En la página **Monitor** del cliente web de VMware vSphere, pueden aparecer alertas y avisos relacionados con problemas del estado de la SAN virtual.

## Solución
Estos avisos no son problemáticas y no indican problemas funcionales. Sin embargo, si desea borrar los avisos del cliente web de vSphere, siga el siguiente procedimiento.

1. Vaya a http://partnerweb.vmware.com/service/vsan/all.json y guarde el archivo JSON, denominado `all.json`, en el sistema local.
2. Asegúrese de haber completado los pasos del apartado [Tiempo de espera excedido de la consola de vCenter](trbl_timeout_vc_console.html).
3. En la página de detalles de la instancia de Cloud Foundation, pulse **consola de vCenter** e inicie una sesión en el cliente web de vSphere utilizando las credenciales que se muestran en la consola de {{site.data.keyword.vmwaresolutions_full}}.
4. En el cliente web de vSphere, vaya a **Gestionar > Configuración** y abra la sección **SAN virtual > Estado > Base de datos HCL**. Pulse **Actualizar desde archivo** y cargue el archivo `all.json` que ha guardado anteriormente.
5. Para borrar los avisos, vaya al panel **Alarmas** de la parte superior derecha del cliente web de vSphere. Pulse con el botón derecho en cada una de las alarmas y seleccione **Restablecer a verde**.

Para obtener más información, consulte [Cómo descargar el archivo HCL de vSAN fuera de línea para el plugin de comprobación del estado de vSAN](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}.
