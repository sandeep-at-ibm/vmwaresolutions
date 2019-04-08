---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

subcollection: vmwaresolutions


---

# Eliminación de HCX
{: #vcshcx-removal}

La eliminación de HCX presupone que las redes extendidas ya no están en uso. Utilice el siguiente procedimiento para eliminar HCX.

1. Elimine la extensión de todas las redes extendidas.
2. En la interfaz de usuario del cliente (IU), suprima los dispositivos L2C. Espere a que los dispositivos L2C desaparezcan de la interfaz de usuario web.
3. Suprima CGW. Esto también elimina el optimizador de WAN. Espere a que se eliminen los dispositivos CGW y optimizador de WAN.
4. Cierre y suprima las máquinas virtuales (VM) del dispositivo HCX Manager desde el lado del cliente y de la nube.
5. Elimine ESG HCX del lado de la nube de NSX.
6. Utilice el navegador de vCenter Mob para eliminar el complemento HCX.

## Enlaces relacionados
{: #vcshcx-removal-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
