---

copyright:

  years:  2016, 2019

lastupdated: "2018-08-16"

---

# Distribuzione di un file OVF mediante il client web VMware vSphere

## Risoluzione

Per distribuire un file OVF (Open Virtualization Format) mediante il client web vSphere, utilizza la seguente procedura:
1. Prima di tentare la distribuzione di un file OVF, aggiungi le seguenti informazioni host al file `/etc/hosts`:

   * Informazioni host per Platform Services Controller (PSC)
   * Informazioni host per il server VMware ESXi
   * Informazioni host per vCenter
2. Controlla il tuo file `/etc/hosts` per assicurarti che queste informazioni siano state aggiunte correttamente. Un esempio di file host potrebbe essere simile al seguente elenco:

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. Assicurati di avere accesso a tutte le VPN (Virtual Private Network) necessarie nel {{site.data.keyword.slportal_full}}. In questo esempio, sarebbero `10.131.7.xx` e `10.131.9.xxx`.
4. Accedi alla VPN per il tuo data center.
5. Fai clic su **vCenter** per accedere al client web vSphere.
6. Fai clic con il tasto destro del mouse su un host e distribuisci un file `.ovf`.
