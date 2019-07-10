---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, secondary vCenter, vSphere inventory issue

subcollection: vmware-solutions


---

# Il sistema vCenter Server secondario non viene visualizzato nell'inventario del client web vSphere
{: #trbl_sec_inst_not_visible}

## Problema
{: #trbl_sec_inst_not_visible-problem}

In una configurazione multisito, dopo aver aggiunto una nuova istanza secondaria, il suo sistema vCenter Server non è visibile quando accedi al client web VMware vSphere di un'istanza ordinata in precedenza.

## Risoluzione
{: #trbl_sec_inst_not_visible-resolution}

Questo è un problema noto di VMware 6.5.

Per risolvere il problema, devi riavviare il client web vSphere:

1. Utilizzando l'account **root**, connettiti attraverso **ssh** alla VM (macchina virtuale) vCenter dell'istanza precedentemente ordinata.
2. Immetti ``shell`` per inserire la shell bash.
3. Immetti `service-control --stop vsphere-client` per arrestare il client.
4. Immetti `service-control --start vsphere-client` per riavviare il client.
5. Dopo il riavvio del client web vSphere dell'istanza precedentemente ordinata, conferma che il sistema vCenter Server per l'istanza secondaria appena aggiunta sia visibile nel client web vSphere.
