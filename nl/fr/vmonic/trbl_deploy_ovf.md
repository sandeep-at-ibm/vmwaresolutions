---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Déploiement d'un fichier OVF à l'aide du client Web VMware vSphere
{: #trbl_deploy_ovf}

## Résolution
{: #trbl_deploy_ovf-resolution}

Pour déployer un fichier OVF (Open Virtualization Format) à l'aide du client Web vSphere, procédez comme suit :
1. Avant de tenter le déploiement d'un fichier OVF, vous devez ajouter les informations d'hôte suivantes dans le fichier `/etc/hosts` :

   * Informations d'hôte pour le contrôleur PSC (Platform Services Controller)
   * Informations d'hôte pour le serveur VMware ESXi
   * Informations d'hôte pour vCenter
2. Vérifiez votre fichier `/etc/hosts` pour vous assurer que ces informations ont bien été ajoutées. Exemple de fichier hosts :

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. Vérifiez que vous avez accès à tous les réseaux privés virtuels (VPN, Virtual Private Network) dans le portail {{site.data.keyword.slportal_full}}. Dans cet exemple, il s'agit de `10.131.7.xx` et `10.131.9.xxx`.
4. Connectez le réseau privé virtuel de votre centre de données.
5. Cliquez sur **vCenter** pour accéder au client Web vSphere.
6. Cliquez sur un hôte avec le bouton droit de la souris et déployez un fichier `.ovf`.
