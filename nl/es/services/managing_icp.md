---

copyright:

  years:  2016, 2019

lastupdated: "2018-09-27"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Solicitud de IBM Cloud Private Hosted - en desuso

La información de este ha quedado en desuso. Para obtener la información más reciente acerca de IBM Cloud Private Hosted, consulte [Visión general de IBM Cloud Private Hosted](icp_overview.html).
{:deprecated}

{{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} despliega automáticamente {{site.data.keyword.cloud_notm}} Private Hosted en las instancias de VMware vCenter Server.

{{site.data.keyword.cloud_notm}} Private Hosted incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware e {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}.

## Especificaciones técnicas de IBM Cloud Private Hosted

Estos son los requisitos mínimos para solicitar el servicio {{site.data.keyword.cloud_notm}} Private Hosted:

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
  **Nota:** VMware vCenter Server on {{site.data.keyword.cloud_notm}} con Hybridity Bundle no está soportado.
* VMware NSX Advanced o Enterprise Edition
* Tres {{site.data.keyword.baremetal_long}}
* Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz
* 384 GB de RAM por servidor
* Un recurso compartido de archivos de almacenamiento NFS compartido con 8.000 GB a 4 IOPS/GB
* 33 licencias de núcleo de procesador de IBM Cloud Private Virtual
* Para la copia de seguridad de datos, se recomienda el servicio Veeam on IBM Cloud.

## Procedimiento para solicitar IBM Cloud Private Hosted

1. Solicite una nueva instancia de vCenter Server siguiendo los pasos del apartado [Solicitud de instancias de vCenter Server](../vcenter/vc_orderinginstance.html). También puede solicitar IBM Cloud Private Hosted para una instancia existente.
  **Importante:** Asegúrese de que el entorno cumple con los requisitos mínimos que se listan anteriormente.
2. Asegúrese de que tiene sus titularidades de IBM Cloud privado.
3. Después de recibir la confirmación de que la instancia de vCenter Server está lista para ser utilizada, continúe con los pasos siguientes para solicitar IBM Cloud Private Hosted.
4. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Cómo comenzar** en el panel de navegación izquierdo.
5. Desplácese hacia abajo en la página y bajo **Pedido de servicios adicionales**, pulse en la tarjeta **IBM Cloud Private Hosted**.
6. En la página **IBM Cloud Private Hosted on vCenter Server on IBM Cloud**, en el recuadro **Póngase en contacto con el equipo de DevOps de IBM Cloud Private Hosted**, describa sus requisitos y pulse **Solicitar una consulta**.

Un representante de {{site.data.keyword.cloud_notm}} Private Hosted DevOps se pondrá en contacto con usted a través de la información de contacto de {{site.data.keyword.cloud_notm}} y le ayudará a comenzar.
