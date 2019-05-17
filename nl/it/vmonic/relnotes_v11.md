---

copyright:

  years:  2016

lastupdated: "2016-11-04"

subcollection: vmware-solutions


---

# Note sulla release per la V1.1
{: #relnotes_v11}

Questa release include nuove funzioni, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Requisito di spanning della VLAN
{: #relnotes_v11-vlan-spanning}

Se utilizzi un account SoftLayer® classico (non VRF), è necessario abilitare lo spanning della VLAN. Se lo spanning della VLAN non è abilitato per gli account classici, i vari componenti dell'ambiente di virtualizzazione VMware potrebbero non essere in grado di comunicare tra loro. Per abilitare lo spanning della VLAN nel tuo account SoftLayer, vedi [Abilita o disabilita il VLAN Spanning](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}.

## Impostazioni e notifiche e-mail
{: #relnotes_v11-email}

Puoi configurare le notifiche e-mail nella pagina **Impostazioni**. Per impostazione predefinita, l'impostazione è abilitata, il che significa che ricevi una notifica via e-mail per ogni istanza appena ordinata, quando tale istanza viene fornita ed è pronta per l'uso. Puoi anche disabilitare le notifiche e-mail nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Informazioni dettagliate sullo stato
{: #relnotes_v11-status-info}

Le informazioni dettagliate sullo stato sono ora disponibili per le istanze Cloud Foundation. Quando fai clic su un nome di istanza, le informazioni sullo stato visualizzate forniscono ulteriori dettagli sull'avanzamento della distribuzione. Se si verifica un errore, vengono visualizzati i messaggi per risolvere il problema.
