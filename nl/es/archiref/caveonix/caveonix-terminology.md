---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Glosario de términos de Caveonix
{: #caveonix-terminology}

Este glosario proporciona algunas descripciones para los términos que están asociados a la solución Caveonix RiskForesight:

-	**NIST Special Publication 800-53:** una infraestructura de gestión de riesgos que se encarga del control de seguridad.
-	**Security Content Automation Protocol (SCAP):** un método que utiliza estándares específicos para habilitar la gestión automatizada de vulnerabilidades, la medición y la evaluación de la conformidad de políticas de los sistemas desplegados en una organización. Las listas de comprobación estandarizan y habilitan la automatización del enlace entre las configuraciones de seguridad del sistema y la infraestructura de controles de NIST Special Publication 800-53.
  - National Vulnerability Database (NVD) es el repositorio de contenido del gobierno de los Estados Unidos para SCAP.
  -	SCAP permite a los administradores de seguridad explorar sistemas, software y otros dispositivos en función de una línea base de seguridad predeterminada para determinar si la configuración y los parches de software se implementan según el estándar con el cual se están comparando.
  Los componentes de SCAP son los siguientes:
  -	Common Vulnerabilities and Exposures (CVE) - Una lista de vulnerabilidades de ciberseguridad conocidas públicamente.
  -	Common Configuration Enumeration (CCE) - Una lista de problemas de configuración del sistema relacionados con la seguridad.
  -	Common Platform Enumeration (CPE) - Un esquema de denominación estructurado para sistemas, software y paquetes de tecnología de la información.
  -	Common Weakness Enumeration (CWE) – Una lista de las vulnerabilidades de seguridad de software más comunes.
  -	Common Vulnerability Scoring System (CVSS) - Proporciona una forma de capturar las características principales de una vulnerabilidad y generar una puntuación numérica que refleja su gravedad.
  -	Extensible Configuration Checklist Description Format (XCCDF) - un lenguaje de especificación para escribir listas de comprobación de seguridad, benchmarks y tipos de documentos relacionados. Un documento XCCDF representa una recopilación estructurada de reglas de configuración de seguridad para algunos conjuntos de sistemas de destino.
  -	Open Vulnerability and Assessment Language (OVAL) – Un lenguaje que se utiliza para codificar detalles del sistema y un surtido de repositorios de contenido. El lenguaje estandariza los tres pasos principales del proceso de evaluación:
      - Representación de la información de configuración de los sistemas para las pruebas.
      -	Análisis del sistema (estado de vulnerabilidades, configuración y parches)
      -	Presentación de informes sobre los resultados de esta evaluación.
-	**Security Technical Implementation Guide (STIG):** una metodología de ciberseguridad para estandarizar protocolos de seguridad en redes, servidores, sistemas y diseños lógicos para mejorar la seguridad general. Estas guías, cuando se implementan, mejoran la seguridad de las arquitecturas de software, hardware, físicas y lógicas para reducir aún más las vulnerabilidades.
-	**Proveedor de servicios:** la organización de nivel superior.
-	**Proveedor de nube**: proporciona la infraestructura en la que opera la nube definida por el software. RiskForesight se puede configurar para múltiples proveedores de nube.
-	**Organizaciones:** las organizaciones de arrendatario y las suborganizaciones del proveedor de servicios. Si el repositorio de activos es vCenter, la lista de organización/arrendatario debe crearse manualmente.
-	**Roles:** roles preconfigurados y roles creados por el proveedor de servicios. El proveedor de servicios no puede editar los roles preconfigurados.
-	**Usuarios de la organización:** usuarios de las organizaciones y suborganizaciones de arrendatario.
-	**Repositorio de activos:** un punto de integración que permite a RiskForesight sincronizar el activo actual en la zona de gestión de CSP y en la zona de cliente. La versión actual de RiskForesight admite la sincronización para VMware vCloud Director y vCenter Servers. También admite la recopilación de datos de VMware NSX Manager. Los activos se recopilan desde el repositorio de activos. El Proveedor de servicios asigna activos que se recopilan de vCenter a las organizaciones del arrendatario y las suborganizaciones del proveedor de servicios. Se puede asignar un activo solo a una organización.
-	**Acceso remoto:** proporciona las credenciales de la máquina final para habilitar las exploraciones de vulnerabilidades y la supervisión de conformidad y para recopilar registros de sucesos del sistema. El proveedor de servicios sólo puede habilitar el acceso remoto para sus propios activos. Los arrendatarios tienen el control sobre el acceso remoto desde sus activos.
-	**Aplicaciones y subaplicaciones:** una forma lógica de agrupar activos. Aplicación de ejemplo: SAP, Subaplicaciones de ejemplo: SAP Front End, SAP Middle Tier, SAP Back End.
-	**Ubicaciones:** los activos se agrupan de forma exclusiva por Ubicación, Proveedor de nube y Repositorio de activos.
-	**Entornos:** una forma de agrupar activos y aplicaciones. A cada entorno se le asigna un factor de riesgo de 1 a 10. Este factor se aplica en el cálculo de la puntuación de riesgo. El proveedor de servicios define los entornos
-	**Tareas:** se utiliza en RiskForesight para:
  -	Sincronizar periódicamente el repositorio de activos con RiskForesight.
  -	Realizar exploraciones de conformidad y vulnerabilidades de SCAP.
  -	Recopilar flujos de red y otra información que utiliza exploraciones de NSX.
  -	Recopile información sobre el software que se ejecuta en los activos supervisados.
  -	Recopilar los sucesos del sistema y syslog para los activos.
-	**Tipos de tareas:** se admiten las siguientes tareas:
  -	**Exploración de VMware vCenter:** recopila activos de vCenter.
	- **Exploración de VMware VCD:** recopila activos de VCD.
  -	**Exploración de VMware NSX:** recopila información de red y flujo de red de NSX Manager.
  - **Exploración de SCAP:** este tipo de exploración se utiliza para explorar la conformidad y ciberriesgos en las cargas de trabajo. Esta exploración se basa en el protocolo SCAP (Security Content Automation Protocol). Los releases futuros están planificados para dar soporte al contenido personalizado en el formato OVAL.
  - **Exploración de software:** esta exploración recopila el inventario de software que está instalado en la carga de trabajo de destino bajo gestión. A continuación, se puede buscar en este inventario a través de la opción de búsqueda en la barra superior de la interfaz de usuario.
  - **LogExtract:** esta exploración admite la recopilación de registros de cargas de trabajo Windows y Linux. Esta se utiliza para fines forenses y se ingiere a través de machine learning para generar información útil.
  - **Tarea de AMQP:** esta tarea de AMQP se utiliza para recopilar sucesos en directo del VCD y habilitar la sincronización en tiempo real. RiskForesight consume sucesos de adición, supresión y actualización de activos y actúa sobre estos sucesos. Por ejemplo, si se añade un nuevo activo y RiskForesight ha recibido dicha notificación a través de AMQP, actualiza inmediatamente la base de datos e inicia la exploración de conformidad y ciberriesgo.
  - **Exploración de infraestructura de VMware:** esta exploración realiza una exploración de infraestructura de los activos de VMware.
  -	**Exploración de vulnerabilidades de VMware:** esta exploración realiza una exploración de vulnerabilidades de los activos de VMware.
-	**Régimen de conformidad:** disponible mediante licencia: NIST, NESA, PCI, ISO, HIPAA, GDPR, Custom, FFIEC, FedRAMP Low, FedRAMP Moderate, FedRAMP High
-	**Gestor de políticas:** el gestor de políticas ofrece la función de creación de políticas para una organización basándose en los resultados de machine learning. Caveonix proporciona de forma predeterminada tres tipos de trabajos de machine learning por organización. Los trabajos no editables y adicionales no están soportados todavía. Los tipos de trabajos de machine learning soportados actualmente son:
  -	Caveo Logs
  -	Caveo Networks
  -	Caveo Scan
-	**Anomalía:** en función de las anomalías que se encuentran en los datos, podemos configurar las políticas para tomar medidas en función de las condiciones definidas por el usuario. Puede seleccionar el tipo de trabajo y configurar las condiciones booleanas para la puntuación de anomalía y definir la acción cuando la condición sea verdadera. Por ejemplo:
```
Trabajo: La puntuación de la anomalía "Caveo Logs" es > 90, entonces Marcar el activo para cuarentena y enviar una notificación al canal de Slack.`
Trabajo: La puntuación de la anomalía "Caveo Network" es > 95, entonces Poner en cuarentena el activo y enviar notificación por correo electrónico y también enviar notificación por interfaz de usuario.
```
