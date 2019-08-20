---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modelos de despliegue para Caveonix RiskForesight
{: #caveonix-deploy}

En esta sección se describen los modelos de despliegue para Caveonix RiskForesight, junto con el proceso de instalación para instalar la solución.

Cuando selecciona la opción {{site.data.keyword.vmwaresolutions_full}} RiskForesight, no tiene que seguir todos los pasos del despliegue, ya que los iniciales se automatizan. Sin embargo, para comprender el despliegue completo y la arquitectura, y para aquellos que desean escalar la solución después del despliegue inicial, se necesita un conocimiento detallado.

La instalación de RiskForesight consta de los siguientes pasos de alto nivel:

1. [Planificación inicial y requisitos previos](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) – Comprender y seleccionar una opción de despliegue, configurar DNS para proporcionar la resolución de FQDN/IP para los componentes de la aplicación.
2. [Despliegue de máquina virtual](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) – Desplegar las máquinas virtuales desde una plantilla de OVF. La máquina virtual ha instalado en ella todos los componentes de la aplicación.
3. [Configuración de la aplicación](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) – Ejecutar el script de configuración de Caveonix que configura el componente de la aplicación en cada una de las máquinas virtuales.
4. [Configuración de la aplicación](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) – Configurar el proveedor de servicios y un Arrendatario u Organización, para que la aplicación sea accesible para los usuarios.

La instalación automatizada suministra una máquina virtual y configura todos los componentes de la aplicación en dicha máquina virtual.
{:note}

## Dimensionamiento del despliegue
{: #caveonix-deploy-sizing}

El dimensionamiento del despliegue se calcula utilizando los siguientes volúmenes.

Tabla 1. Volúmenes

|Tipo de datos	|Volumen |
|---|---|
|Exploraciones al día	|1 |
|Datos de exploración (MB)	|20 |
|Datos de registro (MB)	|500 |
|Datos de flujo (MB)	|200 |
|Datos de activos (MB)	|46 |
|Almacenamiento total por activo al día (MB)	|766 |
|Multiplicador de réplica de datos	|2 |
|Almacenamiento de índice total / Activo / Día (MB)	|1532 |

El Multiplicador de réplica de datos se establece en 2 ya que el Almacén de índices (búsqueda elástica) utiliza de forma predeterminada la réplica n+1 de los índices.
{:note}

El número de máquinas virtuales de escalado se calcula a partir del número de activos y el número de días de datos para indexar.

Tabla 2. Parámetros de máquinas virtuales de escalado

|Número de activos	|100	|500	|5000 |
|---|---|---|---|
|Días de datos	|30	|30	|30 |
|Almacenamiento de índice total / Activo / Día (MB)	|1532	|1532	|1532 |
|Almacenamiento de índice total / Activo / 30 días (TB)	|4	|22	|219 |
|Datos admitidos por nodo de escalado (TB)	|0	|8	|8 |
|Máquinas virtuales de escalado necesarias	|0	|3	|27 |

La cantidad de almacenamiento que se necesita se calcula de la siguiente forma:

Tabla 3. Parámetros de almacenamiento

|Número de activos	|100	|500	|5000 |
|---|---|---|---|
|Retención de datos a largo plazo (Meses)	|8	|8	|8 |
|Almacenamiento total por activo al día (MB)	|766	|766	|766 |
|Días de datos	|30	|30	|30 |
|Retención de datos a corto plazo (TB)	|7	|33	|329 |
|Retención de datos a largo plazo (TB)	|18	|88	|877 |

Desde una perspectiva de datos, los datos se utilizan de la forma siguiente:

-	Los datos de exploración se utilizan en la gestión de conformidad
-	Los datos de registro se utilizan en la gestión forense
-	Los datos de políticas y de flujo se utilizan en la gestión de riesgos y los datos de flujo solo están disponibles desde NSX Manager

El almacenamiento de datos tiene tres niveles:

-	Replicado
-	A corto plazo
-	A largo plazo

En la tabla siguiente se proporciona un resumen de los despliegues:

Tabla 4. Resumen

|Modelo de despliegue	|“todo en uno”	|Distribuido parcialmente	|Distribuido completamente |
|---|---|---|---|
|Número de activos	|100	|500	|5000 |
|Datos en línea generados en 30 días (TB)	|4	|22	|219 |
|Retención de datos Nearline (90 días) (TB)	|7	|33	|329 |
|Retención de datos Offline (8 meses) (TB)	|18	|88	|877 |
|Retención de almacenamiento de datos total (1 año) (TB)	|28	|142	|1425 |
|Máquinas virtuales base	|1	|1	|20 |
|Máquinas virtuales de escalado	|0	|3	|28 |
|Total de máquinas virtuales	|1	|4	|48 |

**Notas:**
Cuando se elimina el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, la automatización de {{site.data.keyword.vmwaresolutions_short}} suprime sólo la única máquina virtual "todo en uno" de Caveonix que se ha desplegado y la subred privada dedicada que se ha solicitado para ella. Por tanto,
* Si ha escalado la máquina virtual de Caveonix en varias máquinas virtuales, esas máquinas virtuales adicionales no se eliminan.
* Si ha utilizado las direcciones IP de la subred privada dedicada en máquinas virtuales adicionales, se deben asignar nuevas direcciones IP a esas máquinas virtuales para que continúen funcionando.
* Si suprime la instancia A de vCenter Server con el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} instalado y ha utilizado las direcciones IP de la subred privada dedicada solicitada para el servicio en la instancia B de vCenter Server, la subred privada dedicada se cancela tras la supresión de la instancia A de vCenter Server.
