---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

# Dépassement du délai d'attente lors de la connexion au client Web VMware vSphere
{: #trbl_timeout_vc_console}

## Problème
{: #trbl_timeout_vc_console-problem}

Lorsque vous essayez de vous connecter au client Web vSphere, il est possible que vous obteniez l'erreur de temporisation suivante :

`The server at <IP_address> is taking too long to respond.`

## Résolution
{: #trbl_timeout_vc_console-resolution}

Procédez comme suit pour identifier et résoudre le problème.

1. Vérifiez que vous avez effectué les opérations indiquées dans l'infobulle qui s'affiche lorsque vous survolez le bouton de **console vCenter**. Par
   commodité, ces opérations sont également répertoriées ci-dessous :   
   1. Installez le plug-in Adobe Flash Player pour votre navigateur.   
   2. Créez un mot de passe de réseau privé virtuel à partir du portail {{site.data.keyword.slportal_full}}.    
   3. [Connectez-vous au réseau privé virtuel du centre de données](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking#login-to-the-vpn) à l'aide des données d'identification de réseau privé virtuel de l'infrastructure {{site.data.keyword.cloud_notm}}.     
   4. Ajoutez le mappage d'adresse IP et de nom d'hôte du contrôleur PSC (Platform Services Controller) dans le fichier hosts à partir de votre ordinateur local. Utilisez le format suivant :

      ```javascript
      IPAddress              HostName
      ```

2. Notez l'adresse IP affichée car vous en aurez besoin dans l'une des prochaines étapes.
3. Vérifiez que vous pouvez accéder au réseau privé virtuel de l'infrastructure {{site.data.keyword.cloud_notm}}. Effectuez les opérations suivantes sur le portail {{site.data.keyword.slportal}} :
   1. Cliquez sur **Compte > Accès VPN**.
   2. Cliquez sur **Liaison SSL** dans la colonne **Accès VPN**.
   3. Sur la page **Accès VPN pour nom d'utilisateur**, affectez à l'option **Accès de sous-réseau** la valeur **Manuel**.
   4. Sur la même page, localisez le sous-réseau de la paire adresse IP-nom d'hôte. Pour plus d'informations, voir **Etape 2**.    

      Par exemple, si l'adresse IP de votre instance est `xx.yyy.zz.15` et que l'adresse IP de vCenter est `xx.yyy.zz.10`, vous devez accorder l'accès au sous-réseau `xx.yyy.zz.0/26`.

   5. Cochez la case **Autoriser l'accès** de ce sous-réseau, puis cliquez sur **Sauvegarder**.
