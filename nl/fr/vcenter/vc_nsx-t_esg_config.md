---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuration du réseau en vue d'utiliser la passerelle NSX-T ESG gérée par le client avec vos machines virtuelles
{: #vc_nsx-t_esg_config}

Configurez le réseau pour vos machines virtuelles de manière à tirer parti de la passerelle VMware NSX-T ESG (Edge Services Gateway) déployée dans vos instances VMware vCenter Server. Pour plus d'informations sur les mesures de sécurité mises en place afin de réduire les risques en matière de sécurité, voir [La passerelle NSX Edge des services de gestion présente-t-elle un risque pour la sécurité ?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T est une plateforme de virtualisation de réseau qui permet de virtualiser des réseaux isolés et qui fournit plusieurs services de
mise en réseau, tels que des commutateurs, des routages et des pare-feu. Pour plus d'informations sur NSX, voir [Présentation de NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Dans le cadre du processus de commande de votre instance vCenter Server with NSX-T, les actions suivantes sont effectuées pour vous :
* Commande d'un sous-réseau client privé pour permettre à vos machines virtuelles d'accéder au réseau privé d'infrastructure {{site.data.keyword.cloud}}.
* Commande d'un sous-réseau client public pour permettre à vos machines virtuelles d'accéder à Internet.
* Déploiement et configuration de NSX-T dans votre instance vCenter Server with NSX-T.
* Déploiement d'un exemple de commutateur logique NSX-T à l'usage des machines virtuelles des charges de travail client.
* Déploiement d'un exemple de routeur logique distribué (DLR) NSX-T pour éventuelle communication d'est en ouest entre des charges de travail locales connectées à des réseaux de la couche 2 (L2).
* Déploiement et configuration d'un dispositif NSX-T Edge pour la conversion des adresses réseau de la plage d'adresses IP du commutateur logique de charge de travail en une adresse IP publique sur les règles de conversion d'adresses réseau.

  NSX-T Edge n'est pas déployé pour les instances qui sont privées uniquement. {:note}

## Procédure de configuration des paramètres réseau pour vos machines virtuelles
{: #vc_nsx-t_esg_config-procedure-config-networking}

Pour profiter des avantages de NSX-T sur vos machines virtuelles de charge de travail, vous devez configurer un certain nombre de paramètres, comme suit, lorsque vous créez vos machines virtuelles :

1. Définissez l'adaptateur de réseau de la machine virtuelle sur le commutateur logique de la charge de travail :
   1. Dans la boîte de dialogue **New Virtual Machine**, cliquez sur l'onglet **Customize Hardware**.
   2. Dans le menu **new device**, sélectionnez **Network**, puis cliquez sur **Add**.
   3. Sur l'adaptateur de réseau que vous venez d'ajouter, sélectionnez le commutateur logique de la charge de travail dans le menu. Exemple de nom de commutateur logique de charge de travail :
   **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   Veillez à ne pas sélectionner le commutateur **Workload Transit**.
   {:important}

2. Identifiez une adresse IP disponible pour la machine virtuelle :
   *  L'adresse IP doit se trouver dans la plage `192.168.10.0/24`. Notez que l'adresse IP `192.168.10.1` est réservée (voir **Etape 3**).
   *  Lorsque vous configurez la mise en réseau du système d'exploitation qui s'exécute sur la machine virtuelle, utilisez l'adresse IP sélectionnée et le masque de réseau
   `255.255.255.0`.

   Vous êtes responsable de la gestion de la plage des adresses IP que vous affectez à vos machines virtuelles.
   {:note}

3. Affectez la passerelle par défaut de la machine virtuelle avec `192.168.10.1`. Cette adresse IP est celle de NSX DLR sur le même commutateur logique que les machines virtuelles de la charge de travail.

## Procédure d'activation de la règle SNAT
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

Si vous voulez que vos machines virtuelles de charge de travail bénéficient d'un accès sortant à Internet, vous devez activer la règle de conversion d'adresses réseau source (SNAT) associée. L'activation de la règle SNAT permet de convertir l'accès à Internet depuis vos machines virtuelles en une seule adresse IP publique. Effectuez les opérations suivantes sur le client VMware vSphere Web Client :

1. Cliquez sur **Home > Networking & Security**.
2. Dans le volet de navigation, cliquez sur **NSX Edges**, puis cliquez deux fois sur le serveur de périphérie nommé **customer-nsx-edge**.
3. Cliquez sur **Management > NAT** pour ouvrir l'onglet **NAT**.
4. Sélectionnez dans la table la règle de conversion d'adresses réseau source par défaut, puis cliquez sur la coche verte au-dessus de la table pour activer la règle.

Pour plus d'informations sur les règles de conversion d'adresses réseau source de NSX-T Edge, voir [Gestion des règles de conversion d'adresses réseau](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Procédure d'identification des détails des sous-réseaux client
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

Etant donné que le serveur de périphérie **customer-nsx-edge** est conçu pour votre usage exclusif, vous pouvez le modifier afin de définir d'autres règles de conversion d'adresses réseau pour le trafic entrant ou sortant. Ces règles doivent utiliser uniquement les adresses IP des sous-réseaux client publics ou privés commandés pour vous.

Pour identifier les détails des sous-réseaux client de manière à pouvoir utiliser les adresses IP commandées, effectuez les opérations suivantes dans le client Web VMware vSphere :

1. Cliquez sur **Home > Networking & Security**.
2. Dans le volet de navigation, cliquez sur **NSX Edges**, puis localisez **customer-nsx-edge edge** dans la liste de serveurs de périphérie sur la droite. 
3. Dans la colonne **Description**, passez en revue la description du serveur de périphérie **customer-nsx-edge** pour voir les identificateurs de sous-réseau à la fois pour les sous-réseaux client privés et publics.

Vous trouverez d'autres détails concernant les sous-réseau client en effectuant les opérations suivantes dans le portail	{{site.data.keyword.slportal}} :

1. Cliquez sur **Networking > IP Management > Subnets**.
2. Cliquez sur le menu de filtre et, dans la zone Subnet, entrez l'identificateur tel qu'indiqué dans la description du serveur de périphérie **customer-nsx-edge** sur l'onglet **Summary** dans le client Web VMware vSphere.
3. Passez en revue les remarques affichées pour les adresses IP. Ces remarques identifient les sous-réseaux et adresses IP commandés et utilisés au cours de la configuration initiale.

   N'utilisez pas les adresses IP commandées et utilisées au cours de la configuration initiale. Toutefois, vous pouvez, au besoin, utiliser d'autres adresses IP sur ces sous-réseaux. Pour définir des règles de conversion d'adresses réseau supplémentaires, voir [Gestion des règles de conversion d'adresses réseau](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Liens connexes
{: #vc_nsx-t_esg_config-related}

* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Passerelle NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
