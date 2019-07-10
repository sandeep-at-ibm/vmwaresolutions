---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: F5 license activation, F5 configuration, order F5

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de F5 on IBM Cloud
{: #f5_ordering}

Puede solicitar el servicio de F5 on {{site.data.keyword.cloud}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de F5 on IBM Cloud para una nueva instancia
{: #f5_ordering-new}

Puede solicitar una nueva instancia con F5 on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **F5 on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **F5 on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de F5 on IBM Cloud para una instancia existente
{: #f5_ordering-existing}

Puede añadir el servicio de F5 on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **F5 on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Solicitud de F5 on IBM Cloud para instancias privadas
{: #f5_ordering-private}

Al solicitar F5 on {{site.data.keyword.cloud_notm}} para instancias que no estén configuradas con interfaces públicas, debe proporcionar un servidor proxy para completar la instalación. El servidor proxy HTTP debe configurarse y estar disponible a través de VRF (Direccionamiento virtual y reenvío) para que se pueda iniciar la instalación de F5 on {{site.data.keyword.cloud_notm}}.

Los puntos finales de BigIP Virtual Edition (VE) deben poder activar su licencia antes de pasar a estar operativos. Una vez que se hayan instalado los puntos finales de BigIP VE, ya no requerirán el uso del servidor proxy.

El servicio F5 on {{site.data.keyword.cloud_notm}} no se puede añadir sin un servidor proxy funcional en el momento de la instalación del servicio.
{:note}

## Configuración del servicio de F5 on IBM Cloud
{: #f5_ordering-config}

Al solicitar el servicio, proporcione los valores siguientes:

### Conexión de activación de licencias de F5
{: #f5_ordering-config-license}

Seleccione **Red pública** o **Red privada** para la activación de la licencia. Si el clúster de destino está configurado con interfaces de red solo privadas, solo está disponible la opción **Red privada**. Esta selección determina la forma en que los servidores virtuales F5 contactarán con el servidor de licencias F5, y no afecta al plano de datos de la carga de trabajo.

Si selecciona **Red privada**, especifique los siguientes valores:
* **Dirección IP de proxy:** la dirección IPv4 del servidor proxy.
* **Número de puerto de proxy**: el número de puerto del servidor proxy, que suele ser 8080 o 3128.

No se da soporte al proxy autenticado.
{:note}

### Nombre
{: #f5_ordering-config-name}

Especifique el nombre de servicio.

### Ancho de banda máximo
{: #f5_ordering-config-bandwidth}

Especifique el rendimiento máximo del dispositivo F5 BIG–IP.

### Modelo de licencia
{: #f5_ordering-config-license-model}

El modelo de licencia del servicio F5 on {{site.data.keyword.cloud_notm}} ofrece las siguientes opciones:
<dl class="dl">
        <dt class="dt dlterm">Good</dt>
        <dd class="dd">Esta oferta utiliza BIG-IP Local Traffic Manager™ (LTM) VE, que funciona como arquitectura completa de proxy, para ofrecer una gestión inteligente del tráfico local, visibilidad completa del tráfico SSL y analíticas y supervisión de estado para garantizar que los servidores de aplicaciones siempre están disponibles para sus usuarios.</dd>
        <dt class="dt dlterm">Better</dt>
        <dd class="dd">Esta oferta se basa en las ventajas de la opción **Good**, con la adición de los módulos BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM) y BIG-IP Application Acceleration Manager™ (AAM). Ofrece servicios de gestión global del tráfico, optimización del rendimiento de las aplicaciones y funciones avanzadas de cortafuegos de red y de mitigación de denegación de servicio distribuida (DDoS).</dd>
        <dt class="dt dlterm">Best</dt>
        <dd class="dd">Además de las ofertas **Good** y **Better**, BIG-IP Application Security Manager™ (ASM) proporciona una protección completa de las aplicaciones frente a las 10 principales amenazas de L7 DDoS, Open Web Application Security Project (OWASP) y frente a vulnerabilidades comunes de las aplicaciones. BIG-IP Access Policy Manager™ (APM) ofrece a los usuarios acceso seguro y simplificado a las aplicaciones situadas en cualquier punto del entorno de nube e incorpora funciones como SSO (inicio de sesión único) y MFA (Multi-Factor Authentication).</dd>
</dl>

No puede cambiar el modelo de licencia después de la instalación del servicio. Para cambiar el modelo de licencia, debe eliminar el servicio existente y reinstalar el servicio seleccionando otro modelo de licencia.
{:important}

## Enlaces relacionados
{: #f5_ordering-releated}

* [Visión general de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [Gestión de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Guías de despliegue de F5](https://www.f5.com/services/resources/deployment-guides){:new_window}
