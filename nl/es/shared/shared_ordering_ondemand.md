---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de Shared bajo demanda
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared se proporciona como una oferta experimental.
{:note}

Para bajo demanda, la vCPU y la RAM del centro de datos virtual se asignan según las necesidades y la cantidad de tiempo de asignación puede variar en función del uso global de vCPU y el consumo de RAM del centro de datos virtual.
* Los límites que se establecen para la cantidad de vCPU y RAM son valores máximos que se pueden consumir en cualquier momento.
* Los recursos de vCPU y RAM se pueden aumentar y disminuir más adelante según las necesidades.
* El coste se calcula por horas y se basa en el uso de recursos en el centro de datos virtual.
* No hay límites en la cantidad de almacenamiento que se puede asignar y utilizar en el centro de datos virtual. Los cargos son por horas en base a los GB de almacenamiento asignado.
* No hay límites en la cantidad de redes públicas de entrada y salida. El ancho de banda público se carga por GB.

## Requisitos para IBM Cloud for VMware Solutions Shared
{: #shared_ordering_ondemand-req}

### Cuenta de la infraestructura IBM Cloud
{: #shared_ordering_ondemand-account-req}

Para utilizar {{site.data.keyword.vmwaresolutions_short}} para solicitar IBM Cloud for VMware Solutions Shared, debe tener una cuenta de {{site.data.keyword.cloud_notm}} de **Pago según uso** o de **suscripción**. El coste de los recursos que se solicitan se factura a esa cuenta de {{site.data.keyword.cloud_notm}}.

### Requisitos de nombre de centro de datos virtual
{: #shared_ordering_ondemand-vdc-name-req}

El nombre del centro de datos virtual *debe* cumplir los requisitos siguientes. Los requisitos de denominación se aplicarán en el futuro.
* Solo se permiten caracteres alfabéticos en minúsculas, numéricos y el guión (-).
* El nombre debe empezar por un carácter alfabético en minúsculas.
* El nombre debe terminar en un carácter alfabético o numérico en minúsculas.
* La longitud máxima del nombre del centro de datos virtual es de 10 caracteres.
* El nombre del centro de datos virtual debe ser exclusivo dentro de su cuenta.

## Procedimiento para solicitar Shared bajo demanda
{: #shared_ordering_ondemand-procedure}

1. En el catálogo de {{site.data.keyword.cloud_notm}}, haga clic en el icono **VMware** en el panel de navegación de la izquierda y, a continuación, haga clic en la tarjeta **IBM Cloud for VMware Solutions Shared** en la sección **VMware Virtual Data Centers**.
2. En la página **IBM Cloud for VMware Solutions Shared**, haga clic en la tarjeta **Bajo demanda** y pulse **Crear**.
3. En la página **IBM Cloud for VMware Solutions Shared - Bajo demanda**, escriba el nombre del centro de datos virtual. Se preselecciona el {{site.data.keyword.CloudDataCent_notm}} donde está disponible la oferta.
4. Seleccione los límites de vCPU y RAM según sus requisitos.
5. En el panel **Resumen del pedido**, verifique la configuración y el coste estimado antes de realizar el pedido.
6. Pulse **Suministro**.

## Resultados después de solicitar Shared bajo demanda
{: #shared_ordering_ondemand-results}

* El despliegue de los recursos se inicia automáticamente y se recibe la confirmación de que el pedido se está procesando. Puede comprobar el estado de despliegue, incluyendo los problemas que puedan requerir su atención, visualizando **Estado del centro de datos virtual**.
* Una vez que los recursos están desplegados satisfactoriamente, se instalan los componentes que se describen en [Especificaciones técnicas de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) en la plataforma virtual de VMware.
* Cuando los recursos están listos para su uso, el estado se cambia a **Listo para su uso**.

## Enlaces relacionados
{: #shared_ordering_ondemand-related}

* [Visión general de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Solicitud de Shared reservado](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Gestión de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
