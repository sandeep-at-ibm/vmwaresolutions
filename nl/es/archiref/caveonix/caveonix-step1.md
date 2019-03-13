---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Paso 1 - Planificación inicial y requisitos previos
{: #caveonix-step1}

Cada componente de la aplicación Caveonix RiskForesight se acopla ligeramente, pero se gestiona de forma centralizada. Por lo tanto, se pueden desplegar en un patrón de despliegue de máquina virtual (VM) "todo en uno" o los componentes de la aplicación se pueden "escalar" y desplegar en varias máquinas virtuales para incrementar la disponibilidad, el rendimiento y la capacidad.

Los patrones de despliegue se basan en los requisitos de disponibilidad y en el dimensionamiento para la retención de datos. Los nodos de despliegue de RiskForesight se pueden caracterizar como:

-	Máquinas virtuales base – Las máquinas virtuales base alojan los componentes de la aplicación que no se escalan debido a la retención de datos. Estos componentes son: interfaz de usuario de RiskForesight, app de RiskForesight, plugins de RiskForesight, recopilador central, recopilador remoto, almacén de datos de índice, almacén de datos de mensajería y almacén de datos relacional.
-	Máquinas virtuales de escalado – Las máquinas virtuales de escalado, la base de datos y el índice de datos se escalan en función del número de activos y la retención de datos necesaria que genera la demanda de más espacio en disco duro y, por tanto, más máquinas virtuales de escalado.

Existen tres modelos de despliegue de Caveonix RiskForesight:

-	“Todo en uno” – Un despliegue y configuración automatizados de una máquina virtual que aloja todos los componentes de la aplicación:
  - Todos los componentes de la aplicación instalados en una máquina virtual.
  - Los recopiladores remotos se pueden instalar en máquinas virtuales separadas.
  - Despliegues pequeños – hasta 100 activos con 7 - 30 días de indexación.
-	Parcialmente distribuido – una vez completado el despliegue automatizado, se puede escalar manualmente aumentando la RAM y el disco en la máquina virtual inicial y añadir tres máquinas virtuales de escalado.
  - La interfaz de usuario, la app, los plugins, el recopilador central, el recopilador remoto, el almacén de datos de índice, el almacén de datos de mensajería y el almacén de datos relacional desplegados en una máquina virtual.
  - Los recopiladores remotos instalados en máquinas virtuales separadas.
  -	Los nodos de datos de índice desplegados en máquinas virtuales separadas.
  -	Despliegues pequeños y medianos - hasta 500 activos con 30 días de indexación.
- Completamente distribuido - Añada más máquinas virtuales base y máquinas virtuales de escalado de acuerdo con el número de activos y requisitos de retención de datos:
  - Componentes de la aplicación distribuidos en máquinas virtuales separadas para facilitar el escalado.
  -	Se necesita un patrón de despliegue porque el número de activos aumente en el rango de 500 - 100.000.
  -	Los recopiladores remotos instalados en máquinas virtuales separadas.
  -	Interfaz de usuario en múltiples máquinas virtuales.
  -	App y plugins en múltiples máquinas virtuales.
  -	Recopilador central configurado en un clúster.
  -	Almacén de datos relacional desplegado en un modelo primario/secundario.
  -	Almacén de datos de mensajería desplegado en un clúster.
  -	Almacén de datos de índice que se despliega con los nodos maestros y de datos.
  -	Se utilizan más nodos de datos para el escalado porque aumenta el número de activos.

Todos los componentes deben tener un FQDN y registrarse en DNS antes de cualquier despliegue de máquina virtual. Este paso lo realiza la automatización de IC4VS para el despliegue "todo en uno" inicial, pero es responsabilidad del cliente cuándo escalar el despliegue.

## Enlaces relacionados
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
