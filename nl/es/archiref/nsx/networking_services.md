---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

# Servicio de red en IBM Cloud

Los servicios de red en {{site.data.keyword.cloud}} constan de dos pares de pasarelas VMware NSX Edge Services Gateways (ESG) para la comunicación entre el {{site.data.keyword.cloud_notm}} y la internet pública o la red local del cliente mediante una red privada virtual (VPN). Estos ESG se segregan para dar soporte a la función de gestión interna de {{site.data.keyword.cloud_notm}} y al tráfico de salida, entrada de tráfico de red relacionado con el cliente.

El gráfico siguiente es un diagrama de red simplificado, que representa el par de gestión y el par de ESG de carga de trabajo. También muestra un NSX Distributed Router (DLR) y una carga de trabajo VXLAN. Estos componentes están pensados para ser un punto de destino inicial para las cargas de trabajo de los clientes sin necesidad de tener el conocimiento específico para establecerlas dentro de NSX. Normalmente se utiliza un DLR para direccionar el tráfico entre VMware Cloud Foundation o VMware vCenter Server y el tráfico entre el este y el oeste, entre redes de capa 2 separadas dentro de la instancia. Este comportamiento contrasta con un ESG, que funciona para facilitar el tráfico de red norte-sur que entra y sale de la instancia de Cloud Foundation o de vCenter Server.

Figura 1. Servicios de red en la nube en Cloud Foundation

![Servicios de red en la nube en Cloud Foundation](cloudnetworkingservicesdiagram.svg "Servicios de red en la nube en Cloud Foundation")

Aunque un solo ESG puede ser suficiente para el tráfico de carga de trabajo de gestión y de cliente, la separación de gestión y tráfico de cliente es una decisión de diseño realizada para evitar una configuración incorrecta accidental del ESG de gestión.

**Nota:** La falta de configuración o la inhabilitación del ESG de gestión no permite que la instancia de Cloud Foundation o vCenter Server funcione, sino que inhabilita todas las funciones de gestión de portal.

## Servicios de gestión de IBM NSX Edge

El ESG de gestión de IBM es un clúster NSX Edge exclusivo solo para el tráfico de red de gestión de {{site.data.keyword.cloud_notm}}. No está pensado para el cruce de tráfico de ningún componente que no esté desplegado y gestionado por la automatización de Cloud Foundation o vCenter Server.

El ESG de gestión proporciona una vía de acceso de comunicación entre las máquinas virtuales (VM) de servicios complementarios que residen en instancias de Cloud Foundation o vCenter Server y la infraestructura de IBM Automation en el {{site.data.keyword.cloud_notm}} tal como se muestra para Cloud Foundation en el gráfico siguiente.

Figura 2. Gestión de comunicaciones de extremo de gestión en Cloud Foundation

![Comunicaciones del extremo de gestión en Cloud Foundation](mgmtvmcommunication.svg "Comunicaciones del extremo de gestión en Cloud Foundation")

Como resultado de la comunicación ligera entre determinadas VM de servicios complementarios y sus correspondientes sistemas de licencias y calibración, los ESG NSX se dimensionan en una configuración grande en un par de alta disponibilidad activo-pasivo (HA) y se despliegan en la agrupación de recursos de gestión del clúster convergente de Cloud Foundation o el clúster de vCenter Server. En la tabla siguiente se proporciona un resumen del despliegue de NSX ESG de gestión de IBM.

Tabla 1. Especificaciones del NSX ESG de gestión de IBM

| NSX Edge de gestión de IBM | vCPU | Memoria | Tamaño de disco | Ubicación de almacenamiento |
|:----------------------- |:---- |:------ |:--------- |:---------------- |
| NSX ESG de gestión de IBM 1 | 2 | 1 GB | 1 GB | vSAN Datastore (Cloud Foundation); Shared Attached Storage for Management (vCenter Server) |
| NSX ESG de gestión de IBM 2 | 2 | 1 GB | 1 GB | vSAN Datastore (Cloud Foundation); Shared Attached Storage for Management (vCenter Server) |

### Servicios de gestión

El acceso de salida es necesario para los servicios siguientes:

* Zerto Virtual Manager. Si se instala, Zerto on {{site.data.keyword.cloud_notm}} requiere acceso de salida a Internet para la activación de licencias y la creación de informes de uso.
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} requiere acceso de salida a Internet para la activación y la supervisión de licencias.
* F5 on {{site.data.keyword.cloud_notm}} requiere acceso de salida a Internet para la activación de licencias.

### Interfaces de Edge

La configuración de las interfaces ESG define las redes L2 a las que tiene acceso ESG. Para la gestión del ciclo de vida de Cloud Foundation y vCenter Server, es necesario que se permita a las VM específicas colocadas en la VLAN de gestión cruzar a la VLAN pública. Las interfaces siguientes se definen en el despliegue:

Tabla 2. Configuración de la interfaz NSX ESG

| Interfaz | Tipo de interfaz | Conectado a | Descripción |
|:--------- |:-------------- |:------------ |:----------- |
| Enlace ascendente público | Enlace ascendente | SDDC-DportGroup-External | Interfaz destinada a Internet pública |
| Enlace ascendente privado | Enlace ascendente | SDDC-DportGroup-Mgmt | Interfaz destinada a una red privada interna |
| Interna | Interna | Carga de trabajo de alta disponibilidad de VXLAN | Interfaz interna utilizada para el latido de par HA de ESG; portgroup en SDDC-Dswitch-Private |

### Subredes

Las siguientes subredes se utilizan para los fines del ESG de gestión:

Tabla 3. Configuración de IP de NSX ESX

| Interfaz | Tipo de interfaz | Tipo de subred IP v4 | Rango | Descripción |
|:--------- |:-------------- |:----------------- |:----- |:----------- |
| Enlace ascendente público | Enlace ascendente | {{site.data.keyword.cloud_notm}} portátil público | /30-representa una dirección IP asignable | Interfaz destinada a Internet pública |
| Enlace ascendente privado | Enlace ascendente | {{site.data.keyword.cloud_notm}} portátil privado (gestión existente) | /26-representa 61 direcciones IP asignables | Interfaz destinada a una red privada interna |
| Interna | Interna | Local de enlace | 169.254.0.0/16 | Interfaz interna utilizada para la comunicación de par de alta disponibilidad ESG |

### Definiciones de conversión de direcciones de red

La conversión de direcciones de red (NAT) se utiliza en el ESG de gestión para permitir el tráfico de red entre espacios de direcciones IP. Esto se suele hacer para conservar IP direccionables a Internet o para ocultar las IP internas de las públicas por motivos de seguridad. NAT también se utiliza para permitir la redirección del puerto TCP (Transmission Control Protocol) y UDP (User Datagram Protocol). El tráfico de gestión siempre se inicia desde dentro de la instancia de Cloud Foundation y vCenter Server, lo que requiere que solo se defina una NAT de origen (SNAT) en el ESG de gestión. No se crea un SNAT individual para cada VM interna que aloja un servicio que tiene que salir de la instancia.

Tabla 4. Configuración NAT de NSX ESG

| Aplicado en la interfaz | Rango de IP de origen | IP de origen traducida |
|:-------------------- |:--------------- |:-------------------- |
| Enlace ascendente público | Direcciones IP individuales en la Management Portable /26 | {{site.data.keyword.cloud_notm}} portátil público |

### Direccionamiento

Es posible que los servicios de VM que tienen que cruzar la ESG de gestión también tengan que llegar a los servicios de {{site.data.keyword.cloud_notm}} dentro de la red privada de {{site.data.keyword.cloud_notm}} del cliente. Para lograr dicha comunicación es necesaria la configuración siguiente.

Aunque es difícil predecir qué rango de IP de destino es necesario como destino para las conexiones destinadas a Internet, cualquier servicio que esté desplegado y gestionado por {{site.data.keyword.cloud_notm}} apunta al ESG de gestión como su pasarela predeterminada. Se necesita una ruta estática para forzar el tráfico a través del BCR de {{site.data.keyword.cloud_notm}} para las conexiones de red externa necesarios para los servicios.

Se recomiendan las siguientes configuraciones para cualquier servicio que esté utilizando el ESG de gestión para cruzar una instancia de Cloud Foundation o vCenter Server:
* La pasarela predeterminada es un ESG de gestión.
* Se necesita una ruta estática para los destinos internos de {{site.data.keyword.cloud_notm}}.

Si es necesario que el servicio o la VM accedan al ESG del cliente, las rutas estáticas se deben mantener dentro del servicio individual o la VM, así como apuntar al ESG del cliente.

Actualmente no hay ningún protocolo de direccionamiento automático configurado para el ESG de gestión.

### Definiciones de VXLAN

El par de alta disponibilidad de gestión requiere una red para la conexión de las interfaces internas. Utilice un vSwitch existente, un grupo de puertos o una VXLAN. Para este diseño, se crea una VXLAN dedicada para la comunicación de pulsaciones de alta disponibilidad del par de alta disponibilidad de ESG de gestión.

Tabla 5. Definiciones VXLAN de NSX ESG

| Definiciones de VLAN de NSX ESG | Zona de transporte | Tipo |
|:------------------------- |:-------------- |:---- |
| Alta disponibilidad de gestión | transport-1 | global |

### Reglas de cortafuegos

De forma predeterminada, el ESG de gestión está configurado para denegar todo el tráfico.

**Denegar:** Para eliminar todo el tráfico sin respuesta cuando una regla o conjunto de reglas previo (en un orden superior) no permite a dicho tráfico cruzar el cortafuegos. Se selecciona la generación automática de reglas para permitir el tráfico de control en el par ESG.

Se establecen las siguientes reglas de cortafuegos, además de las reglas generadas automáticamente:

Tabla 6. Configuración de cortafuegos de NSX ESG

| Servicio | Fuente | Destino | Protocolo | Acción |
|:------- |:------ |:----------- |:-------- |:------ |
| Zerto on {{site.data.keyword.cloud_notm}} | VM de gestión de Zerto | Cualquiera | Puerto 443 | Permitir |
| FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} | VM de servicio | Cualquiera | Puerto 443 | Permitir |
| F5 on {{site.data.keyword.cloud_notm}} | VM de servicio | Cualquiera | Puerto 443 | Permitir |
| Cualquiera | Cualquiera | Cualquiera | Cualquiera | Denegar |

## NSX Edge de carga de trabajo de IBM

El ESG de carga de trabajo de IBM forma parte de una topología simple que está pensada para la comunicación de red de carga de trabajo. En la sección siguiente se describe la intención de diseño de dónde adjuntar cargas de trabajo a una red dentro de una instancia de Cloud Foundation o vCenter Server. Este es un punto de partida para adjuntar redes locales y espacios IP a una instancia particular de Cloud Foundation o vCenter Center y es la base para una auténtica arquitectura de nube híbrida.

Una red de cliente conectada tanto a las redes públicas y privadas de {{site.data.keyword.cloud_notm}} permite el acceso de la carga de trabajo en o desde tráfico destinado a Internet, pero también permite que se cree una VPN de sitio a sitio desde redes públicas o privadas de {{site.data.keyword.cloud_notm}}. Esto permite disminuir drásticamente el tiempo con respecto a la conexión a las redes locales, ya que puede llevar meses traer una red de área amplia dedicada (WAN) debido a los requisitos de seguridad del cliente. Sin embargo, después de que haya un enlace dedicado, la VPN se puede volcar para que cruce dicho enlace sin afectar a la red de superposición dentro del túnel VPN o dentro de la instancia de Cloud Foundation o vCenter Server. Una vez que se haya realizado esto, la interfaz pública para el ESG de carga de trabajo se puede eliminar si es necesario desde una perspectiva de seguridad.

La topología de la figura siguiente consta de los siguientes componentes de NSX:
* NSX Edge Appliance (ESG)
* Direccionador lógico distribuido (DLR)
* VXLAN (L2 por L3)

Figura 3. Diagrama de flujo de red de ejemplo

![Diagrama de flujo de red](customer_network_flow_diagram.svg "Diagrama de flujo de red")

### Interfaces de Edge para el NSX Edge de carga de trabajo de IBM

Al igual que con el ESG de gestión, la configuración de las interfaces de ESG define las redes L2 a las que el ESG tiene acceso. Parte de la intención de diseño de la topología de carga de trabajo consiste en conseguir una superposición de red definida por software (SDN) para aislar las cargas de trabajo del espacio de direcciones {{site.data.keyword.cloud_notm}} subyacente. Este diseño es la base para lograr el diseño de BYOIP. Por lo tanto, las interfaces siguientes se definen en el despliegue:

Tabla 7. Configuración de la interfaz de Edge de carga de trabajo

| Interfaz | Tipo de interfaz | Conectado a | Descripción |
|:--------- |:-------------- |:------------ |:----------- |
| Enlace ascendente público | Enlace ascendente | SDDC-DportGroup-External | Interfaz destinada a Internet pública |
| Enlace ascendente privado | Enlace ascendente | SDDC-DportGroup-Mgmt | Interfaz destinada a una red privada interna |
| Enlace ascendente de tránsito | Enlace ascendente | Carga de trabajo-Tránsito | Tránsito VXLAN entre el ESG de carga de trabajo y el DLR de carga de trabajo |
| Interna | Interna | Carga de trabajo de alta disponibilidad de VXLAN | Interfaz interna utilizada para la pulsación del par de alta disponibilidad de ESG |

En este diseño, se utiliza un DLR para permitir el direccionamiento potencial de este a oeste entre las redes L2 conectadas a la carga de trabajo local. Como esta topología está pensada para ser un ejemplo sencillo, solo se describe una red L2 destinada a las cargas de trabajo. La adición de zonas de seguridad adicionales se puede conseguir simplemente añadiendo VXLAN adicionales conectadas a las nuevas interfaces en el DLR. Las siguientes son interfaces DLR para configurar:

Tabla 8. Interfaces de DLR

| Interfaz | Tipo de interfaz | Conectado a | Descripción |
|:--------- |:-------------- |:------------ |:----------- |
| Enlace ascendente de tránsito | Enlace ascendente | Carga de trabajo-Tránsito | Tránsito VXLAN entre el ESG de carga de trabajo y el DLR de carga de trabajo |
| Uplink de carga de trabajo | Enlace ascendente | Carga de trabajo | VXLAN para conexiones de carga de trabajo |
| Interna | Interna | Carga de trabajo de alta disponibilidad de VXLAN | Interfaz interna utilizada para la pulsación del par de alta disponibilidad de ESG |

### Subredes para NSX Edge de carga de trabajo de IBM

A efectos de la carga de trabajo ESG se utilizan las subredes siguientes:

Tabla 9. Configuración de IP de DLR y ESG de carga de trabajo

| Interfaz | Tipo de interfaz | Tipo de subred IP v4 | Rango | Descripción |
|:--------- |:-------------- |:----------------- |:----- |:----------- |
| Enlace ascendente público (ESG) | Enlace ascendente | {{site.data.keyword.cloud_notm}} portátil público | /30-representa una dirección IP asignable | Interfaz pública destinada a Internet (el cliente puede solicitar IP adicionales por separado) |
| Enlace ascendente privado (ESG) | Enlace ascendente | {{site.data.keyword.cloud_notm}} portátil privado (gestión existente) | /26-representa 61 direcciones IP asignables | Interfaz destinada a una red privada interna |
| Interna (ESG y DLR) | Interna | Local de enlace | 169.254.0.0/16 | Interfaz interna utilizada para la comunicación de par de alta disponibilidad ESG |
| Enlace ascendente de tránsito (ESG y DLR) | Enlace ascendente | Asignado por el cliente | Por determinar. | Conexión de red de tránsito para ESG a DLR |
| Carga de trabajo (DLR) | Enlace ascendente | Asignado por el cliente | Por determinar. | Subred de carga |

### Definiciones NAT para NSX Edge de carga de trabajo de IBM

NAT se utiliza en el ESG de carga de trabajo para permitir el tráfico de red entre espacios de direcciones IP. Para el ESG de carga de trabajo, se requiere NAT no solo para permitir la comunicación a destinos de Internet, sino también para comunicarse con cualquier rango de IP originada de {{site.data.keyword.cloud_notm}}. Para este diseño, el tráfico de carga de trabajo puede salir a Internet, pero no a la gestión ni a ninguna red de {{site.data.keyword.cloud_notm}}. Como tal, solo se debe definir un SNAT en el ESG de carga de trabajo. Tenga en cuenta que toda la red portátil de carga de trabajo se configura para que cruce la SNAT.

Aunque se puede utilizar NAT para permitir la comunicación de carga de trabajo entre varias instancias de Cloud Foundation o vCenter Server, es poco práctico cuando muchas cargas de trabajo tienen que estar conectadas entre instancias. Para obtener ejemplos de cómo utilizar las funciones avanzadas de NSX para crear una red de tránsito de L2 sobre Cloud Foundation o instancias de vCenter Server, consulte [Arquitectura de varios sitios](multi_site.html).

Tabla 10. Reglas de NAT de ESG de carga de trabajo

| Aplicado en la interfaz | Rango de IP de origen | IP de origen traducida | NAT habilitada o inhabilitada |
|:-------------------- |:--------------- |:-------------------- |:----------------------- |
| Enlace ascendente público (carga de trabajo ESG) | Definido por el cliente | {{site.data.keyword.cloud_notm}} IP pública portátil | Cliente definido (inhabilitado de forma predeterminada) |

### Direccionamiento para NSX Edge de carga de trabajo de IBM

Dentro de este diseño, el único requisito para las cargas de trabajo que van del DLR al ESG de carga de trabajo es acceder a Internet. Es necesario que el ESG de carga de trabajo comprenda la vía de acceso a la carga de trabajo VXLAN y a cualquier carga de trabajo futura VXLAN/subredes creadas detrás del DLR. Aunque esto se puede lograr a través de rutas estáticas en el ESG, la intención de la topología de la carga de trabajo es la de un diseño de mejores prácticas demostrado. Por lo tanto, Open Shortest Path First (OSPF) se configura entre la carga de trabajo ESG y el DLR en sentido descendente.

Para obtener más información sobre la configuración, consulte [Configurar protocolo OSPF](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-6E985577-3629-42FE-AC22-C4B56EFA8C9B.html).

Tabla 11. Direccionamiento dinámico

| Área | Tipo de OSPF | IP de interfaz OSPF | Autenticación OSPF |
|:---- |:--------- |:----------------- |:------------------- |
| 51 | auxiliar | Asignar una IP para cada DLR y ESG en la red RFC1918 de tránsito | Ninguna |

### Reglas de cortafuegos para NSX Edge de carga de trabajo de IBM

De forma predeterminada, el ESG de carga de trabajo está configurado para denegar todo el tráfico.

**Denegar:** Para eliminar todo el tráfico sin respuesta cuando una regla o conjunto de reglas previo (en un orden superior) no permite a dicho tráfico cruzar el cortafuegos. Se selecciona la generación automática de reglas para permitir el tráfico de control en el par ESG.

Se establecen las siguientes reglas de cortafuegos, además de las reglas generadas automáticamente:

Tabla 12. Reglas de cortafuegos de ESG de carga

| Servicio | Fuente | Destino | Protocolo | Acción |
|:------- |:------ |:----------- |:-------- |:------ |
| Cargas de trabajo | Subred de carga | Cualquiera | Cualquiera | Permitir |
| Cualquiera | Cualquiera | Cualquiera | Cualquiera | Denegar |

### Definiciones de VXLAN para NSX Edge de carga de trabajo de IBM

Los pares de alta disponibilidad ESG y DLR de topología de carga de trabajo requieren segmentos L2 (VXLAN) para la conexión de las interfaces internas, el tránsito de datos entre los dos y, finalmente, para las cargas de trabajo.

Tabla 13. Interfaces internas de ESG de carga de trabajo

| Nombre de VXLAN | Zona de transporte de Cloud Foundation o vCenter Server | Tipo |
|:---------- |:------------------------------------------------- |:---- |
| Alta disponibilidad de carga de trabajo HA | transit-1 | global |
| Tránsito de carga de trabajo | transit-1 | global |
| Carga de trabajo | transit-1 | global |

### Valores de ESG DLR para NSX Edge de carga de trabajo de IBM

De forma predeterminada, el registro está habilitado en todos los dispositivos NSX Edge nuevos. El nivel de registro predeterminado es NOTICE.

### Enlaces relacionados

* [Diseño de NSX Edge Services Gateway](nsx_design.html)
* [Arquitectura de varios sitios](multi_site.html)
