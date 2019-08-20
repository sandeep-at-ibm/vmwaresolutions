---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: HTDC WebGUI, HTDC console, enable internet HTDC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion de HyTrust DataControl on IBM Cloud
{: #managinghtdc}

Pour gérer le service HyTrust DataControl on {{site.data.keyword.cloud}} (HTDC), accédez à l'interface graphique Web HTDC à partir de la console {{site.data.keyword.vmwaresolutions_short}} ou accédez à la console HTDC à partir du client Web vSphere.

## Accès à l'interface graphique Web HyTrust DataControl à partir de la console IBM Cloud for VMware Solutions
{: #managinghtdc-accessing-webgui}

Connectez-vous à l'interface graphique Web du dispositif HTDC principal ou secondaire, utilisez les données d'identification de l'interface graphique Web qui figurent sur la page des détails du service HyTrust DataControl on {{site.data.keyword.cloud_notm}}.

## Accès à la console HyTrust DataControl à partir du client Web vSphere
{: #managinghtdc-accessing-console}

Pour accéder à la console HTDC à partir du client Web vSphere, procédez comme suit :
1. Dans le client Web vSphere, localisez les machines virtuelles nommées **KC1** et **KC2**.
2. Cliquez avec le bouton droit de la souris sur **KC1** ou **KC2**, puis cliquez sur **Ouvrir la console**.
3. Connectez-vous à la console à l'aide des données d'identification de console qui figurent sur la page des détails du service HyTrust DataControl on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir[Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Activation de l'accès Internet pour les VM HyTrust DataControl
{: #managinghtdc-internet-access}

Pour HTDC 4.3.2 et versions ultérieures, {{site.data.keyword.vmwaresolutions_short}} prend désormais en charge le renouvellement automatique des licences HyTrust pour lesquelles la fonctionnalité Call Home est activée. Pour les instances de vCenter Server qui ne sont pas uniquement privées, HTDC est déployé avec des règles de pare-feu et SNAT définies sur les services de gestion ESG **mgmt-nsx-edge**.

Ces règles vous permettent d'activer l'accès Internet pour les machines virtuelles HyTrust. Si l'accès à Internet n'est pas activé, la licence appliquée à votre installation HTDC expire au bout d'un an.

Pour les environnements vCenter Server exclusivement privés, la passerelle VMware NSX ESG (Edge Services Gateway) **mgmt-nsx-edge** n'est pas ajoutée ; les règles de pare-feu et SNAT ne sont donc pas définies. Par conséquent, la connectivité Internet ne peut pas être activée pour les instances privées uniquement et les licences HyTrust expirent chaque année.
{:note}

### Procédure de recherche des règles de pare-feu et SNAT définies
{: #managinghtdc-proc-find-firewall}

1. Connectez-vous au client VMware vSphere Web Client (FLEX) et recherchez la passerelle ESG **mgmt-nsx-edge**.
2. Cliquez sur **Home > Networking & Security > NSX Edges**.
3. Cliquez deux fois sur la passerelle ESG **mgmt-nsx-edge** et cliquez sur l'onglet **Manage**.
4. Accédez à l'onglet **Firewall** et recherchez les règles HyTrust. Notez les adresses IP source. Il s'agit des adresses IP des machines virtuelles (VM) HyTrust.
5. Accédez à l'onglet **NAT** et recherchez les règles SNAT créées pour les VM HyTrust. Les adresses IP source correspondent aux adresses IP que vous avez notées à l'étape précédente.

### Procédure d'activation de la connectivité Internet pour HTDC
{: #managinghtdc-proc-enable-internet}

1. Effectuez les étapes 1 à 3 de la procédure précédente.
2. Cliquez sur **Paramètres**, puis sur **Interfaces**. Notez l'adresse IP de la liaison montante privée. Cette adresse devient la nouvelle passerelle par défaut.
3. Cliquez sur **Home > Hosts and Clusters** et recherchez les machines virtuelles (VM) HyTrust. Cliquez avec le bouton droit de la souris sur l'une des VM, puis cliquez sur **Ouvrir la console**.
4. Connectez-vous à la console à l'aide des données d'identification de console qui figurent sur la page des détails du service HyTrust DataControl on {{site.data.keyword.cloud_notm}} sur la console {{site.data.keyword.vmwaresolutions_short}}.
5. Pour obtenir l'adresse IP de passerelle par défaut actuelle de la machine virtuelle, cliquez sur **Manage Network Settings > Show Current Network Configuration**. Notez l'adresse IP répertoriée pour **Gateway**. Cette adresse devient la passerelle utilisée pour la route statique.
6. Pour définir une route statique pour la machine virtuelle, cliquez sur **Manage Network Settings > Manage Static Routes > Add Static Route**. Définissez **Network address** sur `10.0.0.0/8` et **Gateway** sur l'adresse IP indiquée à l'étape précédente.
7. Pour définir l'adresse IP de passerelle par défaut pour la machine virtuelle, cliquez sur **Manage Network Settings > Change Current Network Configuration**. Si vous recevez un message d'avertissement, cliquez sur **OK**, puis sur **Custom Configuration**. Définissez la zone **Gateway** sur l'adresse IP de liaison montante privée notée à l'étape 2, puis cliquez sur **OK**. Attendez que la nouvelle configuration réseau soit installée et que les services réseau soient redémarrés.
8. Si vous voyez un message demandant une nouvelle authentification HyTrust SecureOS, cliquez sur **OK** et entrez l'adresse IP de l'autre machine virtuelle HyTrust pour cette installation. Si vous êtes invité à indiquer un mot de passe composé de 16 caractères, appuyez sur entrée pour revenir au menu principal. Vérifiez la configuration réseau pour vous assurer que les modifications sont appliquées.
9. Pour confirmer que la machine virtuelle dispose d'un accès à internet, exécuter la commande ping sur l'adresse IP publique ou le site web. Cliquez sur **Manage Network Settings > Network Diagnostic Tools > Test Inbound Ports of Another Server**. Entrez une adresse de site Web public, par exemple, `www.ibm.com`, cliquez sur **OK**, entrez `80 443` pour les ports (ou tout autre port que vous souhaitez tester). Une réponse doit s'afficher immédiatement avec les ports d'entrée et un message tel que `80 (OK) 443 (OK)`.
10. Répétez les étapes 3 à 9 pour l'autre machine virtuelle HyTrust.


## Liens connexes
{: #managinghtdc-related}

* [Présentation de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web HyTrust](https://www.hytrust.com/){:external}
