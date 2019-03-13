---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# I dispositivi Zerto Virtual Replication Appliance non vengono visualizzati per i server ESXi appena creati
{: #trbl_no_zerto_vra}

## Problema
{: #trbl_no_zerto_vra-problem}

I dispositivi VRA (Virtual Replication Appliance) non vengono visualizzati sulla console Zerto Virtual Replication dopo aver aggiunto i server ESXi a un'istanza VMware vCenter Server in cui è installato il ripristino di emergenza Zerto.

## Risoluzione
{: #trbl_no_zerto_vra-resolution}

Per le istanze vCenter Server, il servizio di ripristino di emergenza Zerto viene installato solo sul server ESXi dal cluster predefinito, **cluster1**. Per qualsiasi cluster aggiuntivo nello stesso ambiente vCenter Server non viene installato automaticamente il ripristino di emergenza Zerto quando il cluster aggiuntivo viene creato, né quando il server ESXi viene aggiunto a quel cluster aggiuntivo.

Sui cluster aggiuntivi, devi installare il ripristino di emergenza Zerto separatamente.

Apri un ticket di supporto {{site.data.keyword.cloud}} e collabora con il supporto IBM per ottenere gli indirizzi IP disponibili per installare i VRA dalla console di Zerto, anziché dalla console {{site.data.keyword.vmwaresolutions_short}}.

Per accedere alla console Zerto, seleziona la scheda Zerto dalla scheda **Servizi** dell'istanza e fai clic su **Visualizza dettagli** e quindi su **Visualizza Zerto Console**.

Per ulteriori informazioni su come contattare il supporto IBM, vedi [Come contattare il supporto IBM](/docs/services/vmwaresolutions//vmonic/trbl_support.html).
