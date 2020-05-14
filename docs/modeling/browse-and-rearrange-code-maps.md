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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e38308c5bb94028fa17e78740da2b0df2779447
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302965"
---
# <a name="browse-and-rearrange-code-maps"></a>Parcourir et réorganiser des cartes de code

Réorganisez les éléments sur les cartes de code pour faciliter leur lecture et améliorer leurs performances.

Vous pouvez personnaliser les cartes de code sans affecter le code sous-jacent dans une solution. Cette opération est utile quand vous souhaitez vous concentrer sur des éléments de code clé ou communiquer vos idées concernant le code. Par exemple, pour mettre en surbrillance des zones intéressantes, vous pouvez sélectionner des éléments de code sur la carte et les filtrer, modifier le style des éléments de code et des liens, masquer ou supprimer des éléments de code et organiser les éléments de code à l'aide de propriétés, de catégories ou de groupes.

 **Configuration requise**

- Pour créer des cartes de code, vous devez disposer de Visual Studio Enterprise.

- Vous pouvez afficher des cartes de code et apporter des modifications mineures aux cartes de code dans Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a>Commencer à travailler avec des cartes de code

Créez une carte de code (voir [les dépendances de carte dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) pour plus de détails). Si vous ne voulez pas attendre que la carte finisse de générer, cliquez sur le lien **Annuler** à tout moment pour arrêter le processus de génération. Toutefois, dans ce cas vous ne verrez pas les détails de toutes les dépendances et tous les liens.

Une fois la carte générée, suivez ces conseils pour procéder à l'examen de votre code :

- Examinez les clusters de dépendances naturelles dans le code. Sur la barre d’outils de carte, choisissez **Layout**,](../modeling/media/quickclustersicon.gif) **Quick Clusters**![Quick Clusters bouton sur la barre d’outils graphique . Voir [Modifier la disposition de la carte](#Selecting).

     ![Graphique de dépendance &#45; mise en page Quick Clusters](../modeling/media/dependencygraph_quickclusters.png)

- Organisez la carte en zones plus petites en regroupant les nœuds connexes. Réduisez ces groupes pour afficher uniquement les dépendances intergroupes, qui sont affichées automatiquement. Voir [les nœuds du groupe](#OrganizeGroups).

- Utilisez des filtres pour simplifier la carte et vous concentrer sur les types de nœuds ou de liens qui vous intéressent. Voir [les nœuds filtres et les liens](#FilterNodes).

- Optimisez les performances des grandes cartes. Consultez [les dépendances de carte dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) pour plus d’informations. Par exemple, allumez **Skip Build** sur la barre d’outils de carte afin que Visual Studio ne reconstruise pas votre solution lorsque vous mettez à jour les éléments de la carte.

## <a name="change-the-map-layout"></a><a name="Selecting"></a>Modifier la disposition de la carte

|**À**|**Exécuter ces étapes**|
|-|-|
|Réorganiser le flux de dépendance pour l'ensemble de la carte dans un sens spécifique. Cela peut vous aider à distinguer les couches architecturales dans le code.|Sur la barre d’outils de carte, choisissez **Layout**, puis:<br /><br /> -   **Bouton** ![graphique de haut en bas de haut en bas](../modeling/media/topbottomgraphbutton.gif)<br />-   **Du bas en haut** ![du bas vers le bouton graphique supérieur](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Bouton de** ![mise en page de gauche à droite](../modeling/media/leftrightgraphbutton.gif)<br />-   **Bouton graphique de droite à gauche** ![à gauche](../modeling/media/rightleftgraphbutton.gif)|
|Afficher les clusters de dépendances naturelles dans le code avec les nœuds les plus dépendants au centre des clusters et les nœuds les moins dépendants à l'extérieur de ces clusters.|Sur la barre d’outils de carte, choisissez **Layout**, puis](../modeling/media/quickclustersicon.gif) **Quick Clusters**![Quick Clusters bouton sur la barre d’outils graphique .|
|Sélectionnez un ou plusieurs nœuds sur la carte.|Cliquez sur un nœud pour le sélectionner. Pour sélectionner ou désélectionner plus d’un nœud, maintenez **CTRL** en cliquant.<br /><br /> Clavier : appuyez sur **TAB** ou utilisez les touches fléchées pour déplacer le rectangle de mise au pointillé vers un nœud et appuyez sur **SPACE** pour le sélectionner. Appuyez sur **CTRL** + **SPACE** pour sélectionner ou désélectionner les nœuds.|
|Déplacer des nœuds spécifiques sur la carte.|Faites glisser les nœuds pour les déplacer. Pour déplacer d’autres nœuds et liens hors de la voie que vous traînez les nœuds, appuyez et maintenez la clé **SHIFT.**<br /><br /> Clavier : tenez **CTRL** et appuyez sur les touches fléchées.|
|Modifier la disposition à l'intérieur d'un groupe, indépendamment des autres nœuds et groupes sur la carte.|Sélectionnez un nœud et ouvrez le menu contextuel. Choisissez **Layout** et sélectionnez un style de mise en page.<br /><br /> - ou -<br /><br /> Sélectionnez un nœud et développez-le pour afficher les nœuds enfants. Cliquez sur le titre de nœud pour afficher la barre d’outils pop-up du groupe, et ouvrez le **changement le style de mise en page du graphique de**![dépendance de groupe &#45; barre d’outils de groupe &#45; liste de mise en page.](../modeling/media/dependencygraph_grouptoolbar.gif) Sélectionnez l’une des dispositions des arbres, **des amas rapides**ou **de la vue de liste** (qui organise le contenu du groupe dans une liste).<br /><br /> Voir [les nœuds du Groupe](#OrganizeGroups) pour plus de détails.|
|Annuler une action sur la carte.|Appuyez sur **CTRL** + **Z** ou utilisez la commande Visual Studio **Undo.**|

## <a name="browse-the-map"></a><a name="Explore"></a>Parcourir la carte

|**À**|**Exécuter ces étapes**|
|-|-|
|Parcourir la carte.|Faites glisser la carte dans n'importe quelle direction à l'aide de la souris.<br /><br /> - ou -<br /><br /> Maintenez **SHIFT** et faites pivoter la roue de la souris pour faire défiler horizontalement. Maintenez **SHIFT** + **CTRL** et faites pivoter la roue de la souris pour faire défiler horizontalement.|
|Effectuer un zoom avant ou arrière sur la carte.|Faites tourner la roulette de la souris.<br /><br /> - ou -<br /><br /> Utilisez la liste **d’abandon Zoom** sur la barre d’outils de la carte de code.<br /><br /> - ou -<br /><br /> Utilisez les raccourcis clavier. Pour zoomer, appuyez sur **CTRL et SHIFT .** (point). Pour effectuer un zoom arrière, appuyez sur **CTRL ET SHIFT ,** (virgule).|
|Effectuer un zoom avant sur une zone spécifique à l'aide de la souris.|Maintenez le bouton droit de la souris enfoncé pendant que vous dessinez un rectangle autour de la zone qui vous intéresse.|
|Redimensionner et ajuster la carte dans sa fenêtre.|Choisissez **Zoom to Fit dans** la liste **Zoom** sur la barre d’outils de la carte de code.<br /><br /> - ou -<br /><br /> Cliquez sur l’icône **Zoom pour s’adapter à** l’icône ![Zoom sur la barre d’outils](../modeling/media/almcodemapzoomicon.png) de la carte sur la barre d’outils de la carte de code. Clavier : appuyez sur **CTRL 0** (zéro).|
|Rechercher un nœud par nom sur la carte. **Conseil:**  Cela ne fonctionne que pour les éléments sur la carte. Pour trouver des éléments dans votre solution, mais pas sur la carte, les trouver dans **Solution Explorer**, puis les faire glisser vers la carte. (Faites glisser votre sélection, ou sur la barre d’outils **Solution Explorer,** cliquez **sur Afficher sur Code Map**).|1. Choisissez **Find** l’icône ![Trouver Trouver](../modeling/media/almcodemapfindicon.png) l’icône sur la barre d’outils de carte sur la barre d’outils de carte de code (Clavier : appuyez sur **CTRL - F**) pour afficher la boîte de recherche dans le coin supérieur droit de la carte.<br />2. Tapez le nom de l’élément et appuyez sur **Retour** ou cliquez sur l’icône " magnificateur ". Le premier élément qui correspond à votre recherche apparaît sélectionné sur la carte.<br />3. Pour personnaliser votre recherche, ouvrez la liste d’abandon et choisissez une option de recherche. Les options sont **Trouver prochaine**, **Trouver précédent**, et **sélectionnez tous**. Cliquez ensuite sur le bouton correspondant en regard de la zone de texte Rechercher.<br />     ![Les options de recherche abandonnent&#45;liste](../modeling/media/almcodemapssearchdropdown.png)<br />     Vous pouvez également utiliser le clavier : appuyez sur **F3** pour sélectionner le prochain nœud correspondant ou **SHIFT F3** pour sélectionner le nœud correspondant précédent.<br />4. Sélectionnez l’une des options qui spécifient comment les termes de recherche sont traités en cliquant sur les icônes ci-dessous la boîte à texte de recherche.<br />     ![Options de correspondance de recherche](../modeling/media/almcodemapssearchmatchicons.png)<br />     Les options disponibles sont, de gauche à droite, le respect de la casse pour la mise en correspondance, la recherche de mot entier uniquement, l'utilisation de la syntaxe d'expression régulière .NET et le développent automatique des groupes pour afficher les correspondances aux éléments entre parenthèses. **Important:**  Vous pouvez utiliser la boîte de recherche pour trouver des correspondances dans les groupes effondrés que si ces groupes ont été élargis précédemment. Pour rechercher ces correspondances et développer automatiquement leurs groupes parents, choisissez cette option sous la zone de recherche.|
|Sélectionner tous les nœuds non sélectionnés.|Ouvrez le menu contextuel pour les nœuds sélectionnés. Choisissez **Select**, **Sélection inversée**.|
|Sélectionner des nœuds supplémentaires qui pointent vers ceux sélectionnés.|Ouvrez le menu contextuel pour les nœuds sélectionnés. Choisissez **Select** et l’un d’eux:<br /><br /> - Pour sélectionner des nœuds supplémentaires qui se lient directement au nœud sélectionné, choisissez **les dépendances entrantes**.<br />- Pour sélectionner des nœuds supplémentaires qui lient directement à partir du nœud sélectionné, choisissez **des dépendances sortantes**.<br />- Pour sélectionner des nœuds supplémentaires qui lient directement vers et à partir du nœud sélectionné, choisissez **les deux**.<br />- Pour sélectionner tous les nœuds qui lient vers et à partir du nœud sélectionné, choisissez **Connected Subgraph**.<br />- Pour sélectionner tous les enfants du nœud sélectionné, choisissez **des enfants**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a>Filtrer les nœuds et les liens

|**À**|**Exécuter ces étapes**|
|-|-|
|Afficher ou masquer le volet Filtres.|Choisissez le bouton **Filtres** sur la barre d’outils de la carte de code. Le volet **Filters** est affiché sous forme de page tabbed dans **Solution Explorer**, par défaut.|
|Filtrer les types de nœuds affichés sur la carte.|Réglez ou effacez les case box dans la liste **des éléments de code** dans le volet Filtres.|
|Filtrer les types de liens affichés sur la carte.|Réglez ou effacez les case box dans la liste **des relations** dans le volet Filtres.|
|Afficher ou masquer les nœuds de projet de test sur la carte.|Réglez ou effacez la case à cocher **Test Assets** dans la liste **divers** dans le volet Filtres.|

Les icônes affichées dans le volet Légende de la carte reflètent les paramètres spécifiés dans la liste. Pour afficher ou masquer le panneau Legend, cliquez sur le bouton **Legend** sur la barre d’outils de la carte de code.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a>Examiner les nœuds et les liens

Les cartes de code affichent les types de liens suivants :

- Un lien individuel représente une relation unique entre deux nœuds.

- Un lien entre les groupes représente une relation entre deux nœuds de différents groupes.

- Un lien global représente toutes les relations qui pointent dans la même direction entre deux groupes.

> [!TIP]
> Par défaut, la carte affiche les liens entre les groupes uniquement pour les nœuds sélectionnés. Pour modifier ce comportement pour afficher ou masquer les liens agrégés entre les groupes, cliquez sur **Layout** sur la barre d’outils de la carte de code et choisissez **Advanced**, puis **afficher tous les liens cross-group** ou **masquer tous les liens cross-group**. Voir [Cachez ou montrez des nœuds et des liens](#HidingShowing) pour plus de détails.

|**À**|**Exécuter ces étapes**|
|-|-|
|Afficher plus d'informations sur un nœud ou un lien.|Déplacez le pointeur de la souris sur le nœud ou le lien jusqu'à ce qu'une info-bulle apparaisse.<br /><br /> L'info-bulle d'un lien global répertorie chaque dépendance qu'il représente.<br /><br /> - ou -<br /><br /> Ouvrez le menu contextuel du nœud ou du lien. Choisissez **Edit**, **Propriétés**.|
|Afficher ou masquer le contenu d'un groupe.|- Pour élargir un groupe, ouvrir le menu raccourci pour le nœud et choisir **Groupe**, **Expand**.<br />     - ou -<br />     Déplacez le pointeur de la souris sur le nœud jusqu'à ce que le bouton chevron (flèche Bas) apparaisse. Cliquez sur ce bouton pour développer le groupe. Clavier : pour élargir ou effondrer le groupe**+** sélectionné, appuyez**-** sur la clé **PLUS** ( ) ou la clé **MINUS** ().<br />- Pour effondrer un groupe, ouvrez le menu raccourci pour le nœud et choisissez **Group**, **Collapse**.<br />     - ou -<br />     Déplacez le pointeur de la souris sur un groupe jusqu'à ce que le bouton chevron (flèche Haut) apparaisse. Cliquez sur ce bouton pour réduire le groupe.<br />- Pour élargir tous les groupes, appuyez sur **CTRL** + **A** pour sélectionner tous les nœuds. Ouvrez le menu raccourci pour la carte et choisissez **Group**, **Expand**. **Note:**      Cette commande n’est pas disponible si l’expansion de tous les groupes génère une carte inutilisable ou des problèmes de mémoire. Nous vous recommandons de développer la carte uniquement au niveau de détail qui vous intéresse.<br />- Pour effondrer tous les groupes, ouvrez le menu raccourci pour un nœud ou pour la carte. Choisissez **Le groupe**, Collapse **All**.|
|Voir la définition de code pour un espace de noms, un type ou un membre.|Ouvrez le menu raccourci pour le nœud et choisissez **Go To Definition**.<br /><br /> -ou-<br /><br /> Double-cliquez sur le nœud. Pour les groupes développés, double-cliquez sur l'en-tête de groupe.<br /><br /> -ou-<br /><br /> Sélectionnez le nœud et appuyez sur **F12**.<br /><br /> Par exemple :<br /><br /> - Pour un espace de nom contenant une classe, le fichier de code de la classe s’ouvre pour afficher la définition de cette classe. Dans d’autres cas, la fenêtre **Résultats du symbole De trouver** affiche une liste de fichiers de code. **Note:**      Lorsque vous effectuez cette tâche sur un espace de nom Visual Basic, le fichier de code derrière l’espace de nom ne s’ouvre pas. Ce problème se produit également lorsque vous effectuez cette tâche sur un groupe de nœuds sélectionnés qui comprennent un espace de nom visual basic. Pour contourner ce problème, accédez manuellement au fichier code-behind de l'espace de noms ou omettez le nœud de l'espace de noms de votre sélection.<br />- Pour une classe ou une classe partielle, le fichier de code de cette classe s’ouvre pour afficher la définition de classe.<br />- Pour une méthode, le fichier de code de la classe parente s’ouvre pour afficher la définition de la méthode.|
|Examiner les dépendances et les éléments qui participent à un lien global.|Sélectionnez les liens qui vous intéressent et ouvrez le menu raccourci pour votre sélection. Choisissez **Afficher les liens contributifs** ou afficher les liens **contributifs sur la nouvelle carte de code**.<br /><br /> Visual Studio développe les groupes aux deux extrémités du lien et affiche uniquement les éléments et les dépendances qui participent au lien. **Note:**  Lorsque vous examinez les dépendances entre les éléments en groupes partiels, vous pouvez voir ce comportement: <ul><li>Les liens vers des éléments qui ne participent pas à votre examen disparaissent de la carte, même si ces liens existent toujours.</li><li>Supposez que vous examinez un lien vers un élément dans un groupe partiel et que vous examinez ensuite un autre lien vers le même élément. Lors de votre second examen, le groupe partiel cible montre uniquement les éléments issus de votre premier examen. Liens et éléments cibles qui n’ont pas participé à votre premier examen, mais qui participent à votre deuxième examen, ne s’affichent pas.</li></ul> Pour voir les éléments manquants d’un groupe,](../modeling/media/dependencygraph_deletednodesicon.png) choisissez **Refetch Children**![Refetch Children Icon (qui indique que tous les membres d’un groupe n’apparaissent pas sur la carte). Vous pouvez également essayer de défaire vos actions (Clavier: appuyez sur **CTRL-Z**) et d’examiner les dépendances sur une nouvelle carte.|
|Examiner les dépendances entre plusieurs nœuds de différents groupes.|Développez les groupes pour afficher tous leurs enfants. Sélectionnez tous les nœuds qui vous intéressent, y compris leurs enfants. La carte affiche les liens entre les groupes entre les nœuds sélectionnés.<br /><br /> Pour sélectionner tous les nœuds d’un groupe, appuyez et maintenez LE bouton **SHIFT** et le bouton de la souris gauche pendant que vous dessinez un rectangle autour de ce groupe. Pour sélectionner tous les nœuds sur une carte, appuyez sur **CTRL**+**A**. **Conseil:**  Pour afficher les liens multi-groupes en tout temps, choisissez **Layout** sur la barre d’outils de la carte, **Advanced**, **Afficher tous les liens cross-Group**.|
|Afficher les éléments auxquels un nœud ou un lien fait référence.|Ouvrez le menu raccourci pour le nœud et choisissez **Trouver toutes les références**. **Note:**  Cela ne s’applique que lorsque l’attribut `Reference` est défini pour le nœud ou le lien dans le fichier .dgml de la carte. Pour ajouter des références à des éléments provenant de nœuds ou de liens, consultez [les cartes de code Customize en éditant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a>Masquer ou montrer des nœuds et des liens

Masquer des nœuds les empêche de participer aux algorithmes de disposition. Par défaut, les liens entre les groupes sont masqués. Les liens entre les groupes sont des liens individuels qui relient vos nœuds entre différents groupes. Quand les groupes sont réduits, la carte rassemble tous les liens entre les groupes sous forme de liens uniques. Lorsque vous développez un groupe et sélectionnez des nœuds dans le groupe, les liens entre les groupes apparaissent et mettent en exergue les dépendances dans ce groupe.

> [!CAUTION]
> Avant de partager une carte créée dans Visual Studio Enterprise avec des personnes qui utilisent Visual Studio Professional, veillez à afficher tous les nœuds et liens entre les groupes que vous souhaitez qu'elles puissent voir. Sinon, ces utilisateurs ne pourront pas afficher ces éléments.

### <a name="to-hide-or-show-nodes"></a>Pour masquer ou afficher les nœuds

|**À**|**Exécuter ces étapes**|
|-|-|
|Masquer les nœuds sélectionnés.|1. Sélectionnez les nœuds que vous voulez cacher.<br />2. Ouvrez le menu raccourci pour les nœuds sélectionnés ou pour la carte. Choisissez **Select**, **Masquez Sélectionné**.|
|Masquer les nœuds non sélectionnés.|1. Sélectionnez les nœuds que vous souhaitez rester visibles.<br />2. Ouvrez le menu raccourci pour les nœuds sélectionnés ou pour la carte. Choisissez **Select**, **Masquer non sélectionné .**|
|Afficher les nœuds masqués.|- Pour montrer tous les nœuds cachés à l’intérieur d’un groupe, assurez-vous d’abord que le groupe est élargi. Ouvrez le menu raccourci et choisissez **Select**, **Unhide Children**.<br />     - ou -<br />     Cliquez sur **l’icône Unhide Children**![Unhide Children Icon](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) dans le coin supérieur gauche du groupe (ce n’est visible que lorsqu’il y a des nœuds cachés).<br />- Pour afficher tous les nœuds cachés, ouvrez le menu raccourci pour la carte ou un nœud et choisissez **Select**, **Unhide All**.|

### <a name="to-hide-or-show-links"></a>Pour masquer ou afficher les liens

|**À**|**Dans la barre d'outils de la carte, choisissez Disposition, Avancé, puis**|
|-|-|
|Afficher en permanence les liens entre les groupes.|**Afficher tous les liens cross-group**. Cela masque les liens globaux entre les groupes.|
|Masquer en permanence les liens entre les groupes.|**Masquer tous les liens entre les groupes**|
|Afficher uniquement les liens entre les groupes pour les nœuds sélectionnés.|**Afficher les liens entre les groupes sur les nœuds sélectionnés**|
|Masquer tous les liens.|**Cachez tous les liens**. Pour réafficher les liens, choisissez l'une des options mentionnées ci-dessus.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a>Nœuds de groupe

|**À**|**Exécuter ces étapes**|
|-|-|
|Afficher les nœuds conteneurs comme nœuds de groupe ou nœuds feuille.|Pour montrer les nœuds de récipient comme nœuds de feuilles : sélectionnez les nœuds, ouvrez le menu de raccourci pour votre sélection, et choisissez **Group**, **Convert To Leaf**.<br /><br /> Pour afficher les nœuds de conteneurs comme nœuds de groupe : sélectionnez les nœuds, ouvrez le menu raccourci pour votre sélection, et choisissez **Group**, **Convert To Group**.|
|Modifier la disposition à l'intérieur d'un groupe.|Sélectionnez le groupe, ouvrez le menu raccourci, choisissez **Layout**et sélectionnez le style de mise en page que vous voulez.<br /><br /> - ou -<br /><br /> 1. Sélectionnez le groupe et assurez-vous qu’il est élargi.<br />2. Cliquez à nouveau sur l’en-tête du groupe et la barre d’outils du groupe apparaît.<br />     ![Graphique de dépendance &#45; barre d’outils de groupe](../modeling/media/dependencygraph_group.png)<br />3. Ouvrez le **changement le style de mise en page du** graphique de dépendance de liste ![de groupe &#45; barre d’outils de groupe &#45; la mise en page](../modeling/media/dependencygraph_grouptoolbar.gif) et choisissez le style de mise en page que vous voulez.<br /><br /> **List View** réorganise les membres du groupe dans la liste. **Graphique Par défaut** réinitialise la disposition du groupe à la disposition par défaut de la carte. Pour d’autres options, voir [Modifier la disposition de la carte](#Selecting).|
|Ajouter un nœud à un groupe.|Faites glisser le nœud dans le groupe.<br /><br /> Pendant que vous faites glisser le nœud, Visual Studio affiche un indicateur qui montre que vous déplacez le nœud.<br /><br /> Vous pouvez également faire glisser des nœuds en dehors d'un groupe.|
|Ajouter un nœud à un nœud non-groupe.|Faites glisser le nœud dans le nœud cible. Vous pouvez convertir n'importe quel nœud cible en un groupe en y ajoutant des nœuds.|
|Regrouper les nœuds sélectionnés.|1. Sélectionnez les nœuds que vous souhaitez regrouper. Une barre d'outils contextuelle s'affiche au-dessus du dernier nœud que vous sélectionnez.<br />     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)<br />2. Sur la barre d’outils, choisissez le quatrième groupe d’icônes **les nœuds sélectionnés** (si le nœud est élargi, il aura cinq au lieu de quatre icônes). Tapez le nom du nouveau groupe et appuyez sur **Return**.<br />     - ou -<br />     Sélectionnez les nœuds que vous souhaitez regrouper et ouvrez le menu contextuel de votre sélection. Choisissez **Group**, **Ajouter Parent Group**, tapez le nom pour le nouveau groupe, et appuyez sur **Retour**.<br /><br /> Vous pouvez renommer un groupe. Ouvrez le menu raccourci pour le groupe et choisissez **Edit**, **Propriétés** pour ouvrir la fenêtre Visual Studio Properties. Dans la propriété **Label,** renommer le groupe au besoin.|
|Supprimer des groupes.|Sélectionnez le groupe ou les groupes que vous souhaitez supprimer. Ouvrez le menu raccourci pour votre sélection et choisissez **Group**, **Remove Group**.|
|Supprimer des nœuds de leur groupe parent.|Sélectionnez les nœuds que vous voulez déplacer. Ouvrez le menu raccourci pour votre sélection et choisissez **Group**, **Remove From Parent**. Cette opération supprime les nœuds jusqu'à leur grand-parent ou jusqu'en dehors du groupe s'ils n'ont aucun groupe grand-parent.<br /><br /> - ou -<br /><br /> Sélectionnez les nœuds et faites-les glisser hors du groupe.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a>Ajouter, supprimer ou renommer les nœuds, les liens et les commentaires

Vous pouvez afficher plus ou moins d'éléments sur une carte pour la détailler ou la simplifier. Vous pouvez aussi renommer des éléments et y ajouter des commentaires.

> [!CAUTION]
> Avant de partager une carte créée à l'aide de Visual Studio Enterprise avec des personnes qui utilisent Visual Studio Professional, veillez à ce que les éléments de code que vous souhaitez que les autres puissent voir soient visibles sur la carte. Sinon, ces utilisateurs ne pourront pas récupérer les éléments de code supprimés.

### <a name="add-a-node-for-a-code-element"></a>Ajouter un nœud pour un élément de code

|**À**|**Exécuter ces étapes**|
|-|-|
|Ajouter un nouveau nœud générique à l'emplacement actuel du pointeur de la souris.|1. Déplacez le pointeur de souris à l’endroit sur la carte où vous voulez mettre le nouvel élément de code et appuyez **sur Insert**.<br />     - ou -<br />     Ouvrez le menu raccourci pour la carte et choisissez **Edit**, **Ajouter**, **Nœud générique**.<br />2. Tapez le nom pour le nouveau nœud et appuyez sur **Retour**.|
|Ajouter un type spécifique de nœud d'élément de code à l'emplacement actuel du pointeur de la souris.|1. Déplacez le pointeur de souris à l’endroit sur la carte où vous voulez mettre le nouvel élément de code et ouvrir le menu raccourci pour la carte.<br />2. Choisissez **Modifier,** **Ajouter,** et sélectionnez le type de nœud que vous voulez.<br />3. Tapez le nom pour le nouveau nœud et appuyez sur **Retour**.|
|Ajouter un type de nœud d'élément de code générique ou spécifique à un groupe.|1. Sélectionnez le nœud de groupe et ouvrez le menu raccourci.<br />2. Choisissez **Modifier,** **Ajouter,** et sélectionnez le type de nœud que vous voulez.<br />3. Tapez le nom pour le nouveau nœud et appuyez sur **Retour**.|
|Ajouter un nouveau nœud du même type et lié à partir d'un nœud existant.|1. Sélectionnez l’élément code. Une barre d'outils contextuelle s'affiche au-dessus de lui.<br />     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)<br />2. Sur la barre d’outils, choisissez la deuxième icône **Créer un nœud avec la même catégorie que ce nœud et ajouter un nouveau lien à elle**.<br />3. Choisissez un endroit sur la carte pour mettre le nouvel élément de code et cliquez sur le bouton de la souris gauche.<br />4. Tapez le nom pour le nouveau nœud et appuyez sur **Retour**.|
|Ajouter un nouveau nœud générique lié à partir d'un élément de code existant qui a le focus.|1. À l’aide du clavier, appuyez sur **Tab** jusqu’à ce que l’élément de code à lier a la mise au point (rectangle pointillé).<br />2. Appuyez sur **Alt**+**Insert**.<br />3. Tapez le nom pour le nouveau nœud et appuyez sur **Retour**.|
|Ajouter un nouveau nœud générique lié à un élément de code existant qui a le focus.|1. À l’aide du clavier, appuyez sur **Tab** jusqu’à ce que l’élément de code pour lier a la mise au point (rectangle pointillé).<br />2. Appuyez sur **Alt**+**Shift**+**Insert**.<br />3. Tapez le nom pour le nouveau nœud et appuyez sur **Retour**.|

|**Pour ajouter des éléments de code pour**|**Exécuter ces étapes**|
|-|-|
|Éléments de code dans la solution.|1. Trouver l’élément de code dans **Solution Explorer**. Utilisez la boîte de recherche **Solution Explorer** ou parcourez la solution. **Conseil:**      Pour trouver des éléments de code qui ont des dépendances sur un type ou un membre, ouvrez le menu raccourci pour le type ou le membre dans **Solution Explorer**. Choisissez la relation qui vous intéresse. **Solution Explorer** n’affiche que les éléments de code avec les dépendances spécifiées.<br />2. Faites glisser les éléments de code qui vous intéressent à la surface de la carte. Vous pouvez aussi faire glisser des éléments de code à partir de l'Affichage de classes ou de l'Explorateur d'objets.<br />     - ou -<br />     Dans **Solution Explorer**, sélectionnez les éléments de code que vous souhaitez cartographier. Ensuite, sur la barre d’outils **Solution Explorer,** cliquez **sur Afficher sur Code Map**.<br /><br /> Par défaut, la hiérarchie du conteneur parent pour les nouveaux éléments de code est affichée sur la carte. Utilisez le bouton **Inclure les parents** sur la barre d’outils de la carte de code pour modifier ce comportement. Si cette option est désactivée, seul l'élément de code proprement dit est ajouté à la carte. Pour inverser ce comportement pour une seule action de traînée et de baisse, appuyez et maintenez la clé **CTRL** pendant que vous faites glisser les éléments de code à la carte.<br /><br /> Visual Studio ajoute les éléments de code pour les éléments de code de niveau supérieur de votre sélection. Pour voir si un élément de code contient d'autres éléments de code, déplacez le pointeur de la souris sur l'élément de code pour que le chevron (flèche Bas) apparaisse. Choisissez le chevron pour développer l'élément de code. Pour étendre tous les éléments de code, appuyez sur **CTRL**+**A** pour sélectionner tous les éléments, ouvrir le menu raccourci pour la carte, et choisir **Group**, **Expand**. Cette commande n'est pas disponible si le développement de tous les groupes génère une carte inutilisable ou des problèmes de mémoire.|
|Éléments de code associés à des éléments de code sur la carte.|Cliquez sur le bouton Afficher le bouton **Afficher la** carte de code sur la barre d’outils de la carte de code et choisir le type d’éléments connexes qui vous intéresse.<br /><br /> - ou -<br /><br /> Ouvrez le menu contextuel de l'élément de code. Choisissez l’un des éléments du **Salon ...** éléments sur le menu en fonction du genre de relation qui vous intéresse. Par exemple, vous pouvez afficher les éléments auxquels l'élément actif fait référence, les éléments qui font référence à l'élément actif, les types de base et dérivés pour les classes, les appelants de méthode et les classes, espaces de noms et assemblys conteneurs.<br /><br /> Pour plus de détails, voir [ce sujet](../modeling/map-dependencies-across-your-solutions.md).|
|Assemblys compilés .NET (.dll ou .exe) ou binaires.|En dehors de Visual Studio, faites glisser les assemblys ou les binaires vers une carte.<br /><br /> Vous pouvez faire glisser à partir de l'Explorateur Windows ou de l'Explorateur de fichiers uniquement si vous exécutez l'un des deux et Visual Studio avec le même niveau d'autorisations de contrôle d'accès d'utilisateur (UAC). Par exemple, si le contrôle de compte d’utilisateur est activé et que vous exécutez Visual Studio en tant qu’administrateur, l’Explorateur Windows ou l’Explorateur de fichiers bloque l’opération de glissement.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Ajouter un lien entre des éléments de code existants

1. Sélectionnez l'élément de code source. Une barre d'outils apparaît au-dessus de l'élément de code.

    ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)

2. Sur la barre d’outils, choisissez la première icône, **Créez un nouveau lien à partir de ce nœud auquel jamais nœud que vous cliquez sur la prochaine**.

3. Sélectionnez l'élément de code cible. Un lien apparaît entre les deux éléments de code.

**Ou**

1. Sélectionnez l'élément de code source sur la carte.

2. Si une souris est installée, déplacez le pointeur en dehors des limites de la carte.

3. Ouvrez le menu raccourci de l’élément code et choisissez **Edit** > **Add** > **Generic Link**.

4. Accéder à l'élément de code cible à l'aide de la touche Tab et le sélectionner pour le lien.

5. Appuyez sur **Entrée**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Ajouter un commentaire à un nœud existant sur la carte

1. Sélectionnez l'élément de code. Une barre d'outils apparaît au-dessus de lui.

     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)

2. Sur la barre d’outils, choisissez la troisième icône, **Créez un nouveau nœud de commentaire avec un nouveau lien vers le nœud sélectionné.**

     \- ou -

     Ouvrez le menu raccourci pour l’élément code et choisissez **Edit** > **New Comment**.

3. Tapez vos commentaires. Pour taper sur une nouvelle ligne, appuyez sur **Shift** + **Enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Ajouter un commentaire à la carte elle-même

1. Ouvrez le menu raccourci pour la carte et choisissez **Edit** > **New Comment**.

2. Tapez vos commentaires. Pour taper sur une nouvelle ligne, appuyez sur **Shift** + **Enter**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Renommer un élément de code ou un lien

1. Sélectionnez l'élément de code ou le lien que vous souhaitez renommer.

2. Appuyez sur **F2**, ou ouvrez le menu raccourci et choisissez **Edit** > **Rename**.

3. Quand la zone d'édition apparaît sur la carte, renommez l'élément de code ou le lien.

**Ou**

1. Ouvrez le menu raccourci et choisissez **Edit** > **Properties**.

2. Modifier la propriété **Label** dans la fenêtre Visual Studio Properties.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Supprimer un élément de code ou un lien de la carte

1. Sélectionnez l’élément de code ou le lien et appuyez sur la clé **Supprimer.**

     \- ou -

     Ouvrez le menu raccourci pour l’élément code ou le lien et choisissez **Edit** > **Supprimer**.

2. Si l’élément ou le lien fait partie d’un groupe, le bouton ![ **Refetch Children** Icon](../modeling/media/dependencygraph_deletednodesicon.png) réféléise les enfants apparaît à l’intérieur du groupe. Cliquez dessus pour récupérer les liens et éléments manquants.

- Vous pouvez supprimer des éléments de code et des liens d'une carte sans affecter le code sous-jacent. Quand vous les supprimez, leurs définitions sont supprimées du fichier DGML (.dgml).

- Les cartes créées en modifiant le DGML, en ajoutant des éléments de code non définis ou en utilisant certaines versions antérieures de Visual Studio ne prennent pas en charge cette fonctionnalité.

#### <a name="flag-a-code-element-for-follow-up"></a>Marquer un élément de code pour le suivi

1. Sélectionnez l'élément de code ou le lien à marquer pour le suivi.

2. Ouvrez le menu raccourci et choisissez **Edit** > **Flag pour le suivi**.

- Par défaut, l'élément de code est affecté d'un arrière-plan rouge. Envisagez [d’y ajouter un commentaire](#AddComments) avec les renseignements de suivi appropriés.

- Modifier la couleur de fond de l’élément ou effacer le drapeau de suivi en choisissant **Edit** > **Autres couleurs de drapeau**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a>Modifier le style d’un élément de code ou d’un lien

Vous pouvez modifier les icônes sur les éléments de code et les couleurs des éléments de code et des liens à l'aide de couleurs et d'icônes prédéfinies. Par exemple, vous pouvez choisir une couleur pour mettre en évidence des éléments de code et des liens ayant une certaine catégorie ou propriété. Vous pouvez ainsi identifier et vous concentrer sur des zones spécifiques de la carte. Vous pouvez spécifier des icônes et des couleurs personnalisées en éditant le fichier .dgml de la carte; voir [personnaliser les cartes de code en éditant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Pour appliquer une icône ou couleur prédéfinie à des éléments de code ou des liens ayant une certaine catégorie ou propriété

1. Sur la barre d’outils de la carte, choisissez **Legend**.

2. Dans la boîte **Legend,** voir si la catégorie ou la propriété de l’élément code apparaît déjà dans la liste.

3. Si la liste n’inclut pas **+** la catégorie ou la propriété, choisissez dans la boîte **Legend,** alors choisissez **Node Property**, **Node Category**, **Link Property**, ou **Link Category**. Choisissez ensuite la propriété ou la catégorie. La catégorie ou la propriété apparaît maintenant dans la boîte **Legend.**

    > [!NOTE]
    > Pour créer et attribuer une catégorie ou une propriété à un élément de code, vous pouvez modifier le fichier .dgml de la carte ; voir [personnaliser les cartes de code en éditant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. Dans la boîte **Legend,** cliquez sur l’icône à côté de la catégorie ou de la propriété que vous avez ajoutée ou que vous souhaitez changer.

5. Utilisez le tableau suivant pour sélectionner le style que vous voulez modifier :

    |**Pour modifier l'élément suivant**|**Choisir**|
    |-|-|
    |Couleur d'arrière-plan|**Fond**|
    |Couleur du contour|**Course**|
    |Couleur de texte (une lettre "f" est affichée pour montrer le résultat)|**Premier plan**|
    |Icône|**Icônes**|

     La boîte de dialogue **Color Set Picker** ou **Icon Set Picker** vous apparaît pour sélectionner une couleur ou une icône.

6. Dans la boîte de dialogue **Color Set Picker** ou **Icon Set Picker,** faites l’une des suivantes :

    |**Pour appliquer l'élément suivant**|**Exécuter ces étapes**|
    |-|-|
    |Jeu de couleurs ou d'icônes|Ouvrez la liste **de la** **couleur Select** (ou **icône).** Sélectionnez un jeu de couleurs ou d'icônes.|
    |Couleur ou icône spécifique|Ouvrez la liste de valeurs des catégories ou des propriétés. Sélectionnez une couleur ou une icône.|

    > [!NOTE]
    > Vous pouvez réorganiser, supprimer ou désactiver temporairement les styles dans la boîte **Legend.** Voir [Modifier la boîte Legend](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a>Modifier la boîte Legend

Vous pouvez réorganiser, supprimer ou désactiver temporairement les styles dans la boîte **Legend** :

1. Ouvrez le menu raccourci pour un style dans la boîte **Legend.**

2. Exécutez l’une des tâches suivantes :

    |**À**|**Choisir**|
    |-|-|
    |Désactiver l'élément de code|**Disable**|
    |Supprimer l'élément de code|**Supprimer**|
    |Déplacer le style vers le haut|**Monter**|
    |Déplacer l'élément de code vers le bas|**Descendre**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a>Copier les styles d’une carte à l’autre

1. Assurez-vous que la boîte **Legend** apparaît sur la carte source. Si elle n’est pas visible, sur la barre d’outils de la carte, cliquez sur **Legend**.

2. Ouvrez le menu raccourci pour la boîte **Legend.** Choisissez **Copy Legend**.

3. Collez la légende sur la carte cible.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a>Fusionner les cartes de code

Vous pouvez fusionner des cartes en copiant et en collant des éléments de code entre les cartes. Si les identificateurs d'éléments de code correspondent, le collage d'éléments de code fonctionne comme une opération de fusion. Pour simplifier cette tâche, placez tous les assemblys ou binaires que vous souhaitez visualiser dans le même dossier pour que le chemin d'accès complet de chaque assembly ou binaire soit le même pour chaque carte que vous souhaitez fusionner.

Vous pouvez également faire glisser ces assemblys ou ces binaires vers la même carte à partir de ce dossier.

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Informations de référence sur le langage DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
