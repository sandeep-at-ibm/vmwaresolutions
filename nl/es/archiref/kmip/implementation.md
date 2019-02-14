---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementación y gestión de KMIP for VMware

## Conexión del servidor de gestión de claves

Para habilitar el cifrado de vSphere o el cifrado de vSAN utilizando KMIP for VMware on {{site.data.keyword.cloud_notm}}, debe completar las tareas siguientes:

1. [Habilite la cuenta para puntos finales de servicio](/docs/services/service-endpoint/enable-servicepoint.html#getting-started).
2. Cree una instancia de [IBM Key Protect](/docs/services/key-protect/index.html).
3. Cree una clave raíz de cliente (CRK) dentro de IBM Key Protect.
4. Cree un [ID de servicio y una clave de API](/docs/iam/serviceid_keys.html) de Identity and Access Management (IAM) para utilizarlos con KMIP for VMware. Otorgue a este ID de servicio acceso de visor de plataforma y acceso de escritura de servicio a la instancia de Key Protect.
5. Cree una instancia de [KMIP for VMware](../../services/kmip_standalone_ordering.html) desde el catálogo de {{site.data.keyword.cloud_notm}}.
6. Dentro de VMware vCenter, cree un clúster de servidor de gestión de claves (KMS) con dos servidores, uno para cada punto final de KMIP for VMware en la región elegida.
7. Seleccione uno de los métodos de VMware para generar o instalar un certificado de cliente de KMS en vCenter.
8. Exporte la versión pública del certificado y configúrela como un certificado de cliente permitido en la instancia de KMIP for VMware.

## Habilitación del cifrado

Para utilizar el cifrado de vSAN, edite los valores generales de vSAN en el clúster de vCenter y seleccione el recuadro de selección de cifrado.

Para utilizar el cifrado de vSphere, edite las políticas de almacenamiento de máquina virtual para que requieran cifrado de disco.

## Rotación de claves

[Rote la clave raíz de cliente de Key Protect (CRK)](/docs/services/key-protect/rotate-keys.html) mediante la consola de {{site.data.keyword.cloud_notm}} o la API.

Para el cifrado de VMware vSAN, rote las claves de cifrado de claves de VMware (KEK) y, opcionalmente, las claves de cifrado de datos (DEK) desde los valores generales de vSAN en el clúster vCenter.

Para el cifrado de VMware vSphere, rote sus KEK y DEK (opcionalmente) de VMware con el mandato de PowerShell **Set-VMEncryptionKey**.

## Revocación de claves

Puede revocar todas las claves que utiliza KMIP for VMware suprimiendo la CRK elegida de Key Protect. 

Cuando se revocan claves, todos los datos que están protegidos por estas claves y por la instancia de KMIP for VMware se destruyen criptográficamente mediante este método. VMware conserva algunas claves mientras haya un host ESXi encendido, por lo que tiene que reiniciar el clúster de vSphere para asegurarse de que todos los datos cifrados ya no se estén utilizando.
{:important}

KMIP for VMware almacena las KEK envueltas individuales en la instancia de Key Protect utilizando los nombres que están asociados con los ID de clave que se conocen en VMware. Puede suprimir claves individuales para revocar el cifrado de discos o unidades individuales. 

VMware no suprime las claves de KMS cuando una máquina virtual que tiene discos cifrados se elimina del inventario. Esto es para permitir la recuperación de dicha VM desde una copia de seguridad o si se restaura para realizar el inventario. Si desea reclamar estas claves e invalidar criptográficamente todas las copias de seguridad, tiene que suprimir las claves de Key Protect después de suprimir las VM.
{:note}

### Enlaces relacionados

* [Visión general de la solución](overview.html)
* [Diseño de la solución](design.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
