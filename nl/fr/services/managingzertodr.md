---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Gestion de Zerto on IBM Cloud

Une fois le service Zerto on {{site.data.keyword.cloud}} déployé dans votre instance, vous pouvez configurer ou mettre à jour la réplication virtuelle Zerto et déployer d'autres dispositifs de réplication virtuelle sur des serveurs ESXi qui viennent d'être ajoutés.

## Utilisation de votre propre certificat pour Zerto

Meilleure pratique : utilisez votre propre certificat SSL pour Zerto Virtual Manager (ZVM). Après avoir déployé le service Zerto on {{site.data.keyword.cloud_notm}}, remplacez le certificat SSL pour ZVM par votre propre certificat. Pour plus d'informations, voir l'article [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Gestion de la configuration des réplications Zerto

Pour gérer la configuration des réplications Zerto, connectez-vous à la console de réplication virtuelle Zerto à l'aide des données d'identification vCenter avec les droits d'administrateur. Par exemple, reconstituez les appariements des instances Zerto ou configurez des groupes de protection virtuels pour répliquer les machines virtuelles.

Lorsque vous effectuez une réplication entre différentes instances Zerto d'{{site.data.keyword.cloud_notm}}, vous pouvez configurer la réplication directement entre les instances Zerto. Si vous effectuez une réplication entre l'instance Zerto d'{{site.data.keyword.cloud_notm}} et votre propre centre de données, vous devez procéder vous-même à l'installation de Zerto dans votre centre de données. Cette instance peut s'octroyer elle-même sa licence automatiquement lorsque vous l'appariez à l'instance Zerto d'{{site.data.keyword.cloud_notm}}.

La réplication Zerto ne prend pas en charge la conversion d'adresses réseau transversale (NAT-T). Pour établir la connectivité entre l'instance Zerto d'{{site.data.keyword.cloud_notm}}, il vous faudra peut-être personnaliser les routes sur les dispositifs ZVM (Zerto Virtual Manager) et les dispositifs de réplication virtuels (VRA) Zerto de chaque côté. Etablir la connectivité peut également nécessiter un système de tunnellisation sécurisé entre les sites. Lorsque vous configurez ou reconfigurez des routes sur des dispositifs ZVM, vous devez vous assurer que tous les dispositifs ZVM peuvent correctement se connecter à `zerto.com` pour la génération de rapports d'utilisation. Pour vérifier cette connexion, ouvrez une session de navigation sur `https://www.zerto.com` depuis le dispositif ZVM.

**Remarque** : La passerelle de gestion VMware NSX (ESG, Edge Services Gateway) des instances Cloud Foundation et vCenter Server sur {{site.data.keyword.cloud_notm}} est préconfigurée de manière à autoriser les communications HTTPS sortantes (port TCP 443) provenant de ZVM.

## Mise à jour de la réplication virtuelle Zerto

Pour mettre à jour la réplication virtuelle Zerto, connectez-vous à la console de réplication virtuelle Zerto.

## Déploiement de dispositifs VRA sur des serveurs ESXi nouvellement ajoutés

Lorsque vous ajoutez ou supprimez des serveurs ESXi pour le cluster principal de votre instance, des dispositifs VRA sont automatiquement déployés ou supprimés. Les dispositifs VRA ne sont pas automatiquement déployés sur les serveurs ESXi des clusters secondaires de votre instance. Vous pouvez les déployer vous-même à partir de la console de réplication virtuelle Zerto.

### Liens connexes

* [Présentation de Zerto on {{site.data.keyword.cloud_notm}}](addingzertodr.html)
* [Demande de services gérés pour Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Site Web zerto.com](https://www.zerto.com){:new_window}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Reprise après incident Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explication des alertes de réplication virtuelle Zerto](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
