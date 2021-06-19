---
title: 'Diagrammes de dépendance : recommandations'
description: Découvrez comment décrire l’architecture de votre application à un niveau élevé en créant des diagrammes de dépendance dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46e2b774cd4da2ef9cdb9ddef7efd19f731ade7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391021"
---
# <a name="dependency-diagrams-guidelines"></a>Diagrammes de dépendance : indications

Décrivez l’architecture de votre application à un niveau élevé en créant des *diagrammes de dépendance* dans Visual Studio. Assurez-vous que votre code reste cohérent avec cette conception en validant votre code avec un diagramme de dépendance. Vous pouvez également inclure la validation de couche dans votre processus de génération. Voir [vidéo Channel 9 : concevoir et valider votre architecture à l’aide de diagrammes de dépendances](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

Pour connaître les éditions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [prise en charge d’édition pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> Les diagrammes de dépendance pour les projets .NET Core sont pris en charge à partir de Visual Studio 2019 version 16,2.

## <a name="what-is-a-dependency-diagram"></a>Qu’est-ce qu’un diagramme de dépendance ?

À l’instar d’un diagramme d’architecture traditionnel, un diagramme de dépendance identifie les principaux composants ou unités fonctionnelles de la conception et leurs interdépendances. Chaque nœud du diagramme, appelé *couche*, représente un groupe logique d’espaces de noms, de projets ou d’autres artefacts. Vous pouvez dessiner les dépendances qui doivent exister dans votre conception. Contrairement à un diagramme d'architecture traditionnel, vous pouvez vérifier que les dépendances réelles dans le code source sont conformes aux dépendances prévues que vous avez spécifiées. En incluant la partie validation d'une build normale dans [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], vous pouvez vous assurer que le code du programme continue à respecter l'architecture du système au travers des modifications futures. Consultez [diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Comment concevoir ou mettre à jour votre application avec des diagrammes de dépendance

Les étapes suivantes fournissent une vue d’ensemble de l’utilisation des diagrammes de dépendance dans le processus de développement. Les sections suivantes de cette rubrique décrivent plus en détail chaque étape. Si vous développez une nouvelle conception, ignorez les étapes qui font référence au code existant.

> [!NOTE]
> Ces étapes s'affichent selon un ordre approximatif. Vous souhaiterez probablement superposer les tâches, les réorganiser en fonction de votre propre cas et les réexaminer au début de chaque itération de votre projet.

1. [Créez un diagramme de dépendance](#Create) pour l’application entière ou pour une couche qu’il contient.

2. [Définissez les couches pour représenter les zones fonctionnelles principales ou les composants](#CreateLayers) de votre application. Nommez ces couches d'après leur fonction, par exemple, « Présentation » ou « Services ». Si vous disposez d’une solution Visual Studio, vous pouvez associer chaque couche à une collection d' *artefacts*, tels que des projets, des espaces de noms, des fichiers, etc.

3. [Découvrez les dépendances existantes entre les](#Generate) couches.

4. [Modifiez les couches et les dépendances](#EditArchitecture) pour afficher la conception mise à jour que vous souhaitez que le code reflète.

5. [Concevez de nouvelles zones de votre application](#NewAreas) en créant des couches pour représenter les principaux composants ou blocs architecturaux et en définissant des dépendances pour montrer comment chaque couche utilise les autres.

6. [Modifiez la disposition et l’apparence du diagramme](#EditLayout) pour vous aider à le discuter avec vos collègues.

7. [Validez le code par rapport au diagramme de dépendance](#Validate) pour mettre en évidence les conflits entre le code et l’architecture dont vous avez besoin.

8. [Mettez à jour le code pour qu’il soit conforme à votre nouvelle architecture](#UpdateCode). Développez le code de manière itérative et refactorisez-le jusqu'à ce que la validation n'affiche aucun conflit.

9. [Incluez la validation de couche dans le processus de génération](#BuildValidation) pour vous assurer que le code continue à adhérer à votre conception.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Créer un diagramme de dépendance

Un diagramme de dépendance doit être créé dans un projet de modélisation. Vous pouvez ajouter un nouveau diagramme de dépendance à un projet de modélisation existant, créer un nouveau projet de modélisation pour le diagramme de dépendances ou copier un diagramme de dépendance existant dans le même projet de modélisation.

> [!IMPORTANT]
> N’ajoutez pas, ne faites pas glisser ou ne copiez pas un diagramme de dépendance existant d’un projet de modélisation vers un autre projet de modélisation ou vers un autre emplacement de la solution. Un diagramme de dépendance copié de cette manière aura les mêmes références que le diagramme d’origine, même si vous modifiez le diagramme. La validation de couche ne peut alors fonctionner correctement et d’autres problèmes peuvent survenir, tels que l’absence d’éléments ou autre erreurs lors de l’ouverture du diagramme.

Consultez [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Définir des couches pour représenter des zones fonctionnelles ou des composants

Les couches représentent des groupes logiques d' *artefacts*, tels que des projets, des fichiers de code, des espaces de noms, des classes et des méthodes. Vous pouvez créer des couches à partir d’artefacts à partir de projets Visual C# et Visual Basic, ou vous pouvez attacher des spécifications ou des plans à une couche en liant des documents, tels que des fichiers Word ou des présentations PowerPoint. Chaque couche apparaît comme un rectangle sur le diagramme et indique le nombre d’artefacts qui lui sont liés. Une couche peut contenir des couches imbriquées qui décrivent des tâches plus spécifiques.

En règle générale, nommez les couches selon leur fonction : par exemple, « Présentation » ou « Services ». Si les artefacts sont étroitement interdépendants, placez-les dans la même couche. Si les artefacts peuvent être mis à jour séparément ou utilisés dans des applications distinctes, placez-les dans des couches différentes. Pour en savoir plus sur les modèles de superposition, visitez le site patterns & Practices à l’adresse [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Il existe certains types d’artefacts que vous pouvez lier aux couches, mais qui ne prennent pas en charge la validation par rapport au diagramme de dépendance. Pour voir si l’artefact prend en charge la validation, ouvrez l' **Explorateur de couches** pour examiner la propriété **prend en charge la validation** du lien d’artefact. Consultez [découvrir les dépendances existantes entre les couches](#Generate).

Lors de la mise à jour d'une application peu familière, vous pouvez également créer des cartes de code. Ces diagrammes peuvent vous aider à découvrir des modèles et des dépendances quand vous explorez le code. Utilisez l'Explorateur de solutions pour explorer des espaces de noms et des classes, qui correspondent souvent à des couches existantes. Assignez ces artefacts de code aux couches en les faisant glisser de Explorateur de solutions vers des diagrammes de dépendance. Vous pouvez ensuite utiliser des diagrammes de dépendances pour vous aider à mettre à jour le code et le garder cohérent avec votre conception.

Consultez l'article :

- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)

- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Découvrir les dépendances existantes entre les couches

Une dépendance existe chaque fois qu'un artefact associé à une couche comporte une référence à un artefact associé à une autre couche. Par exemple, une classe dans une couche déclare une variable qui a une classe dans une autre couche. Vous pouvez découvrir les dépendances existantes par rétroconception.

> [!NOTE]
> Les dépendances ne peuvent pas faire l'objet d'une ingénierie à rebours pour certains genres d'artefacts. Par exemple, aucune dépendance ne fera l'objet d'une ingénierie à rebours depuis ou vers une couche qui est liée à un fichier texte. Pour voir quels artefacts ont des dépendances que vous pouvez rétroconcevoir, cliquez avec le bouton droit sur une ou plusieurs couches, puis cliquez sur **afficher les liens**. Dans l **'Explorateur de couches**, examinez la colonne **prend en charge la validation** . Les dépendances ne feront pas l’objet d’une ingénierie à rebours pour les artefacts pour lesquels cette colonne affiche la **valeur false**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Pour procéder à la rétroconception des dépendances existantes entre couches

Sélectionnez une ou plusieurs couches, cliquez avec le bouton droit sur une couche sélectionnée, puis cliquez sur **générer des dépendances**.

En général, des dépendances qui ne devraient pas exister s'affichent. Vous pouvez modifier ces dépendances pour les ajuster à la conception prévue.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Modifier les couches et les dépendances pour afficher la conception prévue

Pour décrire les modifications que vous envisagez d’apporter à votre système ou à l’architecture prévue, procédez comme suit pour modifier le diagramme de dépendance. vous pouvez aussi envisager d'apporter des modifications de refactorisation pour améliorer la structure du code avant de l'étendre. Consultez [amélioration de la structure du code](#Improving).

|**To**|**Exécuter ces étapes**|
|-|-|
|Supprimer une dépendance qui ne doit pas exister|Cliquez sur la dépendance, puis appuyez sur la touche **Suppr**.|
|Changer ou restreindre la direction d'une dépendance|Définissez sa propriété **direction** .|
|Créer de nouvelles dépendances|Utilisez les outils de **dépendance bidirectionnelle** et de **dépendance** .<br /><br /> Pour dessiner plusieurs dépendances, double-cliquez sur l'outil. Lorsque vous avez terminé, cliquez sur l’outil **pointeur** ou appuyez sur la touche **Échap** .|
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **dépendances de l’espace de noms interdit** de la couche. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la propriété **espaces de noms interdits** de la couche. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la propriété **espace de noms requis** de la couche. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Amélioration de la structure du code

Les modifications de refactorisation sont des améliorations qui n'affectent pas le comportement de l'application, mais qui contribuent à rendre le code plus facile à modifier et à étendre à l'avenir. Le code correctement structuré a une conception qui est facile à extraire dans un diagramme de dépendance.

Par exemple, si vous créez une couche pour chaque espace de noms dans le code, puis soumettez les dépendances à une rétroconception, il doit exister un ensemble minimal de dépendances unidirectionnelles entre les couches. Si vous créez un diagramme plus détaillé à l'aide de classes ou de méthodes en tant que couches, le résultat doit également présenter les mêmes caractéristiques.

Si ce n’est pas le cas, le code sera plus difficile à modifier tout au long de sa durée de vie et sera moins adapté à la validation à l’aide de diagrammes de dépendance.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Concevoir de nouvelles zones de votre application

Lorsque vous démarrez le développement d'un nouveau projet, ou d'une nouvelle partie d'un nouveau projet, vous pouvez dessiner des couches et des dépendances pour aider à identifier les principaux composants avant de commencer à développer le code.

- **Affichez les modèles architecturaux identifiables** dans vos diagrammes de dépendance, si possible. Par exemple, un diagramme de dépendance qui décrit une application de bureau peut inclure des couches telles que la présentation, la logique de domaine et la Banque de données. Un diagramme de dépendance qui couvre une fonctionnalité unique au sein d’une application peut avoir des couches telles que le modèle, la vue et le contrôleur. Pour plus d’informations sur ces modèles, consultez [patterns & Practices : architecture d’application](https://archive.codeplex.com/?p=apparch).

- **Créez un artefact de code pour chaque couche** , tel qu’un espace de noms, une classe ou un composant. Il est ainsi plus facile de suivre le code et de lier les artefacts de code aux couches. Dès que vous créez un artefact, liez-le à la couche appropriée.

- **Vous n’avez pas besoin de lier la plupart des classes et d’autres artefacts aux couches** , car ils sont dans des artefacts plus importants tels que les espaces de noms que vous avez déjà liés à des couches.

- **Créez un nouveau diagramme pour une nouvelle fonctionnalité**. En général, il y aura un ou plusieurs diagrammes de dépendance décrivant l’application entière. Si vous concevez une nouvelle fonctionnalité dans l’application, ne modifiez pas les diagrammes existants ou ne la leur ajoutez pas. Créez à la place votre propre diagramme qui reflète les nouvelles parties du code. Les couches du nouveau diagramme peuvent inclure la présentation, la logique de domaine et les couches de base de données pour la nouvelle fonctionnalité.

     Lorsque vous générez l’application, votre code est validé par rapport au diagramme global et à votre diagramme de fonctionnalités détaillé.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Modifier la disposition pour la présentation et la discussion

Pour vous aider à identifier des couches et des dépendances ou à en discuter avec les membres de l'équipe, modifiez l'aspect et la disposition du diagramme comme suit :

- Modifiez les tailles, formes et positions des couches.

- Modifiez les couleurs des couches et des dépendances.

  - Sélectionnez une ou plusieurs couches ou dépendances, cliquez avec le bouton droit sur, puis cliquez sur **Propriétés**. Dans la fenêtre **Propriétés** , modifiez la propriété **couleur** .

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Valider le code par rapport au diagramme

Une fois que vous avez modifié le diagramme, vous pouvez le valider manuellement par rapport au code à tout moment ou automatiquement chaque fois que vous générez.

Consultez l'article :

- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)

- [Inclure la validation de couche dans le processus de génération](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Mettre à jour le code pour qu’il soit conforme à la nouvelle architecture

En règle générale, des erreurs apparaissent la première fois que vous validez le code par rapport à un diagramme de dépendances mis à jour. Ces erreurs peuvent avoir plusieurs causes :

- Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l’artefact.

- Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d’erreur. Il s'agit généralement d'un processus itératif. Pour plus d’informations sur ces erreurs, consultez [valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Lorsque vous développez ou refactorisez le code, vous pouvez avoir de nouveaux artefacts à lier au diagramme de dépendance. Toutefois, cela peut ne pas être nécessaire : par exemple, lorsque des couches représentent des espaces de noms existants et que le nouveau code ajoute seulement plus de documentation à ces espaces de noms.

Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé de consigner un élément de travail dans Team Foundation. Pour effectuer cette tâche, consultez [valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Inclure la validation de couche dans le processus de génération

Pour vous assurer que les futures modifications du code sont conformes aux diagrammes de dépendance, incluez la validation de couche au processus de génération standard de votre solution. Chaque fois que d’autres membres de l’équipe génèrent la solution, les différences entre les dépendances dans le code et le diagramme de dépendances sont signalées comme des erreurs de Build. Pour plus d’informations sur l’inclusion de la validation de couche dans le processus de génération, consultez [valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Voir aussi

- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)
- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
