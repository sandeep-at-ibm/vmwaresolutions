---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


---

# VRA de Zerto visible en el host ESXi en la consola de vCenter después de que se desinstale Zerto on IBM Cloud
{: #trbl_zerto_vra}

## Problema
{: #trbl_zerto_vra-problem}

Los dispositivos de réplica virtual (VRA) de Zerto no se eliminan después de utilizar el
{{site.data.keyword.slportal}} para desinstalar correctamente el servicio Zerto on {{site.data.keyword.cloud}}.

## Solución
{: #trbl_zerto_vra-resolution}

Elimine manualmente los VRA desde la consola de vCenter.

1. Inicie sesión en la consola de vCenter.
2. Pulse **Hosts y clústeres** y localice las máquinas virtuales con nombres que empiecen por
**Z-VRA-**. Por ejemplo, **Z-VRA-host0-vcs40dal.vcs.icvs.org**.
3. Pulse el botón derecho del ratón sobre la máquina virtual **Z-VRA-** y pulse
**Suprimir del disco**.
