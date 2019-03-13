---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Paso 2 - Despliegue de máquina virtual
{: #caveonix-step2}

La automatización de {{site.data.keyword.vmwaresolutions_full}} solicita una subred IP privada portátil adicional y la máquina virtual (VM) "todo en uno" se configura con una dirección IP desde esta subred para que los componentes de Caveonix RiskForesight puedan:

- Conectarse a vCenter y NSX Manager a través de BCR.
- Conectarse a los recopiladores remotos, ya sea en VXLAN o alojados fuera de las instalaciones.
- Permitir al cliente gestionar el espacio de direcciones IP cuando se escale.


## Enlaces relacionados
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
