---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-28"

subcollection: vmware-solutions


---

# Maillage de services sur site HCX
{: #hcxclient-vcs-mesh-deployment}

Passez en revue les étapes suivantes pour configurer l'instance du client HCX :

## Appariement de sites IBM Cloud for VMware Solutions Environment
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. Connectez-vous à VMware vSphere Web Client.
2. Dans le menu **Home**, sélectionnez l'option **HCX**.
3. Sous **Infrastructure**, **InterConnect**, cliquez sur **Add Site Pairing**.
  1. Affectez à l'URL de site l'URL de HCX Cloud Manager, par exemple, `https://x.x.x.x.x`.
  2. Définissez le nom d'utilisateur et le mot de passe avec les détails d'administrateur de HCX Manager : admin/password.

    Les informations précédentes peuvent être obtenues auprès d'IBM Cloud à partir de la console VMware Solutions, sous **Services**, **HCX on IBM Cloud** pour l'instance vCenter Server. 
    
4. Cliquez sur **Connect**.

### Résultats
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

L'appariement de sites a été enregistré et affiché avec succès dans l'interface utilisateur.

## Création de profils sur site HCX
{: #hcxclient-vcs-mesh-deployment-profiles}

## Profils de réseau de maillage de services sur site
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. Connectez-vous au client vSphere Web Client.
2. Dans le menu **Home**, sélectionnez l'option **HCX**.
3. Sous **Infrastructure**, cliquez sur **InterConnect**.
4. Sous **Multi-Site Service Mesh**, cliquez sur **Network Profiles**.
5. A partir de **Create Network Profile** :
   1. Sélectionnez Distributed Port Group, par exemple, External.
   2. Indiquez une plage d'adresses IP externes, une longueur de préfixe de sous-réseau externe, une passerelle externe et des détails DNS. 
   3. Définissez MTU sur 1500.
   4. Cliquez sur **Create**.
6. Répétez les étapes précédentes pour les réseaux de gestion et vMotion.
   Remarque : MTU doit être défini sur 9000.

## Résultats
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| Nom de réseau | MTU |
| -----| ----|
| Externe | 1500|
| Gestion | 9000|
| vMotion | 9000|

## Profils de calcul de maillage de services sur site
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. Connectez-vous au client vSphere Web Client.
2. Dans le menu **Home**, sélectionnez l'option **HCX**.
3. Sous **Infrastructure**, cliquez sur **InterConnect**.
4. Sous **Multi-Site Service Mesh**, cliquez sur **Compute Profiles**.
5. A partir de **Create Compute Profile** :
   1. Indiquez un nom de profil de calcul. 
   2. Sélectionnez tous les services à activer, puis cliquez sur **Continue**
   3. Sélectionnez le cluster, puis cliquez sur **Continue**
   4. Sélectionnez le magasin de données, puis cliquez sur **Continue**
   5. Sélectionnez Network Profile for Management, puis cliquez sur **Continue**.
   6. Sélectionnez Network Profile for External/Uplink, puis cliquez sur **Continue**.
   7. Sélectionnez Network Profile for vMotion, puis cliquez sur **Continue**.
   8. Sélectionnez Network Profile for vSphere Replication (Management), puis cliquez sur **Continue**.
   9. Sélectionnez Distribute Switch for extension, par exemple, Private-Switch, puis cliquez sur **Finish**.

## Résultats
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

Un profil de calcul pour la combinaison cluster/stockage a été créé et est disponible avec la création du maillage de services.

## Maillage de service sur site HCX
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## Création de maillage de services sur site
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. Connectez-vous au client vSphere Web Client.
2. Dans le menu **Home**, sélectionnez l'option **HCX**.
3. Sous **Infrastructure**, cliquez sur **InterConnect**.
4. Sous **Multi-Site Service Mesh**, cliquez sur **Service Mesh**.
5. A partir de **Create Service Mesh**:
   1. Sélectionnez les sites : sur site et vCloud Organization, puis cliquez sur **Continue**. 
   2. Sélectionnez le profil de calcul source. 
   3. Sélectionnez le profil de calcul distant. Par exemple, CloudCompute.
   4. Sélectionnez All Services, puis cliquez sur **Continue**.
   5. Cliquez sur **Continue** sur la page Advanced Configuration - Override Uplink Network profiles (Optional)
   6. Cliquez sur **Continue**.
   7. Cliquez sur **Continue**, conserver les valeurs par défaut sur la page Advanced Configuration - Configure WAN Optimization Service Bandwidth Limit.
   8. Indiquez un nom de service, puis cliquez sur **Finish**.
6. Observez la liste des tâches de création de maillage de services. Vous devriez voir trois dispositifs HCX à l’emplacement sur site et trois à l’emplacement dans le cloud.

## Résultats
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

Un maillage de services HCX est la configuration efficace des services HCX pour un site source et un site de destination. Un maillage de services peut être ajouté à une paire de sites connectée ayant un profil de calcul valide créé sur les deux sites.

L'ajout d'un maillage de services lance le déploiement de dispositifs virtuels HCX Interconnect sur les deux sites. Un maillage de services d'interconnexion est toujours créé sur le site source.

## Extension du réseau
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## Processus d'extension d'un réseau
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

Pour étendre un réseau (VLAN ou VXLAN) avec HCX, suivez les étapes suivantes à partir de l'interface web vCenter côté client.

1. Connectez-vous au client vSphere Web Client.
2. Dans le menu **Home**, sélectionnez l'option **HCX**.
3. Dans le menu de gauche, sous **Services**, cliquez sur **Network Extension**.
4. Cliquez sur **Extend Network**:
   1. Sélectionnez le réseau à étendre. 
   2. Tapez la passerelle par défaut actuelle et le masque de sous-réseau au format CIDR.
   3. Cliquez sur **Stretch** au bas de l'écran pour lancer le flux d'extension du réseau.

La progression du réseau est surveillée dans le panneau des tâches du client vCenter.

## Concepts et pratiques recommandées pour l'extension du réseau
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

L'élément de jonction qui relie le réseau côté client au VXLAN côté cloud est un VPN multi-tunnel sophistiqué qui consiste en une technologie HCX propriétaire. Il n'est pas basé sur NSX, mais fonctionne avec NSX et étend ses capacités. Ce processus est contrôlé par l'interface utilisateur Web vCenter côté client et automatise le déploiement et l'affichage des points finaux côté client et côté cloud. La sélection du réseau à étendre se fait individuellement ou par lots.

En outre, dans le cadre du flux de travail de l'extension du réseau, NSX du côté cloud est autorisé à construire un VXLAN qui est ensuite connecté à une interface créée sur le périphérique L3 spécifié côté cloud (DLR ou ESG laissé dans un état non connecté) et le dispositif Network Extension côté cloud.

Généralement, lorsque vous migrez une application particulière, tous les réseaux utilisés par les machines virtuelles applicables doivent être étendus à l'ensemble de l'instance {{site.data.keyword.cloud}}.

Pourquoi généralement et pas toujours ? Il peut être avantageux de déconnecter certains trafics du côté client après la migration de la machine virtuelle. Par exemple, les clients de sauvegarde invités des machines virtuelles, qui peuvent entraîner une utilisation importante de la bande passante lorsqu'ils sont déplacés vers le cloud. Le client de sauvegarde invité n'est pas nécessaire lors de la migration de la machine virtuelle car il est automatiquement récupéré par une sauvegarde plus moderne au niveau du bloc côté cloud.

L'adaptateur réseau de sauvegarde du client n'est pas connecté car cela reviendrait à accéder à chaque machine virtuelle pour fermer le programme de sauvegarde du client invité. Par conséquent, si un réseau de sauvegarde est utilisé, la sauvegarde risque d'échouer. Il s'agit d'une situation temporaire jusqu'à ce que toutes les machines virtuelles puissent être atteintes après la migration pour désactiver le client de sauvegarde invité.

La bande passante d'une seule extension de réseau est théoriquement de 4 Gbit/s, mais cela peut être la limite pour tous les réseaux étendus au sein d'une seule paire d'extension de réseau et n'est pas réalisable avec un seul réseau étendu. Un seul réseau étendu peut atteindre environ 1 Gbits/s étant donné qu'il y a suffisamment de bande passante sous-jacente allouée et que la latence est faible (<~10 ms).

### Option de routage de proximité
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

Sans aucun type d'optimisation des routes, les réseaux étendus retournent vers le côté client pour tout accès L3. Ce phénomène de trombone introduit un modèle de trafic inefficace car les paquets doivent faire la navette entre le client (source) et le cloud, même dans les cas où les machines virtuelles source et de destination se trouvent dans le cloud. La fonction de routage de proximité du HCX a été conçue pour répondre à ce problème et à l'évacuation locale du trafic.

## Liens connexes
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [Glossaire des composants et des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Préparation de l'environnement d'installation](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Déploiement du client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Migrations de VMware Hybrid Cloud ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Paramètres et composants de surveillance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Traitement des incidents dans HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
