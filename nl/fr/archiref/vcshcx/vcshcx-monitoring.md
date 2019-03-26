---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Paramètres et composants de surveillance
{: #vcshcx-monitoring}

## Utilisation de l'optimiseur de réseau WAN pour la surveillance
{: #vcshcx-monitoring-using-wan}

Le dispositif d'optimisation de réseau WAN Silver Peak qui est déployé dans le cadre de HCX ne permet pas la configuration de son interface de gestion. L'interface utilisateur Web est un outil utile pour surveiller le débit du trafic et réguler l'utilisation de la bande passante de migration du réseau.

Seul le trafic de tunnel WAN de la passerelle CGW de HCX transite via le dispositif d'optimisation de réseau WAN. Par conséquent, il ne peut pas surveiller le trafic L2 étendu.
{:note}

### Configuration de l'interface utilisateur
{: #vcshcx-monitoring-config-ui}

Hormis la configuration d'une adresse IP pour l'interface utilisateur Web, ne modifiez pas la configuration de l'optimiseur de réseau WAN à moins d'y être invité par le personnel de support d'{{site.data.keyword.IBM}} ou de VMware.   

Pour configurer l'interface utilisateur Web de l'optimiseur de réseau WAN :
1.	Localisez la machine virtuelle de l'optimiseur de réseau WAN sur le client vCenter.
2.	Ouvrez une console dans la machine virtuelle qui utilise le client vCenter.
3.	Dans la console, cliquez sur **F4** pour configurer l'interface de gestion.
4.	Sélectionnez la configuration d'une adresse IP statique.
5.	Utilisez une adresse IP de la plage d'adresses IP portables assignées par {{site.data.keyword.cloud}} et la passerelle par défaut.
6.	Cliquez sur **Apply** sur la page suivante pour enregistrer vos données.
7.  Cliquez sur Edit settings pour la machine virtuelle de l'optimiseur de réseau WAN dans la console vCenter.
8.	Sélectionnez **Connected at Power On** et **Connected for Network Adapter 1**.
9.	Cliquez sur **OK** pour enregistrer.
10.	Localisez CGW-<xxx>-WANOPT dans vCenter.
11.	Editez les paramètres sur la machine virtuelle.
12.	Cliquez sur la case de connexion de l'adaptateur de réseau 1.
13.	Cliquez sur **OK**.
14.	Accédez à `https://<configured_WAN_OPT_IP>`.
15.	Connectez-vous avec l'utilisateur par défaut `admin` et le mot de passe `admin`.

Vous pouvez maintenant utiliser l'interface utilisateur Web de l'optimiseur de réseau WAN pour surveiller le débit, les taux de compression et pour définir les limitations de la bande passante.

### Régulation de la bande passante de migration
{: #vcshcx-monitoring-mig-bandwidth}

Avant de migrer les machines virtuelles, vous devez effectuer une évaluation de la liaison réseau utilisée. A l'aide des ingénieurs réseau, travaillez sur le réseau qui contient l'instance source de vSphere ou examinez l'utilisation hebdomadaire et mensuelle du trafic. Limitez la bande passante disponible pour les migrations si ce trafic passe à travers une liaison critique pour votre entreprise, surtout si cette liaison est inférieure à 1 Gbits/s. Utilisez le côté possédant une bande passante plus restreinte (généralement le côté client).

Utilisez cette procédure lorsque vous déployez les composants de flotte dans l'interface client HCX. Après le déploiement, vous devez aller dans l'interface utilisateur de l'optimiseur de réseau WAN.

Les modifications sont perdues si vous redéployez la passerelle CGW de HCX depuis l'interface Web HCX.
Ceci définit uniquement les limites de la bande passante pour le trafic de migration. Le trafic L2 étendu n'est pas affecté par cette configuration.
{:note}

1. Connectez-vous à l'interface utilisateur Web de l'optimiseur de réseau WAN. 
2. Dans l'onglet **Configuration**, sélectionnez **Shaper** dans le menu déroulant.
3. Dans la zone **Max bandwidth**, définissez la bande passante maximale disponible pour l'optimiseur de réseau WAN en kbits/s. Ne dépassez pas la bande passante maximale de la liaison WAN. Pour définir la valeur en mégabits par seconde, multipliez-la par 1 000. Pour définir la valeur en gigabits par seconde, multipliez-la par 1 000 000. La valeur par défaut est 10 gigabits par seconde (10 000 000 kilobits par seconde).
4. Cliquez sur **Apply**.

Pour la régulation de la bande passante L2 étendue, la QoS peut être utilisée pour UDP 500 et 4500 pour le trafic tunnel entre les dispositifs L2C.

## Surveillance des composants HCX
{: #vcshcx-monitoring-hcx-comp}

Pour surveiller les composants HCX, telles que les opérations de HCX Manager, de la passerelle cloud, de l'optimiseur de réseau WAN et du concentrateur de couche 2, procédez comme suit :

- Configurez HCX Manager pour envoyer des journaux à un serveur syslog. Utilisez l'utilitaire de gestion de HCX Manager pour exécuter la commande `https://<hcxhostname or
IP>:9443`.
- Configurez une commande ping vers une machine virtuelle migrée avant le basculement du réseau pour chaque réseau L2 étendu.
- Surveillez l'état de santé de la machine virtuelle du composant HCX à l'aide de l'outil VMware vRealize Operations Manager ou d'autres outils de surveillance des machines virtuelles VMware.

## Utilisation de la bande passante
{: #vcshcx-monitoring-band-use}

Utilisez les méthodes suivantes pour surveiller l'utilisation de la bande passante et la latence.

- La meilleure façon d'assurer le trafic vMotion est d'utiliser l'interface Web de l'optimiseur de réseau WAN. L'optimiseur de réseau WAN réduit drastiquement le trafic qui passe par le réseau WAN et réduit la perte de paquet en envoyant les paquets redondants. Il a été constaté que le rapport typique entre l'utilisation de bande passante d'un réseau LAN et d'un réseau WAN est d'environ 3:1 (350 Mbits/s LAN = 90-120Mbits/s WAN).

- La migration des machines virtuelles basée sur la réplication (migration en bloc) dans HCX entraîne le déplacement de machines virtuelles avec une mise à disposition de type "thick". Bien que cela ne soit pas souhaitable, l'interface utilisateur de l'optimiseur de réseau WAN révèle un rapport élevé entre le réseau LAN et le réseau WAN lorsque des données de disques inutilisées sont déplacées. Inversement, on observe que lorsque des données non compressibles sont migrées, comme les données de base de données et les médias numériques, l'utilisation du WAN est à son maximum et pratiquement égale à celle du LAN.

Remarques :
- La migration vMotion d'une machine virtuelle dans HCX ne génère pas davantage de débit que la mise en réseau vMotion pour un hôte ESXi. 
- Comme la migration en bloc peut avoir plusieurs migrations en cours simultanément, elle permet une utilisation de la bande passante plus élevée qu'une migration vMotion. Le rapport observé côté client avec des liaisons vMotion de 1 Gbits/s aux hôtes ESX était de : 8 réplications = utilisation de la bande passante de 1 vMotion.
- Le déplacement de l'espace vide sur le disque entraîne l'affichage d'une utilisation élevée du réseau LAN avec un rapport élevé et, par conséquent, une faible utilisation du réseau WAN. Notez que 1 Gbits/s semble être la limite. En effet, dans ce cas particulier, le réseau vMotion n'est capable que de 1 Gbits/s, ce qui est le goulot d'étranglement.
- Migration vMotion d'une base de données Oracle de plusieurs To. Avec une liaison WAN de 1 Gbits/s, la limitation est le réseau vMotion de 1 Gbits/s.

## Trafic L2 étendu
{: #vcshcx-monitoring-stretched-layer-2-traffic}

Le concentrateur de couche 2 du composant de flotte HCX a une limitation de bande passante d'environ 4 Gbits/s pour tout le trafic réseau L2 qui le traverse. Les réseaux étendus individuels ont une limite de bande passante d'environ 1 Gbits/s ou moins selon le type de trafic. Il est possible d'avoir plusieurs réseaux L2 étendus sur une seule paire L2C (maximum autorisé théorique de 4096 réseaux par paire L2C). Bien que le L2C soit conçu pour détecter et protéger les petits flux de trafic afin qu'ils ne soient pas surmontés par des flux importants au sein d'une même paire L2C, il peut être avantageux d'identifier si cette situation se produit et d'augmenter le nombre de L2C pour augmenter la capacité globale de bande passante.

Le déploiement de plusieurs L2C peut également être avantageux lorsqu'il existe plusieurs chemins d'accès entre le site du client et {{site.data.keyword.cloud}}, comme une liaison directe et Internet. On ne peut pas rendre un seul réseau redondant ou lui donner une bande passante accrue sur plusieurs paires L2C.

Surveillez le trafic sur toutes les interfaces qui utilisent l'onglet Monitoring de la machine virtuelle L2C. Si le débit de données total approche 8 Gbits/s (4 Gbits/s en entrée/sortie), pensez à ajouter une autre paire L2 et redistribuez les réseaux étendus pour rééquilibrer.

## Liens connexes
{: #vcshcx-monitoring-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
