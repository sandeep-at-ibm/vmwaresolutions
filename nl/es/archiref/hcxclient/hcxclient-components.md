---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Glosario de componentes y términos de HCX
{: #hcxclient-components}

HCX consta de un lado de nube (destino o entorno VCD) y uno o más clientes (origen). Se debe desplegar una instancia de HCX por vCenter, incluso si los vCenters en los que se despliega HCX están enlazados en el mismo dominio de SSO en el cliente o en la nube. Las configuraciones que admite HCX son, de uno a uno, de uno a muchos, de muchos a uno y de muchos a muchos.

## Lado del destino y lado del cliente
{: #hcxclient-components-cloud-client-side}

HCX tiene el concepto de lado de la nube (destino o entorno VCD) y lado del cliente (origen).

- Lado del destino: el gestor de nube de HCX está predesplegado y configurado con los perfiles de red y de cálculo listos para la creación de malla de servicio.  
- Lado del cliente: cualesquiera instancias de vSphere que cumplan los requisitos previos para la instalación y la operación. El lado del cliente de HCX es el maestro que controla la instancia de esclavo del lado de la nube a través de su complemento de interfaz de usuario de cliente web de vCenter.

## Gestores HCX
{: #hcxclient-components-hcx-manager}

- Lado de la cloud: el gestor HCX Cloud se configura para escuchar el registro, la gestión y el tráfico del control del lado del cliente entrante.
- Lado del cliente: HCX Enterprise Manager es un archivo de imagen OVA específico del lado del cliente, que proporciona la funcionalidad de la interfaz de usuario para gestionar y operar HCX. El HCX Manager del lado del cliente es responsable del registro con el HCX Manager del lado de la nube y de crear un plano de gestión entre el cliente y la nube. Además, es responsable del despliegue de malla de servicio en el lado del cliente y de dar instrucciones al lado de la nube para que haga lo mismo.

## Componentes de malla de servicio
{: #hcxclient-components-fleet}

Los componentes de HCX Service Mesh son responsables de crear los datos y los planos de control entre el lado del cliente y la nube. Desplegados como máquinas virtuales (VM) en pares duplicados, la malla de servicio consta de los componentes siguientes:

- Interconnect Appliance (HCX-IX): crea túneles cifrados que dan soporte al tráfico de réplica y vMotion (migración masiva).
- WAN Optimizer Appliance (HCX-WAN): HCX incluye un dispositivo de optimización Silver Peak™ WAN desplegado de forma opcional. Se despliega como un dispositivo de máquina virtual. Una vez desplegado, el tráfico de túnel de CGW se redirige para atravesar el optimizador de WAN. Como el optimizador de WAN reduce el tráfico de forma significativa en la WAN (normalmente de 3:1 a 6:1 observado) e incrementa la fiabilidad de la conexión, se recomienda desplegar siempre el optimizador de WAN con CGW. La ventaja añadida de desplegar el optimizador de WAN se amplía para limitar el ancho de banda de WAN consumido por el tráfico de migración de VM. La interfaz de gestión del optimizador de WAN no está configurada de forma predeterminada.
- Extensión de red (HCX-NE): proporciona las posibilidades de extensión de red de la capa 2, permitiendo migraciones entre la ubicación local y el entorno de vSphere que necesita reasignar las direcciones IP de las máquinas virtuales.
- Host ESXi de proxy: siempre que HCX-IX esté configurado para conectar con el lado HCX del lado de la nube, aparece un host ESXi de proxy en vCenter fuera de cualquier clúster. Este host ESXi tiene la misma dirección IP de vMotion y gestión que el dispositivo HCX-IX correspondiente. Esto permite que el entorno de vSphere, tanto en el lado del cliente como en el de la nube, funcione como si realizara una vMotion local. Ventajas de este método:
  - Los rangos de IP de gestión de ambos lados podrían solaparse sin pérdida de funcionalidad.
  - El lado de la nube no tiene visibilidad de vSphere sobre el lado del cliente, por lo que es más seguro.

## Portales de usuario de HCX
{: #hcxclient-components-hcx-user-portals}

- Interfaz de usuario web de cliente - El portal web del cliente de HCX es la interfaz de usuario principal para HCX. Cuando HCX Manager del lado del cliente está instalado, aparece como un complemento de la interfaz de usuario web de vCenter. Controla el registro de HCX remoto en la nube (emparejamiento de sitios), el despliegue de componentes de flota, el estiramiento de red y la migración de máquina virtual a y fuera de la nube.
- Interfaz de usuario de la nube - Se puede acceder a la interfaz de usuario de HCX del lado de la nube a través del URL de registro público proporcionado para el registro del cliente de HCX. De forma predeterminada, utiliza las credenciales de vCenter Admin del lado de la nube `administrator@vsphere.local`. Se suele utilizar para actualizar la instalación y modificar alguna configuración de red.

## Enlaces relacionados
{: #hcxclient-components-related}

* [Requisitos de acceso a puertos para VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [Preparación del entorno de instalación](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Despliegue del cliente de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Malla de servicio en instalaciones locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migraciones de VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Supervisión de parámetros y componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolución de problemas de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
