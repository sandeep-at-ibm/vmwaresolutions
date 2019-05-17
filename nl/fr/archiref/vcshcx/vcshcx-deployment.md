---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

# Déploiement cloud et client
{: #vcshcx-deployment}

Une installation minimale de HCX consiste en un seul déploiement côté cloud et côté client. Le côté client de HCX peut s'installer sur n'importe quelle version de vSphere prise en charge par HCX du moment qu'il existe une connectivité réseau entre le côté client et le côté cloud.

## Conditions requises
{: #vcshcx-deployment-req}

- HCX Manager – 8 unités centrales, mémoire 12G, disque 60G
- Passerelle CGW – 8 unités centrales, mémoire 3G, disque 2G
- Concentrateur L2 – 8 unités centrales, mémoire 3G, disque 2G
- Optimiseur de réseau WAN – 8 unités centrales, mémoire 14G, disque 100G

## Cloud
{: #vcshcx-deployment-cloud}

Côté cloud, le déploiement de HCX est effectué de manière automatique par {{site.data.keyword.vmwaresolutions_full}}. La configuration par défaut utilise le groupe de ports public pour configurer la connectivité des noeuds finaux des composants de flotte. Les composants de flotte côté cloud sont déployés avec leurs interfaces de noeud final configurées avec des adresses IP publiques car il s'agit de dispositifs à sécurité renforcée. Il est possible de les déployer derrière un pare-feu. Le côté client et le côté cloud ne peuvent pas se connecter l'un à l'autre à travers un tunnel VPN existant. Si vous souhaitez utiliser le réseau privé pour la connectivité des points finaux de HCX, vous pouvez commander le côté cloud de HCX pour un déploiement de flotte de réseaux privés à utiliser sur un lien dédié tel que MPLS.

## Client
{: #vcshcx-deployment-client}

Le côté client de HCX est déployé par l'utilisateur et requiert des droits de niveau administrateur pour l'accès au vCenter source. A l'heure de la présente publication, le fichier OVA du gestionnaire de côté client HCX est d'environ 1,7 Go. Lorsque vous utilisez la console {{site.data.keyword.vmwaresolutions_short}} pour commander HCX, une URL est fournie avec un lien permettant de télécharger la version de HCX pour le côté client qui correspond à la version de HCX déployée du côté cloud. Ce lien est fourni dans l'interface utilisateur de HCX Manager côté cloud.

Une clé d'enregistrement à usage unique est également fournie. Utilisez les étapes suivantes pour configurer l'enregistrement d'utilisation.

1. Téléchargez le fichier OVA du client HCX (entreprise) du lien fourni dans l'interface HCX du côté client.
    1. Connectez-vous à l'interface utilisateur du HCX côté cloud à l'aide de l'interface utilisateur d'enregistrement de HCX fournie par IBM.
    2. Utilisez l'ID et le mot de passe de cloud vCenter pour vous connecter à l'interface utilisateur.
    3. Sur l'onglet **Administration**, sélectionnez **request download link** pour télécharger le fichier OVA côté client. Utilisez la "boîte de saut" qui est locale au vCenter source où l'OVA est déployé pour compléter cette étape.
2. Connectez-vous au client C++ vSphere (ou au client web avec le snap-in d'intégration client fonctionnel) et importez l'OVA qui utilise l'assistant d'importation de vCenter.
    1. Assurez-vous que le réseau sur lequel le gestionnaire HCX est configuré a accès à la fois au vCenter source et à Internet.  
    2. Entrez la clé d'enregistrement lorsque vous y êtes invité. (Utilisez le client Web si vous avez configuré le snap-in d'outils client.)  
3. Déconnectez-vous et reconnectez-vous au client Web vCenter. L'icône de sélection de menu de **HCX** s'affiche sous le menu de l'écran d'accueil.
4. Pour les certificats auto-signées, sélectionnez l'élément de menu HCX pour accéder à l'interface utilisateur du snap-in HCX. Sélectionnez l'onglet **Administration**.
    1. Sélectionnez l'importation des certificats de l'URL et la clé dans l'URL d'enregistrement du côté cloud HCX fourni par la console {{site.data.keyword.vmwaresolutions_short}} pour HCX.
    2. Sélectionnez **New Site Paring** dans la sous-fenêtre **Site Parings** de l'onglet **Dashboard**.
    3. Suivez les invites et fournissez l'URL d'enregistrement du côté cloud HCX ainsi que l'ID et le mot de passe de l'administrateur vCenter côté cloud.
    4. Continuez de suivre les invites de l'assistant d'enregistrement du site en configurant les composants de flotte, y compris la passerelle cloud, le concentrateur de couche 2 et l'optimiseur de réseau WAN.  

Pour le côté client, utilisez le menu **Tasks** pour surveiller le déploiement des composants Flotte. Pour le déploiement côté cloud, utilisez le menu **Tasks** dans l'interface utilisateur Web vCenter pour l'instance vCenter Server particulière.

Si une erreur de déploiement se produit d'un côté ou de l'autre, les déploiements de composant de flotte sont annulés et supprimés. Après avoir déterminé la cause de l'échec, cliquez sur l'onglet **Interconnect** dans l'interface utilisateur Web vCenter de HCX côté client, puis sélectionnez **Install HCX Components** en haut de l'écran.

Une fois le déploiement des composants de flotte réussi et après quelques minutes, le statut du tunnel des composants CGW et L2C affichent **Up** dans l'onglet **Interconnect**.

## Liens connexes
{: #vcshcx-deployment-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
