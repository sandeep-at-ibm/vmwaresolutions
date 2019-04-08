---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


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
* Déploiement d'un exemple de routeur NSX-T de niveau 1 pour éventuelle communication d'est en ouest entre des charges de travail locales connectées à des réseaux de la couche 2 (L2).
* Déploiement et configuration d'un dispositif NSX-T Edge pour la conversion des adresses réseau de la plage d'adresses IP du commutateur logique de charge de travail en une adresse IP publique sur les règles de conversion d'adresses réseau.

  NSX-T Edge n'est pas déployé pour les instances qui sont privées uniquement.
  {:note}

## Procédure de configuration des paramètres réseau pour vos machines virtuelles
{: #vc_nsx-t_esg_config-procedure-config-networking}

Pour profiter des avantages de NSX-T sur vos machines virtuelles de charge de travail, vous devez configurer un certain nombre de paramètres, comme suit, lorsque vous créez vos machines virtuelles :

1. Définissez l'adaptateur de réseau de la machine virtuelle sur le commutateur logique de la charge de travail :
   1. Dans la boîte de dialogue **New Virtual Machine**, cliquez sur l'onglet **Customize Hardware**.
   2. Dans le menu **new device**, sélectionnez **Network**, puis cliquez sur **Add**.
   3. Sur l'adaptateur de réseau que vous venez d'ajouter, sélectionnez le commutateur logique de réseau dissocié de la charge de travail dans le menu. L'exemple de nom de commutateur est **overlay-ls**.

   Veillez à ne pas sélectionner le commutateur **Workload Transit**.
   {:important}

2. Identifiez une adresse IP disponible pour la machine virtuelle :
   *  L'adresse IP doit se trouver dans la plage `192.168.10.0/24`. Notez que l'adresse IP `192.168.10.1` est réservée (voir **Etape 3**).
   *  Lorsque vous configurez la mise en réseau du système d'exploitation qui s'exécute sur la machine virtuelle, utilisez l'adresse IP sélectionnée et le masque de réseau
   `255.255.255.0`.

   Vous êtes responsable de la gestion de la plage des adresses IP que vous affectez à vos machines virtuelles.
   {:note}

3. Affectez la passerelle par défaut de la machine virtuelle avec `192.168.10.1`. Il s'agit de l'adresse IP du port du routeur de liaison descendante sur le routeur logique de niveau 1 du client connecté sur même commutateur logique de réseau dissocié que les machines virtuelles de la charge de travail.

## Activation de la règle SNAT
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

NSX-T active par défaut la règle SNAT. Pour plus d'informations sur la modification de règles existantes, voir [Configuration d'une règle NAT et de destination sur in routeur logique de niveau 0](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}.

## Procédure d'identification des détails des sous-réseaux client
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

Etant donné que les routeurs logiques **Customer-T1-LR** et **Customer-T0-LR** ainsi que les serveurs Edge **cust-nsx-edge0** et **cust-nsx-edge1** sont conçus pour votre usage exclusif, vous pouvez les modifier afin de définir d'autres règles de conversion d'adresses réseau (NAT) pour le trafic entrant ou sortant. Ces règles doivent utiliser uniquement les adresses IP des sous-réseaux client publics ou privés commandés pour vous.

Pour identifier les détails des sous-réseaux client de manière à pouvoir utiliser les adresses IP commandées, effectuez les opérations suivantes dans le client Web NSX-T :

1. Cliquez sur l'onglet **Advanced Networking & Security**.
2. Dans le volet gauche, cliquez sur **Fabric**, puis dans la liste déroulante, sélectionnez **Nodes**.
3. Dans l'onglet, sélectionnez **Edge Transport Nodes**.
4. Cliquez sur les serveurs Edge du client. Par exemple, **cust-nsx-edge0**. Les sous-réseaux client public et privé s'affichent dans la zone **Description**.

Vous trouverez d'autres détails concernant les sous-réseaux client en effectuant les opérations suivantes dans le portail	{{site.data.keyword.slportal}} :

1. Cliquez sur **Networking > IP Management > Subnets**.
2. Cliquez sur le menu de filtre et, dans la zone **Subnet**, entrez l'identificateur tel qu'indiqué dans la description du serveur Edge **customer-nsx-edge0** dans le client Web NSX-T.
3. Passez en revue les remarques affichées pour les adresses IP. Ces remarques identifient les sous-réseaux et adresses IP commandés et utilisés au cours de la configuration initiale.

   N'utilisez pas les adresses IP commandées et utilisées au cours de la configuration initiale. Toutefois, vous pouvez, au besoin, utiliser d'autres adresses IP sur ces sous-réseaux. Pour définir des règles de conversion d'adresses réseau supplémentaires, voir [Gestion des règles de conversion d'adresses réseau](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Liens connexes
{: #vc_nsx-t_esg_config-related}

* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Passerelle NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
