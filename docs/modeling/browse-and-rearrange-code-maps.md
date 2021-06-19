---
title: Parcourir et réorganiser des cartes de code
description: Découvrez comment vous pouvez réorganiser des éléments sur des cartes de code pour les rendre plus faciles à lire et améliorer leurs performances.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83132cfccd0af7244cf31f502669144eb3388bd8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385550"
---
# <a name="browse-and-rearrange-code-maps"></a>Parcourir et réorganiser des cartes de code

Réorganisez les éléments sur les cartes de code pour faciliter leur lecture et améliorer leurs performances.

Vous pouvez personnaliser les cartes de code sans affecter le code sous-jacent dans une solution. Cette opération est utile quand vous souhaitez vous concentrer sur des éléments de code clé ou communiquer vos idées concernant le code. Par exemple, pour mettre en surbrillance des zones intéressantes, vous pouvez sélectionner des éléments de code sur la carte et les filtrer, modifier le style des éléments de code et des liens, masquer ou supprimer des éléments de code et organiser les éléments de code à l'aide de propriétés, de catégories ou de groupes.

 **Configuration requise**

- Pour créer des cartes de code, vous devez disposer de Visual Studio Enterprise.

- Vous pouvez afficher des cartes de code et apporter des modifications mineures aux cartes de code dans Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Prise en main de l’utilisation des cartes de code

Créer une carte de code (pour plus d’informations, consultez [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) ). Si vous ne souhaitez pas attendre la fin de la génération de la carte, cliquez sur le lien **Annuler** à tout moment pour arrêter le processus de génération. Toutefois, dans ce cas vous ne verrez pas les détails de toutes les dépendances et tous les liens.

Une fois la carte générée, suivez ces conseils pour procéder à l'examen de votre code :

- Examinez les clusters de dépendances naturelles dans le code. Dans la barre d’outils de la carte, choisissez **disposition** **, clusters rapides** ![ clusters rapides sur la barre d’outils du graphique ](../modeling/media/quickclustersicon.gif) . Consultez [modifier la disposition de la carte](#Selecting).

     ![Graphique de dépendance &#45; disposition de clusters rapides](../modeling/media/dependencygraph_quickclusters.png)

- Organisez la carte en zones plus petites en regroupant les nœuds connexes. Réduisez ces groupes pour afficher uniquement les dépendances intergroupes, qui sont affichées automatiquement. Consultez [regrouper les nœuds](#OrganizeGroups).

- Utilisez des filtres pour simplifier la carte et vous concentrer sur les types de nœuds ou de liens qui vous intéressent. Consultez [Filtrer les nœuds et les liens](#FilterNodes).

- Optimisez les performances des grandes cartes. Pour plus d’informations, consultez [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) . Par exemple, activez **ignorer la génération** dans la barre d’outils de la carte afin que Visual Studio ne régénère pas votre solution lorsque vous mettez à jour des éléments sur la carte.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Modifier la disposition de la carte

|**To**|**Exécuter ces étapes**|
|-|-|
|Réorganiser le flux de dépendance pour l'ensemble de la carte dans un sens spécifique. Cela peut vous aider à distinguer les couches architecturales dans le code.|Dans la barre d’outils de la carte, choisissez **disposition**, puis :<br /><br /> -   **De haut en bas** ![ Bouton graphique de haut en bas](../modeling/media/topbottomgraphbutton.gif)<br />-   **De bas en haut** ![ Bouton graphique de bas en haut](../modeling/media/bottomtopgraphbutton.gif)<br />-   **De gauche à droite** ![ Bouton de disposition de gauche à droite](../modeling/media/leftrightgraphbutton.gif)<br />-   **De droite à gauche** ![ Bouton de droite à gauche du graphique](../modeling/media/rightleftgraphbutton.gif)|
|Afficher les clusters de dépendances naturelles dans le code avec les nœuds les plus dépendants au centre des clusters et les nœuds les moins dépendants à l'extérieur de ces clusters.|Dans la barre d’outils de la carte, choisissez **disposition**, puis **clusters** rapides clusters ![ rapides sur la barre d’outils du graphique ](../modeling/media/quickclustersicon.gif) .|
|Sélectionnez un ou plusieurs nœuds sur la carte.|Cliquez sur un nœud pour le sélectionner. Pour sélectionner ou désélectionner plusieurs nœuds, maintenez la **touche Ctrl** enfoncée tout en cliquant.<br /><br /> Clavier : Appuyez sur la touche **Tab** ou utilisez les touches de direction pour déplacer le rectangle de focus en pointillés vers un nœud et appuyez sur **espace** pour le sélectionner. Appuyez sur **CTRL**  +  **Space** pour sélectionner ou désélectionner des nœuds.|
|Déplacer des nœuds spécifiques sur la carte.|Faites glisser les nœuds pour les déplacer. Pour déplacer d’autres nœuds et liens à mesure que vous faites glisser des nœuds, appuyez sur la touche **MAJ** et maintenez-la enfoncée.<br /><br /> Clavier : maintenez la **touche Ctrl** enfoncée et appuyez sur les touches de direction.|
|Modifier la disposition à l'intérieur d'un groupe, indépendamment des autres nœuds et groupes sur la carte.|Sélectionnez un nœud et ouvrez le menu contextuel. Choisissez **disposition** et sélectionnez un style de disposition.<br /><br /> - ou -<br /><br /> Sélectionnez un nœud et développez-le pour afficher les nœuds enfants. Cliquez sur le titre du nœud pour afficher la barre d’outils contextuelle du groupe, puis ouvrez la barre d’outils **modifier le style de disposition du graphique de dépendance du** groupe ![ &#45; &#45; disposition ](../modeling/media/dependencygraph_grouptoolbar.gif) . Sélectionnez l’une des dispositions en arborescence, **clusters rapides** ou **mode liste** (qui réorganise le contenu du groupe en une liste).<br /><br /> Pour plus d’informations, consultez [regrouper des nœuds](#OrganizeGroups) .|
|Annuler une action sur la carte.|Appuyez sur **CTRL**  +  **Z** ou utilisez la commande **Annuler** de Visual Studio.|

## <a name="browse-the-map"></a><a name="Explore"></a> Parcourir la carte

|**To**|**Exécuter ces étapes**|
|-|-|
|Parcourir la carte.|Faites glisser la carte dans n'importe quelle direction à l'aide de la souris.<br /><br /> - ou -<br /><br /> Maintenez la **touche Maj** enfoncée et faites tourner la roulette de la souris pour faire défiler horizontalement. Maintenez la touche **MAJ** enfoncée  +   et faites tourner la roulette de la souris pour faire défiler horizontalement.|
|Effectuer un zoom avant ou arrière sur la carte.|Faites tourner la roulette de la souris.<br /><br /> - ou -<br /><br /> Utilisez la liste déroulante **Zoom** dans la barre d’outils de la carte de code.<br /><br /> - ou -<br /><br /> Utilisez les raccourcis clavier. Pour effectuer un zoom avant, appuyez sur **Ctrl + Maj +.** (point). Pour effectuer un zoom arrière, appuyez sur **Ctrl + Maj +,** (virgule).|
|Effectuer un zoom avant sur une zone spécifique à l'aide de la souris.|Maintenez le bouton droit de la souris enfoncé pendant que vous dessinez un rectangle autour de la zone qui vous intéresse.|
|Redimensionner et ajuster la carte dans sa fenêtre.|Choisissez **Zoom pour ajuster** à la liste **Zoom** dans la barre d’outils de la carte de code.<br /><br /> - ou -<br /><br /> Cliquez sur l’icône zoom **pour ajuster la taille** ![ de la barre d’outils de ](../modeling/media/almcodemapzoomicon.png) la carte de code. Clavier : Appuyez sur **Ctrl + 0** (zéro).|
|Rechercher un nœud par nom sur la carte. **Conseil :**  Cela fonctionne uniquement pour les éléments sur la carte. Pour rechercher des éléments dans votre solution, mais pas sur la carte, recherchez-les dans **Explorateur de solutions**, puis faites-les glisser vers la carte. (Faites glisser votre sélection ou, dans la barre d’outils **Explorateur de solutions** , cliquez sur **afficher sur la carte de code**).|1. **Choisissez l’icône de recherche icône** de recherche ![ dans la barre d’outils ](../modeling/media/almcodemapfindicon.png) de la carte de code (clavier : Appuyez sur **Ctrl + F**) pour afficher la zone de recherche dans le coin supérieur droit de la carte.<br />2. tapez le nom de l’élément et appuyez sur la touche **retour** ou cliquez sur l’icône « Loupe ». Le premier élément qui correspond à votre recherche apparaît sélectionné sur la carte.<br />3. pour personnaliser votre recherche, ouvrez la liste déroulante et choisissez une option de recherche. Les options disponibles sont **suivant**, **précédent** et **Sélectionner tout**. Cliquez ensuite sur le bouton correspondant en regard de la zone de texte Rechercher.<br />     ![Liste déroulante&#45;options de recherche](../modeling/media/almcodemapssearchdropdown.png)<br />     Vous pouvez également utiliser le clavier : Appuyez sur **F3** pour sélectionner le nœud correspondant suivant ou sur **Maj + F3** pour sélectionner le nœud correspondant précédent.<br />4. Sélectionnez l’une des options qui spécifient le mode de traitement des termes de recherche en cliquant sur les icônes sous la zone de texte Rechercher.<br />     ![Options de correspondance de recherche](../modeling/media/almcodemapssearchmatchicons.png)<br />     Les options disponibles sont, de gauche à droite, le respect de la casse pour la mise en correspondance, la recherche de mot entier uniquement, l'utilisation de la syntaxe d'expression régulière .NET et le développent automatique des groupes pour afficher les correspondances aux éléments entre parenthèses. **Important :**  Vous pouvez utiliser la zone de recherche pour rechercher les correspondances dans les groupes réduits uniquement si ces groupes ont été développés précédemment. Pour rechercher ces correspondances et développer automatiquement leurs groupes parents, choisissez cette option sous la zone de recherche.|
|Sélectionner tous les nœuds non sélectionnés.|Ouvrez le menu contextuel pour les nœuds sélectionnés. Choisissez **Sélectionner**, **inverser la sélection**.|
|Sélectionner des nœuds supplémentaires qui pointent vers ceux sélectionnés.|Ouvrez le menu contextuel pour les nœuds sélectionnés. Choisissez **Sélectionner** et l’une des opérations suivantes :<br /><br /> -Pour sélectionner des nœuds supplémentaires qui sont directement liés au nœud sélectionné, choisissez **dépendances entrantes**.<br />-Pour sélectionner des nœuds supplémentaires qui sont directement liés à partir du nœud sélectionné, choisissez **dépendances sortantes**.<br />-Pour sélectionner des nœuds supplémentaires qui sont directement liés à et à partir du nœud sélectionné, choisissez **les deux**.<br />-Pour sélectionner tous les nœuds qui lient vers et depuis le nœud sélectionné, choisissez sous- **graphique connecté**.<br />-Pour sélectionner tous les enfants du nœud sélectionné, choisissez **enfants**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Filtrer les nœuds et les liens

|**To**|**Exécuter ces étapes**|
|-|-|
|Afficher ou masquer le volet Filtres.|Cliquez sur le bouton **filtres** dans la barre d’outils de la carte de code. Par défaut, le volet **filtres** s’affiche sous la forme d’une page à onglets dans **Explorateur de solutions**.|
|Filtrer les types de nœuds affichés sur la carte.|Activez ou désactivez les cases à cocher dans la liste **éléments de code** du volet filtres.|
|Filtrer les types de liens affichés sur la carte.|Activez ou désactivez les cases à cocher de la liste **relations** dans le volet filtres.|
|Afficher ou masquer les nœuds de projet de test sur la carte.|Activez ou désactivez la case à cocher **éléments de test** dans la liste **divers** du volet filtres.|

Les icônes affichées dans le volet Légende de la carte reflètent les paramètres spécifiés dans la liste. Pour afficher ou masquer le panneau légende, cliquez sur le bouton **légende** dans la barre d’outils de la carte de code.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Examiner les nœuds et les liens

Les cartes de code affichent les types de liens suivants :

- Un lien individuel représente une relation unique entre deux nœuds.

- Un lien entre les groupes représente une relation entre deux nœuds de différents groupes.

- Un lien global représente toutes les relations qui pointent dans la même direction entre deux groupes.

> [!TIP]
> Par défaut, la carte affiche les liens entre les groupes uniquement pour les nœuds sélectionnés. Pour modifier ce comportement afin d’afficher ou de masquer les liens agrégés entre les groupes, cliquez sur **disposition** dans la barre d’outils de la carte de code et choisissez **avancé**, puis **Afficher tous les liens entre les groupes** ou **masquer tous les liens entre les** groupes. Pour plus d’informations [, consultez masquer ou afficher les nœuds et les liens](#HidingShowing) .

|**To**|**Exécuter ces étapes**|
|-|-|
|Afficher plus d'informations sur un nœud ou un lien.|Déplacez le pointeur de la souris sur le nœud ou le lien jusqu'à ce qu'une info-bulle apparaisse.<br /><br /> L'info-bulle d'un lien global répertorie chaque dépendance qu'il représente.<br /><br /> - ou -<br /><br /> Ouvrez le menu contextuel du nœud ou du lien. Choisissez **modifier**, **Propriétés**.|
|Afficher ou masquer le contenu d'un groupe.|-Pour développer un groupe, ouvrez le menu contextuel du nœud, puis choisissez **groupe**, **développer**.<br />     - ou -<br />     Déplacez le pointeur de la souris sur le nœud jusqu'à ce que le bouton chevron (flèche Bas) apparaisse. Cliquez sur ce bouton pour développer le groupe. Clavier : pour développer ou réduire le groupe sélectionné, appuyez sur la touche **plus** ( **+** ) ou sur la touche **moins** ( **-** ).<br />-Pour réduire un groupe, ouvrez le menu contextuel du nœud et choisissez **groupe**, **réduire**.<br />     - ou -<br />     Déplacez le pointeur de la souris sur un groupe jusqu'à ce que le bouton chevron (flèche Haut) apparaisse. Cliquez sur ce bouton pour réduire le groupe.<br />-Pour développer tous les groupes, appuyez sur **CTRL**  +  **A** pour sélectionner tous les nœuds. Ouvrez le menu contextuel de la carte, puis choisissez **groupe**, **développer**. **Remarque :**      Cette commande n’est pas disponible si le développement de tous les groupes génère une carte inutilisable ou des problèmes de mémoire. Nous vous recommandons de développer la carte uniquement au niveau de détail qui vous intéresse.<br />-Pour réduire tous les groupes, ouvrez le menu contextuel d’un nœud ou de la carte. Choisissez **groupe**, **réduire tout**.|
|Voir la définition de code pour un espace de noms, un type ou un membre.|Ouvrez le menu contextuel du nœud et choisissez **atteindre la définition**.<br /><br /> -ou-<br /><br /> Double-cliquez sur le nœud. Pour les groupes développés, double-cliquez sur l'en-tête de groupe.<br /><br /> -ou-<br /><br /> Sélectionnez le nœud et appuyez sur **F12**.<br /><br /> Exemple :<br /><br /> -Pour un espace de noms contenant une classe, le fichier de code de la classe s’ouvre et affiche la définition de cette classe. Dans d’autres cas, la fenêtre résultats de la **recherche de symbole** affiche une liste de fichiers de code. **Remarque :**      Lorsque vous effectuez cette tâche sur un espace de noms Visual Basic, le fichier de code derrière l’espace de noms ne s’ouvre pas. Ce problème se produit également lorsque vous effectuez cette tâche sur un groupe de nœuds sélectionnés qui incluent un espace de noms Visual Basic. Pour contourner ce problème, accédez manuellement au fichier code-behind de l'espace de noms ou omettez le nœud de l'espace de noms de votre sélection.<br />-Pour une classe ou une classe partielle, le fichier de code pour cette classe s’ouvre et affiche la définition de classe.<br />-Pour une méthode, le fichier de code de la classe parente s’ouvre pour afficher la définition de la méthode.|
|Examiner les dépendances et les éléments qui participent à un lien global.|Sélectionnez les liens qui vous intéressent et ouvrez le menu contextuel de votre sélection. Choisissez **afficher les liens de contribution**  ou **afficher les liens de contribution sur la nouvelle carte de code**.<br /><br /> Visual Studio développe les groupes aux deux extrémités du lien et affiche uniquement les éléments et les dépendances qui participent au lien. **Remarque :**  Lorsque vous examinez les dépendances entre des éléments dans des groupes partiels, vous pouvez voir ce comportement : <ul><li>Les liens vers des éléments qui ne font pas partie de votre examen disparaissent de la carte, même si ces liens existent toujours.</li><li>Supposez que vous examinez un lien vers un élément dans un groupe partiel et que vous examinez ensuite un autre lien vers le même élément. Lors de votre second examen, le groupe partiel cible montre uniquement les éléments issus de votre premier examen. Les liens et les éléments cibles qui n’ont pas participé à votre premier examen, mais qui participent à votre deuxième examen, n’apparaissent pas.</li></ul> Pour afficher les éléments manquants d’un groupe, choisissez **réextraire** ![ les enfants réextraire les enfants icône ](../modeling/media/dependencygraph_deletednodesicon.png) (ce qui indique que tous les membres d’un groupe n’apparaissent pas sur la carte). Vous pouvez également essayer d’annuler vos actions (clavier : Appuyez sur **Ctrl + Z**) et examinez les dépendances sur un nouveau mappage.|
|Examiner les dépendances entre plusieurs nœuds de différents groupes.|Développez les groupes pour afficher tous leurs enfants. Sélectionnez tous les nœuds qui vous intéressent, y compris leurs enfants. La carte affiche les liens entre les groupes entre les nœuds sélectionnés.<br /><br /> Pour sélectionner tous les nœuds d’un groupe, maintenez la **touche Maj** enfoncée et le bouton gauche de la souris tout en dessinant un rectangle autour de ce groupe. Pour sélectionner tous les nœuds d’une carte, appuyez sur **CTRL** + **a**. **Conseil :**  Pour afficher les liens entre les groupes à tout moment, choisissez **disposition** dans la barre d’outils de la carte, **avancé**, **Afficher tous les liens entre les groupes**.|
|Afficher les éléments auxquels un nœud ou un lien fait référence.|Ouvrez le menu contextuel du nœud, puis choisissez **Rechercher toutes les références**. **Remarque :**  Cela s’applique uniquement lorsque l' `Reference` attribut est défini pour le nœud ou le lien dans le fichier. dgml de la carte. Pour ajouter des références à des éléments à partir de nœuds ou de liens, consultez [personnaliser les cartes de code en modifiant les fichiers dgml](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Masquer ou afficher les nœuds et les liens

Masquer des nœuds les empêche de participer aux algorithmes de disposition. Par défaut, les liens entre les groupes sont masqués. Les liens entre les groupes sont des liens individuels qui relient vos nœuds entre différents groupes. Quand les groupes sont réduits, la carte rassemble tous les liens entre les groupes sous forme de liens uniques. Lorsque vous développez un groupe et sélectionnez des nœuds dans le groupe, les liens entre les groupes apparaissent et mettent en exergue les dépendances dans ce groupe.

> [!CAUTION]
> Avant de partager une carte créée dans Visual Studio Enterprise avec des personnes qui utilisent Visual Studio Professional, veillez à afficher tous les nœuds et liens entre les groupes que vous souhaitez qu'elles puissent voir. Sinon, ces utilisateurs ne pourront pas afficher ces éléments.

### <a name="to-hide-or-show-nodes"></a>Pour masquer ou afficher les nœuds

|**To**|**Exécuter ces étapes**|
|-|-|
|Masquer les nœuds sélectionnés.|1. Sélectionnez les nœuds que vous souhaitez masquer.<br />2. Ouvrez le menu contextuel pour les nœuds sélectionnés ou pour la carte. Choisissez **Sélectionner**, **Masquer les sélections**.|
|Masquer les nœuds non sélectionnés.|1. Sélectionnez les nœuds que vous souhaitez conserver visibles.<br />2. Ouvrez le menu contextuel pour les nœuds sélectionnés ou pour la carte. Choisissez **Sélectionner**, **Masquer non sélectionné**.|
|Afficher les nœuds masqués.|-Pour afficher tous les nœuds masqués à l’intérieur d’un groupe, assurez-vous d’abord que le groupe est développé. Ouvrez le menu contextuel et choisissez **Sélectionner**, **afficher les enfants**.<br />     - ou -<br />     Cliquez sur l’icône d’affichage **des enfants afficher** les enfants ![ ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) dans le coin supérieur gauche du groupe (visible uniquement lorsqu’il y a des nœuds enfants masqués).<br />-Pour afficher tous les nœuds masqués, ouvrez le menu contextuel de la carte ou d’un nœud, puis choisissez **Sélectionner**, **Afficher tout**.|

### <a name="to-hide-or-show-links"></a>Pour masquer ou afficher les liens

|**To**|**Dans la barre d'outils de la carte, choisissez Disposition, Avancé, puis**|
|-|-|
|Afficher en permanence les liens entre les groupes.|**Affiche tous les liens entre les groupes**. Cela masque les liens globaux entre les groupes.|
|Masquer en permanence les liens entre les groupes.|**Masquer tous les liens entre les groupes**|
|Afficher uniquement les liens entre les groupes pour les nœuds sélectionnés.|**Afficher les liens entre les groupes sur les nœuds sélectionnés**|
|Masquer tous les liens.|**Masquer tous les liens**. Pour réafficher les liens, choisissez l'une des options mentionnées ci-dessus.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Nœuds de groupe

|**To**|**Exécuter ces étapes**|
|-|-|
|Afficher les nœuds conteneurs comme nœuds de groupe ou nœuds feuille.|Pour afficher les nœuds conteneurs en tant que nœuds terminaux : sélectionnez les nœuds, ouvrez le menu contextuel de votre sélection, puis choisissez **groupe**, **convertir en feuille**.<br /><br /> Pour afficher les nœuds conteneurs en tant que nœuds de groupe : sélectionnez les nœuds, ouvrez le menu contextuel de votre sélection, puis choisissez **groupe**, **convertir en groupe**.|
|Modifier la disposition à l'intérieur d'un groupe.|Sélectionnez le groupe, ouvrez le menu contextuel, choisissez **disposition**, puis sélectionnez le style de disposition souhaité.<br /><br /> - ou -<br /><br /> 1. Sélectionnez le groupe et assurez-vous qu’il est développé.<br />2. cliquez à nouveau sur l’en-tête du groupe pour afficher la barre d’outils du groupe.<br />     ![Graphique de dépendance &#45; barre d’outils de groupe](../modeling/media/dependencygraph_group.png)<br />3. Ouvrez la barre d’outils **modifier le style de disposition du graphique de dépendance de la liste de groupes** ![ &#45; &#45; disposition ](../modeling/media/dependencygraph_grouptoolbar.gif) et choisissez le style de disposition souhaité.<br /><br /> Le **mode liste** réorganise les membres du groupe dans la liste. La **valeur par défaut du graphique** rétablit la disposition par défaut de la carte. Pour d’autres options, consultez [modifier la disposition de la carte](#Selecting).|
|Ajouter un nœud à un groupe.|Faites glisser le nœud dans le groupe.<br /><br /> Pendant que vous faites glisser le nœud, Visual Studio affiche un indicateur qui montre que vous déplacez le nœud.<br /><br /> Vous pouvez également faire glisser des nœuds en dehors d'un groupe.|
|Ajouter un nœud à un nœud non-groupe.|Faites glisser le nœud dans le nœud cible. Vous pouvez convertir n'importe quel nœud cible en un groupe en y ajoutant des nœuds.|
|Regrouper les nœuds sélectionnés.|1. Sélectionnez les nœuds que vous souhaitez regrouper. Une barre d'outils contextuelle s'affiche au-dessus du dernier nœud que vous sélectionnez.<br />     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)<br />2. dans la barre d’outils, choisissez la quatrième icône **Grouper les nœuds sélectionnés** (si le nœud est développé, il aura cinq icônes au lieu de quatre). Tapez le nom du nouveau groupe, puis appuyez sur **retour**.<br />     - ou -<br />     Sélectionnez les nœuds que vous souhaitez regrouper et ouvrez le menu contextuel de votre sélection. Choisissez **groupe**, **Ajouter un groupe parent**, tapez le nom du nouveau groupe, puis appuyez sur **retour**.<br /><br /> Vous pouvez renommer un groupe. Ouvrez le menu contextuel du groupe, puis choisissez **modifier**, **Propriétés** pour ouvrir la fenêtre Propriétés Visual Studio. Dans la propriété **étiquette** , renommez le groupe selon les besoins.|
|Supprimer des groupes.|Sélectionnez le groupe ou les groupes que vous souhaitez supprimer. Ouvrez le menu contextuel de votre sélection et choisissez **groupe**, **supprimer le groupe**.|
|Supprimer des nœuds de leur groupe parent.|Sélectionnez les nœuds que vous voulez déplacer. Ouvrez le menu contextuel de votre sélection et choisissez **groupe**, **supprimer du parent**. Cette opération supprime les nœuds jusqu'à leur grand-parent ou jusqu'en dehors du groupe s'ils n'ont aucun groupe grand-parent.<br /><br /> - ou -<br /><br /> Sélectionnez les nœuds et faites-les glisser hors du groupe.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Ajouter, supprimer ou renommer des nœuds, des liens et des commentaires

Vous pouvez afficher plus ou moins d'éléments sur une carte pour la détailler ou la simplifier. Vous pouvez aussi renommer des éléments et y ajouter des commentaires.

> [!CAUTION]
> Avant de partager une carte créée à l'aide de Visual Studio Enterprise avec des personnes qui utilisent Visual Studio Professional, veillez à ce que les éléments de code que vous souhaitez que les autres puissent voir soient visibles sur la carte. Sinon, ces utilisateurs ne pourront pas récupérer les éléments de code supprimés.

### <a name="add-a-node-for-a-code-element"></a>Ajouter un nœud pour un élément de code

|**To**|**Exécuter ces étapes**|
|-|-|
|Ajouter un nouveau nœud générique à l'emplacement actuel du pointeur de la souris.|1. Placez le pointeur de la souris à l’emplacement de la carte où vous souhaitez placer le nouvel élément de code et appuyez sur **Inser**.<br />     - ou -<br />     Ouvrez le menu contextuel de la carte et choisissez **modifier**, **Ajouter**, **nœud générique**.<br />2. tapez le nom du nouveau nœud, puis appuyez sur **retour**.|
|Ajouter un type spécifique de nœud d'élément de code à l'emplacement actuel du pointeur de la souris.|1. Placez le pointeur de la souris à l’emplacement de la carte où vous souhaitez placer le nouvel élément de code et ouvrez le menu contextuel de la carte.<br />2. Choisissez **modifier**, **Ajouter**, puis sélectionnez le type de nœud souhaité.<br />3. tapez le nom du nouveau nœud et appuyez sur **retour**.|
|Ajouter un type de nœud d'élément de code générique ou spécifique à un groupe.|1. Sélectionnez le nœud Groupe et ouvrez le menu contextuel.<br />2. Choisissez **modifier**, **Ajouter**, puis sélectionnez le type de nœud souhaité.<br />3. tapez le nom du nouveau nœud et appuyez sur **retour**.|
|Ajouter un nouveau nœud du même type et lié à partir d'un nœud existant.|1. Sélectionnez l’élément de code. Une barre d'outils contextuelle s'affiche au-dessus de lui.<br />     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)<br />2. dans la barre d’outils, choisissez la deuxième icône **créer un nœud avec la même catégorie que ce nœud et lui ajouter un nouveau lien**.<br />3. Choisissez un emplacement sur la carte pour placer le nouvel élément de code, puis cliquez sur le bouton gauche de la souris.<br />4. tapez le nom du nouveau nœud et appuyez sur **retour**.|
|Ajouter un nouveau nœud générique lié à partir d'un élément de code existant qui a le focus.|1. à l’aide du clavier, appuyez sur la touche **Tab** jusqu’à ce que l’élément de code à partir duquel le lien a été activé (rectangle en pointillés).<br />2. Appuyez sur **ALT** + **Inser**.<br />3. tapez le nom du nouveau nœud et appuyez sur **retour**.|
|Ajouter un nouveau nœud générique lié à un élément de code existant qui a le focus.|1. à l’aide du clavier, appuyez sur la touche **Tab** jusqu’à ce que l’élément de code à lier ait le focus (rectangle en pointillés).<br />2. Appuyez sur **ALT** + **MAJ** + **Inser**.<br />3. tapez le nom du nouveau nœud et appuyez sur **retour**.|

|**Pour ajouter des éléments de code pour**|**Exécuter ces étapes**|
|-|-|
|Éléments de code dans la solution.|1. Recherchez l’élément de code dans **Explorateur de solutions**. Utilisez la zone de recherche **Explorateur de solutions** ou parcourez la solution. **Conseil :**      Pour rechercher des éléments de code qui ont des dépendances sur un type ou un membre, ouvrez le menu contextuel du type ou du membre dans **Explorateur de solutions**. Choisissez la relation qui vous intéresse. **Explorateur de solutions** affiche uniquement les éléments de code avec les dépendances spécifiées.<br />2. faites glisser les éléments de code qui vous intéressent à la surface de la carte. Vous pouvez aussi faire glisser des éléments de code à partir de l'Affichage de classes ou de l'Explorateur d'objets.<br />     - ou -<br />     Dans **Explorateur de solutions**, sélectionnez les éléments de code que vous souhaitez mapper. Puis, dans la barre d’outils **Explorateur de solutions** , cliquez sur **afficher sur la carte de code**.<br /><br /> Par défaut, la hiérarchie du conteneur parent pour les nouveaux éléments de code est affichée sur la carte. Utilisez le bouton **inclure les parents** dans la barre d’outils de la carte de code pour modifier ce comportement. Si cette option est désactivée, seul l'élément de code proprement dit est ajouté à la carte. Pour inverser ce comportement pour une seule action de glisser-déplacer, appuyez sur la touche **CTRL** et maintenez-la enfoncée pendant que vous faites glisser les éléments de code sur la carte.<br /><br /> Visual Studio ajoute les éléments de code pour les éléments de code de niveau supérieur de votre sélection. Pour voir si un élément de code contient d'autres éléments de code, déplacez le pointeur de la souris sur l'élément de code pour que le chevron (flèche Bas) apparaisse. Choisissez le chevron pour développer l'élément de code. Pour développer tous les éléments de code, appuyez sur **CTRL** + **A** pour sélectionner tous les éléments, ouvrez le menu contextuel de la carte, puis choisissez **groupe**, **développer**. Cette commande n'est pas disponible si le développement de tous les groupes génère une carte inutilisable ou des problèmes de mémoire.|
|Éléments de code associés à des éléments de code sur la carte.|Cliquez sur le bouton afficher les éléments **associés** dans la barre d’outils de la carte de code et choisissez le type d’éléments associés qui vous intéressent.<br /><br /> - ou -<br /><br /> Ouvrez le menu contextuel de l'élément de code. Choisissez l’un des éléments **Show...** dans le menu en fonction du type de relation qui vous intéresse. Par exemple, vous pouvez afficher les éléments auxquels l'élément actif fait référence, les éléments qui font référence à l'élément actif, les types de base et dérivés pour les classes, les appelants de méthode et les classes, espaces de noms et assemblys conteneurs.<br /><br /> Pour plus d’informations, consultez [cette rubrique](../modeling/map-dependencies-across-your-solutions.md).|
|Assemblys compilés .NET (.dll ou .exe) ou binaires.|En dehors de Visual Studio, faites glisser les assemblys ou les binaires vers une carte.<br /><br /> Vous pouvez faire glisser à partir de l'Explorateur Windows ou de l'Explorateur de fichiers uniquement si vous exécutez l'un des deux et Visual Studio avec le même niveau d'autorisations de contrôle d'accès d'utilisateur (UAC). Par exemple, si le contrôle de compte d’utilisateur est activé et que vous exécutez Visual Studio en tant qu’administrateur, l’Explorateur Windows ou l’Explorateur de fichiers bloque l’opération de glissement.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Ajouter un lien entre des éléments de code existants

1. Sélectionnez l'élément de code source. Une barre d'outils apparaît au-dessus de l'élément de code.

    ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)

2. Dans la barre d’outils, choisissez la première icône, **puis créer un lien à partir de ce nœud vers lequel vous cliquez sur suivant**.

3. Sélectionnez l'élément de code cible. Un lien apparaît entre les deux éléments de code.

**OR**

1. Sélectionnez l'élément de code source sur la carte.

2. Si une souris est installée, déplacez le pointeur en dehors des limites de la carte.

3. Ouvrez le menu contextuel de l’élément de code et choisissez **modifier**  >  **Ajouter** un  >  **lien générique**.

4. Accéder à l'élément de code cible à l'aide de la touche Tab et le sélectionner pour le lien.

5. Appuyez sur **Entrée**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Ajouter un commentaire à un nœud existant sur la carte

1. Sélectionnez l'élément de code. Une barre d'outils apparaît au-dessus de lui.

     ![Barre d'outils du graphique de dépendance](../modeling/media/depedencygraph_toolbar.png)

2. Dans la barre d’outils, choisissez la troisième icône, puis **créez un nouveau nœud de commentaire avec un nouveau lien vers le nœud sélectionné**.

     \- ou -

     Ouvrez le menu contextuel de l’élément de code et choisissez **modifier** le  >  **Nouveau commentaire**.

3. Tapez vos commentaires. Pour taper sur une nouvelle ligne, appuyez sur **MAJ**  +  **entrée**.

#### <a name="add-a-comment-to-the-map-itself"></a>Ajouter un commentaire à la carte elle-même

1. Ouvrez le menu contextuel de la carte et choisissez **modifier** le  >  **Nouveau commentaire**.

2. Tapez vos commentaires. Pour taper sur une nouvelle ligne, appuyez sur **MAJ**  +  **entrée**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Renommer un élément de code ou un lien

1. Sélectionnez l'élément de code ou le lien que vous souhaitez renommer.

2. Appuyez sur **F2**, ou ouvrez le menu contextuel et choisissez **modifier**  >  **Renommer**.

3. Quand la zone d'édition apparaît sur la carte, renommez l'élément de code ou le lien.

**OR**

1. Ouvrez le menu contextuel et choisissez **modifier** les  >  **Propriétés**.

2. Modifiez la propriété **étiquette** dans le fenêtre Propriétés Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Supprimer un élément de code ou un lien de la carte

1. Sélectionnez l’élément de code ou le lien, puis appuyez sur la touche **Suppr** .

     \- ou -

     Ouvrez le menu contextuel de l’élément de code ou du lien, puis choisissez **modifier**  >  **supprimer**.

2. Si l’élément ou le lien fait partie d’un groupe, le bouton **récupérer** à la récupération des enfants ![ ](../modeling/media/dependencygraph_deletednodesicon.png) apparaît à l’intérieur du groupe. Cliquez dessus pour récupérer les liens et éléments manquants.

- Vous pouvez supprimer des éléments de code et des liens d'une carte sans affecter le code sous-jacent. Quand vous les supprimez, leurs définitions sont supprimées du fichier DGML (.dgml).

- Les cartes créées en modifiant le DGML, en ajoutant des éléments de code non définis ou en utilisant certaines versions antérieures de Visual Studio ne prennent pas en charge cette fonctionnalité.

#### <a name="flag-a-code-element-for-follow-up"></a>Marquer un élément de code pour le suivi

1. Sélectionnez l'élément de code ou le lien à marquer pour le suivi.

2. Ouvrez le menu contextuel et choisissez **modifier** l'  >  **indicateur pour suivi**.

- Par défaut, l'élément de code est affecté d'un arrière-plan rouge. Envisagez de lui [Ajouter un commentaire](#AddComments) avec les informations de suivi appropriées.

- Modifiez la couleur d’arrière-plan de l’élément ou effacez l’indicateur de suivi en sélectionnant **modifier** d'  >  **autres couleurs d’indicateur**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Modifier le style d’un lien ou d’un élément de code

Vous pouvez modifier les icônes sur les éléments de code et les couleurs des éléments de code et des liens à l'aide de couleurs et d'icônes prédéfinies. Par exemple, vous pouvez choisir une couleur pour mettre en évidence des éléments de code et des liens ayant une certaine catégorie ou propriété. Vous pouvez ainsi identifier et vous concentrer sur des zones spécifiques de la carte. Vous pouvez spécifier des icônes et des couleurs personnalisées en modifiant le fichier. dgml de la carte. consultez [personnaliser les cartes de code en modifiant les fichiers dgml](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Pour appliquer une icône ou couleur prédéfinie à des éléments de code ou des liens ayant une certaine catégorie ou propriété

1. Dans la barre d’outils de la carte, choisissez **légende**.

2. Dans la zone **légende** , vérifiez si la catégorie ou la propriété de l’élément de code figure déjà dans la liste.

3. Si la liste n’inclut pas la catégorie ou la propriété, choisissez **+** dans la zone **légende** , puis choisissez **propriété de nœud**, catégorie de **nœud**, **propriété de lien** ou **catégorie de lien**. Choisissez ensuite la propriété ou la catégorie. La catégorie ou la propriété apparaît maintenant dans la zone **légende** .

    > [!NOTE]
    > Pour créer et assigner une catégorie ou une propriété à un élément de code, vous pouvez modifier le fichier. dgml de la carte ; consultez [personnaliser les cartes de code en modifiant les fichiers dgml](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. Dans la zone **légende** , cliquez sur l’icône en regard de la catégorie ou de la propriété que vous avez ajoutée ou que vous souhaitez modifier.

5. Utilisez le tableau suivant pour sélectionner le style que vous voulez modifier :

    |**Pour modifier l'élément suivant**|**Choisissez**|
    |-|-|
    |Couleur d’arrière-plan|**Contexte**|
    |Couleur du contour|**Stroke**|
    |Couleur du texte (la lettre « f » s’affiche pour afficher le résultat)|**Sombre**|
    |Icône|**Icônes**|

     La boîte de dialogue **Sélecteur de jeu de couleurs** ou sélecteur de jeu d' **icônes** s’affiche pour vous permettant de sélectionner une couleur ou une icône.

6. Dans la boîte de dialogue **Sélecteur de jeu de couleurs** ou sélecteur de jeu d' **icônes** , effectuez l’une des opérations suivantes :

    |**Pour appliquer l'élément suivant**|**Exécuter ces étapes**|
    |-|-|
    |Jeu de couleurs ou d'icônes|Ouvrez **la liste** **Sélectionner une couleur** (ou une **icône**). Sélectionnez un jeu de couleurs ou d'icônes.|
    |Couleur ou icône spécifique|Ouvrez la liste de valeurs des catégories ou des propriétés. Sélectionnez une couleur ou une icône.|

    > [!NOTE]
    > Vous pouvez réorganiser, supprimer ou temporairement désactiver des styles dans la zone **légende** . Consultez [modifier la zone légende](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Modifier la zone légende

Vous pouvez réorganiser, supprimer ou temporairement désactiver des styles dans la zone **légende** :

1. Ouvrez le menu contextuel d’un style dans la zone **légende** .

2. Exécutez l’une des tâches suivantes :

    |**To**|**Choisissez**|
    |-|-|
    |Désactiver l'élément de code|**Désactiver**|
    |Supprimer l'élément de code|**Supprimer**|
    |Déplacer le style vers le haut|**Monter**|
    |Déplacer l'élément de code vers le bas|**Descendre**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Copier les styles d’une carte vers une autre

1. Assurez-vous que la zone **légende** apparaît sur le mappage source. S’il n’est pas visible, dans la barre d’outils de la carte, cliquez sur **légende**.

2. Ouvrez le menu contextuel de la zone **légende** . Choisissez **copier la légende**.

3. Collez la légende sur la carte cible.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Fusionner les cartes de code

Vous pouvez fusionner des cartes en copiant et en collant des éléments de code entre les cartes. Si les identificateurs d'éléments de code correspondent, le collage d'éléments de code fonctionne comme une opération de fusion. Pour simplifier cette tâche, placez tous les assemblys ou binaires que vous souhaitez visualiser dans le même dossier pour que le chemin d'accès complet de chaque assembly ou binaire soit le même pour chaque carte que vous souhaitez fusionner.

Vous pouvez également faire glisser ces assemblys ou ces binaires vers la même carte à partir de ce dossier.

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Informations de référence sur le langage DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
