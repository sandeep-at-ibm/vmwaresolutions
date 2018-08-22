---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Protección de instancias de VMware Federal

Siga el procedimiento siguiente para proteger la instancia desplegada de VMware Federal, es decir, para eliminar la conexión de gestión abierta para el acceso continuado a la instancia.

## Antes de empezar

Revise la siguiente información para comprender los resultados de proteger la instancia desplegada de VMware Federal:

* Registre y guarde las credenciales que pueda necesitar para el entorno antes de completar este procedimiento. Todas las credenciales correspondientes a su entorno se borran de la base de datos de {{site.data.keyword.vmwaresolutions_full}} y no se pueden recuperar después de que se invoque la acción de protección.
* Con la excepción de una supresión de la instancia completa, todas las funciones de gestión se inhabilitan después de que se invoque la acción de protección.
* La Edge Services Gateway (ESG) de NSX de Vmware para el tráfico de gestión de HTTPS de salida y la máquina virtual de IBM CloudDriver se suprimen como parte de la acción para proteger la instancia de VMware desplegada.

## Procedimiento

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea proteger.
3. Pulse el icono de menú de desbordamiento de la derecha de la **consola de vCenter**.
4. Pulse **Proteger instancia**.
5. Pulse **Aceptar** para confirmar que desea desconectar la instancia de la automatización.

   **Nota**: Antes de completar este paso, asegúrese de que ha revisado la información de la sección **Antes de empezar**.

## Resultados

El estado de la instancia pasa a ser **Modificando**.

Cuando la instancia se haya protegido correctamente, el estado de la instancia pasará a ser **Protegido** y solo estarán disponibles las propiedades de la instancia y el historial de despliegues.

### Enlaces relacionados

* [Visión general de VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Solicitud de instancias de VMware Federal](vc_fed_orderinginstance.html)
* [Visualización de instancias de VMware Federal](vc_fed_viewinginstance.html)
* [Supresión de instancias de VMware Federal](vc_fed_deletinginstance.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
