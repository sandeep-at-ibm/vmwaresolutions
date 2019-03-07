---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Paso 4 - Configuración de la aplicación
{: #caveonix-step4}

Una vez que se han desplegado las máquinas virtuales (VM) y se han instalado los componentes de la aplicación, la solución Caveonix RiskForesight está disponible para que el proveedor de servicios y el primer arrendatario u organización la configuren.

El proveedor de servicios es la organización de nivel superior y hay uno o más arrendatarios/organizaciones a los cuales presta servicio dicho proveedor. El Proveedor de servicios asigna activos que se recopilan desde vCenter al arrendatario u organizaciones, que a continuación los asigna a aplicaciones o subaplicaciones. Estas aplicaciones estarán sujetas a un régimen de conformidad.

Este paso se completa inicialmente mediante la automatización de IC4VS, que utiliza la información que proporciona el cliente durante el proceso de pedido y la información predeterminada. El cliente, tras el despliegue, puede iniciar el proceso de configuración para modificar el proveedor de servicios o la organización de arrendatario en función de la instalación posterior necesaria.

La configuración del proveedor de servicios tiene ocho subpasos:
-	Paso 1: Detalle de organización - Añada los detalles de la organización padre para su proveedor de servicios de nube. Esta organización puede tener múltiples ubicaciones físicas y múltiples centros de datos. Las organizaciones para sus arrendatarios y las suborganizaciones para su proveedor de servicios se añaden más tarde.
-	Paso 2: Ubicaciones – Correlacione la infraestructura en las "Ubicaciones" de RiskForesight, ya que los activos se agrupan por ubicación, proveedor de nube y repositorio de activos.
-	Paso 3: Entornos - Opcional. Los entornos son una forma de agrupar activos. Por ejemplo, DevOps, Sitio de recuperación tras desastre, Producción.
-	Paso 4: Proveedor de nube - Añada los “proveedores” que proporcionan la infraestructura en la que se ejecuta su aplicación.
-	Paso 5: Repositorios de activos - Un repositorio de activos asocia un conjunto de activos con una organización, un proveedor de nube y una ubicación.
-	Paso 6: Organizaciones - Cree una suborganización para sus propias operaciones y organizaciones adicionales - una para cada uno de los arrendatarios del proveedor de servicios. Cada arrendatario debe pasar por su propio proceso de configuración, incluida la creación de sus propias suborganizaciones.
-	Paso 7: Usuarios de la organización - Cree y asigne usuarios a las organizaciones del arrendatario y las suborganizaciones del proveedor de servicios.
-	Paso 8: Planificador de tareas – Configure tareas para: sincronizar con el repositorio de activos, realizar exploraciones de conformidad y vulnerabilidad de SCAP, recopilar flujos de red NSX, recopilar información sobre el software que se ejecuta en activos supervisados, recopilar registros y sucesos del sistema para activos.

La configuración de organización o arrendatario tiene siete subpasos:

-	Paso 1: Organización - Añada detalles para su organización primaria. También puede crear suborganizaciones. Utilice las organizaciones para segmentar sus usuarios, o como una de las formas de agrupar sus activos. Puede crear más organizaciones con una de las organizaciones existentes como padre. Cuando crea una nueva organización, puede seleccionar el "Valor de impacto empresarial", que se utiliza para generar puntuaciones de ciberriesgo.
-	Paso 2: Activos de la organización - Los nuevos activos/cargas de trabajo se agrupan automáticamente por ubicación, proveedor de nube y repositorio de activos. Los activos se pueden asignar solo a una organización al mismo tiempo. El proveedor de servicios tiene que asignar activos a una organización.
-	Paso 3: Asocie el entorno y la ubicación – Opcional. Los entornos están definidos por el proveedor de servicios.
-	Paso 4 y 5: Cree subaplicaciones o aplicaciones - Se utiliza para agrupar activos entre ubicaciones y organizaciones y ver sus flujos y políticas asociados. Cree aplicaciones que coincidan con los servicios de negocio y de TI. Por ejemplo, Application=SAP, Sub-Applications=SAP Front End, SAP Middle Tier y SAP Back End. El valor de impacto empresarial se corresponde con una aplicación, los regímenes de conformidad se aplican a una aplicación.
-	Paso 6: Acceso remoto - El acceso remoto es necesario para ejecutar exploraciones sobre activos, puede ser una cuenta de servicio predeterminada o una cuenta específica del activo.
-	Paso 7: Planificador de tareas - Planifique exploraciones para que se ejecuten de forma periódica. Los tipos de tareas incluyen: Exploración de SCAP-Vulnerabilidad, Exploración de SCAP-XCCDF, Exploración de flujo NSX, exploración de software, exploración de extractos de registro.

La siguiente información se recopila del usuario en el momento del pedido y se utiliza en la configuración de la aplicación.

Tabla 1. Información recopilada del usuario

|Etapa de configuración |Parámetro |
|---|---|
|Organización / Repositorios de activos  |Nombre de la organización |
|Organización |Número de teléfono |
|Organización |Correo electrónico |
|Organización / Repositorios de activos |Línea de dirección 1 |
|Proveedor de nube/ Repositorios de activos |Nombre |
|Proveedor de nube |Descripción |
|Proveedor de nube |Correo electrónico de POC |
|Proveedor de nube |Tipo|
|Proveedor de nube |Nombre de POC |
|Proveedor de nube |Teléfono de POC |

En la configuración de la aplicación se utiliza la siguiente información predeterminada.

Tabla 2. Información predeterminada utilizada en la configuración de la aplicación

|Etapa de configuración |Parámetro |
|---|---|
|Entorno |El nombre de entorno se establece en "Inicial"|
|Entorno | La puntuación se establece en 5|
|Repositorio de activos |Se configuran dos repositorios de activos; vCenter y NSX Manager. El URL de host se establece en https://*vCenter fqdn* y https://*NSX Manager fqdn*|
|Repositorio de activos |Se configuran dos repositorios de activos; vCenter y NSX Manager, ambos utilizan el mismo nombre de usuario. El nombre de usuario se establece en el nombre de usuario administrador de vCenter|
|Repositorio de activos |Se configuran dos Repositorios de activos; vCenter y NSX Manager, ambos utilizan la misma contraseña. La contraseña se establece en la contraseña del administrador de vCenter
|Repositorio de activos |Se configuran dos Repositorios de activos; vCenter y NSX Manager, ambos utilizan la misma contraseña. El tipo se establece en vCenter para un repositorio y NSX para el otro
|Tarea |Se configuran cuatro tareas: exploración de activos, flujos de NSX, exploración de infraestructura VMware y vulnerabilidad de VMware. ScanName se establece en DC1AssetScan, NSXFlows, VMWInfraScan, VMWVulnScan |
|Tarea |Se configuran cuatro tareas: exploración de activos, flujos de NSX, exploración de infraestructura VMware y vulnerabilidad de VMware. El tipo se establece en vCenter, NSX, VMWareInfrastructureScan, VMWareVulnerabilityScan |
|Tarea |La planificación se establece en Por hora para DC1AssetScan y Diaria para los otros |

## Enlaces relacionados
{: #caveonix-step4-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
