---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Protección de instancias de VMware Federal

Siga el procedimiento siguiente para proteger la instancia desplegada de VMware Federal, es decir, para eliminar la conexión de gestión abierta para el acceso continuado a la instancia.

## Antes de empezar

Revise la siguiente información para comprender los resultados de proteger la instancia desplegada de VMware Federal:

* Registre y guarde las credenciales que pueda necesitar para su entorno antes de completar este procedimiento. Todas las credenciales para el entorno se borran de la base de datos de {{site.data.keyword.vmwaresolutions_full}} y no se pueden recuperar después de que se inicie la acción segura.
* Excepto para una supresión de instancia completa, todas las demás funciones de gestión se inhabilitan después de que se inicie la acción segura.

## Procedimiento para proteger las instancias de VMware Federal

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia que desea proteger.
3. Pulse el icono de menú de desbordamiento junto a la **consola de vCenter**.
4. Pulse **Proteger instancia**.
5. Pulse **Aceptar** para confirmar que desea desconectar la instancia de la automatización.

  Antes de completar este paso, asegúrese de que revise la información en la sección **Antes de empezar**.
  {:note}

6. Elimine los servicios de gestión destinados al público de VMware NSX Edge Services Gateway (ESG) del entorno y, opcionalmente, elimine el ESG gestionado por el cliente que se despliega durante la automatización.
7. Restablezca contraseñas o claves para todas las cuentas que utiliza la automatización de IBM. Para obtener más información, consulte [¿Cómo puedo proteger mi entorno para eliminar el acceso por parte de la automatización y el soporte de IBM?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)

## Resultados

El estado de la instancia pasa a ser **Modificando**.

Cuando la instancia se haya protegido correctamente, el estado de la instancia pasará a ser **Protegido** y solo estarán disponibles las propiedades de la instancia y el historial de despliegues.

### Enlaces relacionados

* [Visión general de VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Solicitud de instancias de VMware Federal](vc_fed_orderinginstance.html)
* [Visualización de instancias de VMware Federal](vc_fed_viewinginstance.html)
* [Supresión de instancias de VMware Federal](vc_fed_deletinginstance.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
