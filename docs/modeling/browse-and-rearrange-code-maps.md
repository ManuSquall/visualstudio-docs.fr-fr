---
title: Parcourir et réorganiser des cartes de code
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5a6894a05a0e94885ee4c128db8a22f9113bd41f
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748837"
---
# <a name="browse-and-rearrange-code-maps"></a>Parcourir et réorganiser des cartes de code
Réorganisez les éléments sur les cartes de code pour faciliter leur lecture et améliorer leurs performances.

 Vous pouvez personnaliser les cartes de code sans affecter le code sous-jacent dans une solution. Cette opération est utile quand vous souhaitez vous concentrer sur des éléments de code clé ou communiquer vos idées concernant le code. Par exemple, pour mettre en surbrillance des zones intéressantes, vous pouvez sélectionner des éléments de code sur la carte et les filtrer, modifier le style des éléments de code et des liens, masquer ou supprimer des éléments de code et organiser les éléments de code à l'aide de propriétés, de catégories ou de groupes.

 **Spécifications**

-   Pour créer des cartes de code, vous devez avoir Visual Studio Enterprise.

-   Vous pouvez afficher des cartes de code et apporter des modifications mineures aux cartes de code dans Visual Studio Professional.

##  <a name="ManageLargeGraphs"></a> Commencer à utiliser avec les cartes de code
 Créer une carte de code (consultez [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) pour plus d’informations). Si vous ne souhaitez pas attendre que la carte terminer la création, cliquez sur le **Annuler** lien à tout moment pour arrêter le processus de génération. Toutefois, dans ce cas vous ne verrez pas les détails de toutes les dépendances et tous les liens.

 Une fois la carte générée, suivez ces conseils pour procéder à l'examen de votre code :

-   Examinez les clusters de dépendances naturelles dans le code. Dans la barre d’outils de la carte, choisissez **disposition**, **Clusters rapides**![bouton Clusters rapides sur la barre d’outils du graphique](../modeling/media/quickclustersicon.gif). Consultez [modifier la disposition de la carte](#Selecting).

     ![Graphique de dépendance &#45; disposition Clusters rapides](../modeling/media/dependencygraph_quickclusters.png)

-   Organisez la carte en zones plus petites en regroupant les nœuds connexes. Réduisez ces groupes pour afficher uniquement les dépendances intergroupes, qui sont affichées automatiquement. Consultez [groupe de nœuds](#OrganizeGroups).

-   Utilisez des filtres pour simplifier la carte et vous concentrer sur les types de nœuds ou de liens qui vous intéressent. Consultez [filtrer les nœuds et les liens](#FilterNodes).

-   Optimisez les performances des grandes cartes. Consultez [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) pour plus d’informations. Par exemple, activez **Skip Build** sur la barre d’outils de mappage afin que Visual Studio ne regénérez votre solution lorsque vous mettez à jour les éléments sur la carte.

##  <a name="Selecting"></a> Modifier la disposition de la carte

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Réorganiser le flux de dépendance pour l'ensemble de la carte dans un sens spécifique. Cela peut vous aider à distinguer les couches architecturales dans le code.|Dans la barre d’outils de la carte, choisissez **disposition**, puis :<br /><br /> -   **De haut en bas** ![supérieur au bouton de graphique en bas](../modeling/media/topbottomgraphbutton.gif)<br />-   **Bas en haut** ![bas au bouton du haut du graphique](../modeling/media/bottomtopgraphbutton.gif)<br />-   **De gauche à droite** ![gauche au bouton de mise en page de droite](../modeling/media/leftrightgraphbutton.gif)<br />-   **De droite à gauche** ![de droite à un bouton de graphique de gauche](../modeling/media/rightleftgraphbutton.gif)|
|Afficher les clusters de dépendances naturelles dans le code avec les nœuds les plus dépendants au centre des clusters et les nœuds les moins dépendants à l'extérieur de ces clusters.|Dans la barre d’outils de la carte, choisissez **disposition**, puis **Clusters rapides**![bouton Clusters rapides sur la barre d’outils du graphique](../modeling/media/quickclustersicon.gif).|
|Sélectionnez un ou plusieurs nœuds sur la carte.|Cliquez sur un nœud pour le sélectionner. Pour sélectionner ou désélectionner plusieurs nœuds, maintenez la touche **CTRL** tout en cliquant sur.<br /><br /> Clavier : appuyez sur **onglet** ou utilisez les touches de direction pour déplacer le rectangle de focus en pointillé à un nœud et à appuyer sur **espace** pour le sélectionner. Appuyez sur **CTRL** + **espace** permettant de sélectionner ou désélectionner des nœuds.|
|Déplacer des nœuds spécifiques sur la carte.|Faites glisser les nœuds pour les déplacer. Pour déplacer les autres nœuds et les liens de vous faire glisser des nœuds, maintenez la **MAJ** clé.<br /><br /> Clavier : maintenez la touche **CTRL** et appuyez sur les touches de direction.|
|Modifier la disposition à l'intérieur d'un groupe, indépendamment des autres nœuds et groupes sur la carte.|Sélectionnez un nœud et ouvrez le menu contextuel. Choisissez **disposition** et sélectionnez un style de disposition.<br /><br /> ou<br /><br /> Sélectionnez un nœud et développez-le pour afficher les nœuds enfants. Cliquez sur le titre de nœud pour afficher la barre d’outils contextuelle de groupe, puis ouvrez le **modifier le style de disposition du groupe**![graphique de dépendance &#45; barre d’outils du groupe &#45; disposition](../modeling/media/dependencygraph_grouptoolbar.gif) liste. Sélectionnez une des dispositions de l’arborescence, **Clusters rapides**, ou **mode liste** (qui réorganise le contenu du groupe dans une liste).<br /><br /> Consultez [groupe de nœuds](#OrganizeGroups) pour plus d’informations.|
|Annuler une action sur la carte.|Appuyez sur **CTRL** + **Z** ou utiliser Visual Studio **Annuler** commande.|

##  <a name="Explore"></a> Parcourir la carte

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Parcourir la carte.|Faites glisser la carte dans n'importe quelle direction à l'aide de la souris.<br /><br /> ou<br /><br /> Maintenez la touche **MAJ** et tournez la molette de la souris pour faire défiler horizontalement. Maintenez la touche **MAJ** + **CTRL** et tournez la molette de la souris pour faire défiler horizontalement.|
|Effectuer un zoom avant ou arrière sur la carte.|Faites tourner la roulette de la souris.<br /><br /> ou<br /><br /> Utilisez le **Zoom** liste déroulante, la barre d’outils de mappage de code.<br /><br /> ou<br /><br /> Utilisez les raccourcis clavier. Pour effectuer un zoom, appuyez sur **CTRL + MAJ +.** (point). Pour effectuer un zoom arrière, appuyez sur **CTRL + MAJ +,** (virgule).|
|Effectuer un zoom avant sur une zone spécifique à l'aide de la souris.|Maintenez le bouton droit de la souris enfoncé pendant que vous dessinez un rectangle autour de la zone qui vous intéresse.|
|Redimensionner et ajuster la carte dans sa fenêtre.|Choisissez **Zoom pour ajuster** à partir de la **Zoom** liste sur la barre d’outils de carte de code.<br /><br /> ou<br /><br /> Cliquez sur le **Zoom pour ajuster** icône ![icône Zoom sur la barre d’outils carte](../modeling/media/almcodemapzoomicon.png) sur la barre d’outils de carte de code. Clavier : appuyez sur **CTRL + 0** (zéro).|
|Rechercher un nœud par nom sur la carte. **Conseil :** cela fonctionne uniquement pour les éléments sur la carte. Pour rechercher des éléments dans votre solution, mais pas sur la carte, elles sont disponibles sur **l’Explorateur de solutions**et faites-les glisser vers la carte. (Faites glisser votre sélection, ou dans la barre d’outils de l’Explorateur de solutions, cliquez sur **afficher sur la carte de Code**).|1.  Choisissez le **trouver** icône ![icône Rechercher dans la barre d’outils carte](../modeling/media/almcodemapfindicon.png) sur la barre d’outils de carte de code (clavier : appuyez sur **CTRL + F**) pour afficher la zone de recherche dans le coin supérieur droit de la carte.<br />2.  Tapez le nom de l’élément et appuyez sur **retourner** ou cliquez sur l’icône de loupe «. ». Le premier élément qui correspond à votre recherche apparaît sélectionné sur la carte.<br />3.  Pour personnaliser votre recherche, ouvrez la liste déroulante et choisissez une option de recherche. Les options sont **suivant**, **précédent**, et **sélectionner tout**. Cliquez ensuite sur le bouton correspondant en regard de la zone de texte Rechercher.<br />     ![Liste des options de recherche&#45;liste vers le bas](../modeling/media/almcodemapssearchdropdown.png)<br />     Vous pouvez également utiliser le clavier : appuyez sur **F3** pour sélectionner le nœud correspondant suivant ou **MAJ + F3** pour sélectionner le nœud correspondant précédent.<br />4.  Sélectionnez l'une des options qui spécifient comment gérer les termes de recherche en cliquant sur les icônes sous la zone de texte de recherche.<br />     ![Options de correspondance de recherche](../modeling/media/almcodemapssearchmatchicons.png)<br />     Les options disponibles sont, de gauche à droite, le respect de la casse pour la mise en correspondance, la recherche de mot entier uniquement, l'utilisation de la syntaxe d'expression régulière .NET et le développent automatique des groupes pour afficher les correspondances aux éléments entre parenthèses. **Important :** vous pouvez utiliser la zone de recherche pour rechercher des correspondances dans les groupes réduits uniquement si ces groupes ont été auparavant étendus. Pour rechercher ces correspondances et développer automatiquement leurs groupes parents, choisissez cette option sous la zone de recherche.|
|Sélectionner tous les nœuds non sélectionnés.|Ouvrez le menu contextuel pour les nœuds sélectionnés. Choisissez **sélectionnez**, **inverser la sélection**.|
|Sélectionner des nœuds supplémentaires qui pointent vers ceux sélectionnés.|Ouvrez le menu contextuel pour les nœuds sélectionnés. Choisissez **sélectionnez** et l’autre de ces :<br /><br /> -Pour sélectionner d’autres nœuds qui pointent directement vers le nœud sélectionné, choisissez **dépendances entrantes**.<br />-Pour sélectionner d’autres nœuds qui sont liés directement à partir du nœud sélectionné, choisissez **dépendances sortantes**.<br />-Pour sélectionner d’autres nœuds qui sont liés directement vers et à partir du nœud sélectionné, choisissez **les deux**.<br />-Pour sélectionner tous les nœuds qui renvoient vers et depuis le nœud sélectionné, choisissez **connecté le sous-graphe**.<br />-Pour sélectionner tous les enfants du nœud sélectionné, choisissez **enfants**.|

##  <a name="FilterNodes"></a> Filtrer les nœuds et les liens

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Afficher ou masquer le volet Filtres.|Choisissez le **filtres** bouton sur la barre d’outils de carte de code. Par défaut, le volet Filtres est affiché sous forme de page à onglets dans la fenêtre de l'Explorateur de solutions.|
|Filtrer les types de nœuds affichés sur la carte.|Activez ou désactivez les cases à cocher dans la **des éléments de Code** liste dans le volet filtres.|
|Filtrer les types de liens affichés sur la carte.|Activez ou désactivez les cases à cocher dans la **relations** liste dans le volet filtres.|
|Afficher ou masquer les nœuds de projet de test sur la carte.|Activez ou désactivez le **des ressources de Test** case à cocher dans la **divers** liste dans le volet filtres.|

 Les icônes affichées dans le volet Légende de la carte reflètent les paramètres spécifiés dans la liste. Pour afficher ou masquer le volet de légende, cliquez sur le **légende** bouton sur la barre d’outils de carte de code.

##  <a name="Inspect"></a> Examinez les nœuds et les liens
 Les cartes de code affichent les types de liens suivants :

-   Un lien individuel représente une relation unique entre deux nœuds.

-   Un lien entre les groupes représente une relation entre deux nœuds de différents groupes.

-   Un lien global représente toutes les relations qui pointent dans la même direction entre deux groupes.

> [!TIP]
>  Par défaut, la carte affiche les liens entre les groupes uniquement pour les nœuds sélectionnés. Pour modifier ce comportement pour afficher ou masquer les liens entre les groupes globaux, cliquez sur **disposition** du code de mapper la barre d’outils et choisissez **avancé**, puis **afficher tous les liens entre les groupes** ou **Masquer tous les liens entre les groupes**. Consultez [masquer ou afficher les nœuds et liens](#HidingShowing) pour plus d’informations.

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Afficher plus d'informations sur un nœud ou un lien.|Déplacez le pointeur de la souris sur le nœud ou le lien jusqu'à ce qu'une info-bulle apparaisse.<br /><br /> L'info-bulle d'un lien global répertorie chaque dépendance qu'il représente.<br /><br /> ou<br /><br /> Ouvrez le menu contextuel du nœud ou du lien. Choisissez **modifier**, **propriétés**.|
|Afficher ou masquer le contenu d'un groupe.|-Pour développer un groupe, ouvrez le menu contextuel du nœud et choisissez **groupe**, **Expand**.<br />     ou<br />     Déplacez le pointeur de la souris sur le nœud jusqu'à ce que le bouton chevron (flèche Bas) apparaisse. Cliquez sur ce bouton pour développer le groupe. Clavier : pour développer ou réduire le groupe sélectionné, appuyez sur la **PLUS** clé (**+**) ou le **moins** clé (**-**).<br />-Pour réduire un groupe, ouvrez le menu contextuel du nœud et choisissez **groupe**, **réduire**.<br />     ou<br />     Déplacez le pointeur de la souris sur un groupe jusqu'à ce que le bouton chevron (flèche Haut) apparaisse. Cliquez sur ce bouton pour réduire le groupe.<br />-Pour développer tous les groupes, appuyez sur **CTRL** + **A** pour sélectionner tous les nœuds. Ouvrez le menu contextuel de la carte, sélectionnez **groupe**, **Expand**. **Remarque :** cette commande n’est pas disponible si le développement de tous les groupes génère une carte inutilisable ou des problèmes de mémoire. Nous vous recommandons de développer la carte uniquement au niveau de détail qui vous intéresse.<br />-Pour réduire tous les groupes, ouvrez le menu contextuel pour un nœud ou de la carte. Choisissez **groupe**, **réduire tout**.|
|Voir la définition de code pour un espace de noms, un type ou un membre.|Ouvrez le menu contextuel du nœud et choisissez **atteindre la définition**.<br /><br /> - ou -<br /><br /> Double-cliquez sur le nœud. Pour les groupes développés, double-cliquez sur l'en-tête de groupe.<br /><br /> - ou -<br /><br /> Sélectionnez le nœud, puis appuyez sur **F12**.<br /><br /> Exemple :<br /><br /> -Pour un espace de noms contenant une classe, le fichier de code pour la classe s’ouvre pour afficher la définition de cette classe. Dans d’autres cas, le **résultats** fenêtre affiche une liste des fichiers de code. **Remarque :** lorsque vous effectuez cette tâche sur un espace de noms Visual Basic, le fichier de code derrière l’espace de noms ne s’ouvre pas. Ce problème se produit également lorsque vous effectuez cette tâche sur un groupe de nœuds sélectionnés qui incluent un espace de noms Visual Basic. Pour contourner ce problème, accédez manuellement au fichier code-behind de l'espace de noms ou omettez le nœud de l'espace de noms de votre sélection.<br />-Pour une classe ou une classe partielle, le fichier de code pour cette classe s’ouvre pour afficher la définition de classe.<br />-Pour une méthode, le fichier de code pour la classe parente s’ouvre pour afficher la définition de méthode.|
|Examiner les dépendances et les éléments qui participent à un lien global.|Sélectionnez les liens qui vous intéresse et ouvrez le menu contextuel pour votre sélection. Choisissez **afficher les liens de contribution** ou **afficher les liens de contribution sur la nouvelle carte de Code**.<br /><br /> Visual Studio développe les groupes aux deux extrémités du lien et affiche uniquement les éléments et les dépendances qui participent au lien. **Remarque :** lorsque vous examinez les dépendances entre les éléments dans les groupes partielles, vous pouvez observer ce comportement : <ul><li>Liens vers les éléments qui ne font pas partie de votre examen disparaissent de la carte, même si ces liens existent toujours.</li><li>Supposez que vous examinez un lien vers un élément dans un groupe partiel et que vous examinez ensuite un autre lien vers le même élément. Lors de votre second examen, le groupe partiel cible montre uniquement les éléments issus de votre premier examen. Les liens et éléments cible qui n’a pas participer à votre premier examen mais participer votre deuxième examen n’apparaissent pas.</li></ul> Pour voir manquant des éléments d’un groupe, sélectionnez **récupérer à nouveau les enfants**![icône récupérer à nouveau d’enfants](../modeling/media/dependencygraph_deletednodesicon.png) (ce qui indique que tous les membres d’un groupe s’affichent sur la carte). Vous pouvez aussi essayer d’annuler vos actions (clavier : appuyez sur **CTRL + Z**) et examinez les dépendances sur une nouvelle carte.|
|Examiner les dépendances entre plusieurs nœuds de différents groupes.|Développez les groupes pour afficher tous leurs enfants. Sélectionnez tous les nœuds qui vous intéressent, y compris leurs enfants. La carte affiche les liens entre les groupes entre les nœuds sélectionnés.<br /><br /> Pour sélectionner tous les nœuds dans un groupe, maintenez la touche et **MAJ** et le bouton gauche de la souris pendant que vous dessinez un rectangle autour de ce groupe. Pour sélectionner tous les nœuds sur une carte, appuyez sur **CTRL**+**A**. **Conseil :** pour afficher les liens entre les groupes en permanence, choisissez **disposition** sur la barre d’outils de la carte, **avancé**, **afficher tous les liens entre les groupes**.|
|Afficher les éléments auxquels un nœud ou un lien fait référence.|Ouvrez le menu contextuel du nœud et choisissez **rechercher toutes les références**. **Remarque :** cela s’applique uniquement lorsque le `Reference` attribut est défini pour le nœud ou le lien dans le fichier .dgml de la carte. Pour ajouter des références à des éléments à partir de nœuds ou de liens, consultez [les cartes de code de personnalisation en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

##  <a name="HidingShowing"></a> Masquer ou afficher les nœuds et les liens
 Masquer des nœuds les empêche de participer aux algorithmes de disposition. Par défaut, les liens entre les groupes sont masqués. Les liens entre les groupes sont des liens individuels qui relient vos nœuds entre différents groupes. Quand les groupes sont réduits, la carte rassemble tous les liens entre les groupes sous forme de liens uniques. Lorsque vous développez un groupe et sélectionnez des nœuds dans le groupe, les liens entre les groupes apparaissent et mettent en exergue les dépendances dans ce groupe.

> [!CAUTION]
>  Avant de partager une carte créée dans Visual Studio Enterprise avec des personnes qui utilisent Visual Studio Professional, veillez à afficher tous les nœuds et liens entre les groupes que vous souhaitez qu'elles puissent voir. Sinon, ces utilisateurs ne pourront pas afficher ces éléments.

### <a name="to-hide-or-show-nodes"></a>Pour masquer ou afficher les nœuds

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Masquer les nœuds sélectionnés.|1.  Sélectionnez les nœuds que vous voulez masquer.<br />2.  Ouvrez le menu contextuel des nœuds sélectionnés ou de la carte. Choisissez **sélectionnez**, **masquer sélectionné**.|
|Masquer les nœuds non sélectionnés.|1.  Sélectionnez les nœuds que vous souhaitez rendre visibles.<br />2.  Ouvrez le menu contextuel des nœuds sélectionnés ou de la carte. Choisissez **sélectionnez**, **masquer désactivée**.|
|Afficher les nœuds masqués.|-Pour afficher tous les nœuds masqués à l’intérieur d’un groupe, vérifiez tout d’abord que le groupe est développé. Ouvrez le menu contextuel et choisissez **sélectionnez**, **afficher les enfants**.<br />     ou<br />     Cliquez sur le **afficher les enfants**![afficher une icône d’enfants](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) icône dans le coin supérieur gauche du groupe (cela est visible uniquement lorsqu’il existe des nœuds enfants masqués).<br />-Pour afficher tous les nœuds masqués, ouvrez le menu contextuel pour le mappage ou un nœud et choisissez **sélectionnez**, **afficher tous les**.|

### <a name="to-hide-or-show-links"></a>Pour masquer ou afficher les liens

|**To**|**Dans la barre d’outils de la carte, choisissez mise en page, Avancé, puis choisissez**|
|------------|----------------------------------------------------------------------|
|Afficher en permanence les liens entre les groupes.|**Afficher tous les liens entre les groupes**. Cela masque les liens globaux entre les groupes.|
|Masquer en permanence les liens entre les groupes.|**Masquer tous les liens entre les groupes**|
|Afficher uniquement les liens entre les groupes pour les nœuds sélectionnés.|**Afficher les liens entre les groupes sur les nœuds sélectionnés**|
|Masquer tous les liens.|**Masquer tous les liens**. Pour réafficher les liens, choisissez l'une des options mentionnées ci-dessus.|

##  <a name="OrganizeGroups"></a> Nœuds de groupe

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Afficher les nœuds conteneurs comme nœuds de groupe ou nœuds feuille.|Pour afficher les nœuds de conteneur en tant que nœuds terminaux : sélectionnez les nœuds, ouvrez le menu contextuel pour votre sélection et choisissez **groupe**, **convertir la feuille**.<br /><br /> Pour afficher les nœuds de conteneur en tant que nœuds de groupe : sélectionnez les nœuds, ouvrez le menu contextuel pour votre sélection et choisissez **groupe**, **convertir au groupe**.|
|Modifier la disposition à l'intérieur d'un groupe.|Sélectionnez le groupe, ouvrez le menu contextuel, choisissez **disposition**, puis sélectionnez le style de disposition souhaité.<br /><br /> ou<br /><br /> 1.  Sélectionnez le groupe et assurez-vous qu'il est développé.<br />2.  Cliquez de nouveau sur l'en-tête de groupe. La barre d'outils du groupe apparaît.<br />     ![Graphique de dépendance &#45; barre d’outils du groupe](../modeling/media/dependencygraph_group.png)<br />3.  Ouvrir le **modifier le style de disposition du groupe** liste ![graphique de dépendance &#45; barre d’outils du groupe &#45; disposition](../modeling/media/dependencygraph_grouptoolbar.gif) et choisissez le style de disposition souhaité.<br /><br /> **Mode liste** réorganise les membres du groupe dans la liste. **Graphique par défaut** réinitialise la disposition du groupe à la disposition par défaut de carte. Pour les autres options, consultez [modifier la disposition de la carte](#Selecting).|
|Ajouter un nœud à un groupe.|Faites glisser le nœud dans le groupe.<br /><br /> Pendant que vous faites glisser le nœud, Visual Studio affiche un indicateur qui montre que vous déplacez le nœud.<br /><br /> Vous pouvez également faire glisser des nœuds en dehors d'un groupe.|
|Ajouter un nœud à un nœud non-groupe.|Faites glisser le nœud dans le nœud cible. Vous pouvez convertir n'importe quel nœud cible en un groupe en y ajoutant des nœuds.|
|Regrouper les nœuds sélectionnés.|1.  Sélectionnez les nœuds que vous voulez regrouper. Une barre d'outils contextuelle s'affiche au-dessus du dernier nœud que vous sélectionnez.<br />     ![Barre d’outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)<br />2.  Dans la barre d’outils, cliquez sur l’icône quatrième **regrouper les nœuds sélectionnés** (si le nœud est développé des cinq au lieu de quatre icônes). Tapez le nom pour le nouveau groupe et appuyez sur **retourner**.<br />     ou<br />     Sélectionnez les nœuds que vous souhaitez regrouper et ouvrez le menu contextuel de votre sélection. Choisissez **groupe**, **ajouter un groupe Parent**, tapez le nom pour le nouveau groupe, puis appuyez sur **retourner**.<br /><br /> Vous pouvez renommer un groupe. Ouvrez le menu contextuel pour le groupe et choisissez **modifier**, **propriétés** pour ouvrir la fenêtre Propriétés de Visual Studio. Dans le **étiquette** propriété, renommez le groupe en fonction des besoins.|
|Supprimer des groupes.|Sélectionnez le groupe ou les groupes que vous souhaitez supprimer. Ouvrez le menu contextuel pour votre sélection, puis choisissez **groupe**, **supprimer le groupe**.|
|Supprimer des nœuds de leur groupe parent.|Sélectionnez les nœuds que vous voulez déplacer. Ouvrez le menu contextuel pour votre sélection, puis choisissez **groupe**, **supprimer du Parent**. Cette opération supprime les nœuds jusqu'à leur grand-parent ou jusqu'en dehors du groupe s'ils n'ont aucun groupe grand-parent.<br /><br /> ou<br /><br /> Sélectionnez les nœuds et faites-les glisser hors du groupe.|

##  <a name="AddRemoveNodesLinks"></a> Ajouter, supprimer ou renommer des nœuds, des liens et des commentaires
 Vous pouvez afficher plus ou moins d'éléments sur une carte pour la détailler ou la simplifier. Vous pouvez aussi renommer des éléments et y ajouter des commentaires.

> [!CAUTION]
>  Avant de partager une carte créée à l'aide de Visual Studio Enterprise avec des personnes qui utilisent Visual Studio Professional, veillez à ce que les éléments de code que vous souhaitez que les autres puissent voir soient visibles sur la carte. Sinon, ces utilisateurs ne pourront pas récupérer les éléments de code supprimés.

### <a name="add-a-node-for-a-code-element"></a>Ajouter un nœud pour un élément de code

|**To**|**Procédez comme suit**|
|------------|-----------------------------|
|Ajouter un nouveau nœud générique à l'emplacement actuel du pointeur de la souris.|1.  Déplacez le pointeur de la souris vers l’emplacement sur la carte où vous souhaitez placer le nouvel élément de code et appuyez sur **insérer**.<br />     ou<br />     Ouvrez le menu contextuel de la carte, sélectionnez **modifier**, **ajouter**, **nœud générique**.<br />2.  Tapez le nom pour le nouveau nœud et appuyez sur **retourner**.|
|Ajouter un type spécifique de nœud d'élément de code à l'emplacement actuel du pointeur de la souris.|1.  Placez le pointeur à l'endroit sur la carte où vous souhaitez placer le nouvel élément de code et ouvrez le menu contextuel de la carte.<br />2.  Choisissez **modifier**, **ajouter**, puis sélectionnez le type de nœud que vous souhaitez.<br />3.  Tapez le nom pour le nouveau nœud et appuyez sur **retourner**.|
|Ajouter un type de nœud d'élément de code générique ou spécifique à un groupe.|1.  Sélectionnez le nœud de groupe et ouvrez le menu contextuel.<br />2.  Choisissez **modifier**, **ajouter**, puis sélectionnez le type de nœud que vous souhaitez.<br />3.  Tapez le nom pour le nouveau nœud et appuyez sur **retourner**.|
|Ajouter un nouveau nœud du même type et lié à partir d'un nœud existant.|1.  Sélectionnez l'élément de code. Une barre d'outils contextuelle s'affiche au-dessus de lui.<br />     ![Barre d’outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)<br />2.  Dans la barre d’outils, choisissez la deuxième icône **créer un nœud avec la même catégorie que ce nœud et ajouter un nouveau lien lui**.<br />3.  Choisissez un emplacement sur la carte où placer le nouvel élément de code et cliquez sur le bouton gauche de la souris.<br />4.  Tapez le nom pour le nouveau nœud et appuyez sur **retourner**.|
|Ajouter un nouveau nœud générique lié à partir d'un élément de code existant qui a le focus.|1.  À l’aide du clavier, appuyez sur **onglet** jusqu'à ce que l’élément de liaison à partir de code a le focus (rectangle en pointillé).<br />2.  Appuyez sur **Alt**+**insérer**.<br />3.  Tapez le nom pour le nouveau nœud et appuyez sur **retourner**.|
|Ajouter un nouveau nœud générique lié à un élément de code existant qui a le focus.|1.  À l’aide du clavier, appuyez sur **onglet** jusqu'à ce que l’élément de code pour lier a le focus (rectangle en pointillé).<br />2.  Appuyez sur **Alt**+**MAJ**+**insérer**.<br />3.  Tapez le nom pour le nouveau nœud et appuyez sur **retourner**.|

|**Pour ajouter des éléments de code pour**|**Procédez comme suit**|
|----------------------------------|-----------------------------|
|Éléments de code dans la solution.|1.  Recherchez l’élément de code dans **l’Explorateur de solutions**. Utilisez le **l’Explorateur de solutions** zone de recherche ou parcourez la solution. **Conseil :** pour rechercher des éléments de code qui ont des dépendances sur un type ou un membre, ouvrez le menu contextuel pour le type ou le membre dans **l’Explorateur de solutions**. Choisissez la relation qui vous intéresse. **L’Explorateur de solutions** montre uniquement les éléments de code avec les dépendances spécifiées.<br />2.  Faites glisser les éléments de code qui vous intéressent sur la surface de la carte. Vous pouvez aussi faire glisser des éléments de code à partir de l'Affichage de classes ou de l'Explorateur d'objets.<br />     ou<br />     Dans **l’Explorateur de solutions**, sélectionnez les éléments de code que vous voulez mapper. Puis, dans le **l’Explorateur de solutions** barre d’outils, cliquez sur **afficher sur la carte de Code**.<br /><br /> Par défaut, la hiérarchie du conteneur parent pour les nouveaux éléments de code est affichée sur la carte. Utilisez le **inclure les Parents** bouton sur la barre d’outils de carte de code pour modifier ce comportement. Si cette option est désactivée, seul l'élément de code proprement dit est ajouté à la carte. Pour inverser ce comportement pour qu’un glisser-déplacer des action, maintenez la **CTRL** lorsque vous faites glisser les éléments de code à la carte de clé.<br /><br /> Visual Studio ajoute les éléments de code pour les éléments de code de niveau supérieur de votre sélection. Pour voir si un élément de code contient d'autres éléments de code, déplacez le pointeur de la souris sur l'élément de code pour que le chevron (flèche Bas) apparaisse. Choisissez le chevron pour développer l'élément de code. Pour développer tous les éléments de code, appuyez sur **CTRL**+**A** pour sélectionner tous les éléments, ouvrez le menu contextuel de la carte, puis choisissez **groupe**, **développer** . Cette commande n'est pas disponible si le développement de tous les groupes génère une carte inutilisable ou des problèmes de mémoire.|
|Éléments de code associés à des éléments de code sur la carte.|Cliquez sur le **afficher les** bouton sur la barre d’outils de carte de code et choisissez le type d’éléments connexes vous intéressez.<br /><br /> ou<br /><br /> Ouvrez le menu contextuel de l'élément de code. Choisissez parmi les **afficher...**  éléments du menu en fonction du type de relation qui vous intéresse. Par exemple, vous pouvez afficher les éléments auxquels l'élément actif fait référence, les éléments qui font référence à l'élément actif, les types de base et dérivés pour les classes, les appelants de méthode et les classes, espaces de noms et assemblys conteneurs.<br /><br /> Pour plus d’informations, consultez [cette rubrique](../modeling/map-dependencies-across-your-solutions.md).|
|Assemblys compilés .NET (.dll ou .exe) ou binaires.|En dehors de Visual Studio, faites glisser les assemblys ou les binaires vers une carte.<br /><br /> Vous pouvez faire glisser à partir de l'Explorateur Windows ou de l'Explorateur de fichiers uniquement si vous exécutez l'un des deux et Visual Studio avec le même niveau d'autorisations de contrôle d'accès d'utilisateur (UAC). Par exemple, si le contrôle de compte d'utilisateur est activé et que vous exécutez Visual Studio en tant qu'administrateur, l'Explorateur Windows ou l'Explorateur de fichiers bloque l'opération glisser.|

###  <a name="AddNodes"></a>
##### <a name="add-a-link-between-existing-code-elements"></a>Ajouter un lien entre des éléments de code existants

1.  Sélectionnez l'élément de code source. Une barre d'outils apparaît au-dessus de l'élément de code.

     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)

2.  Dans la barre d’outils, choisissez la première icône **créer nouveau lien à partir de ce nœud vers lequel nœud lorsque vous cliquez sur Suivant**.

3.  Sélectionnez l'élément de code cible. Un lien apparaît entre les deux éléments de code.

 \- ou -

1.  Sélectionnez l'élément de code source sur la carte.

2.  Si une souris est installée, déplacez le pointeur en dehors des limites de la carte.

3.  Ouvrez le menu contextuel de l’élément de code et choisissez **modifier**, **ajouter**, **lien générique**.

4.  Accéder à l'élément de code cible à l'aide de la touche Tab et le sélectionner pour le lien.

5.  Appuyez sur **RETOUR**.

###  <a name="AddComments"></a>
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Ajouter un commentaire à un nœud existant sur la carte

1.  Sélectionnez l'élément de code. Une barre d'outils apparaît au-dessus de lui.

     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)

2.  Dans la barre d’outils, cliquez sur l’icône de tiers, **créer un nouveau nœud de commentaire avec un lien vers le nœud sélectionné**.

     \- ou -

     Ouvrez le menu contextuel de l’élément de code et choisissez **modifier**, **nouveau commentaire**.

3.  Tapez vos commentaires. Pour taper sur une nouvelle ligne, appuyez sur **MAJ** + **retourner**.

##### <a name="add-a-comment-to-the-map-itself"></a>Ajouter un commentaire à la carte elle-même

1.  Ouvrez le menu contextuel de la carte, sélectionnez **modifier**, **nouveau commentaire**.

2.  Tapez vos commentaires. Pour taper sur une nouvelle ligne, appuyez sur **MAJ** + **retourner**.

###  <a name="RenameNodes"></a>
##### <a name="rename-a-code-element-or-link"></a>Renommer un élément de code ou un lien

1.  Sélectionnez l'élément de code ou le lien que vous souhaitez renommer.

2.  Appuyez sur **F2**, ou ouvrez le menu contextuel et choisissez **modifier**, **renommer**.

3.  Quand la zone d'édition apparaît sur la carte, renommez l'élément de code ou le lien.

     \- ou -

4.  Ouvrez le menu contextuel et choisissez **modifier**, **propriétés**.

5.  Modifier la **étiquette** propriété dans la fenêtre Propriétés de Visual Studio.

##### <a name="remove-a-code-element-or-link-from-the-map"></a>Supprimer un élément de code ou un lien de la carte

1.  Sélectionnez l’élément de code ou de lien et d’appuyez sur la **supprimer** clé.

     \- ou -

     Ouvrez le menu contextuel pour l’élément de code ou des liens et choisissez **modifier**, **supprimer**.

2.  Si l’élément ou un lien fait partie d’un groupe, le **récupérer à nouveau les enfants** bouton ![icône récupérer à nouveau d’enfants](../modeling/media/dependencygraph_deletednodesicon.png) apparaît à l’intérieur du groupe. Cliquez dessus pour récupérer les liens et éléments manquants.

-   Vous pouvez supprimer des éléments de code et des liens d'une carte sans affecter le code sous-jacent. Quand vous les supprimez, leurs définitions sont supprimées du fichier DGML (.dgml).

-   Les cartes créées en modifiant le DGML, en ajoutant des éléments de code non définis ou en utilisant certaines versions antérieures de Visual Studio ne prennent pas en charge cette fonctionnalité.

##### <a name="flag-a-code-element-for-follow-up"></a>Marquer un élément de code pour le suivi

1.  Sélectionnez l'élément de code ou le lien à marquer pour le suivi.

2.  Ouvrez le menu contextuel et choisissez **modifier**, **indicateur pour le suivi**.

-   Par défaut, l'élément de code est affecté d'un arrière-plan rouge. Envisagez de [Ajout d’un commentaire](#AddComments) à l’aide d’informations de suivi appropriées.

-   Modifier la couleur d’arrière-plan de l’élément ou effacer l’indicateur de suivi en choisissant **modifier**, **autres couleurs**.

##  <a name="ChangeStyleCodeOrLink"></a> Modifier le style d’un élément de code ou un lien
 Vous pouvez modifier les icônes sur les éléments de code et les couleurs des éléments de code et des liens à l'aide de couleurs et d'icônes prédéfinies. Par exemple, vous pouvez choisir une couleur pour mettre en évidence des éléments de code et des liens ayant une certaine catégorie ou propriété. Vous pouvez ainsi identifier et vous concentrer sur des zones spécifiques de la carte. Vous pouvez spécifier des couleurs et des icônes personnalisées en modifiant le fichier .dgml de la carte ; consultez [les cartes de code de personnalisation en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Pour appliquer une icône ou couleur prédéfinie à des éléments de code ou des liens ayant une certaine catégorie ou propriété

1.  Dans la barre d’outils de la carte, choisissez **légende**.

2.  Dans le **légende** boîte, consultez si la catégorie d’élément de code ou la propriété apparaît déjà dans la liste.

3.  Si la liste n’inclut pas la catégorie ou la propriété, choisissez **+** dans les **légende** zone, puis choisissez **propriété de nœud**, **catégorie de nœud** , **Lier la propriété**, ou **lier catégorie**. Choisissez ensuite la propriété ou la catégorie. La catégorie ou la propriété apparaît maintenant dans le **légende** boîte.

    > [!NOTE]
    >  Pour créer et affecter une catégorie ou une propriété à un élément de code, vous pouvez modifier le fichier .dgml de la carte ; consultez [les cartes de code de personnalisation en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4.  Dans le **légende** zone, cliquez sur l’icône en regard de la catégorie ou la propriété que vous avez ajouté ou à modifier.

5.  Utilisez le tableau suivant pour sélectionner le style que vous voulez modifier :

    |**Pour modifier le**|**Choose**|
    |-----------------------|----------------|
    |Couleur d'arrière-plan|**Arrière-plan**|
    |Couleur du contour|**Trait**|
    |Couleur du texte (une lettre « f » s’affiche pour afficher le résultat)|**Premier plan**|
    |Icône|**Icônes**|

     Le **sélecteur de jeu de couleurs** ou **sélecteur de jeu icône** boîte de dialogue apparaît pour vous permettre de sélectionner une couleur ou une icône.

6.  Dans le **sélecteur de jeu de couleurs** ou **sélecteur de jeu icône** boîte de dialogue, effectuez l’une des opérations suivantes :

    |**Pour appliquer un**|**Procédez comme suit**|
    |--------------------|-----------------------------|
    |Jeu de couleurs ou d'icônes|Ouvrez le **sélectionnez couleur** (ou **icône**) **définir** liste. Sélectionnez un jeu de couleurs ou d'icônes.|
    |Couleur ou icône spécifique|Ouvrez la liste de valeurs des catégories ou des propriétés. Sélectionnez une couleur ou une icône.|

    > [!NOTE]
    >  Vous pouvez réorganiser, supprimer ou temporairement désactiver des styles dans les **légende** boîte. Consultez [modifier la zone de légende](#ModifyLegend).

##  <a name="ModifyLegend"></a> Modifiez la zone de légende
 Vous pouvez réorganiser, supprimer ou temporairement désactiver des styles dans les **légende** zone :

1.  Ouvrez le menu contextuel pour un style dans le **légende** boîte.

2.  Exécutez l’une des tâches suivantes :

    |**To**|**Choose**|
    |------------|----------------|
    |Désactiver l'élément de code|**Désactiver**|
    |Supprimer l'élément de code|**Supprimer**|
    |Déplacer le style vers le haut|**Déplacer vers le haut**|
    |Déplacer l'élément de code vers le bas|**Déplacer vers le bas**|

##  <a name="CopyLegend"></a> Styles de copie à partir d’un mappage à un autre

1.  Assurez-vous que le **légende** boîte apparaît sur la carte de code source. Si elle n’est pas visible, dans la barre d’outils de la carte, cliquez sur **légende**.

2.  Ouvrez le menu contextuel pour le **légende** boîte. Choisissez **copier la légende**.

3.  Collez la légende sur la carte cible.

##  <a name="MergeMaps"></a> Fusion des cartes de code
 Vous pouvez fusionner des cartes en copiant et en collant des éléments de code entre les cartes. Si les identificateurs d'éléments de code correspondent, le collage d'éléments de code fonctionne comme une opération de fusion. Pour simplifier cette tâche, placez tous les assemblys ou binaires que vous souhaitez visualiser dans le même dossier pour que le chemin d'accès complet de chaque assembly ou binaire soit le même pour chaque carte que vous souhaitez fusionner.

 Vous pouvez également faire glisser ces assemblys ou ces binaires vers la même carte à partir de ce dossier.

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Informations de référence sur le langage DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
