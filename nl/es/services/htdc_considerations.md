---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-27"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de HyTrust DataControl on IBM Cloud

El servicio HyTrust DataControl on {{site.data.keyword.cloud}} ofrece un cifrado de alta seguridad con claves de gestión integrada para proteger las cargas de trabajo en todo su ciclo de vida. El servicio proporciona cifrado tanto en el nivel de sistema operativo como en el nivel de datos. Esto permite que cualquier directorio, carpeta o archivo de una carga de trabajo esté cifrado y descifrado.

Este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en, o que se han actualizado a, V2.3 o releases posteriores. La versión actual de HyTrust DataControl que está instalada es la 4.2.1.
{:note}

## Especificaciones técnicas para HyTrust DataControl on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust DataControl
* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente en vSAN en un clúster convergente
* Red: ubicada en una red portátil privada respaldada por VLAN para la gestión

### Alta disponibilidad
Se despliegan dos dispositivos DataControl en una configuración activa-activa.

### Licencias y tarifas

Licencia por host: se solicita una licencia de HyTrust DataControl por cada host del entorno.

## Consideraciones al eliminar HyTrust DataControl on IBM Cloud

Antes de eliminar el HyTrust DataControl en el servicio de {{site.data.keyword.cloud_notm}}, desacopla a todos los clientes de utilizar DataControl. Después de eliminar el servicio, es posible que se supriman las claves y que se le bloqueen de las máquinas virtuales.

### Enlaces relacionados

* [Solicitud de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestión de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtdc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
