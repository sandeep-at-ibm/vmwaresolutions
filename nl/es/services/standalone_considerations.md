---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: VMware HCX standalone, HCX on-premises, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Consideraciones para las instancias locales de VMware HCX on IBM Cloud
{: #standalone_considerations}

Revise las siguientes consideraciones antes de instalar o suprimir las instancias locales de HCX on {{site.data.keyword.cloud}} que ha solicitado para su uso local.

Una instancia de vCenter Server con HCX on {{site.data.keyword.cloud_notm}} está limitada a tres conexiones simultáneas de sitios locales.
{:note}

## Consideraciones antes de instalar instancias locales de HCX on IBM Cloud
{: #standalone_considerations-install}

Los componentes de HCX on {{site.data.keyword.cloud_notm}} deben estar instalados en {{site.data.keyword.cloud_notm}} y en el entorno local de vSphere. Se recomienda instalar el servicio HCX on {{site.data.keyword.cloud_notm}} en la instancia de vCenter Server con el paquete híbrido (Hybridity) en {{site.data.keyword.cloud_notm}} antes de instalar la instancia local de HCX on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Consideraciones al instalar HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-hcx_considerations#hcx_considerations-install).

### Requisitos de las direcciones IP
{: #standalone_considerations-ip}

Para obtener las funciones completas de HCX, necesita al menos cinco direcciones IP privadas que tengan acceso a Internet.

### Proceso de despliegue de instancias locales de HCX on IBM Cloud
{: #standalone_considerations-deploy}

Debe completar las tareas siguientes para realizar una instalación correcta de la instancia local de HCX on {{site.data.keyword.cloud_notm}}:
1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, solicite la instancia local de HCX on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Solicitud de instancias locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
2. En la **consola de HCX Cloud**, siga estos pasos:
    1. Pulse el separador **Administración**.
    2. En el separador **Actualizaciones del sistema**, pulse **SOLICITAR ENLACE DE DESCARGA**.
    3. Pulse **COPIAR ENLACE** y utilice este enlace para descargar el cliente de HCX Enterprise en un entorno local con acceso a su entorno local de vSphere.
3. En el cliente web de VMware vSphere, despliegue el cliente de HCX Enterprise como dispositivo virtual de HCX Manager (HCX Manager) en el entorno local.

   Debe desplegar HCX Manager local en una red privada y debe otorgarle acceso a la red pública. Puede utilizar NSX Edge, Vyatta o pasarelas similares para permitir el acceso internet al HCX Manager local. Si las pasarelas utilizadas para el acceso a la red privada y a la red pública son distintas, se recomienda utilizar la pasarela predeterminada para permitir el acceso a la red pública y a la **consola de administración de HCX Manager** privada para crear una ruta estática para el acceso a la red privada.
   {:note}
4. Una vez completado el despliegue de Manager HCX, utilice la **consola de administración de HCX Manager** para activar el HCX Manager local. Para obtener una clave de activación para el HCX Manager local, solicite una instancia de HCX on {{site.data.keyword.cloud_notm}} local en la consola de {{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte [Solicitud de instancias locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
5. Si ha utilizado un certificado SSL autofirmado al solicitar el servicio HCX on {{site.data.keyword.cloud_notm}}, debe importar el certificado en el HCX Manager local siguiendo los siguientes pasos:
    1. En la **consola de administración de HCX Manager** local, pulse el separador **Administración**.
    2. En el panel de navegación de la izquierda, pulse **Certificado de CA de confianza** y luego pulse **IMPORTAR** a la derecha.
    3. Pulse **URL** y, a continuación, especifique el URL del certificado que desee aplicar, que es la
**IP de HCX Cloud** (``https://<cloud-side public IP>``), que puede encontrar en la página de detalles del servicio de HCX on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
    4. Pulse **APLICAR**.

Ahora ha completado la configuración básica del HCX Manager local. Puede continuar con el emparejamiento del sitio local de HCX on {{site.data.keyword.cloud_notm}} con el sitio de HCX de la nube.

Para obtener más información, consulte [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}.

## Consideraciones antes de suprimir instancias locales de HCX on IBM Cloud
{: #standalone_considerations-delete}

Revise las siguientes consideraciones antes de suprimir una instancia de HCX on {{site.data.keyword.cloud_notm}} solicitada para su uso local:
1. En el cliente web de VMware vSphere, vaya a la interfaz de usuario HCX y compruebe los siguientes elementos:
    1. Asegúrese de que no se esté ejecutando ninguna operación de migración de HCX ni de recuperación tras desastre.
    2. Asegúrese de que se hayan eliminado todas las redes ampliadas.
    3. Asegúrese de que se hayan eliminado todos los componentes de interconexión con sitios de nube emparejados.

   Debe completar todos los pasos anteriores antes de continuar con el siguiente paso. De lo contrario, la licencia de la instancia local de HCX on {{site.data.keyword.cloud_notm}} se cancela. Si la licencia se cancela, no se pueden realizar migraciones y pueden producirse errores en los componentes de HCX.  
   {:important}
2. En la consola de {{site.data.keyword.vmwaresolutions_short}}, suprima la instancia local de HCX on {{site.data.keyword.cloud_notm}} que se ha solicitado para obtener la clave de activación para el HCX Manager local. Asegúrese de que la instancia suprimida deja de estar disponible en la consola antes de continuar con el siguiente paso.

   Para obtener más información, consulte [Supresión de instancias locales de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_deletingserviceinstances).
3. En el cliente web de VMware vSphere, suprima el HCX Manager local.

## Enlaces relacionados
{: #standalone_considerations-related}

* [Visualización de instancias locales de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_viewingserviceinstances)
* [Glosario de términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Documentación de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
