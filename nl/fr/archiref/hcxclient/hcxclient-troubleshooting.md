---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Traitement des incidents dans HCX
{: #hcxclient-troubleshooting}

Passez en revue les points suivants pour connaître les principaux problèmes et corrections de HCX.

## Problèmes au niveau de l'interface utilisateur du client HCX
{: #hcxclient-troubleshooting-hcx-client-issues}

### Expiration du jeton de l'interface utilisateur de HCX
{: #hcxclient-troubleshooting-hcx-ui-issues}

Généralement, si l'interface utilisateur de vCenter est restée ouverte pendant un certain temps, il est possible qu'un dépassement du délai d'attente se produise dans l'interface utilisateur de HCX. Cela est dû au fait que le jeton de connexion au serveur de gestion HCX est arrivé à expiration. Sortez de l'interface utilisateur web de vSphere et retournez-y pour actualiser le jeton.

### Affichage de “NaN” dans l'interface utilisateur du client HCX pour toutes les métriques sur l'écran du tableau de bord
{: #hcxclient-troubleshooting-nan-display}

Ce problème est lié aux droits du compte vCenter actuellement connecté. Assurez-vous que le groupe Administrateur d'entreprise est défini dans l'interface utilisateur du gestionnaire de dispositif côté cloud.

## Problèmes de migration
{: #hcxclient-troubleshooting-mig-issues}

Les problèmes de migration des versions actuelles de HCX entrent généralement dans trois catégories : licences, connectivité réseau de la passerelle cloud et compatibilité matérielle de destination.

### Octroi de licence
{: #hcxclient-troubleshooting-licensing}

Si une migration échoue à cause d'un problème de licence, les versions actuelles de HCX affichent clairement ce problème dans le message d'erreur avec l'interface Web du client dans l'interface de vCenter.

### Connectivité au réseau (WAN)
{: #hcxclient-troubleshooting-wan-connect}

En cas de problème de connectivité avec le réseau WAN, vérifiez toujours le statut du tunnel dans l'écran **Interconnect -> HCX Components** de l'interface utilisateur de HCX. Les composants de la flotte n'ont généralement pas besoin d'être réinitialisés ou redémarrés. Si la connectivité WAN est rétablie, ils se reconnectent automatiquement.

Si des correctifs et des mises à jour ont été appliqués aux gestionnaires HCX (client et cloud) et que ces mises à jour corrigent également des problèmes au niveau des composants de la flotte, vous devez redéployer la passerelle Cloud Gateway et tous les L2Cs déployés. Il est possible d'effectuer un débogage supplémentaire du statut du tunnel, en se connectant au gestionnaire HCX via un client SSH tel que ccli  

1. Accédez via SSH au gestionnaire HCX en utilisant le compte administrateur et le mot de passe fourni.
2. Exécutez la commande `su –` et entrez le mot de passe de l'utilisateur `root` (identique au mot de passe administrateur) pour passer au mode superutilisateur.
3. Accédez à `/opt/vmware/bin` et exécutez la commande `./ccli`. Si cette tentative échoue car l'environnement n'est pas configuré pour un superutilisateur, exécutez la commande `./ccliSetup.pl`.
4. Exécutez la commande `list` dans l'interpréteur de commandes `ccli` pour répertorier les composants de flotte enregistrés auprès du gestionnaire HCX.
5. Spécifiez l'ID de flotte de l'interface `ccli` en tapant l'ID indiqué pour le composant de flotte. Par exemple, `go 8`.
6. Exécutez la commande `debug remoteaccess enable` pour vous connecter au composant de flotte souhaité via SSH.
7. Quittez l'interface `ccli` et connectez-vous via SSH à l'adresse IP du composant de flotte activé pour SSH.
9. Poursuivez le traitement des incidents.
10. Retournez à l'interface `ccli` et désactivez le service `ssh` pour le composant.
11. Si nécessaire, utilisez la commande ccli `hc` pour exécuter un bilan de santé sur les composants.

## Problèmes de compatibilité du matériel de destination
{: #hcxclient-troubleshooting-hw-compatibility}

La migration vMotion peut constituer un problème lorsque la source côté client appartient à une version matérielle et à version vSphere plus récentes que le cloud. Puisque la migration basée sur la réplication copie les données vers une machine virtuelle de fabrication récente du côté de la destination, changer le type de migration à "Migration en bloc" devrait permettre à la migration de réussir dans la plupart des cas.

## Problèmes liés au concentrateur L2 étendu
{: #hcxclient-troubleshooting-stretched-l2}

Très peu de problèmes liés au fonctionnement du concentrateur L2 ont été recensés. Comme pour la passerelle CGW, si le L2C perd sa connectivité, il se reconnecte automatiquement une fois que la connectivité réseau est rétablie. Utilisez l'interpréteur de commande ccli pour vérifier l'intégrité et le fonctionnement. Après avoir activé SSH et connecté le concentrateur L2, exécutez les commandes `ip tunnel` et `ip link |grep t_` pour afficher le statut des tunnels.

## Liens connexes
{: #hcxclient-troubleshooting-related}

* [Glossaire des composants et des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Préparation de l'environnement d'installation](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Déploiement du client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Maillage de services sur site HCX ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrations de VMware Hybrid Cloud ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Paramètres et composants de surveillance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
