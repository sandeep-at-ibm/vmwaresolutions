---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-10"

---

# Casos prácticos

## Migración de cargas de trabajo a IBM Cloud
Acme Skateboards desea extender su VMware SDDC local a una instancia de VMware vCenter Server on {{site.data.keyword.cloud}}. Necesitan mantener su negocio activo y en funcionamiento y reducir al mínimo el tiempo de inactividad. Volver a configurar sus aplicaciones para que se ejecuten en la nube no es la solución óptima.

VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) permite crear conexiones sin fisuras entre {{site.data.keyword.cloud_notm}} y un centro de datos virtualizado de VMware local.

La oferta vCenter Server con el paquete híbrido (Hybridity) de {{site.data.keyword.cloud_notm}} permite establecer conexiones seguras entre el sitio de origen local y el sitio de destino de {{site.data.keyword.cloud_notm}}.

Figura 1. Servicios de VMware Hybridity

![Servicios de VMware Hybrid Cloud Extension](vcsicp-hcx.svg)

VMware Hybrid Cloud Extension Services crea una interconectividad ligeramente acoplada entre un entorno local e {{site.data.keyword.cloud_notm}} y ofrece prestaciones como las siguientes:
- **Interconectividad sencilla**: se establecen fácilmente conexiones lógicas de red sobre cualquier conexión física, como por ejemplo internet pública, VPN privada o {{site.data.keyword.cloud_notm}} Direct Link.
- **Extensión de capa 2**: las redes locales se amplían a la nube, incluidas subredes locales y direccionamiento IP.
- **Cifrado**: el tráfico de red se cifra de forma segura entre los sitios iguales (peer).
- **Optimización de red**: selecciona la mejor conexión y gestiona la conexión de forma eficiente de modo que el tráfico se transmite de la forma más rápida posible.
- **Desduplicación de datos**: se puede conseguir una reducción del 50% en el tráfico de red.
- **Direccionamiento inteligente**: cuando se mueve una carga de trabajo, el direccionamiento de proximidad puede cambiar la vía de acceso de red (es decir, la pasarela) para que el tráfico de la red utilice la pasarela del sitio de destino y no lo "devuelva" (hairpin) al sitio de origen.
- **Migración con tiempo de inactividad cero**: utilice vMotion para trasladar una máquina virtual (VM) en ejecución a la nube o viceversa.
- **Migración planificada**: puede crear una réplica de las máquinas virtuales que desee en el sitio de destino y luego activar en dicho sitio en un momento designado para sustituir los sistemas que se ejecutan en el sitio de origen.
- **Migración de políticas de seguridad**: si NSX se utiliza en local, las políticas de seguridad, los cortafuegos, etc., se trasladan junto con la carga de trabajo.

Con esta solución, Acme Skateboards ha migrado correctamente sus cargas de trabajo locales de VMware a {{site.data.keyword.cloud_notm}}, cumpliendo con los requisitos de tiempo de inactividad bajo y sin tener que volver a configurar las aplicaciones.

## Despliegue de una arquitectura híbrida

Acme Skateboards desea desplegar una arquitectura híbrida en {{site.data.keyword.cloud_notm}}, consistente en vCenter Server e {{site.data.keyword.icpfull_notm}}, para su proceso de modernización de aplicaciones. Los requisitos son ejecutar sus bases de datos en máquinas virtuales y las aplicaciones y los servicios web en contenedores y utilizar un conjunto común de herramientas para la gestión de red y de la seguridad.

Figura 2. Aplicación híbrida de Acme Skateboards

![Aplicación híbrida de Acme Skateboards](vcsicp-acme-skateboards-app.svg)

{{site.data.keyword.vmwaresolutions_short}} proporciona la automatización para desplegar componentes de tecnología VMware en {{site.data.keyword.CloudDataCents_notm}} en todo el mundo. La arquitectura consta de una sola región de nube y permite la ampliación a más regiones de nube ubicadas en otra geografía o en otro pod de {{site.data.keyword.cloud_notm}} dentro del mismo centro de datos.

Los productos {{site.data.keyword.icpfull_notm}} y Cloud Automation Manager (CAM) se despliegan manualmente en la plataforma de virtualización local, lo que permite gestionar la nube desde la ubicación local. Como alternativa, {{site.data.keyword.icpfull_notm}} y CAM se ofrecen como extensiones de servicio de un despliegue de vCenter Server nuevo o existente, mediante automatización, lo que permite gestionar la nube desde {{site.data.keyword.cloud_notm}}.

El diagrama siguiente representa {{site.data.keyword.icpfull_notm}} que se ejecuta en una instancia de vCenter Server. NSX-V está configurado con una conmutación/VXLAN dedicada, un DLR y un ESG específicamente diseñado para la red de superposición de {{site.data.keyword.icpfull_notm}}, y el direccionamiento se configura a través del ESG para acceder a la red subyacente.

Mediante la automatización de {{site.data.keyword.cloud_notm}}, Acme Skateboards puede ofrecer una solución híbrida que incluye VMware on {{site.data.keyword.cloud_notm}} para ejecutar sus VM de base de datos e {{site.data.keyword.icpfull_notm}} on VMware en {{site.data.keyword.cloud_notm}} para ejecutar sus apps y servicios web de cara al cliente en contenedores. NSX les ofrece un conjunto común de herramientas de gestión para red y seguridad en la red subyacente.

Figura 3. vCenter Server con {{site.data.keyword.icpfull_notm}}

![vCenter Server con {{site.data.keyword.icpfull_notm}}](vcsicp-virtual-icp-deployment-vcs.svg)

### Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
