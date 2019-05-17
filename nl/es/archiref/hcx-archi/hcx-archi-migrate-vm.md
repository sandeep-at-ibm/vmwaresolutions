---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Migrar de una máquina virtual
{: #hcx-archi-migrate-vm}

HCX permite la migración bidireccional: desde el entorno local a la nube o desde la nube al centro de datos local. HCX utiliza la tecnología de réplica durante el proceso de migración. La tecnología de réplica está integrada en el dispositivo virtual Hybrid Cloud Gateway. No es necesario instalar ningún otro software de réplica.

## Migración con bajo tiempo de inactividad

La migración con bajo tiempo de inactividad utiliza la réplica basada en host para trasladar una máquina virtual activa de un vCenter a un centro de datos virtual o viceversa. Para reducir el tiempo de inactividad, la máquina virtual de origen permanece en línea durante la réplica y se inicia en el host ESX de destino después de que se complete la réplica.

1. Una solicitud de migración desencadena las acciones siguientes:
  * La réplica inicia una transferencia de sincronización completa en un centro de datos virtual HCX de VCS. El tiempo que se tarda en realizar la réplica depende del tamaño de la VM y del ancho de banda disponible.
  * El consumo de ancho de banda de réplica varía en función de cómo la carga de trabajo cambia los bloques en el disco.
2. Cuando finaliza la sincronización completa, se produce una sincronización delta.
3. Cuando la sincronización delta finaliza, HCX desencadena una acción de conmutación (switchover). La acción de conmutación se puede iniciar de forma inmediata o se puede planificar para un momento específico.
4. Tras la acción de conmutación, la VM de origen se apaga y la réplica migrada se enciende. Si por alguna razón la VM no se puede encender, la nueva VM se apaga (o sigue apagada) y la original se enciende.
5. HCX cambia el nombre de la VM original apagada para evitar un conflicto de nombres con la VM migrada y añade una indicación de fecha y hora binaria al nombre de la máquina virtual original.
6. Si no se ha especificado que se habilite **Retener MAC**, la máquina virtual migrada obtiene una nueva dirección MAC.
7. La migración ha finalizado. Hybrid Cloud Services copia la máquina virtual original en la carpeta **VM migradas** en la vista Plantillas de vSphere.

## vMotion sin tiempo de inactividad
{: #hcx-archi-migrate-vm-no-downtime-vm}

vMotion transfiere una máquina virtual activa desde un vSphere vCenter a una nube VCS. Este vMotion requiere una red extendida. La transferencia vMotion captura la memoria activa de la máquina virtual, su estado de ejecución, su dirección IP y su dirección MAC.

La versión del hardware de la máquina virtual debe ser como mínimo la versión 9; de lo contrario vMotion entre nubes puede fallar.
{:note}

## Migración en frío
{: #hcx-archi-migrate-vm-cold-mig}

La migración en frío utiliza el mismo plano de datos que vMotion entre nubes para transferir una máquina virtual apagada sobre una red extendida. Su dirección IP y su dirección MAC se conservan. Los requisitos y las restricciones de la máquina virtual son los mismos que para vMotion.

### Migración de VM mediante el asistente bidireccional
{: #hcx-archi-migrate-vm-mig-bidir-wiz}

Si se utiliza el web de vSphere, se puede acceder al asistente de migración bidireccional desde el separador Iniciación de Hybrid Cloud Services. Este asistente gestiona todos los detalles de la migración, incluidas varias máquinas virtuales.

Desde el cliente web de vSphere, se puede acceder al asistente de migración bidireccional desde el separador Iniciación de Hybrid Cloud Services. Este asistente gestiona todos los detalles de la migración, incluidas varias máquinas virtuales.
* De vSphere a VCS Hybrid Cloud Services
* De VCS HCX Cloud a vSphere

### Comprobación de las VM antes de la migración
{: #hcx-archi-migrate-vm-check-vms}

Para migrar una máquina virtual, se necesita una conexión segura mantenida por Hybrid Cloud Gateway, y la máquina virtual debe cumplir los requisitos siguientes:
* La máquina virtual debe estar encendida.
* La arquitectura subyacente debe ser x86, independientemente del sistema operativo.
* Para utilizar la migración de vMotion, la versión del hardware debe ser superior a 9.
* La versión del hardware debe ser inferior a 10.
* Las máquinas virtuales con correlación de disco sin formato en modalidad de compatibilidad se pueden migrar.

Las máquinas virtuales con los siguientes atributos no reciben soporte para la migración:
* Superan los 2 TB.
* Comparten archivos VMDK.
* Tienen conectado un soporte virtual o ISO.
* La versión del hardware es inferior a 9.

### Supervisión de una migración
{: #hcx-archi-migrate-vm-monitor-mig}

El progreso de una migración basada en réplica se puede supervisar desde la interfaz de usuario o desde la línea de mandatos. Visualice la consola de tareas, tal como se describe en el apartado sobre supervisión del despliegue de dispositivos de servicio, y busque la tarea **Migrar VM**. Cuando el estado es **Completado**, la VM se migra y se enciende.

En este procedimiento se utiliza una VM no relacionada en el mismo vCenter para realizar el seguimiento del progreso de una VM migrada.

1. Identifique la VM que se va a migrar y elija una VM observadora que pueda ejecutar ping en la máquina virtual de migración.
2. Desde la interfaz de usuario, comience por migrar la VM y supervísela desde la consola de tareas.
3. Mediante SSH, inicie una sesión en el host ESXi que ejecuta la VM observadora.
4. Ejecute el siguiente mandato para obtener el ID de VM (el vmid):

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. Ejecute los siguientes mandatos para supervisar el estado de la réplica, donde vmid es el valor obtenido en el paso anterior:

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. ICMP Ping - Supervisar el ping continuo iniciado anteriormente.

Es posible que se produzca una interrupción en el ping continuo durante el proceso de conmutación. Sin embargo, el ping de prueba se reanuda rápidamente cuando finaliza la tarea **Migrar VM**, tal como queda reflejado en la consola de tareas.

### Visualización de las VM migradas
{: #hcx-archi-migrate-vm-view-vms}

Cuando Hybrid Cloud Services enciende una máquina virtual que se ha migrado correctamente, apaga la máquina virtual original y la guarda en una carpeta en vCenter. Las máquinas virtuales guardadas se conservan hasta que se suprimen manualmente.

Tras la migración, visualice el vCenter y anote las carpetas que están etiquetadas como **VM migradas desde la nube** y **VM migradas a la nube**.
* Como réplicas, las máquinas virtuales apagadas tienen el nombre original, al que se ha añadido una indicación de fecha y hora binaria.
* Las VM migradas se pueden tratar como cualquier otra VM. Por ejemplo, pueden moverse a otra ubicación y encenderse.
* Las VM de estas carpetas que ya no se deseen se pueden suprimir.
* La supresión es final, a menos que se disponga de una solución de copia de seguridad.

## Enlaces relacionados
{: #hcx-archi-migrate-vm-related}

* [Modificación o desinstalación de HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
