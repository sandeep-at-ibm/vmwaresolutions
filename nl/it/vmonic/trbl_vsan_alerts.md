---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Avvertenze e avvisi di integrità di Virtual SAN
{: #trbl_vsan_alerts}

## Problema
{: #trbl_vsan_alerts-problem}

Nella pagina **Monitor** del client web VMware vSphere, potresti visualizzare avvertenze e avvisi relativi ai problemi di integrità della Virtual SAN.

## Risoluzione
{: #trbl_vsan_alerts-resolution}

Queste avvertenze non comportano complicazioni e non indicano problemi funzionali. Tuttavia, se vuoi cancellare le avvertenze dal client web vSphere,
utilizza la seguente procedura.

1. Vai all'indirizzo http://partnerweb.vmware.com/service/vsan/all.json e salva il file JSON, denominato `all.json`, sul tuo sistema locale.
2. Assicurati di aver completato i passi indicati in [Timeout della console vCenter](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console).
3. Nella pagina dei dettagli dell'istanza Cloud Foundation, fai clic sul pulsante **Console vCenter** e accedi al client web vSphere utilizzando le credenziali visualizzate nella console {{site.data.keyword.vmwaresolutions_full}}.
4. Nel client web vSphere, passa a **Gestisci > Impostazioni** e apri la sezione **Virtual SAN > Integrità > Database HCL**. Fai clic su **Aggiorna da file**, quindi carica il file `all.json` salvato in precedenza.
5. Per cancellare le avvertenze, passa al riquadro **Allarmi** nell'angolo superiore destro del client web vSphere. Fai clic con il tasto destro del mouse su ciascun allarme e seleziona **Reimposta su verde**.

Per ulteriori informazioni, vedi [How to download offline vSAN HCL file for vSAN Health Check Plugin](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}.
