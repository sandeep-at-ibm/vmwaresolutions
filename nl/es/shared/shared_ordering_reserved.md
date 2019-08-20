---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resources, order reserved shared, order reserved resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de Shared reservado
{: #shared_ordering_reserved}

{{site.data.keyword.vmwaresolutions_full}} Shared se proporciona como una oferta experimental.
{:note}

Para Shared Reserved, las reservas de vCPU y RAM del centro de datos virtual están preasignadas y su disponibilidad está garantizada.
* El coste se calcula mensualmente para la reserva completa y se basa en el tamaño de asignación del centro de datos virtual.
* Los recursos de vCPU y RAM se pueden aumentar y disminuir más adelante según las necesidades.
* No hay límites en la cantidad de almacenamiento que se puede asignar y utilizar en el centro de datos virtual. Los cargos son por horas en base a los GB de almacenamiento asignado.
* No hay límites en la cantidad de redes públicas de entrada y salida. El ancho de banda público se carga por GB.

## Requisitos para IBM Cloud for VMware Solutions Shared
{: #shared_ordering_reserved-req}

### Cuenta de la infraestructura IBM Cloud
{: #shared_ordering_reserved-account-req}

Para utilizar {{site.data.keyword.vmwaresolutions_short}} para solicitar IBM Cloud for VMware Solutions Shared, debe tener una cuenta de {{site.data.keyword.cloud_notm}} de **Pago según uso** o de **suscripción**. El coste de los recursos que se solicitan se factura a esa cuenta de {{site.data.keyword.cloud_notm}}.

### Requisitos de nombre de centro de datos virtual
{: #shared_ordering_reserved-vdc-name-req}

El nombre del centro de datos virtual *debe* cumplir los requisitos siguientes. Los requisitos de denominación se aplicarán en el futuro.
* Solo se permiten caracteres alfabéticos en minúsculas, numéricos y el guión (-).
* El nombre debe empezar por un carácter alfabético en minúsculas.
* El nombre debe terminar en un carácter alfabético o numérico en minúsculas.
* La longitud máxima del nombre del centro de datos virtual es de 10 caracteres.
* El nombre del centro de datos virtual debe ser exclusivo dentro de su cuenta.

## Procedimiento para solicitar Shared reservado
{: #shared_ordering-procedure}

1. En el catálogo de {{site.data.keyword.cloud_notm}}, haga clic en el icono **VMware** en el panel de navegación de la izquierda y, a continuación, haga clic en la tarjeta **IBM Cloud for VMware Solutions Shared** en la sección **VMware Virtual Data Centers**.
2. En la página **IBM Cloud for VMware Solutions Shared**, haga clic en la tarjeta **Reservado** y pulse **Crear**.
3. En la página **IBM Cloud for VMware Solutions Shared - Reservado**, escriba el nombre del centro de datos virtual.
4. Elija el compromiso de tiempo de reserva de los recursos. Se preselecciona el {{site.data.keyword.CloudDataCent_notm}} donde está disponible la oferta.
5. Especifique la reserva de recursos:
    * Si selecciona **Preconfigurado**, elija una de las configuraciones preestablecidas.
    * Al seleccionar **Personalizado**, especifique la vCPU y las reservas de RAM.
6. En el panel **Resumen del pedido**, verifique la configuración y el coste estimado antes de realizar el pedido.
7. Pulse **Suministro**.

## Resultados después de solicitar Shared Reservado
{: #shared_ordering_reserved-results}

* El despliegue de los recursos se inicia automáticamente y se recibe la confirmación de que el pedido se está procesando. Puede comprobar el estado de despliegue, incluyendo los problemas que puedan requerir su atención, visualizando **Estado del centro de datos virtual**.
* Una vez que los recursos están desplegados satisfactoriamente, se instalan los componentes que se describen en [Especificaciones técnicas de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) en la plataforma virtual de VMware.
* Cuando los recursos están listos para su uso, el estado se cambia a **Listo para su uso**.

## Enlaces relacionados
{: #shared_ordering_reserved-related}

* [Visión general de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Solicitud de Shared bajo demanda](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Gestión de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
