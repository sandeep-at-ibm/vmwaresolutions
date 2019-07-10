---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Malla de servicio en instalaciones locales de HCX
{: #hcxclient-vcs-mesh-deployment}

En la sección siguiente se detallan los pasos para configurar la instancia de cliente de HCX. 
  1. Entorno de emparejamiento de sitios de IBM Cloud para soluciones VMware
  2. Crear perfiles de red de HCX On-Premise
  3. Crear perfiles de cálculo de HCX On-Premise
  4. Crear malla de servicio de HCX
  5. Redes de extensión

## Entorno de emparejamiento de sitios de IBM Cloud para soluciones VMware
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. Inicie una sesión en el cliente web de vSphere. 
2. En el menú **Inicio**, seleccione la opción **HCX**. 
3. En **Infraestructura** -> **InterConnect**, pulse **Añadir emparejamiento de sitio**
   1. URL del sitio: URL de HCX Cloud Manager
     * por ejemplo, `https://x.x.x.x.x`
   2. Nombre de usuario y contraseña Detalles de HCX Manager Admin
     * admin / password
   3. Los detalles anteriores se pueden obtener de IBM Cloud Portal, bajo **Servicios**, HCX on IBM Cloud** para la instancia de solución de IBM Cloud for VMware. 
4. Pulse en **Conectar**

### Resultados
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

El emparejamiento de sitios (Site Pairing) se ha registrado correctamente y se muestra en la interfaz. 

## Creación de perfiles de HCX On-Premise
{: #hcxclient-vcs-mesh-deployment-profiles}

## Perfiles de red de malla de servicio en la instalación local
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. Inicie una sesión en el cliente web de vSphere. 
2. En el menú **Inicio**, seleccione la opción **HCX**. 
3. En **Infraestructura** -> **InterConnect** 
4. En Multi-Site Service Mesh, pulse **Perfiles de red**
5. Desde: **Cree el perfil de red**
   1. Seleccione Grupo de puertos distribuidos: por ejemplo, Externo
   2. Proporcione un rango de direcciones IP de IP externas
   3. Proporcione longitud de prefijo de subred externa
   4. Proporcione pasarela externa
   5. Proporcione detalles de DNS
   6. Establezca MTU en 1500
   7. Pulse Crear. 
6. Repita los pasos anteriores para las redes de gestión y vMotion.
    Nota: la MTU se debe establecer en 9000. 

## Resultados
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| Nombre de red | MTU |
| -----| ----|
| Externa | 1500|
| Gestión | 9000|
| vMotion | 9000|

## Perfiles de cálculo de malla de servicio en la instalación local
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. Inicie una sesión en el cliente web de vSphere. 
2. En el menú **Inicio**, seleccione la opción **HCX**. 
3. En **Infraestructura** -> **InterConnect** 
4. En Multi-Site Service Mesh, pulse **Perfiles de cálculo**
5. Desde: **Cree el perfil de cálculo**
   1. Proporcione un nombre de perfil de cálculo
   2. Seleccione Todos los servicios que desea habilitar, y pulse **continuar**
   3. Seleccione el clúster, y pulse **continuar**
   4. Seleccione el almacén de datos, y pulse **continuar**
   5. Seleccione el perfil de red para gestión, y pulse **continuar**
   6. Seleccione el perfil de red para externo/enlace ascendente, y pulse **continuar**
   7. Seleccione el perfil de red para vMotion, y pulse **continuar**
   8. Seleccione el perfil de red para vSphere Replication (gestión), y pulse **continuar**
   9. Seleccione Distribuir conmutador para la extensión, por ejemplo, Private-Switch
   10. Pulse Finalizar

## Resultados
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

Se ha creado un perfil de cálculo para la combinación de clúster/almacenamiento, y está disponible con la creación de la malla de servicios. 

## Malla de servicio en instalaciones locales de HCX
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## Creación de malla de servicio en la instalación local
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. Inicie una sesión en el cliente web de vSphere. 
2. En el menú **Inicio**, seleccione la opción **HCX**. 
3. En **Infraestructura** -> **InterConnect** 
4. En Multi-Site Service Mesh, pulse **Malla de servicio**
5. Desde: **Crear malla de servicio**
   1. Seleccione sitios; en local y en la organización de vCloud, pulse continuar
   2. Seleccione el perfil de cálculo de origen
   3. Seleccione el perfil de cálculo remoto. Por ejemplo, CloudCompute. 
   4. Seleccione todos los servicios, y pulse continuar
   5. Pulse en continuar, en la página Configuración avanzada - Sustituir perfiles de red de enlace ascendente (Opcional)
   6. Pulse continuar
   7. Pulse Continuar, deje los valores predeterminados en la página Configuración avanzada - Configurar el límite de ancho de banda del Servicio de optimización de WAN
   8. Proporcione el nombre de servicio, pulse **Finalizar**
6. Vea la lista de tareas para la creación de malla de servicio; al final debe haber tres dispositivos HCX en la ubicación local y tres en la ubicación de la nube. 

## Resultados
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

Una malla de servicio HCX es la configuración de servicios HCX efectiva para un sitio de origen y de destino. Se puede añadir una malla de servicio a un Emparejamiento de sitio conectado que tiene un perfil de cálculo válido creado en ambos sitios. 

La adición de una malla de servicio inicia el despliegue de los dispositivos virtuales HCX Interconnect en ambos sitios. Siempre se crea una malla de servicio de interconexión en el sitio de origen. 

## Extensión de red
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## Proceso para extender una red
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

Para extender una red (VLAN o VXLAN) con HCX, complete los siguientes pasos desde la interfaz de usuario web de vCenter del lado del cliente.

1. Inicie una sesión en el cliente web de vSphere. 
2. En el menú **Inicio**, seleccione la opción **HCX**. 
3. Menú de la izquierda, en **Servicios** -> **Extensión de red**
4. pulse **red ampliada**
   1. Seleccione la red a ampliar
   2. Escriba la pasarela y la máscara de subred predeterminadas en formato CIDR.
   3. Pulse **Extender** en la parte inferior de la pantalla para comenzar el flujo de trabajo de extensión de red.

El progreso de red se supervisa en el panel de tareas del cliente de vCenter.

## Conceptos y mejores prácticas para la extensión de red
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

El pegamento que une la red del lado del cliente con la VXLAN del lado de la nube es una red privada virtual (VPN) sofisticada de varios túneles basada en tecnología HCX patentada. No se basa en NSX, pero sí funciona con NSX y amplía su capacidad. Este proceso está controlado por la interfaz de usuario web de vCenter del lado del cliente y automatiza el despliegue y activa ambos puntos finales en el lado del cliente y de la nube. La selección de la red que se va a extender se realiza de forma individual o por lotes.

Además, como parte del flujo de trabajo de extensión de red, NSX en el lado de la nube tiene autorización para crear una VXLAN que luego se conecta a una interfaz creada en el dispositivo L3 del lado de la nube especificado (DLR o ESG dejado en un estado no conectado) y el dispositivo Ampliación de red del lado de la nube. 

Normalmente, al migrar una aplicación concreta, todas las redes que utilizan las máquinas virtuales (VM) aplicables deben extenderse en la instancia de {{site.data.keyword.cloud}}.

¿Por qué normalmente y no siempre? Puede ser beneficioso desconectar determinado tráfico desde el lado del cliente después de migrar la máquina virtual. Por ejemplo, los clientes de copia de seguridad de invitado de máquina virtual, que pueden provocar un alto uso de ancho de banda cuando se mueven a la nube. El cliente de copia de seguridad en el invitado no es necesario cuando se migra la máquina virtual, ya que se recoge automáticamente mediante una copia de seguridad de nivel de bloque más moderna en el lado de la nube.

El adaptador de red de copia de seguridad del cliente, debido a que esto implicaría acceder a cada máquina virtual para concluir la planificación de copia de seguridad del cliente en el invitado. Por lo tanto, si se utiliza una red de copia de seguridad, es posible que falle la copia de seguridad. Se trata de una situación temporal hasta que se puedan alcanzar todas las máquinas virtuales después de la migración para inhabilitar el cliente de copia de seguridad en el invitado.

El ancho de banda de una sola ampliación de red es teóricamente de 4 Gbps, sin embargo, este puede ser el límite para todas las redes extendidas dentro de un solo par de ampliaciones de red y no es alcanzable por una sola red extendida. Una sola red extendida puede alcanzar un máximo de ~1 Gbps, dado que hay suficiente ancho de banda subyacente asignado y la latencia es baja (< ~ 10 ms).

### Opción de direccionamiento de proximidad
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

Sin ningún tipo de optimización de direccionamiento, las redes extendidas se direccionan de nuevo al lado del cliente para cualquier acceso de L3. Este proceso de bumerán introduce un patrón de tráfico ineficiente, ya que los paquetes tienen que desplazarse continuamente entre el cliente (origen) y la nube, incluso cuando las máquinas virtuales de origen y de destino están dentro de la nube. La característica de direccionamiento de proximidad de HCX se ha diseñado para solucionar este problema y la salida del tráfico local.

## Enlaces relacionados
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [Glosario de componentes y términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparación del entorno de instalación](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Despliegue del cliente de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Migraciones de VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Supervisión de parámetros y componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolución de problemas de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
