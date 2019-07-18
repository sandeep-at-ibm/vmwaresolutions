---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Diseño de KMIP for VMware
{: #kmip-design}

KMIP for VMware on {{site.data.keyword.cloud}} proporciona un servicio de gestión de claves compatible con el cifrado de VMware vSAN y con el cifrado de VMware vSphere, mediante el uso de [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial) o [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) para proporcionar almacenamiento de claves raíz y de claves de datos. Key Protect e Hyper Protect Crypto Services funcionan como el servicio de gestión de claves de esta solución.

## Opciones de cifrado de almacenamiento
{: #kmip-design-storage-options}

KMIP for VMware es compatible tanto con el cifrado de VMware vSAN como con el cifrado de vSphere. Ambas soluciones se implementan en la capa de hipervisor, pero proporcionan funciones ligeramente distintas. Evalúe sus funciones de acuerdo con sus requisitos.

### Cifrado de VMware vSAN
{: #kmip-design-vsan-encrypt}

El cifrado de VMware vSAN solo se aplica a los almacenes de datos de vSAN. Con esta solución, VMware vCenter y los hosts VMware ESXi se conectan a un servidor de gestión de claves, como por ejemplo KMIP for VMware, para obtener claves de cifrado. Estas claves se utilizan para proteger las unidades de disco individuales utilizadas para el almacén de datos de vSAN, incluidos los discos de memoria caché y de capacidad. El cifrado vSAN se implementa de forma que se mantienen las ventajas de la compresión y la desduplicación de vSAN.

Puesto que el cifrado de vSAN funciona a nivel de almacén de datos, su objetivo principal es evitar la exposición de los datos si se produce una pérdida de unidades de disco físicas. Además, el cifrado de vSAN es totalmente compatible con todas las tecnologías de copia de seguridad y réplica de máquina virtual, como la réplica de vSphere, vMotion entre vCenter, VMware HCX, Zerto, Veeam e IBM Spectrum Protect Plus.

**Notas**:
* El cifrado de vSAN no cifra las comunicaciones de réplica de vSAN de host a host dentro del clúster.
* El cifrado vSAN no es aplicable a otras soluciones de almacenamiento, como por ejemplo el almacenamiento en bloque o de archivos de resistencia de {{site.data.keyword.cloud_notm}}.
* El cifrado de vSAN necesita la licencia de vSAN Enterprise.
* La comprobación de estado de vSAN puede emitir avisos periódicos que indican que no se puede conectar al clúster de KMS desde uno de los hosts de vSphere. Estos avisos se producen porque el tiempo de espera de conexión de la comprobación de estado de vSAN se excede demasiado rápido. Puede pasar por alto estos avisos. Para obtener más información, consulte [la comprobación de estado del KMS vSAN falla de forma intermitente con un error de tiempo de espera excedido de reconocimiento SSL](https://kb.vmware.com/s/article/67115){:new_window}.

### Cifrado de vSphere
{: #kmip-design-vsphere-encrypt}

El cifrado de VMware vSphere se aplica a todos los tipos de almacenamiento de VMware, incluido el almacenamiento vSAN y el almacenamiento en bloque y de archivos de resistencia de {{site.data.keyword.cloud_notm}}.

Con esta solución, vCenter Server y los hosts ESXi se conectan a un servidor de gestión de claves, como por ejemplo KMIP for VMware, para obtener claves de cifrado. Estas claves se utilizan para proteger discos de máquina virtual (VM) individuales, de acuerdo con las políticas de almacenamiento de VM.

El cifrado de vSphere funciona a nivel de máquina virtual, por lo que puede evitar la exposición de los datos si se produce una pérdida de unidades de disco físicas o de discos de VM. Muchas tecnologías de copia de seguridad y réplica no pueden hacer una copia de seguridad o replicar de forma eficaz porque los datos proporcionados están cifrados.

Por lo tanto, el cifrado de vSphere no es compatible con la réplica de vSphere, vMotion entre vCenter, VMware HCX, Zerto o IBM Spectrum Protect Plus. Sin embargo, si está correctamente configurada, la tecnología de copia de seguridad y réplica de Veeam es compatible con el cifrado de vSphere.

### Más consideraciones
{: #kmip-design-considerations}

Cuando hay algún tipo de cifrado habilitado en el clúster de vSphere, VMware crea una clave adicional para cifrar los volcados de núcleo de ESXi, ya que estos volcados pueden contener datos confidenciales, como por ejemplo credenciales de gestión de claves, claves de cifrado o datos descifrados. Debe familiarizarse con los [volcados de núcleo y de cifrado de máquina virtual de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-63728E8B-810D-418B-B1AA-6A0A2F92AABE.html).

Si se utiliza KMIP for VMware con el cifrado de vSAN o el cifrado de vSphere, existen varias capas de protección de claves.

Si tiene intención de rotar las claves, examine la siguiente información sobre los niveles en los que se pueden rotar las claves:
* La clave raíz del cliente (CRK) protege todas las claves de VMware. Las claves se pueden rotar en la instancia de IBM Key Protect o Hyper Protect Crypto Services asociada a la instancia de KMIP for VMware.
* KMIP for VMware utiliza su CRK para proteger las claves que genera y distribuye a VMware. VMware considera que estas son _claves de cifrado de claves (KEK)_.
  * Si utiliza cifrado de vSphere, puede rotar las claves con el mandato de PowerShell **Set-VMEncryptionKey**.
  * Si utiliza cifrado de vSAN, puede rotar las claves en la interfaz de usuario de vSAN.
* VMware utiliza estas KEK para proteger las claves reales que utiliza para cifrar las unidades de disco y los discos de VM. Puede rotar estas claves utilizando lo que VMware llama una reclave "profunda". Esta operación vuelve a cifrar todos los datos cifrados, por lo que es posible que lleve mucho tiempo.
  * Si utiliza cifrado de vSphere, puede realizar una reclave profunda con el mandato de PowerShell **Set-VMEncryptionKey**.
  * Si está utilizando el cifrado de vSAN, puede realizar una reclave mediante la interfaz de usuario de vSAN.

## KMIP for VMware
{: #kmip-design-kmip-for-vmware}

El cifrado de VMware vSAN y el cifrado de vSphere son compatibles con muchos servidores de gestión de claves. KMIP for VMware proporciona un servicio de gestión de claves gestionado por IBM que utiliza IBM Key Protect o Hyper Protect Crypto Services para proporcionarle control completo sobre las claves. Otros servicios de {{site.data.keyword.cloud_notm}}, como por ejemplo Cloud Object Storage, también se integran con Key Protect e Hyper Protect Crypto Services, convirtiéndolo en su punto central de control para la gestión de claves en {{site.data.keyword.cloud_notm}}.

### Claves dentro de claves
{: #kmip-design-keys}

Los sistemas de gestión de claves suelen utilizar una técnica conocida como *cifrado de sobre* para envolver o proteger las claves con otras claves. Estas claves se denominan _claves raíz_ o _claves de cifrado de claves (KEK)_. Para acceder a una clave, es necesario descifrar o desenvolver la clave utilizando su clave raíz correspondiente. Destruir la clave raíz es una forma eficaz de invalidar todas las claves que protege. Estas claves no se deben almacenar cerca de la clave raíz. Es importante controlar el acceso a la clave raíz.

{{site.data.keyword.cloud_notm}} Key Protect e Hyper Protect Crypto Services proporcionan este servicio utilizando una *clave raíz de cliente* (CRK). Key Protect almacena las CRK exclusivamente en el hardware de {{site.data.keyword.cloud_notm}} CloudHSM, desde donde no se pueden extraer; Hyper Protect Crypto Services almacena claves en HSM de IBM zSeries. Estas CRK se utilizan para envolver más claves de cifrado, como las que genera KMIP for VMware para la instancia de VMware.

VMware implementa este mismo concepto para sus claves. KMIP for VMware proporciona una clave a VMware previa solicitud, y VMware a su vez utiliza esta clave como KEK para envolver o cifrar las claves finales que se utilizan para cifrar las unidades de disco vSAN o los discos de máquina virtual. Estas claves finales se denominan claves de cifrado de datos (DEK).

Por lo tanto, terminamos con la siguiente cadena de cifrado:
* Clave raíz de cliente (CRK) almacenada de forma permanente en IBM Key Protect o Hyper Protect Crypto Services.
* Clave de cifrado de clave (KEK) generada por KMIP for VMware y suministrada a vCenter Server y a los hosts ESXi en la instancia.
* Clave de cifrado de datos (DEK) generada por VMware y almacenada junto con el disco de vSAN o el disco de máquina virtual.

KMIP for VMware almacena la forma envuelta de las KEK en IBM Key Protect o Hyper Protect Crypto Services. Aunque las KEK están protegidas criptográficamente por la CRK y no es necesario que se almacenen dentro de HSM, si las almacena en el servicio de gestión de claves su presencia es visible y puede suprimirlas si necesita revocar claves individuales.

### Autenticación y autorización
{: #kmip-design-authentication}

Tres componentes componen la solución de cifrado de almacenamiento: el clúster de VMware, la instancia de KMIP for VMware y la instancia de Key Protect o Hyper Protect Crypto Services.

VMware vCenter y ESXi se autentican con la instancia de KMIP for VMware utilizando los certificados que se instalan o se generan en VMware vCenter cuando se crea una conexión de servidor de gestión de claves (KMS). Puede instalar el certificado público en KMIP for VMware para identificar el cliente o los clientes de vCenter a los que se permite conectarse. Cada cliente está autorizado a todas las claves almacenadas en dicha instancia de KMIP for VMware.

La instancia de KMIP for VMware está autorizada a la instancia de Key Protect o Hyper Protect Crypto Services utilizando un ID de servicio de {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) al que se ha otorgado acceso a la instancia. El ID de servicio debe tener un acceso mínimo de visor de la plataforma y de gestor de servicios sobre la instancia del gestor de claves. KMIP for VMware utiliza la clave raíz del cliente (CRK) que elija en la instancia del gestor de claves, y almacena todas las KEK generadas en nombre de VMware, en formato envuelto, en la instancia del gestor de claves.

### Topología
{: #kmip-design-topology}

KMIP for VMware está disponible en una serie de regiones multizona (MZR) de {{site.data.keyword.cloud_notm}}. Para ver la lista completa, consulte [Solicitud de KMIP para VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering).

Dentro de cada MZR, KMIP for VMware proporciona dos puntos finales de servicio de red en la red privada de {{site.data.keyword.cloud_notm}} para ofrecer una alta disponibilidad. Configure ambos puntos finales en la configuración del servidor de gestión de claves de vCenter (KMS) como un clúster de KMS. Para ver una lista de los puntos finales de cada MZR y de las firmas de certificado de servidor KMIP, consulte la [documentación del servicio KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering).

Para acceder a KMIP for VMware a través de la red privada, la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} debe estar habilitada para el direccionamiento y el reenvío virtuales (VRF) y las rutas de punto final de servicio de red de {{site.data.keyword.cloud_notm}} se deben añadir a las rutas VRF de la cuenta. Para obtener más información, consulte
[Habilitación de la cuenta para que utilice puntos finales de servicio mediante la CLI de IBM Cloud](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

KMIP for VMware también se conecta a {{site.data.keyword.cloud_notm}} Key Protect utilizando la red privada de {{site.data.keyword.cloud_notm}} en lugar de Internet público.

![Componentes de KMIP para VMware on {{site.data.keyword.cloud_notm}}](../../images/kmip-key-protect.svg "La solución habilita el cifrado de VMware vSphere y el cifrado de vSAN utilizando claves raíz que se almacenan en IBM Key Protect.")

Al utilizar IBM Cloud Hyper Protect Crypto Services, las claves se almacenan en un HSM de IBM zSeries en lugar de en CloudHSM. Además, la conexión entre KMIP for VMware e {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services fluye a través de la red pública, pero está protegida por el cifrado y la autenticación TLS.

## Enlaces relacionados
{: #kmip-design-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [Implementación y gestión](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
