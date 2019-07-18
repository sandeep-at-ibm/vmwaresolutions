---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Déploiement du client HCX
{: #hcxclient-vcs-client-deployment}

Une installation minimale de HCX consiste en un seul déploiement côté cloud et côté client.

Le côté client de HCX peut s'installer sur n'importe quelle version de vSphere prise en charge par HCX du moment qu'il existe une connectivité réseau entre le côté client et le côté cloud.

## Conditions requises
{: #hcxclient-vcs-client-deployment-req}

| Composant | Nombre d'UC | Mémoire (Go) | Disque (Go) |
|--------|--------|---------|-------|
| HCX Manager | 4 | 12G |  60G |
| HCX Interconnect (HCX-IX) | 4 | 3G |  2G |
| HCX Network Extension (HCX-NE) | 4 | 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) | 8 | 14G |  100G |

## Licence client
{: #hcxclient-vcs-client-deployment-licensing}

HCX est un service. HCX est concédé sous licence pour chaque site et pour chaque machine virtuelle à travers des serveurs de licences maintenus par VMware. Les instances HCX côté cloud et côté client ont besoin de communiquer avec le site d'enregistrement VMware durant toute leur durée de vie.
- Le trafic sur 80 et 443 doit être autorisé dans `https://connect.hybridity.vmware.com`
- Une clé d'enregistrement à usage unique est fournie par la console {{site.data.keyword.vmwaresolutions_full}} pour l'installation côté client. Une clé est requise pour chaque installation HCX côté client.

### Procédure de commande de licences HCX locales
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Faites défiler l'écran vers le tableau **Licences HCX locales** et cliquez sur **Mettre à disposition un nouvel élément**.
3. Entrez le nom de la licence.
4. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant de commander la licence.
5. Cliquez sur **Mettre à disposition**.

## Exigences liées aux adresses IP
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

Pour déployer HCX, le nombre correct d'adresses IP doit être disponible à la fois en local et dans l'IBM Cloud cible.

* Adresse vMotion
  La gestion d'un réseau distinct pour vMotion est une pratique courante dans le centre de données local. La passerelle cloud doit avoir accès au réseau vMotion. Si ce n'est pas le cas, une adresse IP supplémentaire est nécessaire pour communiquer avec le réseau vMotion.

* Local
  * Une adresse IP pour le dispositif HCX Manager.
  * Une pour chaque dispositif InterConnect ; ajoutez-en une autre s'il y a un réseau vMotion distinct.
  * Une pour chaque composant Network Extension

* IBM Cloud
  * Deux adresses IP par dispositif HCX Manager connecté à IBM Cloud. Les adresses peuvent être utilisées pour la connexion à Internet ou à une ou plusieurs lignes de connexion directes.
  * Ajoutez-en une autre s'il y a un réseau vMotion distinct.

## Téléchargement de fichier OVA côté client
{: #hcxclient-vcs-client-deployment-client-ova}

HCX côté client est déployé par l'utilisateur et nécessite des droits de niveau administrateur pour l'accès au vCenter source. A l'heure de la présente publication, le fichier OVA du gestionnaire de côté client HCX est d'environ 1,7 Go. Lorsque vous utilisez la console {{site.data.keyword.vmwaresolutions_short}} pour commander HCX, une URL est fournie avec un lien permettant de télécharger la version de HCX pour le côté client qui correspond à la version de HCX déployée du côté cloud. Ce lien est fourni dans l'interface utilisateur de HCX Manager côté cloud.

Une clé d'enregistrement à usage unique est également fournie. Utilisez les étapes suivantes pour configurer l'enregistrement d'utilisation.

1. Téléchargez le fichier OVA du client HCX (entreprise) du lien fourni dans l'interface HCX du côté client.
    1. Connectez-vous à l'interface utilisateur du HCX côté cloud à l'aide de l'interface utilisateur d'enregistrement de HCX fournie par IBM.
    2. Utilisez l'ID et le mot de passe de cloud vCenter pour vous connecter à l'interface utilisateur.
    3. Sur l'onglet **Administration**, sélectionnez **request download link** pour télécharger le fichier OVA côté client. Utilisez la jumpbox qui se trouve sur le vCenter source où l'OVA est déployé pour effectuer cette étape.

## Installation et configuration de HCX sur la source
{: #hcxclient-vcs-client-deployment-install-cfg-src}

L'installation sur site implique le déploiement du dispositif de gestion HCX et son enregistrement auprès de l'environnement vCenter.

### Installation du dispositif HCX Manager
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

Installez le dispositif HCX Manager dans le vCenter sur site.
1. Connectez-vous à **My VMware** et téléchargez le fichier OVA des Services cloud hybrides depuis la page de téléchargement du produit.
2. Ouvrez un navigateur et connectez-vous au client vSphere Web Client. Consultez l'onglet **Home**.
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
10. HCX Manager est sous tension et prêt pour un enregistrement auprès du vCenter local.

## Configuration initiale du dispositif HCX Manager
{: #hcxclient-vcs-client-deployment-inital-config}

1. Assurez-vous que le dispositif virtuel Hybrid Cloud Service dispose d'un accès sortant à `https://connect.hcx.vmware.com`
2. Connectez-vous à l'interface d'administration du dispositif virtuel Hybrid Cloud Services `https://<IP>:9443` avec **admin**
3. Indiquez la clé de licence collectée dans les conditions préalables côté client.
4. Emplacement du centre de données HCX Cloud
    - Entrez la ville la plus proche du centre de données où réside l'instance HCX Cloud. Si la ville n'apparaît pas, sélectionnez la ville principale la plus proche.
5. Indiquez le nom du système

## Importation d'un certificat vSphere Server
{: #hcxclient-vcs-client-deployment-import-cert}

1. Connectez-vous à l'interface d'administration de HCX Manager `https://<IP>:9443`
2. Sélectionnez l'onglet **Administration** sous **Certificate** -> **Trusted CA Certificate**
3. Importez le site Web vSphere Server
   1. Sélectionnez l'importation des certificats de l'URL et la clé dans l'URL d'enregistrement côté cloud HCX.
     * Sao Paulo : `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## Procédure pour l'enregistrement de HCX Manager auprès de vCenter/SSO/NSX
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. Connectez-vous au dispositif virtuel du service cloud hybride.
2. Cliquez sur la vignette **Manage Settings**.
  1. Dans le volet gauche, sous **Configure Systems**, sélectionnez vCenter.
  2. Cliquez sur **Add vCenter** dans l'angle supérieur droit.
  3. Entrez l'adresse IP de vCenter Server au format `https://vCenter-host-name` ou `https://vCenter-IP-address`.
    * Par exemple, `https://My-vCenter` ou `https://10.108.26.211`.
  4. Entrez le nom d'utilisateur et le mot de passe de vCenter Server. Le compte qui est utilisé doit avoir le rôle de l'administrateur vCenter.
  5. Cliquez sur **OK**. Ne redémarrez pas lorsque le message _You need to restart the app_ s'affiche.
3. Configurez le service de recherche / de connexion unique (SSO).
  6. Cliquez sur l'onglet **Manage**.
  7. Cliquez sur **Edit** en regard de la zone de texte **Lookup Service URL**.
  8. Entrez le noeud final de service de réseau recherche sous la forme suivante :
    * Pour vCenter Server 6.5 `https://psc/`
  9.  Indiquez les détails NSX si nécessaire.
  10. Cliquez sur **OK**. Ne redémarrez pas lorsqu'un message demandant le redémarrage du moteur Web s'affiche.
4. Cliquez sur l'onglet **Summary** et recherchez la section **Hybridity Management Components**. Arrêtez et redémarrez à la fois le moteur d'applications et le moteur Web.
5. Pour finaliser l'enregistrement, déconnectez-vous du client vSphere Web Client. Reconnectez-vous à vSphere Web Client pour vérifier que l'onglet HCX est présent.

## Résultats
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

Notez la présence de l'icône **Hybrid Cloud** et de l'élément de menu **Hybrid Cloud Services** sur la gauche. L'enregistrement des Services cloud hybrides met à jour ces étiquettes. Dans l'inventaire, l'étiquette d'icône devient **Services cloud hybrides**.

## Liens connexes
{: #hcxclient-vcs-client-deployment-related}

* [Glossaire des composants et des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Préparation de l'environnement d'installation](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Maillage de services sur site HCX ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrations de VMware Hybrid Cloud ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Paramètres et composants de surveillance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Traitement des incidents dans HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
