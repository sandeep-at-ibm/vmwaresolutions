---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementación y gestión de KMIP for VMware
{: #kmip-implementation}

## Conexión del servidor de gestión de claves
{: #kmip-implementation-connecting-kms}

Para habilitar el cifrado de vSphere o el cifrado de vSAN utilizando KMIP for VMware on {{site.data.keyword.cloud_notm}}, debe completar las tareas siguientes:

1. [Habilite los puntos finales de servicio en su cuenta](/docs/account?topic=account-vrf-service-endpoint#service-endpoint).
2. Cree una instancia de gestor de claves, utilizando
[IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial) o [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started). Si utiliza Hyper Protect Crypto Services, asegúrese de [inicializar la instancia criptográfica](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm) para que Hyper Protect Crypto Services pueda proporcionar funciones relacionadas con claves.
3. Cree una clave raíz de cliente (CRK) dentro de la instancia del gestor de claves.
4. Cree un [ID de servicio y una clave de API](/docs/iam?topic=iam-serviceidapikeys) de Identity and Access Management (IAM) para utilizarlos con KMIP for VMware. Otorgue a este ID de servicio acceso de visor de plataforma y acceso de escritura de servicio a la instancia del gestor de claves.
5. Cree una instancia de [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering) desde el catálogo de {{site.data.keyword.cloud_notm}}.
6. Dentro de VMware vCenter, cree un clúster de servidor de gestión de claves (KMS) con dos servidores, uno para cada punto final de KMIP for VMware en la región elegida.
7. Seleccione uno de los métodos de VMware para generar o instalar un certificado de cliente de KMS en vCenter.
8. Exporte la versión pública del certificado y configúrela como un certificado de cliente permitido en la instancia de KMIP for VMware.

## Habilitación del cifrado
{: #kmip-implementation-enable-encrypt}

Para utilizar el cifrado de vSAN, edite los valores generales de vSAN en el clúster de vCenter y seleccione el recuadro de selección de cifrado.

La comprobación de estado de vSAN puede emitir avisos periódicos que indican que no se puede conectar al clúster de KMS desde uno de los hosts de vSphere. Estos avisos se producen porque el tiempo de espera de conexión de la comprobación de estado de vSAN se excede demasiado rápido. Puede pasar por alto estos avisos. Para obtener más información, consulte [la comprobación de estado del KMS vSAN falla de forma intermitente con un error de tiempo de espera excedido de reconocimiento SSL](https://kb.vmware.com/s/article/67115){:new_window}.
{:note}

Para utilizar el cifrado de vSphere, edite las políticas de almacenamiento de máquina virtual para que requieran cifrado de disco.

## Rotación de claves
{: #kmip-implementation-key-rotation}

Rote la clave raíz de cliente (CRK) de [Key Protect](/docs/services/key-protect?topic=key-protect-rotate-keys#rotate-keys) o [Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-rotating-keys) utilizando la consola o la API de {{site.data.keyword.cloud_notm}}.

Para el cifrado de VMware vSAN, rote las claves de cifrado de claves de VMware (KEK) y, opcionalmente, las claves de cifrado de datos (DEK) desde los valores generales de vSAN en el clúster vCenter.

Para el cifrado de VMware vSphere, rote sus KEK y DEK (opcionalmente) de VMware con el mandato de PowerShell **Set-VMEncryptionKey**.

## Revocación de claves
{: #kmip-implementation-key-revocation}

Puede revocar todas las claves que utiliza KMIP for VMware suprimiendo la CRK elegida de su gestor de claves.

Cuando se revocan claves, todos los datos que están protegidos por estas claves y por la instancia de KMIP for VMware se destruyen criptográficamente mediante este método. VMware conserva algunas claves mientras haya un host ESXi encendido, por lo que tiene que reiniciar el clúster de vSphere para asegurarse de que todos los datos cifrados ya no se estén utilizando.
{:important}

KMIP for VMware almacena las KEK envueltas individuales en la instancia de Key Protect o Hyper Protect Crypto Services utilizando los nombres que están asociados con los ID de clave que se conocen en VMware. Puede suprimir claves individuales para revocar el cifrado de discos o unidades individuales.

VMware no suprime las claves de KMS cuando una máquina virtual que tiene discos cifrados se elimina del inventario. Esto es para permitir la recuperación de dicha VM desde una copia de seguridad o si se restaura para realizar el inventario. Si desea reclamar estas claves e invalidar criptográficamente todas las copias de seguridad, tiene que suprimir las claves de su instancia de gestor de claves después de suprimir las máquinas virtuales.
{:note}

## Enlaces relacionados
{: #kmip-implementation-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [Diseño de la solución](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
* [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)
