---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: Zerto certificate, Zerto config, update Zerto replication

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de Zerto on IBM Cloud
{: #managingzertodr}

Después de desplegar el servicio Zerto on {{site.data.keyword.cloud}} en la instancia, puede configurar o actualizar el servicio de réplica virtual de Zerto y desplegar más dispositivos de réplica virtuales en los servidores ESXi recién añadidos.

## Utilización de su propio certificado para Zerto
{: #managingzertodr-ssl-cert}

Como práctica recomendada, utilice su propio certificado SSL para Zerto Virtual Manager (ZVM). Después de desplegar Zerto on {{site.data.keyword.cloud_notm}}, sustituya el certificado SSL para ZVM por su propio certificado. Para obtener más información, consulte [Cómo utilizar un certificado SSL CER para sustituir el certificado autofirmado para ZVM, ZSSP o ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:external}

## Gestión de la configuración de réplicas Zerto
{: #managingzertodr-manage}

Para gestionar la configuración de las réplicas Zerto, inicie una sesión en la consola del servicio de réplica virtual de Zerto utilizando las credenciales de vCenter con permisos de administrador. Por ejemplo, volver a emparejar instancias de Zerto o configurar grupos de protección virtual para crear réplicas de máquinas virtuales.

Al realizar réplicas entre distintas instancias de {{site.data.keyword.cloud_notm}} Zerto, puede configurar la réplica directamente entre las instancias de Zerto. Si está realizando réplicas entre la instancia de {{site.data.keyword.cloud_notm}} Zerto y su propio centro de datos, debe instalar Zerto en su propio centro de datos. Esta instancia puede obtener una licencia para sí misma automáticamente cuando la empareje con la instancia de {{site.data.keyword.cloud_notm}} Zerto.

El servicio de réplica de Zerto no da soporte a Network Address Translation (NAT) transversal. Para establecer conectividad entre la instancia de {{site.data.keyword.cloud_notm}} Zerto y su propio centro de datos hay que personalizar las rutas en los dispositivos de Virtual Manager Zerto (ZVM) o en los dispositivos de réplica virtual (VRA) de Zerto en ambos extremos. El establecimiento de la conectividad también puede requerir un túnel entre los sitios. Cuando esté configurando o reconfigurando rutas en dispositivos ZVM, debe asegurarse de que todos los dispositivos ZVM se pueden conectar correctamente a `zerto.com` para la creación de informes de uso. Para verificar esta conexión, abra una sesión del navegador en `https://www.zerto.com` desde el dispositivo ZVM.

La pasarela Management VMware NSX Edge Services Gateway (ESG) viene preconfigurada de modo que permite las comunicaciones HTTPS (puerto TCP 443) de salida que se originan en ZVM.
{:note}

## Actualización de la réplica virtual de Zerto
{: #managingzertodr-update}

Para actualizar la réplica virtual de Zerto, inicie una sesión en la consola del servicio de réplica virtual de Zerto.

## Despliegue de VRA en servidores ESXi recién añadidos
{: #managingzertodr-deploy}

Cuando añade o elimina servidores ESXi para el clúster primario de la instancia, los VRA se despliegan o se eliminan automáticamente. Los VRA no se despliegan automáticamente en los servidores ESXi de los clústeres secundarios de la instancia. Puede desplegar desde la consola del servicio de réplica virtual de Zerto.

## Enlaces relacionados
{: #managingzertodr-related}

* [Visión general de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sitio web zerto.com](https://www.zerto.com){:external}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:external}
* [Recuperación tras desastre de Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:external}
* [Explicación de las alertas del servicio de réplica virtual de Zerto](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/){:external}
