---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de VMware HCX on IBM Cloud
{: #hcx_considerations}

Le service HCX on {{site.data.keyword.cloud}} étend en toute transparence les réseaux des centres de données locaux dans {{site.data.keyword.cloud_notm}}, ce qui vous permet de migrer les machines virtuelles (VM) vers et depuis {{site.data.keyword.cloud_notm}} sans aucune conversion ni modification.

Ce service est disponible uniquement pour les instances VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle qui sont déployées dans la version 2.3 ou ultérieure.
{:note}

Vous pouvez mettre à niveau votre instance vCenter Server existante vers une instance vCenter Server with Hybridity Bundle. Pour plus d'informations concernant la mise à niveau de votre instance et le déploiement du service HCX on {{site.data.keyword.cloud_notm}}, voir [Procédure de mise à niveau vers l'instance vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates#procedure-to-upgrade-to-the-vcenter-server-with-hybridity-bundle-instance).

Une instance vCenter Server avec HCX on {{site.data.keyword.cloud_notm}} est limitée à trois connexions simultanées à partir des sites locaux.
{:note}

## Spécifications techniques relatives à HCX on IBM Cloud
{: #hcx_considerations-specs}

Les composants suivants sont commandés et inclus dans le service HCX on {{site.data.keyword.cloud_notm}} :

Les instances HCX locales incluent uniquement l'octroi de licence et l'activation.
{:note}

### Paire active/passive de passerelles VMware NSX Edge Services Gateway pour HCX Management
{: #hcx_considerations-nsx}

* UC : 6 vCPU
* Mémoire RAM : 8 Go
* Disque : VMDK 3 Go

### HCX Management Appliance - Machine virtuelle
{: #hcx_considerations-vm}

* UC : 4 vCPU
* Mémoire RAM : 12 Go
* Disque : VMDK 60 Go

Des dispositifs HCX supplémentaires sont déployés durant la configuration s'il y a lieu pour la connectivité L2, l'optimisation WAN et les connexions de passerelle.

### Utilisation en réseau
{: #hcx_considerations-networking}

* Un sous-réseau portable public avec 16 adresses IP
* Deux sous-réseaux portables privés avec 64 adresses IP
* Huit adresses IP issues du sous-réseau vMotion portable privé

## Remarques relatives à l'installation de HCX on IBM Cloud
{: #hcx_considerations-install}

Passez en revue les remarques suivantes avant d'installer le service HCX on {{site.data.keyword.cloud_notm}}.

### Exigences concernant le nombre de serveurs ESXi
{: #hcx_considerations-esxi-servers}

Le service HCX on {{site.data.keyword.cloud_notm}} ne peut pas être installé dans une instance dont le cluster par défaut contient plus de 51 serveurs ESXi. Etant donné que le service HCX on {{site.data.keyword.cloud_notm}} requiert huit adresses IP dans le sous-réseau vMotion depuis le cluster par défaut, si le nombre de serveurs ESXi est supérieur à 51, aucune adresse IP du sous-réseau vMotion n'est disponible pour le service HCX on {{site.data.keyword.cloud_notm}}.

### Exigences concernant les règles de pare-feu
{: #hcx_considerations-firewall}

Avant d'installer le service HCX on {{site.data.keyword.cloud_notm}}, vous devez ajouter une règle de pare-feu à chaque pare-feu existant afin d'autoriser l'intégralité du trafic HTTPS sortant pour que le dispositif virtuel du gestionnaire HCX (HCX Manager) puisse s'enregistrer. Une fois l'installation de HCX Manager terminée, vous pouvez supprimer la règle de pare-feu. De plus, vous devez configurer des règles de pare-feu pour que le service HCX fonctionne correctement. Pour plus d'informations, voir [Accès aux ports requis pour VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req).

## Remarques relatives au retrait de HCX on IBM Cloud
{: #hcx_considerations-delete}

Passez en revue les remarques suivantes avant de supprimer le service HCX on {{site.data.keyword.cloud_notm}} :
* Vérifiez que les interconnexions et les réseaux étendus entre le site source local et les sites cible {{site.data.keyword.cloud_notm}} sont supprimés. Pour supprimer les interconnexions et les réseaux étendus, utilisez l'interface utilisateur HCX sur le client Web VMware vSphere local.
* Vérifiez que les appariements de sites entre le site source local et les sites cible {{site.data.keyword.cloud_notm}} sont supprimés. Pour supprimer les appariements de sites, utilisez l'interface utilisateur HCX sur le client Web VMware vSphere local.
* La suppression du service HCX on {{site.data.keyword.cloud_notm}} est automatisée. Les opérations suivantes sont effectuées pour supprimer avec succès ce service :
   * La licence HCX qui est commandée pour HCX Manager côté cloud est désactivée.
   * HCX Manager est supprimé.
   * Les adresses IP vMotion qui étaient réservées pour HCX sont libérées.
   * S'ils sont vides, les pools de ressources liés au service HCX sont retirés.
   * S'ils sont vides, les dossiers liés au service HCX sont retirés.
   * Les dispositifs de serveur de périphérie de gestion HCX sont supprimés.

## Liens connexes
{: #hcx_considerations-related}

* [Commande de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [Gestion de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Glossaire des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Présentation de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentation VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
