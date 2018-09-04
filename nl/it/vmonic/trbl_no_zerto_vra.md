---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# I dispositivi Zerto Virtual Replication Appliance non vengono visualizzati per i server ESXi appena creati

## Problema
I dispositivi VRA (Virtual Replication Appliance) non vengono visualizzati sulla console Zerto Virtual Replication dopo aver aggiunto i server ESXi a un'istanza VMware vCenter Server in cui è installato il ripristino di emergenza Zerto.

## Risoluzione
Per le istanze vCenter Server, il servizio di ripristino di emergenza Zerto viene installato solo sul server ESXi dal cluster predefinito, **cluster1**. Per eventuali cluster aggiuntivi nello stesso ambiente vCenter Server non verrà installato automaticamente il ripristino di emergenza Zerto quando viene creato il cluster aggiuntivo, né quando il server ESXi viene aggiunto a tale cluster aggiuntivo.

Sui cluster aggiuntivi, devi installare il ripristino di emergenza Zerto separatamente.

Apri un ticket di supporto {{site.data.keyword.cloud}} e collabora con il supporto IBM per ottenere gli indirizzi IP disponibili per installare i VRA dalla console di Zerto, anziché dalla console {{site.data.keyword.vmwaresolutions_short}}.

Per accedere alla console Zerto, seleziona la scheda Zerto dalla scheda **Servizi** dell'istanza e fai clic su **Visualizza dettagli** e quindi su **Visualizza Zerto Console**.

Per ulteriori informazioni su come contattare il supporto IBM, vedi [Come contattare il supporto IBM](trbl_support.html).
