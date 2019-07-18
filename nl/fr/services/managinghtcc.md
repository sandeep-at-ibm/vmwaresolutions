---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion de HyTrust CloudControl on IBM Cloud
{: #managinghtcc}

Pour gérer le service HyTrust CloudControl on {{site.data.keyword.cloud}} (HTCC), accédez à l'interface graphique Web HTCC à partir de la console {{site.data.keyword.vmwaresolutions_short}} ou accédez à la console HTCC à partir du client Web vSphere.

## Accès à l'interface graphique Web HyTrust CloudControl à partir de la console IBM Cloud for VMware Solutions
{: #managinghtcc-accessing-webgui}

Connectez-vous à l'interface graphique Web du dispositif HTCC principal ou secondaire, utilisez les données d'identification de l'interface graphique Web qui figurent sur la page des détails du service HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

## Accès à la console HyTrust CloudControl à partir du client Web vSphere
{: #managinghtcc-accessing-console}

Pour accéder à la console HTCC à partir du client Web vSphere, procédez comme suit :
1. Dans le client Web vSphere, localisez les machines virtuelles nommées **CC1** et **CC2**.
2. Cliquez avec le bouton droit de la souris sur **CC1** ou **CC2**, puis cliquez sur **Ouvrir la console**.
3. Connectez-vous à la console à l'aide des données d'identification de console qui figurent sur la page des détails du service HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir [Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Activation de l'accès Internet pour les VM HyTrust CloudControl
{: #managinghtcc-internet-access}

Pour HTCC 5.5.1 et versions ultérieures, {{site.data.keyword.vmwaresolutions_short}} prend désormais en charge le renouvellement automatique des licences HyTrust pour lesquelles la fonctionnalité Call Home est activée. Pour les instances de vCenter Server qui ne sont pas uniquement privées, HTCC est déployé avec des règles de pare-feu et SNAT définies sur les services de gestion ESG **mgmt-nsx-edge**.

Ces règles vous permettent d'activer l'accès Internet pour les machines virtuelles HyTrust. Si l'accès à Internet n'est pas activé, la licence appliquée à votre installation HTCC expire au bout d'un an.

Pour les environnements vCenter Server exclusivement privés, la passerelle VMware NSX ESG (Edge Services Gateway) **mgmt-nsx-edge** n'est pas ajoutée ; les règles de pare-feu et SNAT ne sont donc pas définies. Par conséquent, la connectivité Internet ne peut pas être activée pour les instances privées uniquement et les licences HyTrust expirent chaque année.
{:note}

### Procédure de recherche des règles de pare-feu et SNAT définies
{: #managinghtcc-proc-find-firewall}

1. Connectez-vous au client VMware vSphere Web Client (FLEX) et recherchez la passerelle ESG **mgmt-nsx-edge**.
2. Cliquez sur **Home > Networking & Security > NSX Edges**.
3. Cliquez deux fois sur la passerelle ESG **mgmt-nsx-edge** et cliquez sur l'onglet **Manage**.
4. Accédez à l'onglet **Firewall** et recherchez les règles HyTrust. Notez les adresses IP source. Il s'agit des adresses IP des machines virtuelles (VM) HyTrust.
5. Accédez à l'onglet **NAT** et recherchez les règles SNAT créées pour les VM HyTrust. Les adresses IP source correspondent aux adresses IP que vous avez notées à l'étape précédente.

### Procédure d'activation de la connectivité Internet pour HTCC
{: #managinghtcc-enable-internet}

Les étapes suivantes s'appliquent à la mise à jour des paramètres réseau HTCC sur la machine virtuelle (VM) principale, utilisée pour les mises à niveau de licence. Il est inutile de mettre à jour les paramètres de la machine virtuelle secondaire.
{:note}

1. Effectuez les étapes 1 à 3 de la procédure précédente.
2. Cliquez sur **Paramètres**, puis sur **Interfaces**. Notez l'adresse IP de la liaison montante privée, qui devient la nouvelle passerelle par défaut.
3. Accédez à la page de détails du service HyTrust CloudControl sur IBM Cloud, cliquez sur **Afficher l'interface utilisateur Web HTCC** et connectez-vous avec les données d'identification de la page des détails du service.
4. Notez la passerelle par défaut existante. Par exemple, pour HTCC 5.5.1, cliquez sur **Configuration > Réseau**. Notez l'adresse IP de la passerelle répertoriée, qui devient la passerelle de la route statique.
5. Ajoutez une route statique. Par exemple, pour HTCC 5.5.1, cliquez sur **Configuration > Routes statiques**. Cliquez sur **Aouter**, entrez les informations suivantes et cliquez sur **OK**.

  ```
  Network Address: 10.0.0.0
  Mask: 255.0.0.0
  Gateway: IP noted in step 4
  Device: Network 1
  ```

6. Modifiez la passerelle par défaut. Par exemple, pour HTCC 5.5.1, cliquez sur **Configuration > Réseau** et remplacez l'adresse IP dans la zone **Passerelle** par celle que vous avez notée à l'étape 3, puis cliquez sur **Sauvegarder**. 

  Assurez-vous de définir la route statique avant de modifier la passerelle par défaut, sinon la console Web pourrait devenir inaccessible.
  {:important}

  La machine virtuelle principale a désormais accès à Internet.

7. Pour confirmer que la machine virtuelle principale a un accès Internet, exécutez une commande `wget` sur une adresse IP publique ou un site Web. Pour ce faire, revenez dans vCenter et cliquez avec le bouton droit de la souris sur **CC1 > Open Console**. Connectez-vous à la console à l'aide des données d'identification de console qui figurent sur la page des détails du service HyTrust CloudControl on IBM Cloud. Exécutez une commande `wget` telle que `wget www.ibm.com` ; vous devriez obtenir une réponse immédiate. Vérifiez que la demande a été envoyée et qu'une réponse `200` a été reçue. 

## Liens connexes
{: #managinghtcc-related}

* [Présentation de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web HyTrust](https://www.hytrust.com/){:external}
