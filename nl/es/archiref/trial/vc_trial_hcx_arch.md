---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Diseño de la arquitectura de HCX on IBM Cloud para la versión de prueba de un solo nodo para vCenter Server on IBM Cloud
{: #vc_trial_hcx_arch}

VMware HCX on {{site.data.keyword.cloud}} con la prueba de un solo nodo para VMware vCenter Server on {{site.data.keyword.cloud_notm}} es una nueva oferta que facilita la conexión entre instancias de {{site.data.keyword.vmwaresolutions_short}} y el centro de datos virtualizado de VMware local. Aunque la recomendación para vCenter Server es un mínimo de tres nodos, la prueba de un solo nodo proporciona un método de bajo coste para probar y experimentar las ventajas de una implementación de nube híbrida.

{{site.data.keyword.vmwaresolutions_short}} incluye despliegues rápidos y totalmente automatizados de configuraciones de vCenter Server en {{site.data.keyword.cloud_notm}}. La oferta de la prueba de un solo nodo para vCenter Server complementa la infraestructura local y permite ejecutar cargas de trabajo existentes y futuras en {{site.data.keyword.cloud_notm}} sin conversión. La oferta utiliza las mismas herramientas, habilidades y procesos que se utilizan en el entorno local. Para obtener más información sobre las ofertas de {{site.data.keyword.vmwaresolutions_short}}, consulte [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

El servicio HCX on {{site.data.keyword.cloud_notm}} combina instancias de vCenter Server con los centros de datos virtualizados locales existentes al permitir crear extensiones de red y facilitar la migración bidireccional de las cargas de trabajo. Los componentes de HCX on IBM Cloud, que se despliegan como máquinas virtuales (VM) en el sitio de destino de {{site.data.keyword.cloud_notm}} VMware, permiten establecer una conexión con los componentes de HCX on {{site.data.keyword.cloud_notm}} instalados en el sitio de origen local homólogo.

Figura 1. Arquitectura de HCX

![Arquitectura de HCX](hcx-architecture.svg "Arquitectura de HCX")

En la siguiente información se muestra el diseño de la implementación del servicio HCX on {{site.data.keyword.cloud_notm}}. Incluye tanto los componentes de la instancia de {{site.data.keyword.vmwaresolutions_short}} del lado del destino como los componentes que se despliegan en el entorno de origen local.

## Visión general de HCX on IBM
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} integra de forma transparente las redes de vSphere vCenter locales en despliegues de {{site.data.keyword.vmwaresolutions_short}}. La red híbrida amplía las redes de vSphere locales a {{site.data.keyword.cloud_notm}}, lo que da soporte a la movilidad bidireccional de VM.

HCX es propietario de los procesos de cifrado y de descifrado de origen y de destino, lo que garantiza la seguridad y proporciona métodos de admisión para flujos de trabajo híbridos, como migración de máquinas virtuales y extensión de red. Esta oferta crea una red de área amplia (WAN) optimizada definida por software para aumentar el rendimiento de la red extendida, ofreciendo un rendimiento que se acerca a la velocidad de la LAN. HCX habilita la carga de trabajo bidireccional y la migración de políticas de seguridad de VMware NSX a {{site.data.keyword.cloud_notm}}, se integra con vSphere vCenter y se gestiona desde el cliente web de vSphere.

### Extensión de red de capa 2
{: #vc_trial_hcx_arch-layer-2-extension}

HCX permite que una propiedad de vSphere local existente pueda extender de forma segura una red desde su vCenter local a un {{site.data.keyword.CloudDataCent_notm}} que ejecute VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} o vCenter Server. Esto se consigue gracias a las siguientes características:

* HCX proporciona un dispositivo denominado concentrador de capa 2 (L2C).
* Las redes extendidas se enlazan a dispositivos {{site.data.keyword.cloud_notm}} NSX Edge desplegados en vCenter Server.
* La posibilidad de desplegar varios concentradores de capa 2 estándar para lograr la escalabilidad y aumentar el rendimiento desde el vCenter local.
* Las VM que se migran a través de la pasarela de nube y sobre la capa 2 extendida pueden conservar sus direcciones IP y MAC.

### Migración de máquinas virtuales
{: #vc_trial_hcx_arch-vm-mig}

HCX proporciona los tres métodos siguientes de traslado de VM:

* Migración con bajo tiempo de inactividad
* Migración de vSphere vMotion
* Migración en frío

#### Migración con bajo tiempo de inactividad
{: #vc_trial_hcx_arch-low-downtime-mig}

La migración con bajo tiempo de inactividad se basa en la réplica de vSphere, que es una tecnología distribuida que se implementa en el hipervisor de VMware ESX o de VMware ESXi. El despliegue de HCX local crea una réplica de una VM activa en {{site.data.keyword.cloud_notm}}, realiza una conmutación para apagar la VM de origen y enciende la máquina virtual migrada. El método de migración es siempre a través de la pasarela de nube. El medio de transporte puede ser Internet, una red extendida de capa 2 o una línea Direct Connect. Puede migrar una VM más de una vez en cualquier dirección.

#### Migración de vSphere vMotion
{: #vc_trial_hcx_arch-vmotion-mig}

Puede transferir máquinas virtuales activas mediante la migración de vSphere vMotion a través de una red que se extiende a {{site.data.keyword.cloud_notm}}. La migración de vMotion también se denomina migración con tiempo de inactividad cero o vMotion entre nubes.

#### Migración en frío
{: #vc_trial_hcx_arch-cold-mig}

La migración en frío proporciona la capacidad de transferir una máquina virtual apagada a {{site.data.keyword.cloud_notm}} a través de una red expandida creada mediante el concentrador de capa 2.

#### Características comunes de la migración
{: #vc_trial_hcx_arch-common-feat}

Las características siguientes están disponibles en los tres tipos de migración:

* Optimización de WAN definida por software, que aumenta el rendimiento y la velocidad de la migración.
* Planificación de la migración en un momento especificado.
* Conservación del nombre de host, del nombre de VM o de ambos.

### Redes
{: #vc_trial_hcx_arch-network}

Las siguientes características de red están integradas en la pasarela de nube y en los concentradores de capa 2.

#### Direccionamiento inteligente de flujos
{: #vc_trial_hcx_arch-intel-flow}

El direccionamiento inteligente de flujos selecciona automáticamente la mejor conexión en función de la vía de acceso a internet, aprovechando de forma eficiente toda la conexión de modo que las cargas de trabajo se muevan lo más rápido posible. Cuando flujos de gran tamaño, como copias de seguridad o réplicas, provocan una contención de la CPU, los flujos más pequeños se direccionan a las CPU menos ocupadas, lo que mejora el rendimiento del tráfico interactivo.

#### Direccionamiento de proximidad
{: #vc_trial_hcx_arch-prox-routing}

El direccionamiento de proximidad garantiza que el reenvío entre VM conectadas a redes extendidas y direccionadas, tanto en el entorno local como en la nube, es simétrico. Esta característica requiere servicios avanzados de red con direccionamiento dinámico, que se configura entre el entorno local del cliente y la nube.

Cuando los usuarios extienden sus redes a la nube, la conectividad de capa 2 se extiende a las redes de {{site.data.keyword.cloud_notm}}. Sin embargo, sin la optimización de direccionamiento, las solicitudes de comunicación de capa 3 deben volver al origen de red local que se direccionen. Este viaje de retorno se denomina "tromboning" o "hairpinning". El método tromboning no resulta eficiente porque los paquetes deben realizar un viaje de ida y vuelta entre el origen de red y la nube, aunque tanto la VM de origen como la de destino residan en la nube.

Si la vía de acceso reenvío incluye cortafuegos con estado u otro equipo en línea que deba ver los dos lados de la conexión, es posible que la comunicación falle. Se produce un error de comunicación de VM, sin optimización de rutas, cuando la vía de acceso de salida de la nube es la red extendida de capa 2 o la red direccionada de la organización. La red local no conoce el "acceso directo" de la red extendida. Este problema se denomina direccionamiento asimétrico. La solución consiste en habilitar el direccionamiento de proximidad para que la red local pueda conocer las rutas desde {{site.data.keyword.cloud_notm}}.

La pasarela de nube mantiene un inventario de las VM en la nube. También comprende los siguientes estados de VM:

* Transferida a {{site.data.keyword.cloud_notm}} sin vMotion (migración con tiempo de inactividad cero).
* Migrada a la nube mediante una réplica basada en host (migración con bajo tiempo de inactividad)
* Creada en la nube (en una red extendida)

#### Seguridad
{: #vc_trial_hcx_arch-sec}

La pasarela de nube ofrece AES-GCM compatible con Suite B con IKEv2, descarga AES-NI y control de admisiones basado en flujo. HCX también es propietario del proceso de cifrado y de descifrado de origen y de destino, lo que garantiza la seguridad y la administración de los flujos de trabajo híbridos, como migración de VM y extensión de red. Puede migrar políticas de seguridad definidas y asignadas a una máquina virtual de forma local con la VM en {{site.data.keyword.cloud_notm}}.

Es necesario cumplir las condiciones siguientes para la migración de políticas:

* El centro de datos local ejecuta NSX V6.2.2 o superior.
* En vSphere, la política de seguridad es una sola sección de NSX que puede tener muchas reglas.
* Puede nombrar un conjunto de direcciones IP o direcciones MAC para que participen en la política.
* El nombre del conjunto de MAC o del conjunto de IP no puede superar los 218 caracteres.
* Las reglas soportadas especifican direcciones IP de capa 3 o conjuntos de IP, o bien direcciones MAC de capa 2 o conjuntos de MAC como el origen o el destino.

### Componentes de HCX
{: #vc_trial_hcx_arch-hcx-comp}

El servicio HCX on {{site.data.keyword.cloud_notm}} despliega cuatro dispositivos virtuales que se instalan y configuran tanto en el centro de datos local como en el destino de IBM Cloud. En la siguiente información se describe cada uno de los cuatro dispositivos virtuales necesarios. Opcionalmente, es posible que se necesiten dispositivos de borde, en función del diseño de implementación.

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

El dispositivo virtual HCX Manager es una extensión de vCenter local. El dispositivo se despliega como una VM y su estructura de archivos contiene los otros dispositivos virtuales de servicio híbrido. HCX Manager supervisa el despliegue y la configuración de la pasarela de nube, los concentradores de capa 2 y el dispositivo virtual de optimización de WAN, tanto en el entorno local como en {{site.data.keyword.cloud_notm}}.

#### Hybrid Cloud Gateway
{: #vc_trial_hcx_arch-hcg}

Hybrid Cloud Gateway (CGW) mantiene un canal seguro entre el estado de vSphere local e {{site.data.keyword.cloud_notm}}. HCX utiliza cifrado potente para arrancar la conexión de sitio a sitio con {{site.data.keyword.cloud_notm}}. El canal seguro entre vSphere e {{site.data.keyword.cloud_notm}} evita problemas de seguridad de red de tipo "middle mile". La pasarela de nube también incorpora la tecnología de réplica de vSphere para realizar la migración bidireccional.

#### Optimización de WAN
{: #vc_trial_hcx_arch-wan-opt}

El dispositivo de optimización de WAN es el componente que realiza el acondicionamiento de la WAN para reducir los efectos de la latencia. También incorpora correcciones de errores de reenvío para evitar escenarios de pérdida de paquetes y desduplicación de los patrones de tráfico redundantes. En conjunto, estos recursos reducen el uso de ancho de banda y garantizan un uso eficiente de la capacidad de red disponible para acelerar la transferencia de datos a y desde {{site.data.keyword.cloud_notm}}.

La migración de VM se basa en la combinación de pasarela de nube y del dispositivo de optimización de WAN para lograr una movilidad sin igual entre vSphere local e {{site.data.keyword.cloud_notm}}. Además, la extensión de capa 2 se beneficia de la optimización de WAN cuando la vía de acceso de datos se direcciona a través de la pasarela de nube.
{:important}

#### Concentradores de capa 2
{: #vc_trial_hcx_arch-layer-2-conc}

Los dispositivos concentradores de capa 2 (L2C) permiten la extensión de una red de capa 2 del centro de datos de vSphere local a {{site.data.keyword.cloud_notm}}.

Los concentradores de capa 2 tienen las siguientes interfaces:

* **Interfaz troncal interna** esta interfaz maneja el tráfico de VM local para las redes ampliadas utilizando una correlación de puente de traslado con una red extendida correspondiente en {{site.data.keyword.cloud_notm}}.
* **Interfaz de enlace ascendente** HCX utiliza esta interfaz para enviar el tráfico de superposición encapsulado a y desde {{site.data.keyword.cloud_notm}}. Los datos de la aplicación viajan a través de la interfaz de enlace ascendente.

### Arquitectura de despliegue
{: #vc_trial_hcx_arch-deployment}

Para obtener información sobre el despliegue de HCX on {{site.data.keyword.cloud_notm}}, consulte [Despliegue y operaciones de VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf).
