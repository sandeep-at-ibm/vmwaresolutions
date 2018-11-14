---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Création de lignes de base et association à des objets d'inventaire

Les lignes de base contiennent une collection d'un ou plusieurs correctifs, extensions, packs de service, correctifs de bogue ou mises à niveau pouvant être classées comme lignes de base de correctifs, d'extensions ou de mises à niveau. Les groupes de lignes de base sont constitués à partir de lignes de base existantes. Ces groupes peuvent contenir une seule ligne de base de mise à niveau et différentes lignes de base de correctifs et d'extensions. Les groupes de lignes de base de machines virtuelles et de dispositifs virtuels peuvent contenir jusqu'à trois lignes de base de mise à niveau : une ligne de base de mise à niveau de VMware Tools, une ligne de base de mise à niveau de matériel de machine virtuelle et une ligne de base de mise à niveau de dispositif virtuel.

VUM comprend des lignes de base prédéfinies qui ne sont pas modifiables et ne peuvent pas être supprimées. Vous pouvez les utiliser ou créer des lignes de base de correctifs, d'extensions et de mise à niveau qui répondent à vos critères. Les lignes de base personnalisées que vous créez et les lignes de base prédéfinies peuvent être combinées dans des groupes de lignes de base.

VUM comprend des lignes de base par défaut que vous pouvez utiliser pour analyser l'un des dispositifs suivants afin de déterminer si les hôtes de votre environnement sont mis à jour avec les correctifs les plus récents, ou si les dispositifs virtuels et les machines virtuelles sont mis à jour à la dernière version disponible :
* Une machine virtuelle
* Un dispositif virtuel
* Un hôte

Ces lignes de base prédéfinies se présentent comme suit :
* **Correctifs d'hôtes critiques (prédéfinie)** - Vérifie la conformité des hôtes ESXi avec tous les correctifs critiques.
* **Correctifs d'hôtes non critiques (prédéfinie)** - Vérifie la conformité des hôtes ESXi avec tous les correctifs facultatifs
* **Mise à niveau de VMware Tools pour correspondre à l'hôte (prédéfinie)** - Vérifie la conformité des machines virtuelles avec la dernière version de VMware Tools sur l'hôte. Update Manager prend en charge la mise à niveau de VMware Tools pour les machines virtuelles sur les hôtes exécutant ESXi 5.5.x et version ultérieure.
* **Mise à niveau du matériel de machine virtuelle pour correspondre à l'hôte (prédéfinie)** - vérifie la conformité du matériel virtuel d'une machine virtuelle avec la dernière version prise en charge par l'hôte. Update Manager prend en charge mise à niveau vers la version vmx-13 du matériel virtuel sur les hôtes exécutant ESXi 6.5.
* **Mise à niveau de dispositif virtuel à la dernière version (prédéfinie)** - Vérifie la conformité d'un dispositif virtuel avec la dernière version publiée du dispositif virtuel

Pour utiliser des lignes de base et des groupes de lignes de base, vous devez les associer à des objets d'inventaire sélectionnés, tels que des objets conteneur, des machines virtuelles, des dispositifs virtuels ou des hôtes. Bien qu'il vous soit possible d'associer des lignes de base et des groupes de lignes de base à des objets individuels, une méthode plus efficace consiste à les associer à des objets conteneur, tels que des dossiers, des applications virtuelles (vApp), des clusters ou des centres de données. Dans cette étape, nous allons utiliser les lignes de base prédéfinies par rapport aux hôtes dans le cluster.

1. A l'aide du client vSphere Web Client, accédez à **Home** > **Hosts and Clusters**.
2. Cliquez sur l'objet de cluster que vous souhaitez analyser.
3. Cliquez sur **Attach Baseline**, puis sélectionnez les deux lignes de base de correctifs prédéfinies, puis cliquez sur **OK**.

### Liens connexes

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
