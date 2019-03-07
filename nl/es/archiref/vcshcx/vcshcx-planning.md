---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Planificación previa al despliegue
{: #vcshcx-planning}

La mayor parte del tiempo que se emplea en el despliegue de HCX se destina a la etapa previa al despliegue.
Aunque es frecuente que los proyectos de migración de sistemas de información duren muchos meses, e incluso años, HCX permite que las migraciones y la conectividad de red a la nube se inicien inmediatamente después del despliegue. Puesto que en el despliegue de HCX para un cliente a nivel de empresa normalmente trabajan equipos de seguridad, redes, almacenamiento e infraestructura de vSphere, tiene sentido implicar a estos equipos en la prueba de concepto (POC), si es posible. Una gestión efectiva de los proyectos y una pronta inclusión de los participantes es fundamental para garantizar la velocidad del despliegue y el funcionamiento de HCX.

## Cómo evitar la parálisis del análisis
{: #vcshcx-planning-avoiding}

Muchos de los obstáculos y el tiempo que requiere la migración de una máquina virtual (VM) o un grupo de máquinas virtuales se deben a la necesidad de modificar partes del entorno de la aplicación, el diseño de estos cambios y la planificación del tiempo de inactividad necesario para realizar dichos cambios. Una vez que se han realizado estos cambios, es difícil revertir la migración, lo que aumenta aún más la parálisis del análisis. Tratar de capturar todos los aspectos de la migración, coordinar los distintos equipos y cambiar las principales partes implicadas en el tiempo que se tarda en finalizar el plan puede retrasar o forzar el avance del proyecto.

HCX permite la migración cruzada de instancias de vSphere de una máquina virtual o un grupo de máquinas virtuales que representan una aplicación compuesta completa o parcial, sin realizar ninguna modificación en la aplicación. Gracias a ello, revertir una migración significa volver a mover las máquinas virtuales o volver a extender las redes. Esto anula la necesidad de una gran parte de la planificación de la migración y facilita cierto paralelismo en el proceso de planificación. Después de seleccionar las aplicaciones para mover y crear un diseño de red de alto nivel, las aplicaciones pueden empezar la migración con una configuración mínima en la instancia de nube mientras se trabaja en el diseño y la conectividad final de la red.

## Redes extendidas
{: #vcshcx-planning-stretched-net}

Los componentes de extensión de red de la flota de HCX son muy estables. En un cliente determinado con más de 20 VLAN que se han extendido en {{site.data.keyword.cloud}} a través de una WAN de 1 Gbps compartida con otros túneles de migración de tráfico y HCX, no existen problemas de aplicación atribuidos a la red.
Los enlaces de red se mantienen activos durante más de 6 meses de esta forma.
Se han añadido y eliminado más redes extendidas sin problemas.
La selección de un {{site.data.keyword.CloudDataCent_notm}} cercano (< 6 ms de latencia para este cliente en particular) también influye en la estabilidad de red de las redes extendidas. El hecho de dejar las redes extendidas activas a largo plazo no debería ser un factor negativo en su diseño, dado que tiene suficiente ancho de banda y baja latencia para sus aplicaciones.


## Ciclo de vida de la migración
{: #vcshcx-planning-mig-lifecycle}

En las secciones siguientes se describen las fases de un ciclo de vida de migración de HCX típico, indicando dónde se pueden realizar las secuencias de trabajo en paralelo.

## Inventario de vSphere
{: #vcshcx-planning-vsphere-planning}

- Utilice una aplicación, por ejemplo [RVTOOLS](https://www.robware.net/rvtools/) para volcar el inventario de los vCenters de origen en el formulario de la hoja de cálculo.
- Evaluación general de las máquinas virtuales dentro de una aplicación que se va a migrar.
La evaluación general implica comprender las máquinas virtuales que participan en una aplicación, sin ahondar en detalles.
- Si tiene previsto migrar muchas máquinas virtuales y el ancho de banda de red está limitado entre los sitios de origen y de destino, agrupe las máquinas virtuales por VLAN o VXLAN, si se utiliza NSX en el origen. De esta manera, se habilita un plan de migración de HCX en cascada en el que se migran grupos de máquinas virtuales por VLAN y las redes L2 en las que residen solo se extienden hasta que las VLAN se evacuan. Esto significa que el grupo inicial de redes L2 extendidas relacionadas solo se puede desextender cuando el diseño de red del lado de la nube se ha completado y desplegado. La eliminación de la extensión implica dirigir el tráfico de VXLAN específico hacia una nueva dirección a través de la infraestructura NSX de la instancia de nube específica.


## Configuración de red de línea base
{: #vcshcx-planning-baseline-net-config}

Cree una red perimetral reforzada dentro de la instancia de vSphere del lado de la nube. Esto normalmente consiste en un dispositivo NSX DLR o Edge. Si utiliza el direccionamiento de proximidad de HCX, no es necesario crear ninguna regla de cortafuegos ni ninguna topología de enlace ascendente, ya que se puede completar más tarde o simultáneamente sin que afecte al tráfico de la L2 extendida.

## 	Extensión de red
{: #vcshcx-planning-net-extension}

La extensión de la red significa básicamente coger la VLAN o VXLAN existente desde el entorno de vSphere de origen, representado por un grupo de puertos de conmutador virtual distribuido (vDS), y extenderla a una NSX VXLAN en el lado de la nube de HCX.

## Pruebas previas
{: #vcshcx-planning-preflight-tests}

Las pruebas previas consisten en realizar una migración de HCX con la función de migración masiva y de vMotion con el objetivo de establecer una velocidad de transferencia de línea base.

## Migración de apps de no producción
{: #vcshcx-planning-mig-non-prod-apps}

En este punto, la migración de máquinas virtuales empieza con los conjuntos planificados de máquinas virtuales que son menos críticas. El desarrollo o las pruebas, entre otros, utilizan la conectividad de Internet para la migración y el tráfico de la L2 extendida.


## Empieza el diseño y la implementación de la red en la nube
{: #vcshcx-planning-cloud-net-begins}

Mientras las migraciones continúan, los diseños de red del lado de la nube finalizan y se implementan dentro de la instancia de vSphere del lado de la nube.

## Más consideraciones sobre la conectividad de red
{: #vcshcx-planning-connect-considerations}

Mientras las migraciones siguen en curso, se solicita la conectividad de red de WAN privada, ya que suele tardar unas semanas o meses en establecerse con el proveedor de la nube. Una vez completada la conectividad de red privada, se puede configurar HCX para que utilice ambos, el enlace de red privada dedicada e Internet para la migración y el tráfico de la L2 extendida.

## Servidores físicos
{: #vcshcx-planning-physical-servers}

Cuando el objetivo es la migración del centro de datos a la nube, cualquier servidor físico que interactúe con las máquinas virtuales que se están migrando se puede evaluar para determinar la migración a {{site.data.keyword.cloud_notm}} como máquina virtual (P2V), servidor nativo o permanecer en el origen. Si el servidor físico va a permanecer en el origen, y HCX solo se utilizará durante la migración hasta que se establezca una red dedicada, es importante comprender si reside en cualquier red que se extienda en la nube con HCX. En este caso de ejemplo, HCX no solo permite migrar las máquinas virtuales, sino toda la subred a la nube. Para eliminar HCX al final de la migración, la subred no puede existir en el origen y en el destino si se desea mantener la conexión entre los dispositivos físicos y las máquinas virtuales migradas. Esto implica que los dispositivos físicos que quedan en el sitio de origen y que existen en las redes L2 extendidas, deben migrarse a otra subred de red que pueda ser direccionada al lado de la nube. La excepción a esto es si se utiliza alguna otra tecnología de L2 extendida, como NSX L2 VPN, para sustituir los puntos finales de la L2 extendida de HCX.

## Migración de aplicaciones complejas y de producción
{: #vcshcx-planning-mig-prod-complex-app}

Las máquinas virtuales con VMDK de varios escritores compartidos, como los clústeres de MS Exchange/SQL u Oracle RAC o máquinas virtuales con correlaciones de dispositivos en bruto, son ejemplos de máquinas virtuales que necesitan una consideración adicional antes de la migración.

## Oscilación de red
{: #vcshcx-planning-net-swing}

La oscilación de red se produce tras completarse la evacuación de las máquinas virtuales en las redes del lado del origen y una vez finalizado el diseño/implementación de la red en el lado de la nube. La configuración de HCX para eliminar la extensión de las redes relacionadas con las máquinas virtuales completadas en las migraciones, permite a las máquinas virtuales migradas direccionar el tráfico de red utilizando la infraestructura de NSX del lado de la nube.

## Plataformas de cliente soportadas
{: #vcshcx-planning-client-platforms}

Para la extensión de red, solo se admiten los grupos de puertos con un conmutador distribuido virtual (vDS) de vSphere. Esto también implica que no se admiten los hosts ESXi autónomos, ya que solo puede tener un vDS cuando los hosts ESXi están gestionados por vCenter.
- vSphere 5.1 (línea de mandatos solo para vCenter 5.1 a través de API)
- vSphere 5.5 (interfaz de usuario de cliente web soportada en vCenter 5.5u3 y superior)
- vSphere 6.0
- vSphere 6.5 (vDS debe estar a un nivel de 6.0)

## Plataformas de nube soportadas
{: #vcshcx-planning-cloud-platforms}

El lado de HCX Cloud se suministra mediante la automatización de {{site.data.keyword.cloud_notm}}.

## Opciones de conectividad
{: #vcshcx-planning-connect-options}

### Conectividad de HCX estándar
{: #vcshcx-planning-standard-connect}

Como se despliega mediante la automatización de {{site.data.keyword.vmwaresolutions_short}}, la instalación del lado de la nube de HCX se configura para conectarse a través de Internet público de forma predeterminada.

### Conectividad opcional
{: #vcshcx-planning-optional-connect}

La conexión a través de la red privada de {{site.data.keyword.cloud_notm}} se puede seleccionar al realizar el pedido.

## Enlaces relacionados
{: #vcshcx-planning-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
