---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Despliegue todo en uno
{: #caveonix-allinone}

Un despliegue y configuración automatizados de una sola máquina virtual (VM) que aloja todos los componentes de la aplicación RiskForesight. Este modelo de despliegue es adecuado para despliegues pequeños, hasta un máximo de 100 activos con 7-30 días de indexación. En la siguiente tabla se muestran los detalles de máquina virtual de “todo en uno”:

Tabla 1. Parámetros todo en uno

|Parámetro	|Valor|
|---|---|
|Tipo	|Base|
|Cantidad de VM	|1|
|vCPU	|16|
|RAM	|32 GB|
|Disco	|80 GB|
|SO	|CentOS 7|
|Componentes de aplicación instalados|	IU, App, Plugins, Recopilador central, Almacén de datos de índice, Almacén de datos de mensajería, Almacén de datos relacional, Almacén de datos de índice, Recopilador remoto|

En la siguiente tabla se muestran los detalles de máquina virtual del recopilador remoto adicional.

Tabla 2. Recopilador remoto

|Parámetro	|Valor|
|---|---|
|Cantidad de VM	|Según sea necesario|
|vCPU	|8|
|RAM	|8 GB|
|Disco	|1 TB|
|SO	|CentOS 7|
|Componentes de aplicación instalados	|Recopilador remoto|
