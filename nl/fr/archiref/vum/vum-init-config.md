---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

# Configuration initiale
{: #vum-init-config}

L'automatisation {{site.data.keyword.vmwaresolutions_full}} configure le dispositif VCSA avec une passerelle par défaut définie sur le routeur BCR (Backend Customer Router) d'{{site.data.keyword.cloud}}. Cependant, il n'y a pas de route vers Internet via le routeur BCR. La route standard vers Internet à partir de l'instance VMware vCenter Server on {{site.data.keyword.cloud_notm}} passe par la passerelle Management ESG. Comme il n'est pas recommandé de modifier la configuration du dispositif VCSA ou Management ESG, l'implémentation d'un serveur proxy sur le sous-réseau du client est recommandée pour activer VUM.

Cette approche signifie que vous n'avez pas à reconfigurer les dispositifs VCSA ou Management ESG. Cependant, une machine virtuelle ou un dispositif de petite taille doit être installé. Un serveur proxy est un système, installé entre deux unités de noeud final qui fait office d'unité intermédiaire. Dans ce cas, il est placé entre VUM et les serveurs de mises à jour dans VMware.

Lorsque VUM demande une ressource du serveur de mises à jour dans VMware, la demande est d'abord envoyée au serveur proxy qui l'envoie ensuite au serveur de mises à jour. Une fois que le serveur proxy obtient la ressource, il l'envoie à VUM. Un serveur proxy peut être utilisé pour faciliter la sécurité, les contrôles administratifs et les services de mise en cache.

Vous pouvez utiliser un serveur proxy basé sur CentOS et Squid. Le proxy Squid est un proxy de mise en cache open source pour le Web. Il prend en charge de nombreux protocoles, notamment HTTP et HTTPS. Il existe un certain nombre de proxys basés sur les machines virtuelles et les dispositifs accessibles et vous devez sélectionner celui qui vous convient en fonction des exigences de votre entreprise, puis effectuer l'installation et la configuration selon les conseils du fournisseur. Les clients qui optent pour l'utilisation d'une implémentation de type CentOS/Squid doivent suivre la procédure ci-dessous.

* Télécharger CentOS ISO sur un serveur intermédiaire
* Créer une bibliothèque vCenter
* Transférer ISO sur la bibliothèque vCenter
* Créer une machine virtuelle, installer et configurer CentOS, puis installer Squid

## Recherche de l'information de sous-réseau
{: #vum-init-config-subnet}

Avant de commencer cette tâche, recueillez les informations pour remplir le tableau suivant. Examinez les valeurs suggérées et assurez-vous qu'elles conviennent à votre environnement. Cette configuration est basée sur un proxy de petite taille conçu uniquement pour VUM et utilisant CentOS-Minimal et Squid.

Pour trouver le sous-réseau portable privé du client :

1. Accédez à la page **Ressources** dans la console {{site.data.keyword.vmwaresolutions_short}}.
2. Sélectionnez l'**instance** requise, sélectionnez **Infrastructure** puis le **cluster** requis.
3. Sélectionnez **VLAN privé** et localisez le sous-réseau indiquant `Private subnet for customer workload edge`.
4. Sélectionnez le **sous-réseau** et vous serez redirigé vers la page des détails du sous-réseau qui affiche les adresses IP et leurs affectations.
5. A l'aide de ces informations, sélectionnez une adresse IP non affectée et mettez à jour la **remarque** avec les commentaires correspondants. Utilisez cette adresse IP pour le paramètre `proxy ip` dans le tableau suivant.

Tableau 1. Valeurs de déploiement

| Paramètre | Valeurs suggérées | Remarques |
|:--------- |:-------------- |:------ |
| UC du proxy | 1 vCPU | Squid n'a pas de configuration requise minimale |
| Mémoire RAM du proxy | 2 Go | Squid n'a pas de configuration requise minimale |
| Disque du proxy | 25 | Squid n'a pas de configuration requise minimale |
| Nom d'hôte | Proxy01 | |
| Adresse | IP proxy | Une Adresse IP de secours doit être utilisée à partir du sous-réseau portable privé du client affectée lors du processus de mise à disposition. Seules deux adresses IP ont été réservées sur ce sous-réseau ; l'une pour le routeur BCR et l'autre pour le dispositif ESG du client (customer-esg)
| Masque de réseau | 255.255.255.192 | |
| Passerelle| Adresse IP de la liaison montante privée customer-nsx-edge | Il s'agit du paramètre de passerelle par défaut pour le serveur proxy, qui correspond à l'adresse IP de la liaison montante privée de customer-nsx-edge. L'adresse IP peut être obtenue en consultant l'onglet **Paramètres** pour **customer-nsx-edge**. |
| Serveur DNS | Adresse IP AD/DNS | Cette adresse IP peut être obtenue sur la page **Ressources** dans la console {{site.data.keyword.vmwaresolutions_short}}. |
| IP BCR | Adresse IP du routeur BCR | Il s'agit de l'adresse IP du routeur BCR (Backend Customer Router) d'{{site.data.keyword.cloud_notm}} qui est la passerelle pour 10.0.0.0/8 et 161.26.0.0/16. Cette adresse est utilisée dans une route statique du serveur proxy pour que le dispositif VCSA et le serveur AD/DNS puissent y accéder. |

## Configuration de NSX
{: #vum-init-config-config-nsx}

Le pare-feu NSX ESG du client et les paramètres de conversion NAT sont requis pour activer le trafic du serveur proxy.

### Pare-feu
{: #vum-init-config-firewall}

1. Accédez à **Home** > **Networking & Security**.
2. Sélectionnez **NSX Edges**, customer-nsx-edge, puis **Firewall**.
3. Cliquez sur le symbole **+** et ajoutez une règle de pare-feu
4. Fournissez les paramètres requis comme indiqué dans le tableau suivant. La nouvelle règle de pare-feu doit s'insérer avant la dernière règle par défaut Deny.

Tableau 2. Règle de pare-feu

| Paramètre | Valeurs suggérées |
|:--------- |:-------------- |
| Nom | Proxy01 sortant |
| Type | Utilisateur |
| Source | IP du serveur proxy |
| Destination | N'importe laquelle |
| Service | HTTP/HTTPS/ICMP Echo |
| Action | Accepter |

Une fois les paramètres indiqués, cliquez sur **Publish Changes**.

### NAT
{: #vum-init-config-nat}

1. Sélectionnez **NAT**.
2. Cliquez sur le signe **+** et ajoutez une règle de conversion d'adresse réseau.
3. Fournissez les paramètres requis comme indiqué dans le tableau suivant et cliquez sur **OK**. Ensuite, cliquez sur **Publish Changes**.

Tableau 3. Règle de conversion d'adresse réseau

| Paramètre | Valeurs suggérées |
|:--------- |:-------------- |
| Type de règle | USER |
| Action | SNAT |
| Appliqué sur | Liaison montante publique |
| Protocole d'origine | N'importe lequel |
| Adresse IP source d'origine | IP du serveur proxy |
| Ports source d'origine | N'importe lequel |
| Adresse IP de destination d'origine | N'importe laquelle |
| Ports de destination d'origine | N'importe lequel |
| Adresse IP convertie | IP de conversion d'adresse réseau |
| Plage de ports convertie | N'importe laquelle |
| Statut | Activation |
| Journalisation | Activation |
| Description | SNAT Proxy01 |

### Installation et configuration d'un serveur proxy
{: #vum-init-config-inst-cfg-proxy}

Le processus suivant déploie une machine virtuelle pour héberger CentOS et Squid à partir de la bibliothèque de contenu et comprend les étapes suivantes. Il suppose que vous ayez Windows VSI mis à disposition pour servir de serveur intermédiaire et que vous utilisiez le protocole RDP (Remote Desktop Protocol) pour vous connecter à l'interface publique de VSI :

* Téléchargement du fichier CentOS-Minimal ISO
* Configuration d'une bibliothèque de contenu vCenter et remplissage avec le fichier CentOS ISO
* Configuration de la machine virtuelle du proxy et installation de CentOS et de Squid

### Téléchargement du fichier CentOS-Minimal ISO
{: #vum-init-config-downloading-centos}

Dans un navigateur sur votre serveur intermédiaire, téléchargez le fichier CentOS-Minimal ISO depuis [CentOS](https://www.centos.org/download/). Notez qu'{{site.data.keyword.cloud_notm}} conserve un miroir de nombreuses distributions Linux populaires. Ce miroir n'est disponible que sur le réseau privé et les fichiers CentOS ISO sont disponibles à l'adresse suivante : `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Configuration d'une bibliothèque de contenu et remplissage avec le fichier CentOS ISO
{: #vum-init-config-config-conent-library}

Créez une bibliothèque de contenu vCenter locale. La bibliothèque est accessible uniquement dans l'instance vCenter Server dans laquelle elle a été créée. Remplissez la bibliothèque avec les modèles et les fichiers ISO requis pour déployer des machines virtuelles.

1. Via le client vSphere Web Client, accédez à **Home** > **Content library** > **Objects** > **Create a new content library** > **Create subscribed library on the vCenter**.
2. Entrez un nom pour la bibliothèque de contenu, par exemple, ISO, et dans la zone de texte Notes, entrez sa description et cliquez sur **Next**.
3. Sélectionnez **Local content library** et cliquez sur **Next**.
4. Sélectionnez un magasin de données puis cliquez sur un magasin de données approprié, par exemple : `vsanDatastore`.
5. Passez en revue les informations sur la page **Ready to Complete** et cliquez sur **Finish**.

### Configuration de la machine virtuelle du proxy et installation de CentOS et Squid
{: #vum-init-config-config-proxy}

Cette activité comprend les tâches suivantes :

*	Création d'une nouvelle machine virtuelle
*	Installation de CentOS
*	Installation de Squid

#### Création d'une nouvelle machine virtuelle
{: #vum-init-config-create-new-vm}

Cette tâche permet de créer une machine virtuelle prête à l'emploi à utiliser comme serveur proxy. Les paramètres figurant dans le Tableau 1 - Valeurs de déploiement doivent être utilisés dans la configuration.

1.	Via le client vSphere Web Client, accédez à **Home** > **VMs and Templates**.
2.	Dans le volet de navigation, cliquez sur **datacenter1**, puis cliquez avec le bouton droit de la souris et sélectionnez **New Virtual Machine** > **New Virtual Machine**.
3.	Sélectionnez **Create a new Virtual Machine** et cliquez sur **Next**.
4.	Entrez un nom pour la machine virtuelle, par exemple, Proxy01, puis sélectionnez **datacenter1** et cliquez sur **Next**.
5.	Sélectionnez **cluster1** et cliquez sur **Next**.
6.	Sélectionnez un magasin de données approprié, par exemple, vsanDatastore, puis cliquez sur **Next** et à nouveau sur **Next**.
7.	Dans la zone **Guest OS Family**, sélectionnez **Linux** et dans la zone **Guest OS version**, sélectionnez **CentOS 7 (64-bit)** et cliquez sur **Next**.
8.	Sous l'onglet **Customized Hardware** de Virtual Hardware, définissez **CPU sur 1**, **Memory sur 2048 MB** et **New Hard disk sur 25 GB**. Sous **New CD/DVD drive**, sélectionnez **Content Library ISO File** puis **CentOS-7-x86_64-Minimal**, cliquez sur **OK** puis cochez la case **Connected**.
9.	Dans la zone New device, sélectionnez **Network** et cliquez sur **Add**.
10.	Sélectionnez le réseau **SDDC-DPortGroup-Mgmt** et vérifiez que la case Connect est cochée avant de cliquer sur **Next**.
11.	Vérifiez et cliquez sur **Finish**.

#### Installation de CentOS
{: #vum-init-config-install-centos}

Cette tâche permet d'installer et de configurer la machine virtuelle qui vient d'être créée pour qu'elle soit prête pour l'installation de Squid

1.	Dans le volet de navigation de vSphere Web Client, sélectionnez la **machine virtuelle** que vous venez de créer, Proxy01, puis sélectionnez l'onglet **Summary**.
2.	Cliquez sur le bouton **"Play"** pour mettre sous tension la machine virtuelle.
3.	La machine virtuelle se met sous tension et démarre à partir de l'image ISO CentOS 7. Démarrez soit une **console distante ou une console Web** sur la machine virtuelle. Vous devez installer la console distante et le système qui exécute le navigateur doit résoudre les hôtes vSphere ESXi par nom.
4.	Dans l'écran de bienvenue de CentOS 7, sélectionnez la langue requise et cliquez sur **Continue**.
5.	Dans l'écran **LOCALIZATION**, cliquez sur **DATE & TIME** et sélectionnez votre fuseau horaire, puis cliquez sur **Done**.
6.	Dans l'écran **LOCALIZATION**, cliquez sur **KEYBOARD** pour modifier la valeur par défaut si nécessaire, puis cliquez sur **Done**.
7.	Dans l'écran **LOCALIZATION**, cliquez sur **INSTALLATION DESTINATION**, cliquez sur l'**icône du disque virtuel VMware**, puis sur **Done**.
8.	Dans l'écran **LOCALIZATION**, cliquez sur **NETWORK & HOSTNAME**, remplacez le nom d'hôte par le nom d'hôte de votre choix, par exemple, Proxy01.
9.	Cliquez sur **Configure**, puis sur **IPv4 Settings**. Dans la zone **Method**, sélectionnez **Manual**.
10.	En utilisant le bouton **Add**, insérez une _adresse et un masque de réseau_, ainsi qu'une _passerelle_ à partir du _Tableau 1 – Valeurs de déploiement_.
11.	Entrez l'_adresse IP du serveur DNS_ indiqué dans le Tableau 1 – Valeurs de déploiement.
12.	Cliquez sur le bouton **Routes** et ajoutez les routes statiques suivantes : _10.0.0.0/8 et 161.26.0.0/16_ avec une adresse IP de passerelle correspondant à l'_adresse IP BCR_ du Tableau 1 Valeurs de déploiement, comme passerelle. Cette route statique permet au serveur proxy d'accéder au serveur DNS.
13.	Cliquez sur **Save** et vérifiez que l'interface Ethernet est activée (On) et qu'elle est à l'état connecté. Cliquez sur **Done** et **Begin Installation**.
14.	Au cours du processus d'installation, définissez un mot de passe root et configurez un utilisateur.
15.	Une fois l'installation terminée, connectez-vous en tant qu'utilisateur, puis entrez la commande _ping vmware.com_. Le nom est résolu avec une adresse IP et vous obtenez une réponse. Si vous n'obtenez pas de réponse, vérifiez les adresses IP, les règles de pare-feu et les paramètres NAT.

#### Installation et configuration de Squid
{: #vum-init-config-install-cfg-squid}

Squid n'a pas de configuration matérielle requise minimale mais la quantité de mémoire RAM peut varier en fonction des utilisateurs qui accèdent à Internet via votre proxy et des objets stockés en mémoire cache. Comme le serveur proxy n'est accessible que par VUM et que le cache n'est pas activé, une seule machine virtuelle de petite taille a été configurée.

1. A l'aide de la console Web ou de la console distante de vSphere Web Client, connectez-vous au serveur proxy en tant qu'utilisateur, puis exécutez `su` avec le mot de passe root.
2. Avant d'installer des modules, vous devez utiliser la commande suivante pour mettre à jour le système et les modules :
  `yum -y update`

3. Pour installer Squid, vous devez installer le référentiel EPEL sur le système car Squid n'est pas disponible dans le référentiel yum par défaut. Exécutez la commande suivante pour installer le référentiel EPEL :
  `yum -y install epel-release`

4. Effectuez une mise à jour et un nettoyage à l'aide des commandes suivantes :

  `yum -y update`
  `yum clean all`

5. Squid est installé à l'aide de la commande suivante : `yum -y install squid`.
6. Dès qu'il est installé, démarrez immédiatement Squid à l'aide de la commande suivante : `systemctl start squid`.
7. Pour lancer Squid automatiquement au démarrage, exécutez la commande suivante : `systemctl enable squid`.
8. Pour vérifier que Squid est opérationnel, exécutez la commande suivante : `systemctl status squid`.
9. Le pare-feu de CentOS nécessite d'autoriser l'accès au port de Squid, TCP 3128, à l'aide de la commande suivante :  `firewall-cmd –add-port=3128/tcp –permanent`.
10. Pour sauvegarder la règle et redémarrer le service, utilisez la commande suivante : `firewall-cmd –reload`.

## Configuration initiale de VUM
{: #vum-init-config-init-setup-vum}

Configurez VUM pour utiliser le serveur proxy afin d'accéder aux référentiels sur Internet.
1. A l'aide du client vSphere Web Client, accédez à **Home** > **Update Manager**. Cliquez sur votre vCenter Server.
2. Sélectionnez l'onglet **Manage** et cliquez sur **Settings**.
3. Sélectionnez **Download Settings**, puis sous _Proxy settings_, cliquez sur **Edit**.
4. Cochez la case **Use Proxy** et entrez l'_adresse IP du serveur proxy_ et le _port 3128_, puis cliquez sur **OK**. La zone Connectivity Status passe à _Validating_ puis à _Connected_.
    **Remarque** : ne vous inquiétez pas si vous recevez le message ``Some URLs have been accessed successfully, but others are inaccessible`` pendant le test de la connexion au serveur proxy.
5. Cliquez sur **Download Now**. Dans le panneau _Recent Tasks_, vous devez voir que cette activité est terminée.
6. Si cette activité échoue, redémarrez le dispositif vCSA (vCenter Server Appliance) :
  1. Connectez-vous à l'interface de gestion vCSA à l'adresse `https://vcsaFQDN:5480` en tant que **superutilisateur**.
  2. Cliquez sur **Summary** et sur **Reboot**.
  3. Dans la fenêtre de confirmation, cliquez sur **Yes** pour confirmer l'opération.

## Liens connexes
{: #vum-init-config-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (démonstrations)
