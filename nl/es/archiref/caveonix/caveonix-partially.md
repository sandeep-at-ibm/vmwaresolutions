---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# Parcialmente distribuido
{: #caveonix-partially}

Una vez completado el despliegue automatizado, se puede escalar manualmente aumentando la RAM y el disco en la máquina virtual (VM) inicial y añadir tres VM de escalado. Se puede ejecutar el script de configuración de Riskforesight para habilitar y configurar los componentes de la aplicación en las cuatro máquinas virtuales.

Se espera que este modelo de despliegue dé servicio a hasta 500 activos con un máximo de 30 días de indexación de datos.

Seleccione las siguientes direcciones IP disponibles desde la subred portátil privada de {{site.data.keyword.cloud}}. Configure los nombres FQDN en ADDNS.

El dimensionamiento de las máquinas virtuales es el siguiente:

Tabla 1. Parámetros base

|Parámetro	|Valor|
|---|---|
|Tipo	|Base|
|Cantidad de VM	|1|
|vCPU	|16|
|RAM	|64 GB|
|Disco	|1000 GB|
|SO	|CentOS 7|
|Componentes de aplicación instalados	|IU, App, Plugins, Recopilador central, Almacén de datos de índice, Almacén de datos de mensajería, Almacén de datos relacional, Recopilador remoto|

Los detalles de la máquina virtual de escalado son los siguientes:

Tabla 2. Parámetros de escalado

| Parámetro	| Valor |
|---|---|
| Tipo	| Escalado (Scale-out) |
| Cantidad de VM	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| Disco	| 4 TB |
| SO	| CentOS 7 |
| Componentes de aplicación instalados	| Nodos de datos (escalado) |

Los detalles de la VM del recopilador remoto se muestran en la tabla siguiente.

Tabla 3. Parámetros del recopilador remoto

|Parámetro	|Valor|
|---|---|
|Cantidad de VM	|Según sea necesario|
|vCPU	|8|
|RAM	|8 GB|
|Disco	|1 TB|
|SO	|CentOS 7|
|Componentes de aplicación instalados	|Recopilador remoto|

## Enlaces relacionados
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
