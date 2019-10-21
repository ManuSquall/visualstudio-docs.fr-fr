---
title: Créer des diagrammes de couche à partir de votre code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 138f818eab34b0b1860c7daa85f1b6814888fc9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652848"
---
# <a name="create-layer-diagrams-from-your-code"></a>Créer des diagrammes de couche à partir de votre code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour visualiser l’architecture logique de haut niveau de votre système logiciel, créez un *diagramme de couche* dans Visual Studio. Pour vous assurer que votre code demeure conforme à cette conception, validez-le avec un diagramme de couche. Vous pouvez créer des diagrammes de couche pour les projets Visual C# .NET et Visual Basic .NET. Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [prise en charge des versions pour les outils d’architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Créer un diagramme de couche](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 Un diagramme de couche vous permet d’organiser les éléments de solution Visual Studio en groupes logiques abstraits appelés *couches*. Vous pouvez utiliser les couches pour décrire des tâches importantes que ces artefacts effectuent ou bien les principaux composants du système. Chaque couche peut contenir d'autres couches qui décrivent des tâches plus détaillées. Vous pouvez également spécifier les *dépendances* prévues ou existantes entre les couches. Ces dépendances, qui sont représentées par des flèches, indiquent quels couches peuvent utiliser ou utilisent actuellement la fonctionnalité représentée par d'autres couches. Pour maintenir le contrôle architecturel du code, affichez les dépendances prévues sur le diagramme, puis validez le code par rapport au diagramme.

## <a name="CreateDiagram"></a>Créer un diagramme de couche
 Avant de créer un diagramme de couche, vérifiez que votre solution a un projet de modélisation. Consultez [créer des projets et des diagrammes de modélisation UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Vous ne pouvez pas ajouter, glisser-déposer ni copier un diagramme de couche existant d'un projet de modélisation à un autre, ou bien vers un autre emplacement de la solution. Cela permet de conserver les références du diagramme d'origine, même si vous modifiez le diagramme. Cela empêche également un mauvais fonctionnement de la validation de couche et pourra provoquer d’autres problèmes, tels que des éléments manquants ou autre erreurs lorsque vous essayez d’ouvrir le diagramme.
>
> Ajoutez au lieu de cela un nouveau diagramme de couche au projet de modélisation. Copiez les éléments depuis le diagramme source vers le nouveau diagramme. Enregistrez le projet de modélisation et le nouveau diagramme de couche.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Pour ajouter un nouveau diagramme de couche à un projet de modélisation

1. Dans le menu **architecture** , choisissez **nouveau diagramme UML ou diagramme de couche**.

2. Sous **modèles**, choisissez **diagramme de couche**.

3. Nommez le diagramme.

4. Dans **Ajouter au projet de modélisation**, recherchez et sélectionnez un projet de modélisation existant dans votre solution.

     ou

     Choisissez **créer un nouveau projet de modélisation** pour ajouter un nouveau projet de modélisation à la solution.

    > [!NOTE]
    > Le diagramme de couche doit être présent dans un projet de modélisation. Toutefois, vous pouvez le lier à des éléments situés n'importe où dans la solution.

5. Veillez à enregistrer à la fois le projet de modélisation et le diagramme de couche.

## <a name="CreateLayers"></a>Créer des couches à partir d’artefacts
 Vous pouvez créer des couches à partir d'éléments de solution Visual Studio, tels que des projets, des fichiers de code, des espaces de noms, des classes et des méthodes. Cela crée automatiquement des liens entre ces couches et les éléments, les incluant dans le processus de validation de couche.

 Afin de pouvoir associer une couche à des caractéristiques ou des plans, vous pouvez également lier des couches à des éléments qui ne prennent pas en charge la validation, tels que des documents Word ou des présentations PowerPoint. Vous pouvez également lier des couches à des fichiers dans des projets qui sont partagés sur plusieurs applications, mais le processus de validation n’inclut pas ces couches qui s’affichent avec des noms génériques tels que « Couche 1 » et « Couche 2 ».

 Pour voir si un élément lié prend en charge la validation, ouvrez l' **Explorateur de couches** et examinez la propriété **prend en charge la validation** de l’élément. Consultez [gestion des liens vers les artefacts](#Managing).

|**Pour**|**Procédez comme suit**|
|------------|----------------------------|
|Créer une couche pour un artefact unique|<ol><li>Faites glisser l'élément sur le diagramme de couche à partir de ces sources :<br /><br /> <ul><li>**Explorateur de solutions**<br /><br />         Par exemple, vous pouvez faire glisser des fichiers ou des projets.</li><li>Cartes de code<br /><br />         Consultez [mapper les dépendances entre vos solutions](../modeling/map-dependencies-across-your-solutions.md) et [utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>Explorateur d' **objets** ou de **affichage de classes**</li></ul><br />     Une couche s’affiche sur le diagramme et est liée à l’artefact.</li><li>Renommez la couche pour refléter les responsabilités du code ou des artefacts associés.</li></ol> **Important :**  Le fait de faire glisser des fichiers binaires vers le diagramme de couche n’ajoute pas automatiquement leurs références au projet de modélisation. Vous devez ajouter manuellement au projet de modélisation les fichiers binaires que vous voulez valider. **Pour ajouter des fichiers binaires au projet de modélisation** <ol><li>Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet de modélisation, puis choisissez **Ajouter un élément existant**.</li><li>Dans la boîte de dialogue **Ajouter un élément existant** , accédez aux fichiers binaires, sélectionnez-les, puis choisissez **OK**.     Les fichiers binaires s'affichent dans le projet de modélisation.</li><li>Dans **Explorateur de solutions**, choisissez un fichier binaire que vous avez ajouté, puis appuyez sur **F4** pour ouvrir la fenêtre **Propriétés** .</li><li>Sur chaque fichier binaire, définissez la propriété **action de génération** sur **valider**.</li></ol>|
|Créer une couche unique pour tous les artefacts sélectionnés|Faites glisser en même temps tous les artefacts vers le diagramme de couche.<br /><br /> Une couche qui est liée à tous les artefacts s’affiche sur le diagramme.|
|Créer une couche pour chaque artefact sélectionné|Maintenez la touche **MAJ** enfoncée pendant que vous faites glisser tous les artefacts vers le diagramme de couche en même temps. **Remarque :**  Si vous utilisez la touche **MAJ** pour sélectionner une plage d’éléments, relâchez la touche après avoir sélectionné les artefacts. Appuyez de nouveau sur celle-ci et maintenez-la enfoncée lorsque vous faites glisser les artefacts vers le diagramme. <br /><br /> Une couche s’affiche sur le diagramme pour chaque artefact, auquel elle est liée.|
|Ajouter un artefact à une couche|Faites glisser l'artefact vers la couche.|
|Créer une couche non liée|Dans la **boîte à outils**, développez la section **diagramme de couche** , puis faites glisser une **couche** vers le diagramme de couche.<br /><br /> Pour ajouter plusieurs couches, double-cliquez sur l'outil. Lorsque vous avez terminé, choisissez l’outil **pointeur** ou appuyez sur la touche **Échap** .<br /><br /> ou<br /><br /> Ouvrez le menu contextuel du diagramme de couche, choisissez **Ajouter**, puis **couche**.|
|Créer des couches imbriquées|Faites glisser une couche existante sur une autre couche.<br /><br /> ou<br /><br /> Ouvrez le menu contextuel d’une couche, choisissez **Ajouter**, puis **couche**.|
|Créer une nouvelle couche qui contient deux ou plusieurs couches existantes|Sélectionnez les couches, ouvrez le menu contextuel de votre sélection, puis choisissez **groupe**.|
|Modifier la couleur d'une couche|Affectez à sa propriété **Color** la couleur de votre choix.|
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **espaces de noms interdits** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **dépendances de l’espace de noms interdit** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la propriété **espace de noms requis** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|

 Le nombre indiqué sur une couche représente le nombre d’artefacts liés à cette couche. Toutefois, à la lecture de ce nombre, souvenez-vous de ce qui suit :

- Si une couche est liée à un artefact contenant d'autres artefacts, mais n'est pas directement liée à ces autres artefacts, le nombre représentera uniquement les artefacts auxquels elle est directement liée. Toutefois, les autres artefacts sont inclus dans l'analyse pendant la validation de couche.

     Par exemple, si une couche est liée à un espace de noms unique, le nombre d'artefacts liés est égal à 1, même si l'espace de noms contient des classes. Si la couche a également des liens vers chaque classe de l'espace de noms, le nombre comprendra les classes liées.

- Si une couche contient d'autres couches liées à des artefacts, la couche du conteneur est également liée à ces artefacts, même si le nombre indiqué sur la couche du conteneur ne comprend pas ces artefacts.

## <a name="Managing"></a>Gérer les liens entre les couches et les artefacts

1. Dans le diagramme de couche, ouvrez le menu contextuel de la couche, puis choisissez **afficher les liens**.

     L' **Explorateur de couches** affiche les liens d’artefact pour la couche sélectionnée.

2. Utilisez les tâches suivantes pour gérer ces liens :

|**Pour**|**Dans l’Explorateur de couches**|
|------------|---------------------------|
|Supprimer le lien entre la couche et un artefact|Ouvrez le menu contextuel du lien d’artefact, puis choisissez **supprimer**.|
|Déplacer le lien d'une couche vers une autre|Faites glisser le lien d’artefact vers une couche existante sur le diagramme.<br /><br /> ou<br /><br /> 1. Ouvrez le menu contextuel du lien d’artefact, puis choisissez **couper**.<br />2. dans le diagramme de couche, ouvrez le menu contextuel de la couche, puis choisissez **coller**.|
|Copier le lien d'une couche vers une autre|1. Ouvrez le menu contextuel du lien d’artefact, puis choisissez **copier**.<br />2. dans le diagramme de couche, ouvrez le menu contextuel de la couche, puis choisissez **coller**.|
|Créer une nouvelle couche à partir d’un lien d’artefact existant|Faites glisser le lien d’artefact vers une zone vide sur le diagramme.|
|Vérifiez qu’un artefact lié prend en charge la validation par rapport au diagramme de couche.|Examinez la colonne **prend en charge la validation** du lien d’artefact.|

## <a name="Discovering"></a>Ingénierie à rebours des dépendances existantes
 Une dépendance existe chaque fois qu'un artefact associé à une couche comporte une référence à un artefact associé à une autre couche. Par exemple, une classe dans une couche déclare une variable qui a une classe dans une autre couche. Vous pouvez effectuer une ingénierie à rebours des dépendances existantes pour les artefacts liés aux couches sur le diagramme.

> [!NOTE]
> Les dépendances ne peuvent pas faire l'objet d'une ingénierie à rebours pour certains genres d'artefacts. Par exemple, aucune dépendance ne fera l'objet d'une ingénierie à rebours depuis ou vers une couche qui est liée à un fichier texte. Pour voir quels artefacts ont des dépendances que vous pouvez rétroconcevoir, ouvrez le menu contextuel pour une ou plusieurs couches, puis choisissez **afficher les liens**. Dans l **'Explorateur de couches**, examinez la colonne **prend en charge la validation** . Les dépendances ne feront pas l’objet d’une ingénierie à rebours pour les artefacts pour lesquels cette colonne affiche la **valeur false**.

- Sélectionnez une ou plusieurs couches, ouvrez le menu contextuel d’une couche sélectionnée, puis choisissez **générer des dépendances**.

  En général, des dépendances qui ne devraient pas exister s'affichent. Vous pouvez modifier ces dépendances pour les ajuster à la conception prévue.

## <a name="EditDependencies"></a>Modifier les couches et les dépendances pour afficher la conception prévue
 Pour décrire les modifications que vous envisagez d'apporter à votre système ou l'architecture attendue, modifiez le diagramme de couche :

|**Pour**|**Procédez comme suit**|
|------------|-----------------------------|
|Changer ou restreindre la direction d'une dépendance|Définissez sa propriété **direction** .|
|Créer de nouvelles dépendances|Utilisez les outils de **dépendance bidirectionnelle** et de **dépendance** .<br /><br /> Pour dessiner plusieurs dépendances, double-cliquez sur l'outil. Lorsque vous avez terminé, choisissez l’outil **pointeur** ou appuyez sur la touche **Échap** .|
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **dépendances de l’espace de noms interdit** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **espaces de noms interdits** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la propriété **espace de noms requis** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|

## <a name="EditLayout"></a>Modifier le mode d’affichage des éléments dans le diagramme
 Vous pouvez modifier la taille, la forme, la couleur et la position des couches ou de la couleur des dépendances en modifiant leurs propriétés.

## <a name="Codemaps"></a>Découvrir des modèles et des dépendances sur une carte de code
 Lors de la création de diagrammes de couche, vous pouvez également créer des **cartes de code**. Ces diagrammes peuvent vous aider à découvrir des modèles et des dépendances quand vous explorez le code. Utilisez l'Explorateur de solutions, l'Affichage de classes ou l'Explorateur d'objets pour explorer les assemblys, les espaces de noms et les classes, qui correspondent souvent à des couches existantes. Pour plus d'informations sur les cartes de code, consultez :

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)

- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)

- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Voir aussi
 [Vidéo Channel 9 : concevoir et valider votre architecture à l’aide](http://go.microsoft.com/fwlink/?LinkID=252073) de diagrammes de couche [diagrammes de couche :](../modeling/layer-diagrams-reference.md) [indications](../modeling/layer-diagrams-guidelines.md) [valider le code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md) [visualiser le code](../modeling/visualize-code.md)