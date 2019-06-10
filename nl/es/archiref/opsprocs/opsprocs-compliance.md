---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# Riesgo de
{: #opsprocs-compliance}

La conformidad es un conjunto de requisitos necesarios para cumplir los controles mínimos establecidos por una agencia reguladora o basados en las mejores prácticas del sector. Los marcos de cumplimiento de normativas suelen ser marcos amplios que proporcionan orientación sobre un amplio abanico de tecnologías, mientras que las mejores prácticas del sector son, por lo general, tecnologías específicas para abordar riesgos tecnológicos.

Para su instancia de vCenter Server, sugerimos gestionar la seguridad utilizando un postdespliegue con un equipo dedicado. Esta separación de tareas debe aumentar y supervisar la posición de seguridad de su instancia. HyTrust CloudControl puede dar asistencia a sus equipos con su separación de tareas basada en roles.

HyTrust DataControl y KeyControl pueden ayudarle a ofrecer una protección de la carga de trabajo, como por ejemplo el cifrado en reposo y el geofencing. Puede que le interese desplegar el servicio Caveonix RiskForesight para ayudarle, no sólo en sus requisitos de conformidad, sino también en gestionar ciberriesgos y en la gestión forense.

Las Guías para reforzar la seguridad en VMware proporcionan instrucciones prescriptivas sobre cómo desplegar y utilizar productos VMware de forma segura. Las guías para vSphere se proporcionan en un formato de hoja de cálculo fácil de utilizar, con metadatos enriquecidos para permitir la clasificación de directrices y la evaluación de riesgos. También incluyen ejemplos de scripts para permitir automatizar la seguridad. Se proporcionan documentos de comparación que listan los cambios en las sucesivas versiones de la guía.

Mientras que muchos de los controles documentados en las Guías para reforzar la seguridad en VMware se han incorporado en la arquitectura de referencia de {{site.data.keyword.vmwaresolutions_full}} y, por lo tanto, se despliegan automáticamente, asegúrese de adaptar la postura de seguridad de la plataforma a sus propias necesidades y a la política de empresa. Las Guías para reforzar la seguridad en VMware proporcionan los controles específicos de tecnología necesarios para llevar a cabo esta revisión. Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} automatiza esta tarea de conformidad y proporciona una guía adicional de la agencia reguladora.

vRealize Operations Manager le permite controlar las violaciones de las reglas de conformidad de la Guía de configuración de seguridad de vSphere por parte de los objetos de VMware. Se desencadenan alertas de conformidad en la instancia, los hosts, las máquinas virtuales, los grupos de puertos distribuidos o los conmutadores distribuidos de vCenter Server, permitiendo investigar la violación de conformidad. Además, los clientes interesados en el cumplimiento de la Ley de Responsabilidad y Portabilidad del Seguro Médico (HIPAA - Health Insurance Portability and Accountability Act) y el Estándar de Seguridad de Datos para la Industria de Tarjetas de Pago (PCI DSS - Payment Card Industry Data Security Standard), pueden descargarse, obtener la licencia e instalar paquetes de conformidad de vRealize Operations Manager del sitio web de VMWare Solutions Exchange. Estos paquetes de conformidad proporcionan alertas, políticas e informes para validar los recursos de vSphere en las guías para reforzar HIPAA y PCI.


## Enlaces relacionados
{: #opsprocs-compliance-links}

* [Guía para reforzar la seguridad en VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Guía de seguridad de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fsa_considerations#fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-f5_considerations#f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html#hytrust-cloudcontrol-on-ibm-cloud-overview)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html#hytrust-datacontrol-on-ibm-cloud-overview)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html#hytrust-keycontrol-on-ibm-cloud-overview)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/caveonix/caveonix-intro.html#caveonix-riskforesight)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
