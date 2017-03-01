---
title: "Créer des diagrammes de dépendance à partir de votre code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: b17d12160920952170d042eb46191df66542c80a
ms.openlocfilehash: e51f32303496d20980d7442458cd35350db01687
ms.lasthandoff: 02/22/2017

---
# <a name="create-dependency-diagrams-from-your-code"></a>Créer des diagrammes de dépendance à partir de votre code.
Pour visualiser l’architecture de haut niveau et logique de votre système logiciel, créez un *diagramme de dépendances* dans Visual Studio. Pour vous assurer que votre code demeure conforme à cette conception, validez votre code avec un diagramme de dépendances. Vous pouvez créer des diagrammes de dépendance pour les projets Visual c# .NET et Visual Basic .NET. Pour connaître les versions de Visual Studio prennent en charge cette fonctionnalité, consultez [Version prise en charge pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Créer un diagramme de dépendance](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Un diagramme de dépendance vous permet d’organiser les éléments de solution Visual Studio en groupes logiques et abstraits appelés *couches*. Vous pouvez utiliser les couches pour décrire des tâches importantes que ces artefacts effectuent ou bien les principaux composants du système. Chaque couche peut contenir d’autres couches qui décrivent des tâches plus détaillées. Vous pouvez également spécifier prévues ou existantes *dépendances* entre les couches. Ces dépendances, qui sont représentées par des flèches, indiquent quels couches peuvent utiliser ou utilisent actuellement la fonctionnalité représentée par d'autres couches. Pour maintenir le contrôle architecturel du code, affichez les dépendances prévues sur le diagramme, puis validez le code par rapport au diagramme.  
  
 [Vidéo : Valider les dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 
  
##  <a name="a-namecreatediagrama-create-a-dependency-diagram"></a><a name="CreateDiagram"></a>Créer un diagramme de dépendance  
 Avant de créer un diagramme de dépendances, assurez-vous que votre solution contient un projet de modélisation. 
  
> [!IMPORTANT]
>  Ne pas ajouter, faites glisser ou copier un diagramme de dépendance existant à partir d’un projet de modélisation vers un autre projet de modélisation ou vers un autre emplacement dans la solution. Cela permet de conserver les références du diagramme d'origine, même si vous modifiez le diagramme. Cela empêche également un mauvais fonctionnement de la validation de couche et pourra provoquer d’autres problèmes, tels que des éléments manquants ou autre erreurs lorsque vous essayez d’ouvrir le diagramme.  
>   
>  Au lieu de cela, ajoutez un nouveau diagramme de dépendance pour le projet de modélisation. Copiez les éléments depuis le diagramme source vers le nouveau diagramme. Enregistrez le projet de modélisation et le nouveau diagramme de dépendance.  
  
#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Pour ajouter un nouveau diagramme de dépendance à un projet de modélisation  
  
1.  Sur le **Architecture** menu, choisissez **nouveau diagramme de dépendance**.  
  
2.  Sous **modèles**, choisissez **diagramme de dépendances**.  
  
3.  Nommez le diagramme.  
  
4.  Dans **ajouter au projet de modélisation**, recherchez et sélectionnez un projet de modélisation existant dans votre solution.  
  
     ou  
  
     Choisissez **créer un nouveau projet de modélisation** pour ajouter un nouveau projet de modélisation à la solution.  
  
    > [!NOTE]
    >  Le diagramme de la dépendance doit exister à l’intérieur d’un projet de modélisation. Toutefois, vous pouvez le lier à des éléments situés n'importe où dans la solution.  
  
5.  Veillez à enregistrer le projet de modélisation et le diagramme de dépendances.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Faites glisser et déposer, ou copier et coller, à partir d’une carte de Code

1. Générer une carte de Code de la solution en utilisant la **Architecture** menu. 

2. Pensez à appliquer un filtre de mappage de Code pour supprimer des dossiers de solution et « Ressources de Test » si vous souhaitez uniquement appliquer les dépendances dans le code de produit.

3. Sur la carte du Code généré, supprimez le nœud « External », ou développer et afficher des assemblys externes, selon que vous souhaitez appliquer les dépendances de l’espace de noms et supprimer des assemblys non requis à partir de la carte de Code. 

4. Créer un nouveau diagramme de dépendance de la solution en utilisant la **Architecture** menu

5. Sélectionner tous les nœuds sur la carte de Code (utilisez _Ctrl_ + _A_, ou utiliser la sélection élastique en appuyant sur la _MAJ_ avant de cliquer, faites glisser et relâchez la clé.

6. Glisser-déplacer, ou une copie et collage, les éléments sélectionnés vers le nouveau diagramme de Validation de dépendance. 

7. Cela illustre l’architecture d’application actuelle. Décider ce que vous voulez l’architecture pour être et modifier le diagramme de dépendances en conséquence.

![Diagramme de dépendances généré à partir d’une carte de Code](media/dependency-validation-01.png)
  
##  <a name="a-namecreatelayersa-create-layers-from-artifacts"></a><a name="CreateLayers"></a>Créer des couches à partir d’artefacts  
 Vous pouvez créer des couches à partir d'éléments de solution Visual Studio, tels que des projets, des fichiers de code, des espaces de noms, des classes et des méthodes. Cela crée automatiquement des liens entre ces couches et les éléments, les incluant dans le processus de validation de couche.  
  
 Afin de pouvoir associer une couche à des caractéristiques ou des plans, vous pouvez également lier des couches à des éléments qui ne prennent pas en charge la validation, tels que des documents Word ou des présentations PowerPoint. Vous pouvez également lier des couches à des fichiers dans des projets qui sont partagés sur plusieurs applications, mais le processus de validation n’inclut pas ces couches qui s’affichent avec des noms génériques tels que « Couche 1 » et « Couche 2 ».  
  
 Pour voir si un élément lié prend en charge la validation, ouvrez **Explorateur de couches** et examinez le **prend en charge la Validation** propriété de l’élément. Consultez la page [gestion des liens vers les artefacts](#Managing).  
  
|**Pour**|**Procédez comme suit**|  
|------------|----------------------------|  
|Créer une couche pour un artefact unique|<ol><li>Faites glisser l’élément sur le diagramme de dépendances à partir de ces sources :<br /><br /> <ul><li>**Explorateur de solutions**<br /><br />         Par exemple, vous pouvez faire glisser des fichiers ou des projets.</li><li>Cartes de code<br /><br />         Consultez la page [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) et [mappe d’utiliser du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Affichage de classes** ou **Explorateur d’objets**</li></ul><br />     Une couche s’affiche sur le diagramme et est liée à l’artefact.</li><li>Renommez la couche pour refléter les responsabilités du code ou des artefacts associés.</li></ol> **Important :** en faisant glisser des fichiers binaires vers le diagramme de dépendance n’ajoute pas automatiquement leurs références au projet de modélisation. Vous devez ajouter manuellement au projet de modélisation les fichiers binaires que vous voulez valider. **Pour ajouter des fichiers binaires au projet de modélisation** <ol><li>Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le projet de modélisation, puis choisissez **ajouter un élément existant**.</li><li>Dans le **ajouter un élément existant** boîte de dialogue, recherchez les fichiers binaires, sélectionnez-les, puis choisissez **OK**.     Les fichiers binaires s'affichent dans le projet de modélisation.</li><li>Dans **l’Explorateur de solutions**, choisissez un fichier binaire que vous avez ajouté, puis appuyez sur **F4** pour ouvrir le **propriétés** fenêtre.</li><li>Sur chaque fichier binaire, affectez le **Action de génération** propriété **validation**.</li></ol>|  
|Créer une couche unique pour tous les artefacts sélectionnés|Faites glisser tous les artefacts vers le diagramme de dépendance en même temps.<br /><br /> Une couche qui est liée à tous les artefacts s’affiche sur le diagramme.|  
|Créer une couche pour chaque artefact sélectionné|Maintenez la **MAJ** enfoncée pendant que vous faites glisser en même temps tous les artefacts vers le diagramme de dépendances. **Remarque :** si vous utilisez la **MAJ** clé pour sélectionner une plage d’éléments, relâchez la touche après avoir sélectionné les artefacts. Appuyez de nouveau sur celle-ci et maintenez-la enfoncée lorsque vous faites glisser les artefacts vers le diagramme. <br /><br /> Une couche s'affiche sur le diagramme pour chaque artefact, auquel elle est liée.|  
|Ajouter un artefact à une couche|Faites glisser l'artefact vers la couche.|  
|Créer une couche non liée|Dans le **boîte à outils**, développez le **diagramme de dépendances** section et faites-le glisser vers un **couche** pour le diagramme de dépendances.<br /><br /> Pour ajouter plusieurs couches, double-cliquez sur l'outil. Lorsque vous avez terminé, choisissez le **pointeur** outil ou appuyez sur la **ÉCHAP** clé.<br /><br /> ou<br /><br /> Ouvrez le menu contextuel pour le diagramme de dépendances, choisissez **ajouter**, puis choisissez **couche**.|  
|Créer des couches imbriquées|Faites glisser une couche existante sur une autre couche.<br /><br /> ou<br /><br /> Ouvrez le menu contextuel d’une couche, choisissez **ajouter**, puis choisissez **couche**.|  
|Créer une nouvelle couche qui contient deux ou plusieurs couches existantes|Sélectionnez les couches, ouvrez le menu contextuel de votre sélection, puis choisissez **groupe**.|  
|Modifier la couleur d'une couche|Définir son **couleur** couleur dans la propriété que vous souhaitez.|  
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la couche **interdit les espaces de noms** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la couche **interdit les dépendances Namespace** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la couche **espace de noms requis** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
  
 Le nombre indiqué sur une couche représente le nombre d’artefacts liés à cette couche. Toutefois, à la lecture de ce nombre, souvenez-vous de ce qui suit :  
  
-   Si une couche est liée à un artefact contenant d'autres artefacts, mais n'est pas directement liée à ces autres artefacts, le nombre représentera uniquement les artefacts auxquels elle est directement liée. Toutefois, les autres artefacts sont inclus dans l'analyse pendant la validation de couche.  
  
     Par exemple, si une couche est liée à un espace de noms unique, le nombre d'artefacts liés est égal à 1, même si l'espace de noms contient des classes. Si la couche a également des liens vers chaque classe de l'espace de noms, le nombre comprendra les classes liées.  
  
-   Si une couche contient d'autres couches liées à des artefacts, la couche du conteneur est également liée à ces artefacts, même si le nombre indiqué sur la couche du conteneur ne comprend pas ces artefacts.  
  
##  <a name="a-namemanaginga-manage-links-between-layers-and-artifacts"></a><a name="Managing"></a>Gérer les liens entre les couches et les artefacts  
  
1.  Dans le diagramme de la dépendance, ouvrez le menu contextuel de la couche, puis choisissez **afficher les liens**.  
  
     **Explorateur de couches** affiche les liens d’artefact pour la couche sélectionnée.  
  
2.  Utilisez les tâches suivantes pour gérer ces liens :  
  
|**Pour**|**Dans l’Explorateur de couches**|  
|------------|---------------------------|  
|Supprimer le lien entre la couche et un artefact|Ouvrez le menu contextuel pour le lien d’artefact, puis choisissez **supprimer**.|  
|Déplacer le lien d'une couche vers une autre|Faites glisser le lien d'artefact vers une couche existante sur le diagramme.<br /><br /> ou<br /><br /> 1.  Ouvrez le menu contextuel pour le lien d’artefact, puis choisissez **couper**.<br />2.  Dans le diagramme de la dépendance, ouvrez le menu contextuel de la couche, puis choisissez **coller**.|  
|Copier le lien d'une couche vers une autre|1.  Ouvrez le menu contextuel pour le lien d’artefact, puis choisissez **copie**.<br />2.  Dans le diagramme de la dépendance, ouvrez le menu contextuel de la couche, puis choisissez **coller**.|  
|Créer une nouvelle couche à partir d’un lien d’artefact existant|Faites glisser le lien d’artefact vers une zone vide sur le diagramme.|  
|Vérifiez qu’un artefact lié prend en charge la validation par rapport au diagramme de dépendance.|Examinez le **prend en charge la Validation** colonne pour le lien d’artefact.|  
  
##  <a name="a-namediscoveringa-reverse-engineer-existing-dependencies"></a><a name="Discovering"></a>Ingénierie à rebours des dépendances existantes  
 Une dépendance existe chaque fois qu’un artefact associé à une couche comporte une référence à un artefact associé à une autre couche. Par exemple, une classe dans une couche déclare une variable qui a une classe dans une autre couche. Vous pouvez effectuer une ingénierie à rebours des dépendances existantes pour les artefacts liés aux couches sur le diagramme.  
  
> [!NOTE]
>  Les dépendances ne peuvent pas faire l'objet d'une ingénierie à rebours pour certains genres d'artefacts. Par exemple, aucune dépendance ne fera l'objet d'une ingénierie à rebours depuis ou vers une couche qui est liée à un fichier texte. Pour voir les artefacts ayant des dépendances que vous pouvez réaliser la rétroconception, ouvrez le menu contextuel pour une ou plusieurs couches, puis choisissez **afficher les liens**. Dans **Explorateur de couches**, examinez le **prend en charge la Validation** colonne. Dépendances ne sera pas à rebours pour les artefacts pour lesquels cette colonne affiche **False**.  
  
-   Sélectionnez une ou plusieurs couches, ouvrez le menu contextuel pour une couche sélectionnée, puis choisissez **générer des dépendances**.  
  
 En général, des dépendances qui ne devraient pas exister s'affichent. Vous pouvez modifier ces dépendances pour les ajuster à la conception prévue.  
  
##  <a name="a-nameeditdependenciesa-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a>Modifier les couches et les dépendances pour afficher la conception prévue  
 Pour décrire les modifications que vous envisagez d’apporter à votre système ou de l’architecture prévue, modifiez le diagramme de dépendances :  
  
|**Pour**|**Procédez comme suit**|  
|------------|-----------------------------|  
|Changer ou restreindre la direction d'une dépendance|Définir son **Direction** propriété.|  
|Créer de nouvelles dépendances|Utilisez le **dépendance** et **dépendance bidirectionnelle** tools.<br /><br /> Pour dessiner plusieurs dépendances, double-cliquez sur l'outil. Lorsque vous avez terminé, choisissez le **pointeur** outil ou appuyez sur la **ÉCHAP** clé.|  
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la couche **interdit les dépendances Namespace** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la couche **interdit les espaces de noms** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la couche **espace de noms requis** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
  
##  <a name="a-nameeditlayouta-change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a>Modifier l’apparaissent des éléments sur le diagramme  
 Vous pouvez modifier la taille, la forme, la couleur et la position des couches ou de la couleur des dépendances en modifiant leurs propriétés.  
  
##  <a name="a-namecodemapsa-discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a>Détecter des modèles et des dépendances sur une carte de code  
 Lors de la création de diagrammes de dépendance, vous pouvez également créer **cartes de code**. Ces diagrammes peuvent vous aider à découvrir des modèles et des dépendances quand vous explorez le code. Utilisez l'Explorateur de solutions, l'Affichage de classes ou l'Explorateur d'objets pour explorer les assemblys, les espaces de noms et les classes, qui correspondent souvent à des couches existantes. Pour plus d'informations sur les cartes de code, consultez :  
  
-   [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vidéo : Valider les dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)   
 [Diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md)   
 [Valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualiser du code](../modeling/visualize-code.md)

