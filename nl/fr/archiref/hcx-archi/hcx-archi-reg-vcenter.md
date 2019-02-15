---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Enregistrement de HCX Manager auprès de vCenter

Enregistrez le plug-in Services cloud hybrides dans le client Web VMware vSphere et démarrez le service Services cloud hybrides.

## Avant de commencer

Le dispositif virtuel Services cloud hybrides doit être sous tension pour pouvoir être enregistré.

## Procédure pour l'enregistrement de HCX Manager auprès de vCenter

1. Connectez-vous au dispositif virtuel du service Services cloud hybrides.
2. Cliquez sur la vignette **Manage Settings**.
  1. Dans le volet gauche, sous **Configure Systems**, sélectionnez vCenter.
  2. Cliquez sur **Add vCenter** dans l'angle supérieur droit.
  3. Entrez l'adresse IP de vCenter Server sous la forme `https:vCenter-host-name` ou `https:vCenter-IP-address`. Par exemple, `https:My-vCenter` ou `https:10.108.26.211`.
  4. Entrez le nom d'utilisateur et le mot de passe de vCenter Server. Le compte qui est utilisé doit avoir le rôle de l'administrateur vCenter.
  5. Cliquez sur **OK**. Ne redémarrez pas lorsque le message _You need to restart the app_ s'affiche.
3. Configurez le service de recherche.
  1. Cliquez sur l'onglet **Manage**.
  2. Cliquez sur le bouton **Edit** ou complètement à droite de la zone de texte **Lookup Service URL**.
  3. Entrez le noeud final de service de recherche sous la forme suivante :
    * Pour vCenter Server 5.5u3, `https://ssoip:/7444/lookupservice/sdk`
    * Pour vCenter Server 6.0u2, `https://ssoip/lookupservice/sdk`
  4. Cliquez sur **OK**. Ne redémarrez pas lorsqu'un message demandant le redémarrage du moteur Web s'affiche.
4. Cliquez sur l'onglet **Summary** et recherchez la section **Hybridity Management Components**. Arrêtez et redémarrez à la fois le moteur d'applications et le moteur Web.
5. Pour finaliser l'enregistrement, déconnectez-vous du client web vSphere. Connectez-vous à nouveau pour vérifier que la mise à jour de l'écran a bien été effectuée.

## Résultats

Notez la présence de l'icône **Hybrid Cloud** et de l'élément de menu **Hybrid Cloud Services** sur la gauche. L'enregistrement des Services cloud hybrides met à jour ces étiquettes. Dans l'inventaire, l'étiquette d'icône devient **Services cloud hybrides**.

### Liens connexes

* [Installation et configuration de services hybrides](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-install-cfg-hybrid.html)
