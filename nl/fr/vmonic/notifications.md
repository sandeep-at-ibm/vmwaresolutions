---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Gestion des notifications système
{: #notifications}

Les notifications vous permettent de vérifier le statut des opérations système ou utilisateur. Elles fournissent également des informations permettant d'identifier et résoudre les éventuels problèmes.

## Affichage des notifications
{: #notifications-view}

1. A partir de la console {{site.data.keyword.vmwaresolutions_full}}, cliquez sur **Notifications** dans le panneau de navigation de gauche.
2. Affichez le récapitulatif de toutes les notification.

   Tableau 1. Historique des notifications

    <table>
      <tr>
        <th>Colonne</th>
        <th>Description</th>
      </tr>
      <tr>
        <td>Gravité</td>
        <td>Gravité de l'événement signalé par la notification.
          <dl class="dl">
          <dt class="dt dlterm">Critique</dt>
          <dd class="dd">Un événement critique peut avoir un impact sur l'ensemble du système ou du service.</dd>
          <dt class="dt dlterm">Erreur</dt>
          <dd class="dd">Un événement d'erreur se produit durant une opération qui peut nécessiter une intervention de la part de l'administrateur ou de l'utilisateur.</dd>
          <dt class="dt dlterm">Avertissement</dt>
          <dd class="dd">Echec ou fonctionnement inadéquat d'un composant. L'erreur n'interrompt toutefois pas le processus en cours du composant.</dd>
            <dt class="dt dlterm">Information</dt>
            <dd class="dd">Achèvement d'une opération utilisateur ou système. En général, les événements suivants génèrent des notifications d'information :
              <ul class="ul">
                <li class="li">Installation d'un service.</li>
                <li class="li">Mise à niveau d'un service.</li>
                <li class="li">Suppression d'un service.</li>
                <li class="li">Reconfiguration de tous les services pour les serveurs ESXi ajoutés.</li>
                <li class="li">Reconfiguration de tous les services pour les serveurs ESXi supprimés.</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>Type</td>
         <td>Type du composant concerné par l'événement signalé :<ul><li>Instances vCenter Server</li><li>Instances Cloud Foundation</li><li>Services</li><li>Système</li></ul></td>
       </tr>
       <tr>
         <td>Ressource</td>
         <td>Nom de l'instance ou du service qui envoie la notification.</td>
       </tr>
       <tr>
         <td>Description</td>
         <td>Brève description de la notification.</td>
       </tr>
       <tr>
         <td>Date</td>
         <td>Date et heure auxquelles la notification a été envoyée.</td>
       </tr>
    </table>                                       

3. Cliquez sur la ligne d'une notification pour en afficher les détails.

## Filtrage des notifications
{: #notifications-filter}

Par défaut, toutes les notifications non lues s'affichent. Vous pouvez filtrer les notifications par statut, gravité et type. Pour filtrer les notifications, ne cochez que les cases des éléments que vous désirez afficher dans les listes **Statut**, **Gravité** ou **Type**.

## Liens connexes
{: #notifications-related}

* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
