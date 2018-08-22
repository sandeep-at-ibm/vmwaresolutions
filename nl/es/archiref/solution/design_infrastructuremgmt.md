---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-13"

---

# Diseño de gestión de infraestructura

La gestión de infraestructura hace referencia a los componentes que están gestionando la infraestructura de VMware. Este diseño utiliza una única instancia de controlador de servicios de plataforma externa (PSC) y una sola instancia de servidor de vCenter:
* El vCenter Server es la plataforma centralizada para la gestión de entornos de vSphere y es uno de los componentes fundamentales de esta solución.
* Se utiliza en esta solución para proporcionar un conjunto de servicios de infraestructura que incluyen el inicio de sesión único de VMware vCenter, el servicio de licencia, el servicio de búsqueda y la Autoridad certificadora de VMware.

Las instancias de PSC y de vCenter Server son máquinas virtuales (VM) independientes.

## Diseño de PSC

Este diseño despliega un único PSC externo como un dispositivo virtual en una subred portátil en la VLAN privada que está asociada con las máquinas virtuales de gestión. Su pasarela predeterminada se establece en el direccionador de cliente de fondo (BCR). El dispositivo virtual se configura con las especificaciones de la tabla siguiente.

**Nota**: Estos valores se establecen en el momento del despliegue y no se pueden cambiar.

Tabla 1. Especificaciones del controlador de servicios de plataforma

| Atributo                    | Especificación                  |
|------------------------------|--------------------------------|
| Platform Services Controller | Dispositivo virtual              |
| Número de vCPU              | 2                              |
| Memoria                       | 4 GB                           |
| Disco                         | 114 GB en almacén de datos VMFS local |
| Tipo de disco                    | Ligero suministrado               |

El PSC ubicado en la instancia primaria tiene asignado el dominio de SSO predeterminado de `vsphere.local`.

## Diseño de vCenter Server

El vCenter Server también se despliega como un dispositivo virtual. Además, el vCenter Server se instala en una subred portátil en la VLAN privada que está asociada con las VM de gestión. Su pasarela predeterminada se establece en la dirección IP asignada en el BCR para dicha subred determinada. El dispositivo virtual se configura con las especificaciones de la tabla siguiente.

Tabla 2. Especificaciones del dispositivo de vCenter Server

| Atributo                    | Especificación                       |
|------------------------------|-------------------------------------|
| vCenter Server               | Dispositivo virtual                   |
| Tamaño de instalación del dispositivo  | Medio (hasta 400 hosts, 4.000 VM) |
| Platform Services Controller | Externo                            |
| Número de vCPU              | 8                                   |
| Memoria                       | 24 GB                               |
| Disco                         | 400 GB en almacén de datos local           |
| Tipo de disco                    | Ligero suministrado                    |

### Base de datos de vCenter Server

La configuración del vCenter Server utiliza una base de datos local e incorporada de PostgreSQL incluida con el dispositivo. La base de datos incorporada se utiliza para eliminar las dependencias sobre bases de datos y licencias externas.

### Especificación de clúster de vCenter Server

Este diseño le permite agrupar los hosts ESXi de vSphere que se suministran a través de la solución. Antes de que se puedan crear clústeres, sin embargo, se crea un objeto de centro de datos que significa la ubicación de los hosts ESXi de vSphere, así como el pod dentro del centro de datos. Se crea un clúster una vez creado el objeto de centro de datos. El clúster se despliega con la alta disponibilidad (HA) de VMware vSphere y con el planificador de recursos distribuidos (DRS) de VMware vSphere habilitado.

### Planificador de recursos distribuidos de vSphere

Este diseño utiliza la planificación de recursos distribuidos (DRS) de vSphere en el clúster inicial para colocar las VM y utiliza DRS en clústeres adicionales para migrar dinámicamente las máquinas virtuales para lograr clústeres equilibrados. El nivel de automatización se establece en totalmente automatizado para que la ubicación inicial y las recomendaciones de migración sean ejecutadas automáticamente por vSphere. Además, el umbral de migración se establece en moderado, de modo que vCenter aplicará las recomendaciones de prioridad 1, 2 y 3 para lograr al menos una mejora decente en el equilibrio de carga del clúster.

**Nota:** La gestión de alimentación a través de la característica **Distributed Power Management** no se utiliza en este diseño.

### Alta disponibilidad de vSphere

Este diseño utiliza la alta disponibilidad (HA) de vSphere en el clúster inicial y los clústeres adicionales para detectar anomalías de cálculo y recuperar las VM que se ejecutan dentro de un clúster. La característica de HA de vSphere en este diseño se configura con las opciones **Supervisión de host** y **Control de admisión** habilitadas dentro del clúster. Además, el clúster inicial reserva los recursos de un nodo como capacidad de reserva para la política de control de admisión.

**Nota**: Usted es responsable de ajustar la política de control de admisión cuando el clúster se expanda o se contraiga más tarde.

De forma predeterminada, la opción **Prioridad de reinicio de VM** se establece en medio y la opción **Respuesta de aislamiento de host** está inhabilitada. Además, la **supervisión de VM** está inhabilitada y la característica **Latido del almacén de datos** se configura para incluir cualquiera de los almacenes de datos del clúster. Este enfoque utiliza los almacenes de datos NAS si están presentes.

## Automatización

La piedra angular de estas soluciones es la automatización. La automatización trae las siguientes ventajas:
* Reduce la complejidad del despliegue.
* Reduce drásticamente el tiempo de despliegue.
* Garantiza que la instancia de VMware se ha desplegado de forma coherente.

Las VM de {{site.data.keyword.IBM}} CloudBuilder, IBM CloudDriver y SDDC Manager trabajan juntas para crear una nueva instancia de VMware y realizar funciones de gestión del ciclo de vida.

### IBM CloudBuilder e IBM CloudDriver

La instancia de servidor virtual de IBM CloudBuilder e IBM CloudDriver (VSI) son componentes desarrollados por IBM a los que no puede acceder.
* IBM CloudBuilder es una instancia de servidor virtual (VSI) de {{site.data.keyword.cloud_notm}} temporal que arranca el despliegue, la configuración y la validación de los componentes de solución dentro de los hosts ESXi nativos suministrados.
* El VSI de IBM CloudDriver se despliega para la creación de instancias y, a continuación, periódicamente, según sea necesario, con el último código de {{site.data.keyword.cloud_notm}} for VMware para operaciones como, por ejemplo, el despliegue de nodos, clústeres o servicios adicionales. IBM CloudDriver se comunica con la consola de {{site.data.keyword.vmwaresolutions_short}} a través de una pasarela VMware NSX Edge Services Gateway desplegada exclusivamente para la gestión de instancias y que actúa como un agente para mantener la instancia. IBM CloudDriver es responsable de las acciones en curso como, por ejemplo, la adición de nuevos hosts nativos en el clúster y el despliegue de servicios complementarios en la instancia. Para las instancias de Cloud Foundation, IBM CloudDriver se comunica con la máquina virtual de VMware SDDC Manager para realizar funciones como, por ejemplo, la adición y el parcheado de hosts.

Es posible que el usuario suprima o dañe las máquinas virtuales descritas en las secciones siguientes. Cuando se elimina una VM, se cierra o se vuelve inoperable, se interrumpen las siguientes operaciones de Cloud Foundation o vCenter Server en la consola de {{site.data.keyword.vmwaresolutions_short}}:
* Visualización del estado de la instancia o del host
* Adición o eliminación de clústeres
* Adición o eliminación de hosts ESXi
* Adición o eliminación de servicios
* Parches

### SDDC Manager

Para las instancias de Cloud Foundation, la VM de SDDC Manager es un componente desarrollado y mantenido por VMware. Se mantiene como parte de la instancia durante todo su ciclo de vida. Es responsable de las siguientes funciones de ciclo de vida de las instancias:
* Gestión de los componentes de VMware: vCenter Server, Platform Services Controller (PSC), vSAN y NSX, incluida la asignación de direcciones IP y la resolución de nombre de host.
* Expansión y retracción de los hosts ESXi dentro del clúster, incluidos los servicios afectados, como NSX VTEP, vSAN, agrupaciones de recursos.

Para las instancias de vCenter Server, estas actividades las realiza IBM CloudDriver, ya que no hay ningún Gestor de SDDC.

### Flujo de automatización

El procedimiento siguiente describe el pedido de los sucesos cuando se solicita una instancia de VMware a través de la consola de {{site.data.keyword.vmwaresolutions_short}}:
1.  Pedido de VLAN y subredes para la red desde {{site.data.keyword.cloud_notm}}.
2.  Pedido de {{site.data.keyword.baremetal_short}} con vSphere Hypervisor instalado.
3.  Si es aplicable, solicite a Microsoft Windows Virtual Server Instance (VSI) que se sirva como controlador de dominio de Active Directory.
4.  Validación de la red y el hardware desplegado.
5.  Si es aplicable, configuración inicial de vSAN de nodo único.
6.  Si es aplicable, el despliegue y la configuración de dos máquinas virtuales de Microsoft Windows para servir como controladores de dominio de Active Directory.
7.  Despliegue y configuración de vCenter, PSC y NSX.
8.  Agrupación en clúster de nodos ESXi restantes, expansión de vSAN, si procede, y configuración de los componentes NSX (VTEP).
9.  Despliegue de la VM de VMware Cloud Foundation SDDC Manager, si procede, y el VSI de IBM CloudDriver.
10.  Validación de la instalación y configuración del entorno.
11. Eliminación del VSI de CloudBuilder.
12. Despliegue de servicios opcionales como, por ejemplo, el servidor de copia de seguridad y el almacenamiento.

### Enlaces relacionados

* [Diseño de infraestructura física](design_physicalinfrastructure.html)
* [Diseño de infraestructura virtual](design_virtualinfrastructure.html)
* [Diseño de servicios comunes](design_commonservice.html)
