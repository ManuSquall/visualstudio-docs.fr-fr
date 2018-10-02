---
title: Modifier des modèles UML et des diagrammes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0620f0a1212d7abd864a9428492d95067098ef16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502541"
---
# <a name="edit-uml-models-and-diagrams"></a>Modifier des modèles et des diagrammes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [modèles et diagrammes UML modifier](https://docs.microsoft.com/visualstudio/modeling/edit-uml-models-and-diagrams).  
  
Vous pouvez créer et modifier un modèle UML par l'intermédiaire des vues fournies par plusieurs types de diagrammes. Grâce à ces différentes perspectives de votre système, ces diagrammes vous aident à comprendre et à discuter des différents aspects de sa conception et de ses impératifs. Visual Studio fournit des modèles pour cinq des types de diagrammes UML les plus fréquents.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Cette rubrique décrit des techniques de modification du modèle communes aux différents types de diagrammes. Pour plus d’informations spécifiques à des types de diagrammes particuliers, consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>Dans cette rubrique  
  
-   [Diagrammes UML sont des vues d’un modèle UML](#Views)  
  
-   [Création de diagrammes de modélisation UML](#Creating)  
  
-   [Dessin de diagrammes de modélisation UML](#Drawing)  
  
-   [Modification des formes et connecteurs](#Editing)  
  
-   [Annulation de modifications apportées au modèle](#Undo)  
  
-   [Partage d’éléments entre des diagrammes](#Sharing)  
  
-   [Copie d’éléments et les groupes d’éléments connexes](#Copying)  
  
-   [Suppression d’un élément de modèle ou de ses vues](#Deleting)  
  
-   [Recherche de texte dans un diagramme](#Searching)  
  
-   [Préparation d’un diagramme de présentation](#presentation)  
  
-   [Extension des concepteurs UML](#extensions)  
  
##  <a name="Views"></a> Diagrammes UML sont des vues d’un modèle UML  
 Vous pouvez créer et utiliser des diagrammes UML uniquement dans les projets de modélisation. Pour plus d’informations sur la création de projets et des diagrammes, consultez [diagrammes et projets de modélisation UML créer](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
-   Un projet de modélisation contient un seul modèle UML. Chaque diagramme UML dans le projet est une vue du modèle UML.  
  
-   Vous pouvez voir le modèle dans **Explorateur de modèles UML**. Sur le **Architecture** menu, pointez sur **Windows**, puis cliquez sur **Explorateur de modèles UML**.  
  
-   Chaque forme dans un diagramme est une vue d'un élément du modèle. Quand vous placez une nouvelle forme dans un diagramme, vous créez un nouvel élément dans le modèle.  
  
-   Lorsque vous enregistrez un diagramme, Visual Studio enregistre le modèle entier, tous ses diagrammes et la modélisation fichier projet.  
  
##  <a name="Creating"></a> Création de diagrammes de modélisation UML  
  
1.  Sur le **Architecture** menu dans Visual Studio, cliquez sur **nouveau UML ou diagramme de couche**.  
  
2.  Sélectionnez et nommez votre diagramme.  
  
3.  Dans **ajouter au projet de modélisation**, sélectionnez un projet de modélisation existant, ou **créer un nouveau projet de modélisation**.  
  
    > [!NOTE]
    >  Un projet de modélisation doit obligatoirement comporter un diagramme de modélisation.  
  
 Vous pouvez également ajouter un diagramme à un projet de modélisation existant dans l'Explorateur de solutions. Cliquez sur le projet de modélisation, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Pour créer un projet de modélisation UML vide  
  
-   Sur le **fichier** menu, pointez sur **New**, cliquez sur **projet**, puis, dans le **nouveau projet** boîte de dialogue, double-cliquez sur **de modélisation Projets**.  
  
 Pour plus d’informations sur la gestion des projets de modélisation, consultez [diagrammes et projets de modélisation UML créer](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
##  <a name="Drawing"></a> Dessin de diagrammes de modélisation UML  
 Un diagramme de modélisation illustre une collection d'éléments de modèle liés par des relations. Chaque élément est affiché en tant que forme et chaque relation est affichée en tant que connecteur entre deux formes.  
  
 Il existe deux genres d'outils, un pour les éléments et un pour les relations. Par exemple, dans le diagramme de classes UML boîte à outils, **classe** est un outil d’élément, et **Association** est un outil de relation.  
  
> [!NOTE]
>  Si vous souhaitez des informations qui sont spécifiques aux types de diagrammes particuliers, consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Pour créer des éléments et des relations dans un diagramme de modélisation UML  
  
1.  Pour créer un élément de modèle, cliquez sur un outil d'élément dans la boîte à outils, puis cliquez sur le diagramme où vous souhaitez qu'il apparaisse. Une fois l'élément créé, ajustez sa taille et sa forme en faisant glisser ses poignées.  
  
     Dans certains cas, vous pouvez placer un nouvel élément dans un autre. Par exemple, dans un diagramme de classes UML, vous pouvez placer une classe à l'intérieur d'un package.  
  
    > [!NOTE]
    >  Si vous ne voyez pas la boîte à outils, cliquez sur **boîte à outils** sur le **vue** menu.  
  
2.  Pour créer une relation, cliquez sur un outil de relation, cliquez sur l'élément d'origine de la relation, puis cliquez sur l'élément de destination.  
  
     Différents types de relations peuvent avoir comme origine et comme destination différents types d'éléments. Par exemple, dans un diagramme de classes UML, une relation Association ne peut pas avoir comme origine ou comme destination un élément Commentaire.  
  
    > [!NOTE]
    >  Pour utiliser le même outil plusieurs fois, double-cliquez dessus. Lorsque vous avez terminé, cliquez sur le **pointeur** outil.  
  
 Dans certains types de diagrammes, vous pouvez également dessiner des formes simples. Ces formes ne font pas partie du modèle, mais vous pouvez les utiliser pour attirer l'attention sur des parties du diagramme ou pour le diviser en différentes zones.  
  
##  <a name="Editing"></a> Modification des formes et connecteurs  
 Quand vous redimensionnez ou colorez une forme, ou quand vous réacheminez un connecteur, cela n'a aucun effet sur le modèle sous-jacent. En revanche, quand vous renommez une forme dans le diagramme ou dans l'Explorateur de modèles UML, l'élément correspondant est renommé dans l'Explorateur de modèles UML et dans tous les autres diagrammes où figure cet élément.  
  
> [!NOTE]
>  Il existe un moyen simple de créer des éléments de boîte à outils à partir desquels vous pouvez créer des groupes d'éléments ou des éléments avec votre propre choix de propriétés. Pour plus d’informations, consultez [définir un personnalisé élément de boîte à outils de modélisation](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 La figure suivante montre comment modifier la taille ou le nom d'une forme.  
  
 ![Ajustement d’un élément de modèle](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  Les commandes intégrées ne comprennent pas de commande pour aligner correctement les formes. Toutefois, vous pouvez créer facilement votre propre commande d’alignement en copiant le code dans l’exemple de [afficher un modèle UML sur des diagrammes](../modeling/display-a-uml-model-on-diagrams.md).  
  
 La figure suivante montre comment ajuster l'itinéraire et la position d'un connecteur ou de ses étiquettes.  
  
 ![Ajustement d’un connecteur](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Pour déplacer une extrémité d'un lien vers une autre forme  
  
1.  Effectuez l’une des opérations suivantes :  
  
    -   Appuyez sur **CTRL** et déplacez l’extrémité.  
  
     \- ou -  
  
    -   Cliquez sur le connecteur, puis cliquez sur **reconnexion**.  
  
2.  Cliquez sur l'extrémité du connecteur que vous souhaitez déplacer.  
  
3.  Cliquez sur la forme de destination souhaitée du connecteur.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Pour modifier la couleur ou d'autres propriétés d'un élément, d'une relation ou d'un diagramme  
  
-   Cliquez sur l’élément et définissez les champs dans le **propriétés** fenêtre.  
  
     Si vous ne voyez pas le **propriétés** fenêtre, cliquez sur l’élément, puis cliquez sur **propriétés.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Pour effectuer un zoom avant ou arrière dans un diagramme de modélisation  
  
-   Maintenez la **CTRL** enfoncée pendant que vous faites tourner la roulette de la souris.  
  
     \- ou -  
  
-   Maintenez la touche et **CTRL + MAJ**, puis cliquez sur le bouton gauche ou droit de la souris.  
  
     \- ou -  
  
-   Sur le **concepteurs d’Architecture** barre d’outils, cliquez sur le signe plus (**+**) ou signe moins (**-**), ou choisissez un niveau de zoom.  
  
##  <a name="Searching"></a> Recherche dans un diagramme  
 La fonction Recherche rapide permet de rechercher des éléments dans un diagramme. Vous devez définir **Regarder dans :** à **Document actif**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Pour rechercher du texte dans un diagramme de modélisation  
  
1.  Appuyez sur **CTRL + F**.  
  
     \- ou -  
  
     Sur le **modifier** menu, pointez sur **rechercher et remplacer**, puis cliquez sur **recherche rapide**.  
  
    > [!NOTE]
    >  Dans le **rechercher et remplacer** boîte de dialogue, vous devez laisser le **Regarder dans** champ la valeur **Document actif**. Les autres options ne sont pas prises en charge.  
  
2.  Tapez le texte que vous souhaitez rechercher, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Si le texte à rechercher est à l'intérieur d'une forme réduite, la forme est mise en surbrillance. Développer la forme, puis cliquez sur **suivant** à nouveau.  
  
##  <a name="Undo"></a> Annulation de modifications apportées au modèle  
 Vous pouvez annuler et rétablir les modifications que vous avez apportées au modèle et aux diagrammes à l’aide de la **Annuler** et **de restauration par progression** commandes sur le **modifier** menu.  
  
 **Chaque projet de modélisation possède une seule pile de modifications.** Toutes les modifications que vous apportez au modèle et aux diagrammes sont conservées sur cette pile. La pile comprend également les modifications de focus d'un diagramme à un autre. La commande Annuler annule les modifications sur cette pile.  
  
 Par exemple, supposez que vous effectuez les opérations suivantes : modification du diagramme 1 ; basculement du focus vers le diagramme 2 ; modification du diagramme 2. Si vous annulez les modifications, le premier clic sur Annuler annule la dernière modification, le second redéplace le focus vers le diagramme 1 et le troisième annule la modification apportée au diagramme 1.  
  
 **Fermeture d’un diagramme tronque la pile de modifications.** Si vous fermez un diagramme, vous ne pouvez pas annuler les modifications que vous lui avez apportées, ni annuler les modifications précédentes apportées au modèle ou à l'un de ses diagrammes.  
  
 **Vous ne pouvez pas annuler pendant que vous modifiez une propriété.** Pendant que vous modifiez une propriété dans la fenêtre Propriétés, ou dans une étiquette dans un diagramme, vous pouvez annuler uniquement les modifications que vous avez effectuées dans cette propriété. Terminez votre modification dans la propriété en appuyant sur Entrée ou annulez-la en appuyant sur Échap. Vous pourrez alors annuler les modifications dans le modèle et les diagrammes.  
  
 **Fermeture d’un diagramme sans l’enregistrer peut-être pas l’effet attendu.** Si vous apportez des modifications et fermez ensuite un diagramme sans l'enregistrer, vos modifications seront tout de même conservées dans le modèle. Nous vous recommandons de fermer le modèle entier si vous souhaitez le fermer sans l'enregistrer.  
  
##  <a name="Sharing"></a> Partage d’éléments entre des diagrammes  
 Vous pouvez faire apparaître une instance spécifique d'un élément de modèle plusieurs fois dans vos diagrammes. Cela s'applique aux classes, interfaces, composants, cas d'usage et acteurs.  
  
 Cela est utile si vous souhaitez afficher différents groupes de relations dans différents diagrammes. Par exemple, dans un diagramme, vous pouvez afficher les associations entre les classes Client et Adresse. Dans un autre diagramme, vous pouvez afficher une deuxième fois la classe Adresse, avec son association à Code postal.  
  
 Vous pouvez modifier les propriétés d'un élément de modèle, telles que son nom, en sélectionnant l'une de ses vues dans n'importe quel diagramme ou en le sélectionnant dans l'Explorateur de modèles UML.  
  
 Chaque type de diagramme peut afficher uniquement certains types d'éléments de modèle. Par exemple, vous ne pouvez pas afficher un cas d'usage dans un diagramme de composant. Ainsi, les procédures suivantes fonctionnent uniquement pour certaines combinaisons d'élément de modèle et de diagramme.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Pour ajouter une nouvelle vue d'un élément de modèle à l'aide de l'Explorateur de modèles UML  
  
1.  Pour ouvrir **Explorateur de modèles UML**, dans le **Architecture** menu, pointez sur **Windows**, puis cliquez sur **Explorateur de modèles UML**.  
  
2.  Faites glisser l’élément de modèle à partir de **Explorateur de modèles UML** vers un diagramme compatible dans le même projet.  
  
     Une forme qui fournit une vue de l'élément de modèle apparaît, éventuellement en plus des vues dans d'autres diagrammes ou dans le même diagramme.  
  
    > [!NOTE]
    >  L'effet est différent quand vous faites glisser une classe ou un composant vers un diagramme de séquence. Dans ce cas, une nouvelle ligne de vie est créée, dont le type est cette classe ou ce composant. Pour plus d’informations, consultez [diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Pour ajouter une nouvelle vue d'un élément de modèle à l'aide de l'option Coller la référence  
  
1.  Avec le bouton droit à un élément existant, puis cliquez sur **copie**.  
  
    -   Vous pouvez copier plusieurs éléments à la fois. Maintenez la touche CTRL enfoncée et cliquez sur chaque élément, cliquez sur un d'entre eux, puis cliquez sur **copie**.  
  
2.  Cliquez sur une partie vide d’un diagramme compatible, puis cliquez sur **coller la référence**.  
  
     Une autre vue du même élément apparaît.  
  
    > [!NOTE]
    >  Cela diffère la **coller** commande, qui crée un nouvel élément dans le modèle. Pour plus d’informations, consultez [copie d’éléments et les groupes d’éléments connexes](#Copying).  
  
> [!NOTE]
>  Si vous ajoutez à un diagramme des vues de deux éléments de modèle qui sont déjà connectées par une relation, une vue de la relation apparaît également dans le diagramme. Vous ne pouvez supprimer cette vue qu'en supprimant l'un des éléments du diagramme ou en supprimant la relation du modèle.  
  
##  <a name="Copying"></a> Copie d’éléments et les groupes d’éléments connexes  
 Vous pouvez copier et coller des éléments de modèle, et copier et coller des groupes d'éléments et les relations entre eux.  
  
> [!NOTE]
>  Le **coller** et **coller la référence** commandes ont des effets différents. **Coller** crée des éléments dont les propriétés sont semblables à celles des éléments copiés. **Coller la référence** crée des vues des mêmes éléments.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Pour copier des éléments et leurs relations  
  
1.  Dans le diagramme qui contient les éléments à copier, sélectionnez un ou plusieurs éléments.  
  
    > [!NOTE]
    >  Vous ne pouvez pas copier des relations, sauf dans le cadre d'un groupe d'éléments.  
  
2.  Sur le **modifier** menu, cliquez sur **copie**.  
  
3.  Si vous souhaitez copier les éléments vers un autre diagramme, créez le nouveau diagramme ou ouvrez le diagramme existant.  
  
4.  Sur le **modifier** menu, cliquez sur **coller**.  
  
    -   Les copies des éléments apparaissent, avec des copies de toutes les relations qui les lient.  
  
    -   Chaque nouvel élément aura un nouveau nom généré automatiquement.  
  
5.  Ajustez les positions, les noms et les autres propriétés des nouveaux éléments et relations.  
  
> [!NOTE]
>  Vous ne pouvez pas copier un élément de modèle d'un modèle vers un autre, par exemple si vous avez deux modèles dans la même solution. En revanche, vous pouvez copier des éléments d'un diagramme vers un autre.  
  
#### <a name="to-copy-an-entire-diagram"></a>Pour copier un diagramme entier  
  
1.  Créez un diagramme.  
  
2.  Sélectionnez tous les éléments d'un diagramme existant, copiez-les et collez-les dans le nouveau diagramme.  
  
 Vous ne pouvez pas dupliquer un diagramme en le copiant et en le collant dans l'Explorateur de solutions.  
  
##  <a name="Deleting"></a> Suppression d’un élément de modèle ou de ses vues  
 Certains types d'éléments (les classifieurs) peuvent être supprimés d'un diagramme sans être supprimés du modèle. Les classifieurs sont les éléments majeurs affichés sur les diagrammes de classes, de composants et de cas d'usage. Ils peuvent figurer dans plusieurs diagrammes. Pour ces types d’éléments, il existe deux commandes distinctes : **supprimer du diagramme** et **supprimer du modèle**.  
  
 Par contre, quand vous supprimez une relation d'un diagramme, elle est toujours supprimée du modèle.  
  
> [!NOTE]
>  Certains types d'éléments dans un diagramme UML ont des étiquettes. Quand vous sélectionnez ces types d'éléments en dessinant un rectangle autour d'eux, vous pouvez sélectionner les étiquettes, mais pas les éléments propriétaires de ces étiquettes. La suppression d'un sous-ensemble d'éléments qui sont sélectionnés de cette façon n'est pas prise en charge. Pour sélectionner un sous-ensemble de ces éléments, maintenez la **CTRL** enfoncée pendant que vous cliquez sur chaque élément.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Pour supprimer la vue d'un classifieur dans un diagramme  
  
-   Cliquez sur l’élément sur le diagramme, puis cliquez sur **supprimer du diagramme**.  
  
 \- ou -  
  
-   Cliquez sur l’élément dans le diagramme, puis appuyez sur la **supprimer** clé.  
  
    -   Cette vue de l'élément disparaît. Toutefois, l’élément reste dans le modèle, et vous pouvez toujours y accéder dans **Explorateur de modèles UML**. Toutes les autres vues du même élément sont également conservées.  
  
    -   Chaque connecteur qui se termine à cette forme est supprimé du diagramme, mais la relation qu'il représente reste dans le modèle. Vous pouvez voir la relation dans **Explorateur de modèles UML** sous **relations**, sous chaque élément qu’il se connecte.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Pour supprimer un élément du modèle  
  
-   Cliquez sur l’élément soit dans **Explorateur de modèles UML** ou dans un diagramme, puis cliquez sur **supprimer du modèle**.  
  
    -   L'élément est supprimé de chaque diagramme où il figure.  
  
    -   Chaque relation qui se termine à cet élément est également supprimée du modèle.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>Pour supprimer une relation du modèle  
  
-   Avec le bouton droit de la relation sur un diagramme ou dans **Explorateur de modèles UML**, puis cliquez sur **supprimer du modèle**.  
  
    > [!CAUTION]
    >  Vous ne pouvez pas supprimer une relation d'un diagramme sans la supprimer du modèle.  
  
     La relation est supprimée du modèle et de chaque diagramme où elle apparaît.  
  
##  <a name="presentation"></a> Préparation d’un diagramme de présentation  
 Les fonctionnalités suivantes vous aident à attirer l'attention sur une partie spécifique de votre diagramme, à ajouter des explications ou à diviser un diagramme en différentes zones d'intérêt.  
  
-   Vous pouvez copier une partie d'un diagramme dans un document Word, PowerPoint ou autre. Sélectionnez les formes et connecteurs que vous souhaitez, avec le bouton droit, puis cliquez sur **copie**.  
  
-   Vous pouvez modifier la couleur d'une forme ou d'un connecteur. Sélectionnez une ou plusieurs formes et modifiez le **couleur** propriété. Si la fenêtre **Propriétés** n’apparaît pas, appuyez sur **F4**.  
  
-   Sur les diagrammes de certains types, vous pouvez dessiner des lignes, rectangles et ellipses à partir de la **formes simples** section de la boîte à outils. Ces formes ne font pas partie du modèle UML.  
  
-   Pour étiqueter une zone, vous pouvez faire glisser un commentaire à partir de la boîte à outils, puis définissez son **Transparent** propriété **True**. Comme les formes simples, les commentaires ne font pas partie du modèle UML et n'apparaissent pas dans l'Explorateur de modèles UML.  
  
-   Pour ajouter des remarques et des explications à des éléments de modèle, vous pouvez créer des commentaires et les lier à des éléments.  
  
-   Pour aligner correctement une ligne ou une colonne de formes dans le diagramme, vous pouvez installer la commande Aligner les formes. Cette option est disponible en tant qu’un exemple d’extension UML : [UML : Command to Align Shapes](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Pour exporter un diagramme en tant qu'image  
 Pour plus d’informations, consultez [exporter des diagrammes en tant qu’images](../modeling/export-diagrams-as-images.md).  
  
##  <a name="extensions"></a> Extension des concepteurs UML  
 Vous pouvez ajouter de nouvelles fonctionnalités aux outils UML et adapter la notation de diagramme à vos besoins. Pour plus d’informations, consultez [modèles et diagrammes UML étendre](../modeling/extend-uml-models-and-diagrams.md).  
  
 Plusieurs exemples d'extensions sont disponibles. Vous pouvez simplement les installer et les utiliser, ou vous pouvez utiliser leur code source comme base pour vos propres extensions. Les exemples suivants sont disponibles :  
  
|||  
|-|-|  
|[Aligner des formes](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Commande de menu qui vous permet d'optimiser la présentation d'un diagramme.|  
|[Lier à docs](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Lier n'importe quel élément UML à des titres Word, des diapositives PowerPoint, des fichiers de n'importe quel type, des diagrammes UML ou d'autres éléments UML. Pour créer un lien, une simple opération de glissement suffit. Ultérieurement, vous pouvez double-cliquer sur l'élément pour afficher l'élément lié. Par exemple, vous pouvez lier des cas d'usage à des spécifications Word ou des diagrammes d'activités détaillés, et des actions à des diapositives de storyboard.|  
|[Entrée rapide](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Créer rapidement un modèle à l'aide de l'entrée de texte. Utile pour capturer des idées lors des réunions.|  
|[Couleur par stéréotype](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Colorer des classes selon le stéréotype. Vous pouvez facilement étendre le code pour vos propres stéréotypes.|  
|[Modélisation de domaine](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Modèles par défaut pratiques pour les modèles d'entreprise. Les associations sont affichées sans flèches par défaut et les opérations n'apparaissent pas dans les classes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des diagrammes et projets de modélisation UML](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Analyse et modélisation de l’Architecture](../modeling/analyze-and-model-your-architecture.md)   
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)



