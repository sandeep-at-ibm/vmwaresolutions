---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Gestion de Zerto on IBM Cloud

Une fois le service Zerto on {{site.data.keyword.cloud}} déployé dans votre instance, vous pouvez configurer ou mettre à jour la réplication virtuelle Zerto et déployer d'autres dispositifs de réplication virtuelle sur des serveurs ESXi qui viennent d'être ajoutés.

## Utilisation de votre propre certificat pour Zerto

La meilleure pratique consiste à utiliser votre propre certificat SSL pour le gestionnaire virtuel Zerto (ZVM, Zerto Virtual Manager). Après avoir déployé Zerto on {{site.data.keyword.cloud_notm}}, remplacez le certificat SSL pour ZVM par votre propre certificat en suivant les instructions de la rubrique [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Gestion de la configuration des réplications Zerto

Pour gérer la configuration de réplications Zerto (telles que le réappariement d'instances Zerto ou la configuration de groupes de protection virtuels afin de répliquer des machines virtuelles), connectez-vous à la console de réplication virtuelle Zerto à l'aide des données d'identification vCenter avec des droits d'administrateur.

Si vous effectuez une réplication entre différentes instances {{site.data.keyword.cloud_notm}} Zerto, vous pouvez configurer la réplication directement entre les instances Zerto. Si vous effectuez une réplication entre l'instance {{site.data.keyword.cloud_notm}} Zerto et votre propre centre de données, vous devez procéder vous-même à l'installation de Zerto dans votre centre de données. Cette instance de Zerto que vous installez dans votre centre de données peut s'octroyer elle-même sa licence automatiquement lorsque vous l'appariez à l'instance {{site.data.keyword.cloud_notm}} Zerto.

Etant donné que la réplication Zerto ne prend pas en charge la traversée de conversion d'adresses réseau, établir la connectivité entre l'instance {{site.data.keyword.cloud_notm}} Zerto et votre propre centre de données risque de nécessiter la personnalisation de routes sur les dispositifs de gestionnaire virtuel Zerto (ZVM, Zerto Virtual Manager) ou les dispositifs de réplication Zerto (VRA, Virtual Replication Appliances) de chaque côté, et nécessite également une tunnellisation sécurisée entre les sites. Lorsque vous configurez ou reconfigurez des routes sur des dispositifs ZVM, vous devez vous assurer que tous les dispositifs ZVM peuvent correctement se connecter à `zerto.com` pour la génération de rapports d'utilisation. Pour vérifier cette connexion, ouvrez une session de navigation sur `https://www.zerto.com` depuis le dispositif ZVM.

**Remarque** : La passerelle de gestion VMware NSX (ESG, Edge Services Gateway) des instances Cloud Foundation et vCenter Server sur {{site.data.keyword.cloud_notm}} est préconfigurée de manière à autoriser les communications HTTPS sortantes (port TCP 443) provenant de ZVM.

## Mise à jour de la réplication virtuelle Zerto

Pour mettre à jour la réplication virtuelle Zerto, connectez-vous à la console de réplication virtuelle Zerto.

## Déploiement de dispositifs VRA sur des serveurs ESXi nouvellement ajoutés

Lorsque vous ajoutez ou supprimez des serveurs ESXi pour le cluster principal de votre instance, des dispositifs VRA sont are automatiquement déployés ou supprimés. Les dispositifs VRA ne sont pas automatiquement déployés sur les serveurs ESXi des clusters secondaires de votre instance, mais vous pouvez les déployer manuellement depuis la console de réplication Zerto.

### Liens connexes

* [Présentation de Zerto on {{site.data.keyword.cloud_notm}}](addingzertodr.html)
* [Demande de services gérés pour Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Site Web zerto.com](https://www.zerto.com){:new_window}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Reprise après incident Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explication des alertes de réplication virtuelle Zerto](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
