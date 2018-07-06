---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Présentation de VMware HCX on IBM Cloud

Le service HCX on {{site.data.keyword.cloud}} peut en toute transparence étendre les réseaux des centres de données local dans {{site.data.keyword.cloud_notm}}, ce qui permet de migrer les machines virtuelles vers et depuis {{site.data.keyword.cloud_notm}} sans aucune conversion ni modification.

**Disponibilité** : ce service est disponible uniquement pour les instances VMware vCenter Server on IBM Cloud with Hybridity Bundle qui sont déployées en version 2.3 et dans des éditions ultérieures.

Vous pouvez mettre à niveau votre instance vCenter Server existante vers une instance vCenter Server with Hybridity Bundle. Pour plus d'informations sur la mise à niveau de votre instance et le déploiement du service HCX on {{site.data.keyword.cloud_notm}}, voir [Mise à niveau vers l'instance vCenter Server with Hybridity Bundle](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance).

**Remarque :** une instance vCenter Server avec HCX on {{site.data.keyword.cloud_notm}} est limitée à trois connexions simultanées à partir des sites locaux.

## Remarques relatives à l'installation du service HCX on IBM Cloud

Passez en revue les remarques suivantes avant d'installer le service HCX on {{site.data.keyword.cloud_notm}}.

### Exigences concernant le nombre de serveurs ESXi

Le service HCX on {{site.data.keyword.cloud_notm}} ne peut pas être installé dans une instance dont le cluster par défaut contient plus de 51 serveurs ESXi. Etant donné que le service HCX on {{site.data.keyword.cloud_notm}} requiert huit adresses IP dans le sous-réseau vMotion depuis le cluster par défaut, si le nombre de serveurs ESXi est supérieur à 51, aucune adresse IP du sous-réseau vMotion n'est disponible pour le service HCX on {{site.data.keyword.cloud_notm}}.

### Exigences concernant les règles de pare-feu

Avant d'installer le service HCX on {{site.data.keyword.cloud_notm}}, vous devez ajouter une règle de pare-feu à chaque pare-feu existant afin d'autoriser l'intégralité du trafic HTTPS sortant pour que le dispositif virtuel de HCX Manager puisse s'enregistrer. Une fois l'installation de HCX Manager terminée, vous pouvez supprimer la règle de pare-feu. De plus, vous devez configurer des règles de pare-feu pour que le service HCX fonctionne correctement. Pour plus d'informations, voir *Appendix A - Port Access Requirements* dans le document [HCX on {{site.data.keyword.cloud_notm}} Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Remarques relatives au retrait de HCX on IBM Cloud

Passez en revue les remarques suivantes avant de supprimer le service HCX on {{site.data.keyword.cloud_notm}} :
* Vérifiez que les interconnexions et les réseaux étendus entre le site source local et les sites cible {{site.data.keyword.cloud_notm}} sont supprimés. Pour supprimer les interconnexions et les réseaux étendus, utilisez l'interface utilisateur HCX sur le client Web VMware vSphere local.
* Vérifiez que les appariements de sites entre le site source local et les sites cible {{site.data.keyword.cloud_notm}} sont supprimés. Pour supprimer les appariements de sites, utilisez l'interface utilisateur HCX sur le client Web VMware vSphere local.
* La suppression du service HCX on {{site.data.keyword.cloud_notm}} est automatisée. Les opérations suivantes sont effectuées pour supprimer avec succès ce service :
   * La licence HCX commandée pour HCX Manager côté cloud est désactivée.
   * HCX Manager est supprimé.
   * Les adresses IP vMotion qui étaient réservées pour HCX sont libérées.
   * S'ils sont vides, les pools de ressources liés au service HCX sont retirés.
   * S'ils sont vides, les dossiers liés au service HCX sont retirés.
   * Les dispositifs de serveur de périphérie de gestion HCX sont supprimés.

## Liens connexes

* [Commande de HCX on {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [Gestion de HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glossaire des termes HCX](hcx_glossary.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Présentation de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentation VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
