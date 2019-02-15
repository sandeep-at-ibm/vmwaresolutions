---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Implémentation et gestion de KMIP for VMware

**Remarque **: Dans cette édition, KMIP for VMware on {{site.data.keyword.cloud_notm}} est limité au chiffrement vSphere uniquement.

## Connexion du serveur de gestion des clés

Pour activer le chiffrement vSphere ou le chiffrement vSAN à l'aide de KMIP for VMware on {{site.data.keyword.cloud_notm}}, vous devez exécuter les tâches suivantes :

1. [Activer votre compte pour les noeuds finaux de service](/docs/services/service-endpoint/enable-servicepoint.html#getting-started).
2. Créer une instance [IBM Key Protect](/docs/services/key-protect/index.html).
3. Créer une clé racine de client (CRK) au sein d'IBM Key Protect.
4. Créer un ID de service IAM (Identity and Access Management) [et une clé d'API](/docs/iam/serviceid_keys.html) à utiliser avec KMIP for VMware. Accorder à cet ID de service un accès plate-forme viewer et service write à votre instance Key Protect.
5. Créer une instance [KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html) depuis le catalogue {{site.data.keyword.cloud_notm}}.
6. Au sein de VMware vCenter, créer un cluster KMS (serveur de gestion de clés) avec deux serveurs, un pour chaque noeud final KMIP for VMware dans la région de votre choix.
7. Sélectionner l'une des méthodes VMware&rsquo; pour générer ou installer un certificat client KMS dans vCenter.
8. Exporter la version publique du certificat et le configurer en tant que certificat client autorisé dans votre instance KMIP for VMware.

## Activation du chiffrement

Pour utiliser le chiffrement vSAN, éditez les paramètres généraux vSAN dans votre cluster vCenter et sélectionnez la case à cocher du chiffrement.

Pour utiliser le chiffrement vSphere, éditez vos règles de stockage de machine virtuelle pour demander le chiffrement de disque.

## Rotation des clés

[Effectuez une rotation de votre clé racine de client Key Protect (CRK)](/docs/services/key-protect/rotate-keys.html) à l'aide de la console {{site.data.keyword.cloud_notm}} ou de l'API.

Pour le chiffrement VMware vSAN, effectuez une rotation des clés de chiffrement (KEK) de votre clé VMware et si vous le souhaitez des clés de chiffrement de données (DEK) dans les paramètres généraux vSAN de votre cluster vCenter.

Pour le chiffrement VMware vSphere, effectuez une rotation de vos clés VMware KEK et DEK (si vous le souhaitez) à l'aide de la commande PowerShell **Set-VMEncryptionKey**.

## Révocation de clé

Vous pouvez révoquer toutes les clés utilisées par KMIP for VMware en supprimant la clé CRK de votre choix de Key Protect.

Lorsque les clés sont révoquées, toutes les données qui sont protégées par ces clés et par votre instance KMIP for VMware sont broyées de manière cryptographique avec cette méthode. VMware conserve certaines clés tant que l'hôte ESXi est sous tension ; vous devez donc redémarrer votre cluster vSphere afin de vous assurer que toutes les données chiffrées ne sont plus utilisées.
{:important}

KMIP for VMware stocke des clés KEK encapsulées individuelles dans votre instance Key Protect en utilisant des noms qui sont associés aux ID de clé et connus de VMware. Vous pouvez supprimer ces clés individuelles afin de révoquer le chiffrement d'unités ou de disques individuels.

VMware ne supprime pas les clés de KMS lorsqu'une machine virtuelle comportant des disques chiffrés est retirée de l'inventaire. Cela permet le rétablissement de cette machine virtuelle depuis une sauvegarde ou en cas de restauration dans l'inventaire. Si vous souhaitez récupérer ces clés et invalider de manière cryptographique toutes les sauvegardes, vous devez supprimer les clés de Key Protect après les avoir supprimées de vos machines virtuelles.
{:note}

### Liens connexes

* [Présentation de la solution](/docs/services/vmwaresolutions/archiref/kmip/overview.html)
* [Conception de la solution](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
