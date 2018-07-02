---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-05"

---

# Une instance secondaire en version 1.7 ne peut pas être ajoutée à une instance principale en version 1.5

## Problème
Dans une configuration Cloud Foundation multisite, vous ne pouvez pas ajouter une instance secondaire en version 1.7 à une instance principale en version 1.5 en raison de la différence entre les versions de système d'exploitation sur le serveur Microsoft Active Directory (AD).

## Résolution
Effectuez les opérations suivantes sur l'instance principale en version 1.5 afin d'accorder à l'utilisateur de l'automatisation principale le droit d'intégrer les groupes **Administrateurs de l'entreprise** et **Administrateurs du schéma**.

1. Connectez-vous au serveur Windows AD avec le mot de passe **administrateur**.
2. Ouvrez **Gestionnaire de serveur**, puis cliquez sur **Outils -> Utilisateurs et ordinateurs Active Directory**.
4. Dans la fenêtre **Utilisateurs et ordinateurs Active Directory**, cliquez sur la section **Utilisateurs** sous votre domaine racine.
5. Cliquez avec le bouton droit de la souris sur l'utilisateur de l'automatisation pour ouvrir la fenêtre **Propriétés**. 
6. Cliquez sur l'onglet **Membre de**.
7. Cliquez sur **Ajouter** et entrez les groupes **Administrateurs de l'entreprise** et **Administrateurs du schéma** comme noms d'objet dans la liste.  

A l'issue de ces étapes, vous pouvez ajouter une instance secondaire V1.7 à une instance principale V1.5. 
