---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Preguntas más frecuentes sobre licencias y BYOL
{: #faq_byol}

Encuentre las respuestas a las preguntas más frecuentes sobre licencias, incluida la característica Traer su propia licencia (BYOL), de {{site.data.keyword.vmwaresolutions_full}}.

## ¿Qué es BYOL?
{: #faq_byol-def}
{: faq}

Traer su propia licencia (Bring Your Own License o BYOL) es una característica disponible en VMware vCenter Server y los clústeres de VMware vSphere en V2.0 y posteriores. Con BYOL, puede utilizar sus propias licencias de VMware para uno o varios de los siguientes componentes de software de VMware:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Si opta por utilizar su propia licencia para un componente de VMware y proporciona para el mismo una clave de licencia válida, no se solicita ninguna licencia a IBM para dicho componente y no se incurre en cargos de licencia mensuales en su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} para este componente.

La característica BYOL no está disponible para los usuarios de Business Partners.
{:note}

## ¿Dónde se gestionan las licencias y los componentes solicitados a través de VMware vSphere on IBM Cloud?
{: #faq_byol-license-mgmt}
{: faq}

Después de solicitar la creación de un nuevo clúster para VMware vSphere on {{site.data.keyword.cloud_notm}}, se suministra licencias de VMware, servidores ESXi y otros componentes de red y se pueden gestionar desde el {{site.data.keyword.slportal}}.

Después del despliegue, vaya a la consola de {{site.data.keyword.vmwaresolutions_short}} para escalar el clúster nuevo utilizando la configuración guardada. Para obtener más información, consulte [Escalado de clústeres existentes de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).

## ¿Qué ediciones de licencias y qué número de CPU se necesitan para BYOL?
{: #faq_byol-license-cpu-reqs}
{: faq}

Se aplican los siguientes requisitos a las ediciones de licencias para BYOL.

### Requisitos de BYOL para instancias de vCenter Server
{: #faq_byol-vcs-reqs}

Tabla 1. Ediciones de licencias y requisitos mínimos de CPU para instancias de vCenter Server

  | Componente VMware | Edición licencia necesaria | CPU mínima necesaria
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | N/D |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Standard, Advanced o Enterprise | 8 CPU |

## ¿Qué sucede si la clave de licencia que proporciono no es correcta?
{: #faq_byol-incorrect-license}
{: faq}

Todas las claves de licencia que proporcione se validan para garantizar de que son correctos para los componentes correspondientes de VMware y que cumplen los requisitos mínimos de edición y de CPU de los componentes de VMware. Si la validación de alguna clave de licencia falla, recibe una notificación y no puede continuar con el pedido de la instancia.

## ¿Puedo proporcionar una clave de licencia con más de 8 CPU?
{: #faq_byol-license-key}
{: faq}

Sí. Para cada componente de VMware se necesita una licencia por CPU. Actualmente, todos los servidores vCenter Server tienen dos CPU. Por lo tanto, se necesitan dos licencias por cada servidor. Se recomienda proporcionar una clave de licencia que dé soporte a la instancia básica y a los nodos de expansión que desee añadir a la instancia en el futuro.

## ¿Puedo utilizar la característica BYOL para algunos componentes de VMware y adquirir licencias mensuales para otros?
{: #faq_byol-mthly-license}
{: faq}

Sí. Puede utilizar la característica BYOL o adquirir licencias para cualquier combinación de los cuatro componentes de VMware. La consola de {{site.data.keyword.vmwaresolutions_short}} le facilita la selección de la opción de licencia cuando solicita la instancia. La opción de licencia en vigor en el momento de realizar el pedido de la instancia inicial se aplica durante todo el tiempo de vida de dicha instancia.

## Para un componente específico de VMware, ¿puedo utilizar BYOL para algunas licencias y comprar el resto de las licencias de IBM?
{: #faq_byol-purchase}
{: faq}

Sí. Si ha seleccionado BYOL para un componente de VMware específico al crear un clúster, tiene las opciones siguientes:
* Especificar una nueva clave de BYOL
* Continuar utilizando una clave BYOL existente
* Adquirir licencias proporcionadas por IBM para dicho clúster.

En la actualidad, solo se pueden adquirir licencias de VMware vSphere Enterprise y VMware vSAN por clúster.

## ¿Puedo utilizar BYOL cuando cree un clúster?
{: #faq_byol-cluster}
{: faq}

Sí. Puede utilizar BYOL de licencias de BYOL existentes o puede especificar un nuevo BYOL cuando cree un clúster. También puede adquirir una licencia de suscripción proporcionada por IBM al crear un clúster.

En la actualidad, solo se pueden adquirir licencias de VMware vSphere Enterprise y VMware vSAN por clúster.

## ¿Cómo gestiono mis licencias BYOL?
{: #faq_byol-mgmt}
{: faq}

Puede gestionar sus licencias BYOL mediante el cliente web de VMware vSphere una vez finalizado el despliegue de la instancia.

## Cuando posteriormente añada más servidores ESXi a mi instancia, ¿valida la instancia si mis licencias de BYOL tienen suficiente capacidad?
{: #faq_byol-add-esxi}
{: faq}

Sí. Cuando añada más servidores ESXi a una instancia desplegada, se comprueba automáticamente la capacidad de las licencias BYOL para el número especificado de servidores ESXi. Si la capacidad no es suficiente, los servidores ESXi no se añaden y recibe una notificación en la consola.

## ¿Cómo puedo saber la capacidad de licencia que tengo disponible en un clúster con BYOL?
{: #faq_byol-capacity}
{: faq}

Para encontrar el número de CPU disponibles en la clave de licencia, complete los pasos siguientes:
1. Vaya a la página **Recursos**.
2. Localice y pulse la instancia.
3. En el separador **Infraestructura**, pulse en el clúster para el que desee comprobar la capacidad de la licencia.
   El número de CPU disponibles se muestra en la tabla **Licencia proporcionada por el usuario**.

## ¿Proporciona IBM soporte si selecciono la opción de licencia BYOL?
{: #faq_byol-support}
{: faq}

El equipo de soporte de IBM sigue siendo su punto de contacto para cualquier duda o problema relacionado con la configuración de una instancia. Sin embargo, si el problema notificado corresponde a un componente de VMware BYOL, se le dirigirá al equipo de soporte de VMware.

## ¿Por qué aparecen cargos de licencia de vSphere en la lista de estimaciones de precio si utilizo BYOL? ¿Se me va a facturar por ello?
{: #faq_byol-vsphere}
{: faq}

Los {{site.data.keyword.baremetal_short}} se suministran con VMware vSphere ya instalado y con las licencias de vSphere ya incluidas. Si ha seleccionado BYOL para vSphere, se inicia automáticamente un proceso sobre el despliegue de la instancia para eliminar las licencias de vSphere incluidas. Luego, los cargos de licencia se abonarán a su cuenta de {{site.data.keyword.cloud_notm}}. En este proceso no tiene que hacer nada.

## ¿Puedo seguir utilizando el proceso manual existente para BYOL?
{: #faq_byol-manual-process}
{: faq}

Con la introducción de la característica BYOL, no se recomienda seguir utilizando el proceso manual. Si desea utilizar BYOL, proporcione sus propias licencias al solicitar la instancia.

## ¿Recibe BYOL soporte para otros productos VMware, como VMware vRealize Automation, VMware vRealize Operations o VMware vRealize Log Insight?
{: #faq_byol-other-support}
{: faq}

No, porque estos productos VMware no forman parte del despliegue de la instancia. Estos productos VMware se pueden instalar además del despliegue inicial, lo que requiere que los clientes o sus agentes instalen y adquieran la licencia de dichos productos.

## ¿Puedo solicitar almacenamiento de NFS con vCenter Server con el paquete híbrido (Hybridity)?
{: #faq_byol-nfs}
{: faq}

Para instancias desplegadas recientemente, solo se da soporte al almacenamiento all-flash de vSAN. La oferta de vCenter Server con el paquete híbrido (Hybridity) incluye licencia de vSAN Advanced o Enterprise.

Si tiene una instancia de vCenter Server con almacenamiento NFS, puede actualizar la instancia existente a vCenter Server con el paquete híbrido (Hybridity). Aunque la licencia de vSAN Advanced se solicite durante la actualización, no será necesario que suministre un clúster all-flash vSAN.

## ¿Puedo utilizar BYOL con vCenter Server con el paquete híbrido (Hybridity)?
{: #faq_byol-hybridity}
{: faq}

No puede traer su propia licencia VMware (BYOL) a {{site.data.keyword.cloud_notm}}. vCenter Server con el paquete híbrido (Hybridity) requiere que IBM proporcione todas las licencias de VMware.

## ¿Cuál es la diferencia entre vCenter Server con licencia del paquete híbrido (Hybridity) y licencia de vCenter Server?
{: #faq_byol-hybridity-vcs}
{: faq}

Las licencias individuales de VMware que están disponibles en vCenter Server se tarifican por CPU. Al igual que todas las licencias por CPU VMware proporcionadas por IBM, hay un recargo de 1,3x en el precio en todos los servidores que tienen más de 16 núcleos por CPU, por ejemplo, para Dual Intel Xeon Gold 6140.

vCenter Server con el paquete híbrido (Hybridity) es un conjunto prescrito de licencias y ediciones de VMware que se licencian por núcleo, y no por CPU. Por lo tanto, el precio de licencias para estas instancias no cambia.

## ¿Qué componentes y ediciones de licencia de VMware proporcionados por IBM están disponibles para vCenter Server con el paquete híbrido (Hybridity)?
{: #faq_byol-hybridity-avail}
{: faq}

Las nuevas instancias de vCenter Server con el paquete híbrido (Hybridity) incluyen VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced o Enterprise, VMware vSAN Advanced o Enterprise y VMware Hybrid Cloud Extension (HCX).

Si tiene una instancia de vCenter Server con la edición NSX Base, se le actualizará a NSX Advanced automáticamente al solicitar vCenter Server con el paquete híbrido (Hybridity).

## ¿Puedo actualizar la edición de NSX Advanced que se incluye en vCenter Server con el paquete híbrido (Hybridity) a la edición NSX Enterprise?
{: #faq_byol-nsx-upgrade}
{: faq}

Aunque el vCenter Server con el paquete híbrido (Hybridity) incluye NSX Advanced, puede actualizar a la edición NSX Enterprise después de solicitar el vCenter Server con el paquete híbrido (Hybridity). Para ello, utilice el separador **Actualización y parche** en el separador de página de detalles de instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}.

## Enlaces relacionados
{: #faq_byol-related}

* [Acceso a la consola](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
