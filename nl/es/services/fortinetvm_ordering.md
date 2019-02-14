---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de FortiGate Virtual Appliance on IBM Cloud

Puede solicitar FortiGate Virtual Appliance en el servicio de {{site.data.keyword.cloud}} cuando solicite una nueva instancia con el servicio incluido o añadiendo el servicio a la instancia existente.

## Solicitud de FortiGate Virtual Appliance on IBM Cloud para una nueva instancia

Puede solicitar una nueva instancia con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **FortiGate Virtual Appliance on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **FortiGate Virtual Appliance on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de FortiGate Virtual Appliance on IBM Cloud para una instancia existente

Puede añadir el servicio de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} a una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **FortiGate Virtual Appliance on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Configuración del servicio de FortiGate Virtual Appliance on IBM Cloud

Al solicitar el servicio, proporcione los valores siguientes:

### FortiGuard Network Connection

Seleccione **Red pública** o **Red privada** para FortiGuard. Si el clúster de destino está configurado con interfaces de red solo privadas, solo está disponible la opción **Red privada**. Esta selección determina la forma en que FortiGuard contactará con el servidor de licencias Fortinet para activar la licencia y para descargar los parches de seguridad y no afecta al plano de datos de la carga de trabajo.

Si selecciona **Red privada**, especifique los siguientes valores:
* **Dirección IP de proxy:** la dirección IPv4 del servidor proxy.
* **Número de puerto de proxy**: el número de puerto del servidor proxy, que suele ser 8080 o 3128.
* **Nombre de usuario de proxy**: si necesita autenticación de proxy, especifique el nombre de usuario del servidor proxy.
* **Contraseña de proxy**: si necesita autenticación de proxy, especifique la contraseña del servidor proxy.

### Nombre

Especifique el nombre de servicio.

### Tamaño del despliegue

{{site.data.keyword.cloud_notm}} proporciona las siguientes opciones de tamaño de despliegue:
* Pequeño (2 vCPU / 4 GB de RAM)
* Medio (4 vCPU / 6 GB de RAM)
* Grande (8 vCPU / 12 GB de RAM)

### Modelo de licencia

El modelo de licencia de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} ofrece las siguientes opciones:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Este paquete incluye Stateful Packet Inspection, VLAN Protection y Advanced Logging, Ingress and Egress Firewall Rules, SSL/IPSec VPN Termination y soporte las 24 horas.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Este paquete incluye todos los servicios de cortafuegos estándar además del servicio de protección de malware avanzado (AMP). Incluye Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service y Content Disarm & Reconstruct. También incluye servicios de filtrado de web, IPS, antispam, control de aplicaciones y FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Este paquete incluye todos los servicios de cortafuegos estándar y los servicios UTM, además de los siguientes servicios:<ul><li>Cloud Access Security Broker (CASB): este servicio proporciona visibilidad, conformidad, seguridad de datos y protección frente a amenazas para los servicios basados en la nube.</li><li>Industrial Security: este servicio ofrece firmas para los protocolos ICS/SCADA más utilizados.</li><li>Security Rating: este servicio ofrece funciones de auditoría para identificar las principales vulnerabilidades y los puntos débiles de la configuración e implementar las recomendaciones de las mejores prácticas.</li></ul></dd>
</dl>

En el tercer trimestre de 2018, Fortinet ha añadido tres nuevos servicios (CASB, Industrial Security y Security Rating) a su paquete Enterprise. Estos servicios solo están disponibles en FortiGate 6.0.
{:note}

No puede cambiar el modelo de licencia después de la instalación del servicio. Para cambiar el modelo de licencia, debe eliminar el servicio existente y reinstalar el servicio seleccionando otra opción de licencia.
{:important}

### Enlaces relacionados

* [Visión general de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_considerations.html)
* [Gestión de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos de Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
