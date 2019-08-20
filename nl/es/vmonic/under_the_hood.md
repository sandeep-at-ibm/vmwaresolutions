---

copyright:

  years:  2019

lastupdated: "2019-07-09"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions: visión general
{: #under_the_hood}

## Desplegar y gestionar entornos virtualizados de VMware
{: #under_the_hood-deploy}

Eche un vistazo en profundidad a la arquitectura de {{site.data.keyword.vmwaresolutions_full}}, una oferta de
{{site.data.keyword.cloud_notm}} que proporciona el despliegue y la gestión de entornos virtualizados de VMware. En esta guía de aprendizaje, se mostrarán los componentes de la oferta, de manera que pueda ver cómo funcionan de manera conjunta para suministrar y mantener el entorno en la nube pública.

## Dos empresas, una solución optimizada
{: #under_the_hood-two-companies}

Desde hace algún tiempo, los usuarios han estado desplegando entornos virtualizados de VMware en la nube pública de IBM, ya sea por sí mismos o con la ayuda de servicios profesionales. En febrero de 2016, [IBM y VMware anunciaron su asociación](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external} para automatizar el proceso de despliegue de software de VMware y entornos de VMware en
{{site.data.keyword.cloud_notm}}. Uno de los primeros frutos de esta asociación ha sido la posibilidad de solicitar diversos despliegues y licencias de productos de VMware desde la consola de {{site.data.keyword.vmwaresolutions_short}} y, posteriormente, ofrecer
[VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external} en
{{site.data.keyword.cloud_notm}}. Además, IBM y VMware han colaborado para producir conjuntamente una
[arquitectura de referencia estándar y una prescripción de despliegue para VMware](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external} en la nube pública de IBM.

En otoño de 2016, IBM y VMware publicaron conjuntamente {{site.data.keyword.vmwaresolutions_short}}. Este conjunto de ofertas se basa en las tecnologías de virtualización de VMware, incluyendo el cálculo virtualizado (VMware vSphere), redes (VMware NSX) e incluyendo de manera opcional almacenamiento virtualizado (VMware vSAN). Estos entornos se denominan, con acierto, centros de datos definidos por software.

{{site.data.keyword.vmwaresolutions_short}} se basa en la tecnología de VMware para optimizar de manera significativa el despliegue y la gestión de estos centros de datos definidos por software en la nube pública de IBM. Mediante el uso de
{{site.data.keyword.vmwaresolutions_short}}, ahora es posible desplegar partes de la arquitectura de referencia estándar en
{{site.data.keyword.cloud_notm}} de manera automática en lugar de manual. Entornos que anteriormente se desplegaban y configuraban en semanas, ahora se pueden suministrar en cuestión de horas.

Esta facilidad de despliegue le permite centrarse en la implementación de soluciones por encima de VMware, en lugar de crear su entorno. Con entornos a su disposición de forma rápida, puede crear tanto soluciones de nube híbridas que abarquen su nube privada y la nube pública de IBM como soluciones nativas de la nube en la nube pública de IBM. Mediante la combinación de varios despliegues, puede añadir fácilmente funciones de recuperación tras desastre o alta disponibilidad a sus soluciones.

Echemos un vistazo ahora a la arquitectura de {{site.data.keyword.vmwaresolutions_short}}. Obtendrá información sobre los distintos componentes que forman parte de la solución y cómo funcionan de manera conjunta para proporcionar y gestionar su centro de datos definido por software en {{site.data.keyword.cloud_notm}}. También aprenderá sobre la topología de la red y sobre las diversas opciones de las que dispone para conectarse a su entorno.

## Aspectos básicos de IBM Cloud for VMware Solutions

Los centros de datos definidos por software se suministran y gestionan utilizando la
[consola de {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}. Inicie sesión en la consola utilizando su cuenta de IBMid.

Desde el catálogo de VMware Solutions, puede suministrar uno de los diversos tipos de entornos de virtualización. La solución de virtualización destacada es *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*, que ofrece el hipervisor vSphere de VMware, VMware vCenter Server, VMware NSX y, de manera opcional, VMware vSAN. También puede suministrar a este entorno más servicios adicionales que proporcionen servicios de copia de seguridad, recuperación tras desastre, migración, seguridad, conformidad y red.

Antes de solicitar una instancia de vCenter Server, debe configurar la clave de API de la infraestructura de
{{site.data.keyword.cloud_notm}} en el catálogo de VMware Solutions. Para ello, pulse sobre el enlace
[Valores](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external} del menú de la izquierda de la consola y especifique su nombre de usuario y clave de API cuando se le soliciten las credenciales de infraestructura de
{{site.data.keyword.cloud_notm}}. El sistema verificará que su clave de API y su cuenta tienen los permisos y valores adecuados para desplegar su instancia.

Al solicitar su instancia de vCenter Server, elija primero su nombre y la versión de VMware vSphere. Todas las instancias de VMware se despliegan conjuntamente con controladores de dominio de Microsoft Active Directory, y para fines del inicio de sesión único, debe designar la instancia como un sitio primario o secundario. Una instancia primaria es la primera o la única instancia del dominio de inicio de sesión único. Puede desplegar más instancias secundarias y asociarlas al mismo dominio de inicio de sesión único de una instancia primaria existente. A continuación, elija si desea traer sus propias licencias de VMware o la edición de la licencia que desee alquilar de {{site.data.keyword.cloud_notm}}. Por último, elija la región de {{site.data.keyword.cloud_notm}} y el centro de datos para su instancia, así como las características de CPU y memoria de los hosts del clúster.

En la siguiente parte de la página del pedido, debe especificar las características de almacenamiento y redes de la instancia. Puede elegir entre el almacenamiento vSAN y NFS para el clúster, con la posibilidad de elegir el tamaño y el número de discos flash vSAN y la edición de la licencia de vSAN, o el tamaño, recuento y rendimiento de los volúmenes de almacenamiento NFS. Para la red, puede elegir el prefijo de nombre de red de los hosts y el subdominio y el dominio del clúster. Tiene la opción de desplegar los controladores de Active Directory como una instancia de servidor virtual (VSI) de {{site.data.keyword.cloud_notm}} individual. O bien puede desplegar los controladores como dos máquinas virtuales (VM) dentro del clúster (para esas VM tiene que proporcionar licencias y activación).

En la parte inferior de la página del pedido de vCenter Server, puede seleccionar entre diversos servicios adicionales que puede desplegar para su instancia de VMware y que se facturarán en su cuenta de {{site.data.keyword.cloud_notm}}. Algunos servicios requieren configuración adicional, que puede especificar como parte del formulario de pedido.

El formulario de pedido calcula y muestra una estimación de precio en función de lo que seleccione. Tiene la oportunidad de revisar esta estimación, así como los diversos términos y condiciones, antes de realizar su pedido.

### Opciones de despliegue
{: #under_the_hood-deploy-options}

El formulario de pedido de vCenter Server le ofrece varias opciones de CPU, memoria y almacenamiento para su instancia. Hay nuevas opciones disponibles de manera regular, por lo que debe comprobar el catálogo de
{{site.data.keyword.cloud_notm}} para ver la información de disponibilidad más reciente.

{{site.data.keyword.cloud_notm}} despliega su instancia de vCenter Server utilizando tres VLAN: una pública y dos privadas. La VLAN pública está conectada a interfaces duales de 10 GbE y se reserva en gran medida para un uso según su criterio para la conectividad pública o el tunelado para sus propios despliegues de carga de trabajo. No obstante, en tiempo de despliegue, se despliega un par de NSX Edge Services Gateway en la VLAN pública para permitir que algunos servicios adicionales se conecten a la red pública para fines de licencia y facturación. Las VLAN privadas están conectadas a interfaces duales de 10 GbE independientes: la primera VLAN privada se utiliza para comunicaciones de gestión y NSX VTEP, y la segunda se utiliza para vMotion y para el tráfico del almacenamiento NFS.

Las instancias de VMware se pueden suministrar en 35 {{site.data.keyword.CloudDataCents_notm}} distintos. {{site.data.keyword.cloud_notm}} suministra nuevos centros de datos de vez en cuando. Consulte el catálogo de {{site.data.keyword.cloud_notm}} para ver la lista de ubicaciones disponibles más reciente.

### Despliegue de la instancia
{: #under_the_hood-inst-deploy}

Cuando solicite una nueva instancia de VMware vCenter, debe elegir la especificación y la ubicación de la instancia. {{site.data.keyword.vmwaresolutions_short}} utilizará a continuación su nombre de usuario y clave de API de
{{site.data.keyword.cloud_notm}} seleccionados con anterioridad para coordinar el proceso completo de solicitud, instalación y configuración del entorno de virtualización. Esto incluye:

1. Solicitud de VLAN y subredes para la red.
2. Pedido de {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} con vSphere Hypervisor instalado.
3. Despliegue y configuración de VMware vCenter Server con un Platform Services Controller incorporado, VMware NSX Manager, controladores y Edge Services Gateways.
4. Solicitud y configuración del almacenamiento del clúster, incluyendo almacenamiento VMware vSAN o {{site.data.keyword.cloud_notm}} Endurance.
5. Despliegue de un componente de gestión de IBM denominado IBM CloudDriver.
6. Despliegue y configuración de los servicios adicionales que haya seleccionado para su instancia.
7. Validación de la instalación y configuración del entorno.

Puede seleccionar el {{site.data.keyword.CloudDataCent_notm}} donde desea que se suministre su instancia. Siempre que el hardware esté disponible en su {{site.data.keyword.CloudDataCent_notm}} seleccionado, el proceso de suministro de la instancia tardará normalmente menos de 24 horas.

Una vez que se haya suministrado su instancia, si se conecta a su cuenta de
{{site.data.keyword.cloud_notm}} a través de una VPN, puede conectarse al servidor de vCenter directamente desde el navegador web de su estación de trabajo.

Normalmente se accede a los componentes de su instancia a través de sus nombres de host en lugar de hacerlo por sus direcciones IP. Para poder conectarse y autenticarse en vCenter, debe asegurarse de que su estación de trabajo pueda resolver el nombre de host de vCenter y de Platform Services Controller (PSC) añadiéndolo al archivo de hosts de la estación de trabajo tal como se muestra en el Listado 1. Puede encontrar el nombre de host y la dirección IP en la consola de
{{site.data.keyword.vmwaresolutions_short}}, en el separador
**Resumen** de la instancia. Es posible que también desee añadir los nombres de host y las direcciones IP de los hosts de vSphere al archivo de hosts.

*Listado 1. Archivo de hosts*

<pre># Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# Dallas site hosts
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

Una vez que se haya desplegado la instancia, puede gestionarla desde la consola. Las funciones de gestión incluyen la posibilidad de realizar cualquiera de las acciones siguientes:

* Desplegar y eliminar nodos del clúster
* Desplegar y eliminar clústeres adicionales en el mismo centro de datos y pod, o en centros de datos y pods alternativos
* Desplegar y eliminar servicios adicionales para la instancia
* Actualizar determinadas ediciones de la licencia de su instancia

La consola de {{site.data.keyword.vmwaresolutions_short}} proporciona una vista detallada de cada una de las instancias de vCenter Server. Para cada instancia, el separador **Resumen** incluye un enlace a la consola de vCenter y otros detalles acerca de la instancia y los componentes de gestión. El separador **Infraestructura** muestra detalles acerca de los clústeres, los hosts, el almacenamiento y la red de la instancia, y le permite añadir o eliminar clústeres, hosts y almacenamiento. En el separador **Actualización y parche**, puede actualizar determinadas ediciones de la licencia. En el separador **Servicios**, puede ver y gestionar servicios adicionales desplegados para su instancia. El separador **Historial de despliegue** muestra un historial de todas las acciones que se realizan en la instancia.

## Componentes de IBM Cloud for VMware Solutions
{: #under_the_hood-comp}

Una serie de componentes distintos trabajan de manera conjunta para suministrar y gestionar su entorno. La mayoría de estos componentes se despliegan en su cuenta de {{site.data.keyword.cloud_notm}}. Debido a que la solución depende del trabajo conjunto de todos estos componentes, no debe modificar ni cancelar ninguno de estos componentes de su cuenta de {{site.data.keyword.cloud_notm}}. La manera correcta de eliminar una instancia en ejecución es utilizando la consola en lugar de cancelar los componentes individuales.

Aunque este es un entorno de virtualización integrado, el coste de los diversos componentes de virtualización (como las licencias de VMware), los componentes de infraestructura (servidores nativos, VLAN, subredes y almacenamiento) y los componentes de gestión está detallado en la factura que recibe de {{site.data.keyword.cloud_notm}}.

### La consola de IBM Cloud for VMware Solutions
{: #under_the_hood-console}

Inicie sesión en la [consola de {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external} para crear y gestionar sus instancias. Esta parte de la solución es responsable de la solicitud y el suministro inicial del entorno, así como de la gestión en curso de su entorno. Sus instancias desplegadas se comunican con la consola utilizando la red de {{site.data.keyword.cloud_notm}} Private.

### El componente IBM CloudBuilder
{: #under_the_hood-ibm-cb}

Cuando suministra una nueva instancia, la consola muestra una instancia de servidor virtual (VSI) temporal en su cuenta de
{{site.data.keyword.cloud_notm}}. Este servidor virtual se conoce como IBM CloudBuilder. Lleva a cabo la instalación y configuración de todos los componentes de la instancia y la validación del entorno. Una vez que se haya completado el suministro, CloudBuilder se suprimirá.

### El componente IBM CloudDriver
{: #under_the_hood-ibm-cd}

Muy similar a CloudBuilder, IBM CloudDriver es una instancia de servidor virtual (VSI) temporal desplegada en la cuenta de
{{site.data.keyword.cloud_notm}} para realizar operaciones posteriores en la instancia. Se despliega según sea necesario para configurar o eliminar hosts, clústeres, almacenamiento o servicios de la instancia.

### Componentes de VMware
{: #under_the_hood-vmware-comp}

Para todas las instancias, vSphere Hypervisor se instala en los servidores nativos. {{site.data.keyword.cloud_notm}} despliega a continuación un dispositivo vCenter Server Appliance con Platform Services Controller (PSC) integrado, un NSX Manager, tres controladores NSX y dos pares de NSX Edge Services Gateway en el clúster de gestión de VMware.

### Componentes adicionales
{: #under_the_hood-add-comp}

En función de su elección, se desplegará una VSI de Microsoft Windows o dos máquinas virtuales de Microsoft Windows junto o dentro del clúster como servidores de Active Directory para los componentes de gestión. Opcionalmente, puede añadir sus propios servidores de Active Directory como orígenes de identidad adicionales para el acceso de gestión.

Independientemente de cómo decida proporcionar la continuidad de negocio para sus propias cargas de trabajo,
{{site.data.keyword.cloud_notm}} recomienda encarecidamente que haga una copia de seguridad de los componentes de gestión de su instancia. La consola de {{site.data.keyword.vmwaresolutions_short}} le permite desplegar un servidor de copia de seguridad IBM Spectrum Protect Plus integrado o un servidor de copia de seguridad Veeam Backup & Replication junto con su instancia. Estos servicios de copia de seguridad se pueden utilizar como parte de una [solución de copia de seguridad completa](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup) para la instancia.

### Licencias
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} proporciona una serie de licencias de VMware (como vCenter Server y NSX), que se instalan en la instancia y se facturan en la cuenta de {{site.data.keyword.cloud_notm}}.

## Arquitectura de red de IBM Cloud for VMware Solutions
{: #under_the_hood-network}

Su instancia de vCenter Server se conecta a una VLAN pública para su uso con las cargas de trabajo desplegadas. La VLAN pública se reserva en gran medida para su uso según su criterio, pero se conecta un par de NSX Edge Services Gateway a la VLAN pública, permitiendo que determinados servicios adicionales se comuniquen con fines de licencia y facturación. Es posible desplegar una instancia sin el uso de la red pública, en cuyo caso no todos los servicios adicionales tienen soporte, y es posible que necesite proporcionar un proxy web para habilitar el uso de determinados servicios adicionales.

Su instancia de vCenter Server tiene dos VLAN privadas que se conectan de manera troncal en la interfaz de red privada para los hipervisores. La primera VLAN privada se utiliza para la conectividad de gestión (como las comunicaciones de vCenter con los hipervisores) y por medio de NSX para el tunelado de todo el tráfico de VXLAN para las cargas de trabajo desplegadas. La segunda VLAN privada se utiliza para vMotion y para el tráfico de almacenamiento. El tráfico de almacenamiento puede ser del protocolo NFS o del protocolo vSAN.

{{site.data.keyword.cloud_notm}} proporciona determinados servicios adicionales en estas VLAN privadas. Los servidores de Active Directory se comunican con los servidores DNS de {{site.data.keyword.cloud_notm}} a través de la VLAN de gestión privada. Los hosts y otros componentes se comunican con los servidores NTP de {{site.data.keyword.cloud_notm}} a través de la VLAN de gestión privada. IBM CloudBuilder y CloudDriver se comunican con la consola de {{site.data.keyword.vmwaresolutions_short}} a través de esta VLAN también. Los hosts se conectan al almacenamiento {{site.data.keyword.cloud_notm}} Endurance a través del a VLAN de almacenamiento privada.

### Conexión con la instancia
{: #under_the_hood-connect-inst}

Tiene una serie de opciones para conectarse a sus instancias. Puede conectarse directamente a las direcciones IP privadas de su instancia (por ejemplo, vCenter) utilizando la [VPN de {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/VPN-Access){:external}. También puede solicitar [dispositivos de red de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-appliances){:external} y [hardware de {{site.data.keyword.cloud_notm}} o cortafuegos virtuales](https://www.ibm.com/cloud/network-security) como FortiGate y vSRX para su cuenta. {{site.data.keyword.cloud_notm}} también ofrece
[enlaces directos](https://www.ibm.com/cloud/direct-link){:external} entre su red y las VLAN de su cuenta de
{{site.data.keyword.cloud_notm}}.

Para acceder a las máquinas virtuales desplegadas, puede aplicar direcciones IP públicas directamente a sus máquinas virtuales. No obstante, también puede utilizar el dispositivo de red de
{{site.data.keyword.cloud_notm}} y las funciones de cortafuegos para configurar un acceso público más seguro a sus máquinas virtuales utilizando NAT y el cortafuegos. También puede desplegar servidores NSX Edge y utilizar dichos servidores para configurar la conectividad VPN o NAT de sus máquinas virtuales.

## Conclusión
{: #under_the_hood-conclusion}

En esta guía de aprendizaje, ha obtenido información sobre las funciones básicas de
{{site.data.keyword.vmwaresolutions_short}} para desplegar y gestionar entornos de virtualización de VMware estandarizados en la nube pública. Debido a que puede suministrar estos entornos más rápido que nunca, puede centrar su esfuerzo en desplegar sus aplicaciones y soluciones sobre ellos, y en conectar las nubes entre sí para la recuperación tras desastre y la alta disponibilidad.

Hemos explorado los diversos componentes que se despliegan en su cuenta de
{{site.data.keyword.cloud_notm}}, que aparecen en su declaración de facturación de
{{site.data.keyword.cloud_notm}} y que trabajan conjuntamente para mantener el entorno en ejecución. Finalmente, hemos tenido en cuenta la arquitectura de red de la solución junto con algunas opciones para establecer la conectividad en el entorno, ya sea utilizando diversas opciones de conectividad segura para que las comunicaciones sean privadas, o utilizando diversas opciones para la conectividad de Internet pública.

Ahora que tiene las armas que necesita para saber por dónde empezar, siga adelante y despliegue hoy mismo su próximo entorno de virtualización de VMware en {{site.data.keyword.cloud_notm}}.

## Enlaces relacionados
{: #under_the_hood-related}

* [Iniciación](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Arquitectura de VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
