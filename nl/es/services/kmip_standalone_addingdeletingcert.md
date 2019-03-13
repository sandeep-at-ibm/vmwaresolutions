---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adición, visualización y supresión de certificados para instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert}

Cuando la instancia de KMIP for VMware on {{site.data.keyword.cloud}} esté lista, debe añadirle certificados. Cuando ya no necesite un certificado, lo puede suprimir de la instancia.

## Procedimiento para añadir certificados a instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert-add}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. Desplácese hacia abajo en la tabla **Instancias de KMIP for VMware on IBM Cloud** y pulse la instancia a la que desea añadir certificados.
3. Pulse **Añadir**.
4. En la ventana **Añadir certificado SSL de cliente**, especifique el nombre y el contenido del certificado.

   El nombre de certificado no se puede reutilizar dentro de la instancia seleccionada. El contenido del certificado debe ser válido, debe contener los códigos BEGIN CERTIFICATE y END CERTIFICATE y el certificado no se puede reutilizar en la región seleccionada en la que se ha desplegado la instancia.
   {:note}
5. Pulse **Añadir**.

## Procedimiento para ver certificados de instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert-view}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. Desplácese hacia abajo en la tabla **Instancias de KMIP for VMware on IBM Cloud** y pulse la instancia cuyos certificados desea ver.
3. Visualice la lista de certificados añadidos bajo la sección **Certificados SSL de cliente**.
4. Para ver el contenido de un determinado certificado, pulse **Descargar**.

## Procedimiento para suprimir certificados de instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_addingdeletingcert-delete}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. Desplácese hacia abajo en la tabla **Instancias de KMIP for VMware on IBM Cloud** y pulse la instancia cuyos certificados desea suprimir.
3. En la tabla **Certificados SSL de cliente**, localice el certificado que desea suprimir y pulse el icono **Suprimir**.

   El cliente pierde de forma inmediata el acceso a todas las claves con el fin de cifrar y descifrar datos o datos de copia de seguridad. Para que el cliente obtenga acceso de nuevo, debe volver a añadir el certificado SSL del cliente.
   {:note}

## Enlaces relacionados
{: #kmip_standalone_addingdeletingcert-related}

* [Visualización de instancias de KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Solicitud de instancias de KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Supresión de instancias de KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Sucesos de Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
