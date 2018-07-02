---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visión general de HyTrust DataControl on IBM Cloud

El servicio HyTrust DataControl on {{site.data.keyword.cloud}} ofrece un cifrado de alta seguridad con claves de gestión integrada para proteger las cargas de trabajo en todo su ciclo de vida. El servicio puede proporcionar cifrado tanto a nivel de sistema operativo como a nivel de datos, lo que significa que se puede cifrar y descifrar cualquier directorio, carpeta o archivo de una carga de trabajo.

**Disponibilidad:** este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

## Componentes de HyTrust DataControl on IBM Cloud

Se despliega un par de alta disponibilidad (HA) de dispositivos de HyTrust DataControl (HTDC) en el clúster predeterminado en modalidad activa. Los dispositivos HTDC tienen licencia para proporcionar funciones de HyTrust KeyControl a las cargas de trabajo.

Cada par de dispositivos HTDC se despliega en la misma subred portátil que está especificada para las máquinas virtuales (VM) de gestión, como NSX Manager, vCenter Server Appliances y Platform Services Controller. Los dispositivos se direccionan a través de los direccionadores de cliente de programa de fondo (BCR) de {{site.data.keyword.cloud_notm}} y se les asigna la pasarela asociada con la subred de las VM de gestión. Además, los dispositivos se colocan en el almacenamiento predeterminado del clúster predeterminado.

## Consideraciones al eliminar HyTrust DataControl on IBM Cloud

Antes de eliminar el servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}}, asegúrese de cifrar todos los discos de DataControl o realizar una copia de seguridad de los mismos. Después de eliminar el servicio, puede que las claves se supriman y que se le desconecte de las VM por seguridad.

## Enlaces relacionados

* [Solicitud de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestión de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
