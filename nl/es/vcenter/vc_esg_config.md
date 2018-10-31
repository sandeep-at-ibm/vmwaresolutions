---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Configuración de la red para que utilice NSX ESG gestionado por el cliente con las VM

Configure la red para las máquinas virtuales de modo que pueda aprovechar el servicio VMware NSX Servicios Edge Gateway (ESG) que se despliega en las instancias de VMware vCenter Server. Para obtener más información sobre las medidas de seguridad en vigor para ayudar a minimizar los riesgos de seguridad, consulte [¿Representa NSX Edge se servicios de gestión un riesgo para la seguridad?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX es una plataforma de virtualización de red que permite la virtualización de redes aisladas y proporciona varios servicios de red, como conmutadores, direccionamiento y cortafuegos. Para obtener más información sobre NSX, consulte [Visión general de NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Como parte del proceso de pedido de la instancia de vCenter Server, se llevan a cabo las siguientes acciones en su nombre:
* Se solicita una subred de cliente privada que utilizarán las VM (máquinas virtuales) para acceder a la red privada de la infraestructura de {{site.data.keyword.cloud}}.
* Se solicita una subred de cliente pública que permitirá a las VM acceder a Internet.
* Se despliega y se configura NSX en la instancia de vCenter Server.
* Se despliega un conmutador lógico NSX de ejemplo que utilizarán las VM de carga de trabajo del cliente.
* Se despliega un direccionador lógico distribuido (DLR) NSX para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2).
* Se despliega y se configura un dispositivo NSX Edge para que realiza la conversión de direcciones de red (NAT) entre el rango de direcciones IP del conmutador lógico de carga de trabajo y una dirección IP pública en las reglas NAT.
* Si ha instalado el servicio Veeam on {{site.data.keyword.cloud_notm}}, se configura NSX Manager para que realice una copia de seguridad diaria de las configuraciones NSX. Para obtener más información, consulte [Consideraciones al instalar Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html#considerations-when-you-install-veeam-on-ibm-cloud).

## Procedimiento para configurar los valores de red para las máquinas virtuales

Para aprovechar el servicio NSX para sus VM de carga de trabajo, debe configurar una serie de valores siguiendo los siguientes pasos cuando al crear las VM:

1. Establezca el adaptador de red de la VM en el conmutador lógico de carga de trabajo:
   1. En el recuadro de diálogo **Nueva máquina virtual**, pulse el separador **Personalizar hardware**.
   2. En el menú **nuevo dispositivo**, seleccione **Red** y pulse **Añadir**.
   3. En el adaptador de red recién añadido, seleccione el conmutador lógico de carga de trabajo en el menú. Un ejemplo de nombre de conmutador lógico de carga de trabajo sería **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   **Importante:** asegúrese de no seleccionar el conmutador **Tránsito de carga de trabajo**.

2. Identifique una dirección IP disponible para la VM:
   *  La dirección IP debe estar en el rango `192.168.10.0/24`. Tenga en cuenta que la dirección IP `192.168.10.1` está reservada (consulte el **Paso 3**).
   *  Cuando configure el sistema de redes del sistema operativo que se ejecuta en la máquina virtual, utilice la dirección IP seleccionada y la máscara de `255.255.255.0`.

   **Nota:** el cliente es el responsable de gestionar el rango de direcciones IP a las que ha asignado las VM.

3. Asignar la pasarela predeterminada de la VM como `192.168.10.1`. Esta dirección es la dirección IP de NSX DLR del mismo conmutador lógico que las VM de carga de trabajo.

## Procedimiento para habilitar la regla de SNAT

Si desea que sus máquinas virtuales de carga de trabajo tengan acceso de salida a Internet, debe habilitar la regla SNAT (conversión de direcciones de red de origen) asociada. La habilitación de la regla SNAT permite convertir el acceso a Internet desde las VM en una sola dirección IP pública. Siga estos pasos en el cliente web de VMware vSphere:

1. Pulse **Inicio > Redes y seguridad**.
2. En el panel de navegación, pulse **NSX Edges** y realice una doble pulsación en el extremo denominado **customer-nsx-edge**.
3. Pulse **Gestión > NAT** para abrir el separador **NAT**.
4. Seleccione la regla SNAT predeterminada en la tabla y pulse la marca de comprobación verde que hay sobre la tabla para habilitar la regla.

Para obtener más información sobre las reglas NAT de NSX Edge, consulte [Gestión de reglas NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Procedimiento para identificar los detalles de subredes del cliente

El extremo **customer-nsx-edge** está pensado para que lo utilice el cliente, de modo que puede modificarlo para definir más reglas NAT para el tráfico de entrada o de salida. Estas reglas solo deben utilizar direcciones IP de las subredes públicas o privadas del cliente que se han solicitado en su nombre.

Para identificar los detalles de las subredes del cliente para que pueda utilizar las direcciones IP solicitadas, siga los pasos siguientes en el cliente web de VMware vSphere:

1. Pulse **Inicio > Redes y seguridad**.
2. En el panel de navegación, pulse **NSX Edges** y realice una doble pulsación en el extremo **customer-nsx-edge**.
3. En el separador **Resumen** de este extremo, revise la descripción del extremo, que contiene los identificadores de subred de las subredes del cliente privada y pública.

Encontrará más detalles sobre las subredes del cliente siguiendo estos pasos en el {{site.data.keyword.slportal}}:

1. Pulse **Redes > Gestión de IP > Subredes**.
2. Pulse el menú de filtro y en el campo de subred escriba el identificador tal como aparece en la descripción del extremo **customer-nsx-edge** del separador **Resumen** del cliente web de VMware vSphere.
3. Revise las notas que se muestran para las direcciones IP. Estas notas identifican cuáles de las subredes y direcciones IP se han solicitado y utilizado durante la configuración inicial.

   **Aviso:** no utilice las direcciones IP que se ha solicitado y utilizado durante la configuración inicial. Sin embargo, puede utilizar otras direcciones IP en estas subredes según sus requisitos. Para configurar reglas adicionales de conversión de direcciones de red, consulte [Gestión de reglas NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

### Enlaces relacionados

* [Resolución de problemas](../vcenter/vcenter_chg_impact.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
