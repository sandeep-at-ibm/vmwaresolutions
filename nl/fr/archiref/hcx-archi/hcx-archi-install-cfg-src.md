---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---
# Installation et configuration de HCX sur la source
{: #hcx-archi-install-cfg-src}

L'installation sur site implique le déploiement du dispositif de gestion HCX et son enregistrement auprès de vCenter et auprès d'un ou de plusieurs noeuds finaux du cloud compatibles VCS HCX.

## Installation du dispositif HCX Manager
{: #hcx-archi-install-cfg-src-install-hma}

Installez le dispositif HCX Manager dans le vCenter sur site.

1. Connectez-vous à **My VMware** et téléchargez le fichier OVA des Services cloud hybrides depuis la page de téléchargement du produit.
2. Ouvrez un navigateur et connectez-vous au client vSphere Web Client. Cette tâche ne peut pas être effectuée depuis le client vSphere. Consultez l'onglet **Home**.
3. Dans la liste **Inventories Trees**, cliquez sur **Host and Clusters**.
4. Développez la hiérarchie pour afficher les centres de données.
5. Cliquez avec le bouton droit de la souris et sélectionnez **Deploy OVF Template** dans le menu. Quelques secondes peuvent être nécessaires pour que l'élément de menu **Deploy OVF template** apparaisse.
6. Choisissez **Deploy OVF template**.
  1. Sélectionnez **Local file** et cliquez sur **Browse** pour rechercher le fichier OVA téléchargé sur l'ordinateur. Cliquez sur **Next**.
  2. Dans la page **Review details**, sélectionnez l'option **Accept extra configuration options** et cliquez sur **Next**.
  3. Dans la page **Accept EULAs**, faites défiler pour passer en revue le contrat de licence utilisateur VMware. Cliquez sur **Accept** et sur **Next**.
  4. Dans la page **Select name and folder**, modifiez le nom si nécessaire et sélectionnez l'emplacement des Services cloud hybrides. Cliquez sur **Next**.
  5. Dans la page **Select a resource**, sélectionne l'emplacement d'installation.
  6. Dans la page **Select storage**, sélectionnez le stockage pour les Hybrid Cloud Services et cliquez sur **Next**. Depuis la liste **Select virtual disk format**, vous pouvez sélectionner **thin provisioning** ou **thick provisioning**.
  7. Dans la page **Setup networks**, mappez l'adaptateur des Services cloud hybrides à un réseau hôte de la liste **Destination**.
7. Dans la page **Customized template**, entrez les valeurs spécifiques à l'environnement :
  * Pour les mots de passe, le nom d'utilisateur par défaut pour l'interface de ligne de commande et l'interface utilisateur Web est **admin**. L'utilisateur et le mot de passe **admin** pour la connexion à l'interface utilisateur Web sont obligatoires tout comme l'est également un compte utilisateur **root** dont le mot de passe peut être défini.
  * Entrez et entrez de nouveau le mot de passe utilisateur **admin** de l'interface de ligne de commande.
  * Entrez et entrez de nouveau le mot de passe utilisateur **root**. Ultérieurement, si une assistance auprès de VMware Global Support Services (GSS) est nécessaire, ce mot de passe devra peut-être être partagé afin de permettre le dépannage du système.
  * Pour les propriétés réseau, entrez le nom d'hôte pour la machine virtuelle HCX Manager. Entrez l'adresse IPv4 du réseau, le préfixe IPv4 (le CIDR), ainsi que la passerelle par défaut. Le tableau suivant illustre des valeurs exemples :

Tableau 1. Valeurs exemple pour les propriétés réseau

| Zone                    | Valeur           |
|--------------------------|-----------------|
| Hostname                 | HCM_1           |
| Network 1 IPv4 Address   | 192.168.200.101 |
| Network 1 IPv4 Prefix    | 24              |
| Default IPv4 Gateway     | 192.168.200.1   |
| Network 1 IPv6 Address   |                 |
| Network 1 IPv6 Prefix    |                 |

8. Passez en revue la page des liaisons vService. Cliquez sur **Next** pour continuer.
9. Dans la page **Ready to complete**, procédez comme suit :
  * Sélectionnez l'option **Power on after deployment**.
  * Passez en revue les paramètres des Services cloud hybrides, puis cliquez sur **Finish**. Plusieurs minutes peuvent être nécessaires pour que le dispositif des Services cloud hybrides se mette sous tension.
  * Pour vérifier l'état, accédez à la page d'accueil de vSphere Web Client, et, sous l'onglet **Home**, accédez à **Inventories** et cliquez sur **Hosts and Clusters**. Développez la hiérarchie du centre de données, puis cliquez sur la machine virtuelle du service cloud hybride pour afficher un récapitulatif dans le volet central.
  * Consultez l'onglet **Summary**, la console indique **Powered On** et le bouton **Play** est vert.
10. HCX Manager est sous tension et prêt pour un enregistrement auprès de vCenter.

## Liens connexes
{: #hcx-archi-install-cfg-src-related}

* [Préparation de l'environnement d'installation](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-prep-install)
