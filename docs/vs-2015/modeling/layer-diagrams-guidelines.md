---
title: 'Diagrammes de couche : indications | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aee4ddc6062e465384921fa2632636c480736a77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646134"
---
# <a name="layer-diagrams-guidelines"></a>Diagrammes de couche : instructions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Décrivez l’architecture de votre application à un niveau élevé en créant des *diagrammes de couche* dans Visual Studio. Assurez-vous que votre code demeure conforme à cette conception en le validant avec un diagramme de couche. Vous pouvez également inclure la validation de couche dans votre processus de génération. Voir [vidéo Channel 9 : concevoir et valider votre architecture à l’aide de diagrammes de couche](http://go.microsoft.com/fwlink/?LinkID=252073).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>Qu'est-ce qu'un diagramme de couche ?
 À l'image d'un diagramme d'architecture traditionnel, un diagramme de couche identifie les principaux composants ou unités fonctionnelles de la conception et leurs interdépendances. Chaque nœud du diagramme, appelé *couche*, représente un groupe logique d’espaces de noms, de projets ou d’autres artefacts. Vous pouvez dessiner les dépendances qui doivent exister dans votre conception. Contrairement à un diagramme d'architecture traditionnel, vous pouvez vérifier que les dépendances réelles dans le code source sont conformes aux dépendances prévues que vous avez spécifiées. En incluant la partie validation d'une build normale dans [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], vous pouvez vous assurer que le code du programme continue à respecter l'architecture du système au travers des modifications futures. Consultez [diagrammes de couche : référence](../modeling/layer-diagrams-reference.md).

## <a name="Update"></a>Comment concevoir ou mettre à jour votre application avec des diagrammes de couche
 Les étapes suivantes fournissent une vue d'ensemble de l'utilisation des diagrammes de couche dans le processus de développement. Les sections suivantes de cette rubrique décrivent plus en détail chaque étape. Si vous développez une nouvelle conception, ignorez les étapes qui font référence au code existant.

> [!NOTE]
> Ces étapes s'affichent selon un ordre approximatif. Vous souhaiterez probablement superposer les tâches, les réorganiser en fonction de votre propre cas et les réexaminer au début de chaque itération de votre projet.

1. [Créez un diagramme de couche](#Create) pour l’application entière ou pour une couche qu’il contient.

2. [Définissez les couches pour représenter les zones fonctionnelles principales ou les composants](#CreateLayers) de votre application. Nommez ces couches d'après leur fonction, par exemple, « Présentation » ou « Services ». Si vous disposez d’une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez associer chaque couche à une collection d' *artefacts*, tels que des projets, des espaces de noms, des fichiers, etc.

3. [Découvrez les dépendances existantes entre les](#Generate) couches.

4. [Modifiez les couches et les dépendances](#EditArchitecture) pour afficher la conception mise à jour que vous souhaitez que le code reflète.

5. [Concevez de nouvelles zones de votre application](#NewAreas) en créant des couches pour représenter les principaux composants ou blocs architecturaux et en définissant des dépendances pour montrer comment chaque couche utilise les autres.

6. [Modifiez la disposition et l’apparence du diagramme](#EditLayout) pour vous aider à le discuter avec vos collègues.

7. [Validez le code par rapport au diagramme de couche](#Validate) pour mettre en évidence les conflits entre le code et l’architecture dont vous avez besoin.

8. [Mettez à jour le code pour qu’il soit conforme à votre nouvelle architecture](#UpdateCode). Développez le code de manière itérative et refactorisez-le jusqu'à ce que la validation n'affiche aucun conflit.

9. [Incluez la validation de couche dans le processus de génération](#BuildValidation) pour vous assurer que le code continue à adhérer à votre conception.

## <a name="Create"></a>Créer un diagramme de couche
 Un diagramme de couche doit être créé à l'intérieur d'un projet de modélisation. Vous pouvez ajouter un nouveau diagramme de couche à un projet de modélisation existant, créer un nouveau projet de modélisation pour le diagramme de couche ou copier un diagramme de couche existant au sein du même projet de modélisation.

> [!IMPORTANT]
> Vous ne pouvez pas copier un diagramme de couche existant d'un projet de modélisation vers un autre projet de modélisation ou un autre emplacement de la solution, ni l'y ajouter ou l'y glisser-déposer. Un diagramme de couche ainsi copié aura les mêmes références que le diagramme d'origine, même si vous modifiez le diagramme. La validation de couche ne peut alors fonctionner correctement et d’autres problèmes peuvent survenir, tels que l’absence d’éléments ou autre erreurs lors de l’ouverture du diagramme.

 Consultez [créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a>Définir des couches pour représenter des zones fonctionnelles ou des composants
 Les couches représentent des groupes logiques d' *artefacts*, tels que des projets, des fichiers de code, des espaces de noms, des classes et des méthodes. Vous pouvez créer des couches à partir d'artefacts de projets Visual C# .NET et Visual Basic .NET, ou vous pouvez attacher des spécifications ou des plans à une couche en liant des documents, tels que des fichiers Word ou des présentations PowerPoint. Chaque couche apparaît comme un rectangle sur le diagramme et indique le nombre d’artefacts qui lui sont liés. Une couche peut contenir des couches imbriquées qui décrivent des tâches plus spécifiques.

 En règle générale, nommez les couches selon leur fonction : par exemple, « Présentation » ou « Services ». Si les artefacts sont étroitement interdépendants, placez-les dans la même couche. Si les artefacts peuvent être mis à jour séparément ou utilisés dans des applications distinctes, placez-les dans des couches différentes. Pour en savoir plus sur les modèles de superposition, visitez le site patterns & Practices à l’adresse [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Il existe certains types d’artefacts que vous pouvez lier aux couches, mais qui ne prennent pas en charge la validation par rapport au diagramme de couche. Pour voir si l’artefact prend en charge la validation, ouvrez l' **Explorateur de couches** pour examiner la propriété **prend en charge la validation** du lien d’artefact. Consultez [découvrir les dépendances existantes entre les couches](#Generate).

 Lors de la mise à jour d'une application peu familière, vous pouvez également créer des cartes de code. Ces diagrammes peuvent vous aider à découvrir des modèles et des dépendances quand vous explorez le code. Utilisez l'Explorateur de solutions pour explorer des espaces de noms et des classes, qui correspondent souvent à des couches existantes. Assignez ces artefacts de code à des couches en les faisant glisser de l'Explorateur de solutions vers des diagrammes de couche. Vous pouvez ensuite utiliser les diagrammes de couche pour vous aider à mettre à jour le code et à garantir sa cohérence avec votre conception.

 Consultez :

- [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)

- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a>Découvrir les dépendances existantes entre les couches
 Une dépendance existe chaque fois qu'un artefact associé à une couche comporte une référence à un artefact associé à une autre couche. Par exemple, une classe dans une couche déclare une variable qui a une classe dans une autre couche. Vous pouvez découvrir les dépendances existantes par rétroconception.

> [!NOTE]
> Les dépendances ne peuvent pas faire l'objet d'une ingénierie à rebours pour certains genres d'artefacts. Par exemple, aucune dépendance ne fera l'objet d'une ingénierie à rebours depuis ou vers une couche qui est liée à un fichier texte. Pour voir quels artefacts ont des dépendances que vous pouvez rétroconcevoir, cliquez avec le bouton droit sur une ou plusieurs couches, puis cliquez sur **afficher les liens**. Dans l **'Explorateur de couches**, examinez la colonne **prend en charge la validation** . Les dépendances ne feront pas l’objet d’une ingénierie à rebours pour les artefacts pour lesquels cette colonne affiche la **valeur false**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Pour procéder à la rétroconception des dépendances existantes entre couches

- Sélectionnez une ou plusieurs couches, cliquez avec le bouton droit sur une couche sélectionnée, puis cliquez sur **générer des dépendances**.

  En général, des dépendances qui ne devraient pas exister s'affichent. Vous pouvez modifier ces dépendances pour les ajuster à la conception prévue.

## <a name="EditArchitecture"></a>Modifier les couches et les dépendances pour afficher la conception prévue
 Pour décrire les modifications que vous envisagez d'apporter à votre système ou l'architecture prévue, utilisez la procédure suivante pour modifier le diagramme de couche : vous pouvez aussi envisager d'apporter des modifications de refactorisation pour améliorer la structure du code avant de l'étendre. Consultez [amélioration de la structure du code](#Improving).

|**Pour**|**Procédez comme suit**|
|------------|-----------------------------|
|Supprimer une dépendance qui ne doit pas exister|Cliquez sur la dépendance, puis appuyez sur la touche **Suppr**.|
|Changer ou restreindre la direction d'une dépendance|Définissez sa propriété **direction** .|
|Créer de nouvelles dépendances|Utilisez les outils de **dépendance bidirectionnelle** et de **dépendance** .<br /><br /> Pour dessiner plusieurs dépendances, double-cliquez sur l'outil. Lorsque vous avez terminé, cliquez sur l’outil **pointeur** ou appuyez sur la touche **Échap** .|
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **dépendances de l’espace de noms interdit** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **espaces de noms interdits** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la propriété **espace de noms requis** de la couche. Utilisez un point-virgule ( **;** ) pour séparer les espaces de noms.|

### <a name="Improving"></a>Amélioration de la structure du code
 Les modifications de refactorisation sont des améliorations qui n'affectent pas le comportement de l'application, mais qui contribuent à rendre le code plus facile à modifier et à étendre à l'avenir. Le code correctement structuré présente une conception qu'il est facile de résumer en un diagramme de couche.

 Par exemple, si vous créez une couche pour chaque espace de noms dans le code, puis soumettez les dépendances à une rétroconception, il doit exister un ensemble minimal de dépendances unidirectionnelles entre les couches. Si vous créez un diagramme plus détaillé à l'aide de classes ou de méthodes en tant que couches, le résultat doit également présenter les mêmes caractéristiques.

 Si tel n’est pas le cas, le code sera plus difficile à modifier tout au long de son cycle de vie et sera moins adapté à la validation à l’aide de diagrammes de couche.

## <a name="NewAreas"></a>Concevoir de nouvelles zones de votre application
 Lorsque vous démarrez le développement d'un nouveau projet, ou d'une nouvelle partie d'un nouveau projet, vous pouvez dessiner des couches et des dépendances pour aider à identifier les principaux composants avant de commencer à développer le code.

- **Affichez les modèles architecturaux identifiables** dans vos diagrammes de couche, si possible. Par exemple, un diagramme de couche qui décrit une application bureautique peut inclure des couches telles que Présentation, Logique de domaine et Magasin de données. Un diagramme de couche qui couvre une fonctionnalité unique au sein d'une application peut avoir des couches telles que Modèle, Vue et Contrôleur. Pour plus d’informations sur ces modèles, consultez [patterns & Practices : architecture d’application](http://go.microsoft.com/fwlink/?LinkId=145794).

     Si vous créez fréquemment des modèles similaires, créez un outil personnalisé. Consultez [définir un élément de boîte à outils de modélisation personnalisé](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Créez un artefact de code pour chaque couche** , tel qu’un espace de noms, une classe ou un composant. Il est ainsi plus facile de suivre le code et de lier les artefacts de code aux couches. Dès que vous créez un artefact, liez-le à la couche appropriée.

- **Vous n’avez pas besoin de lier la plupart des classes et d’autres artefacts aux couches** , car ils sont dans des artefacts plus importants tels que les espaces de noms que vous avez déjà liés à des couches.

- **Créez un nouveau diagramme pour une nouvelle fonctionnalité**. En général, il y a un ou plusieurs diagrammes de couche décrivant toute l'application. Si vous concevez une nouvelle fonctionnalité dans l’application, ne modifiez pas les diagrammes existants ou ne la leur ajoutez pas. Créez à la place votre propre diagramme qui reflète les nouvelles parties du code. Les couches du nouveau diagramme peuvent inclure la présentation, la logique de domaine et les couches de base de données pour la nouvelle fonctionnalité.

     Lorsque vous générez l’application, votre code est validé par rapport au diagramme global et à votre diagramme de fonctionnalités détaillé.

## <a name="EditLayout"></a>Modifier la disposition pour la présentation et la discussion
 Pour vous aider à identifier des couches et des dépendances ou à en discuter avec les membres de l'équipe, modifiez l'aspect et la disposition du diagramme comme suit :

- Modifiez les tailles, formes et positions des couches.

- Modifiez les couleurs des couches et des dépendances.

  - Sélectionnez une ou plusieurs couches ou dépendances, cliquez avec le bouton droit sur, puis cliquez sur **Propriétés**. Dans la fenêtre **Propriétés** , modifiez la propriété **couleur** .

## <a name="Validate"></a>Valider le code par rapport au diagramme
 Lorsque vous avez modifié le diagramme, vous pouvez le valider manuellement par rapport au code à tout moment ou automatiquement chaque fois que vous exécutez une génération locale ou [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].

 Consultez :

- [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)

- [Inclure la validation de couche dans le processus de génération](#BuildValidation)

## <a name="UpdateCode"></a>Mettre à jour le code pour qu’il soit conforme à la nouvelle architecture
 En général, les erreurs apparaissent la première fois que vous validez le code par rapport à un diagramme de couche mis à jour. Ces erreurs peuvent avoir plusieurs causes :

- Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l’artefact.

- Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

  Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d’erreur. Il s'agit généralement d'un processus itératif. Pour plus d’informations sur ces erreurs, consultez [valider le code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Lorsque vous développez ou refactorisez le code, il se peut que vous ayez de nouveaux artefacts à lier au diagramme de couche. Toutefois, cela peut ne pas être nécessaire : par exemple, lorsque des couches représentent des espaces de noms existants et que le nouveau code ajoute seulement plus de documentation à ces espaces de noms.

 Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé d’entrer un élément de travail dans [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Pour effectuer cette tâche, consultez [valider le code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a>Inclure la validation de couche dans le processus de génération
 Pour vous assurer que les futures modifications du code sont conformes aux diagrammes de couche, incluez la validation de couche au processus de génération standard de votre solution. Chaque fois que les autres membres de l'équipe génèrent la solution, les différences entre les dépendances dans le code et le diagramme de couche sont signalées comme erreurs de build. Pour plus d’informations sur l’inclusion de la validation de couche dans le processus de génération, consultez [valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Voir aussi
 [Diagrammes de couche : référence](../modeling/layer-diagrams-reference.md) [créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
