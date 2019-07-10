---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

subcollection: vmware-solutions


---

# Glosario de componentes y términos de HCX
{: #vcshcx-components}

HCX consta de un lado de nube (destino) y uno o más clientes (origen). Se debe desplegar una instancia de HCX por vCenter, incluso si los vCenters en los que se despliega HCX están enlazados en el mismo dominio de SSO en el cliente o en la nube. Las configuraciones que admite HCX son, de uno a uno, de uno a muchos, de muchos a uno y de muchos a muchos.

## Lado de la nube y lado del cliente
{: #vcshcx-components-cloud-client-side}

HCX tiene el concepto de lado de la nube (destino) y lado del cliente (origen).
- Lado de la nube - vCenter Server on 	{{site.data.keyword.cloud}} con el paquete híbrido. El lado de la nube de HCX es la instancia de esclavo de una relación de cliente de HCX con la nube. Se controla del lado del cliente.
- Lado del cliente - Cualquier instancia de vSphere que cumpla los requisitos previos para la instalación y la operación. El lado del cliente de HCX es el maestro que controla la instancia de esclavo del lado de la nube a través de su complemento de interfaz de usuario de cliente web de vCenter.

## HCX Manager
{: #vcshcx-components-hcx-manager}

- El HCX Manager del lado del cliente es la primera parte de una instalación de HCX desplegada en el lado de la nube por la automatización de {{site.data.keyword.vmwaresolutions_short}}.
Inicialmente se trata de un único archivo de imagen OVA desplegado, específico del lado de la nube, junto con un cortafuegos de equilibrador de carga de NSX Edge que se configura específicamente para el rol de HCX. HCX Manager se configura para
escuchar el registro, la gestión y el tráfico del control del lado del cliente entrante.
- El HCX Manager del lado del cliente es un archivo de imagen OVA específico del lado del cliente, que proporciona la funcionalidad de la interfaz de usuario para gestionar y operar HCX. El HCX Manager del lado del cliente es responsable del registro con el HCX Manager del lado de la nube y de crear un plano de gestión entre el cliente y la nube. Además, es responsable del despliegue de componentes de flota en el lado del cliente y de dar instrucciones al lado de la nube para que haga lo mismo.

## Componentes de la flota
{: #vcshcx-components-fleet}

Los componentes de la flota HCX son responsables de crear los datos y los planos de control entre el lado del cliente y la nube. Desplegados como máquinas virtuales (VM) en pares duplicados, la flota consta de los componentes siguientes:

- Cloud Gateway (CGW) - Cloud Gateway es un componente opcional, responsable de la creación de túneles cifrados que dan soporte al tráfico de réplica y vMotion (migración masiva). Solo existe un par por sitio de HCX enlazado.
- Concentrador de capa 2 (L2C) - El Concentrador de capa 2 es un componente opcional, responsable de crear túneles cifrados para el plano de datos y de control correspondiente al tráfico de capa 2 extendida. Cada par L2C puede manejar hasta 4096 redes extendidas. Se despliegan más pares de L2C según sea necesario. La capacidad de ancho de banda está limitada a ~4 Gbps, por lo que si la capacidad de ancho de banda externa es mayor que 4 Gbps, el uso de más pares de L2C permite una mayor utilización de la red subyacente.
- Optimizador de WAN - HCX incluye un dispositivo de optimización Silver Peak™ WAN
desplegado de forma opcional. Se despliega como un dispositivo de máquina virtual. Una vez desplegado, el tráfico de túnel de
CGW se redirige para atravesar el optimizador de WAN.
Como el optimizador de WAN reduce el tráfico de forma significativa en la WAN
(normalmente de 3:1 a 6:1 observado) e incrementa la fiabilidad de la conexión, se recomienda desplegar siempre el optimizador de WAN con CGW. La ventaja añadida de desplegar el optimizador de WAN se amplía para limitar el ancho de banda de WAN consumido por el tráfico de migración de VM. La interfaz de gestión del optimizador de WAN no está configurada de forma predeterminada.
- Host ESXi de proxy - Siempre que CGW esté configurado para conectar con el lado HCX del lado de la nube, aparece un host ESXi de proxy en vCenter fuera de cualquier clúster. Este host ESXi tiene la misma dirección IP de vMotion y gestión que el dispositivo CGW correspondiente. Esto permite que el entorno de vSphere, tanto en el lado del cliente como en el de la nube, funcione como si realizara una vMotion local. Ventajas de este método:
    - Los rangos de IP de gestión de ambos lados podrían solaparse sin pérdida de funcionalidad.
    - El lado de la nube no tiene visibilidad de vSphere sobre el lado del cliente, por lo que es más seguro.

## Portales de usuario de HCX
{: #vcshcx-components-hcx-user-portals}

- Interfaz de usuario web de cliente - El portal web del cliente de HCX es la interfaz de usuario principal para HCX. Cuando HCX Manager del lado del cliente está instalado, aparece como un complemento de la interfaz de usuario web de vCenter. Controla el registro de HCX remoto en la nube (emparejamiento de sitios), el despliegue de componentes de flota, el estiramiento de red y la migración de máquina virtual a y fuera de la nube.

- Interfaz de usuario de la nube - Se puede acceder a la interfaz de usuario de HCX del lado de la nube a través del URL de registro público proporcionado para el registro del cliente de HCX. De forma predeterminada, utiliza el inicio de sesión único (SSO) de vSphere del lado de la nube (` administrator@vsphere.local`). Se suele utilizar para actualizar la instalación y modificar alguna configuración de red. También se utiliza para crear redes virtuales dentro de HCX.

- Interfaz de usuario de gestión de dispositivos de HCX Manager de cliente/nube - Acceso a la interfaz de usuario de gestión de dispositivos para el lado del cliente o la nube a través de la dirección IP privada de la máquina virtual tal como se ve en vCenter `https://<hcxmanager_IP>:9443`. El ID (normalmente “admin”) y la contraseña se proporcionan a través del portal de {{site.data.keyword.vmwaresolutions_short}}. La interfaz de usuario de gestión se utiliza para iniciar y detener los servicios de HCX Manager, configurar la supervisión de registros, la configuración de red básica, las actualizaciones manuales, la recopilación de registros de soporte cuando la interfaz de usuario web no funciona, el registro con los componentes de vSphere (vCenter, PSC, NSX Manager) y la gestión de certificados.

## Enlaces relacionados
{: #vcshcx-components-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
