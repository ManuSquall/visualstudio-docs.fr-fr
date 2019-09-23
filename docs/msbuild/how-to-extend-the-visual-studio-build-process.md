---
title: Étendre le processus de génération
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba701d123e739bc2dfa24ff798aef5338c51f532
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913184"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procédure : Étendre le processus de génération Visual Studio
Le processus de génération [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est défini par une série de fichiers *.targets* [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] importés dans votre fichier projet. Parmi ces fichiers importés, *Microsoft.Common.targets* peut être étendu de manière à exécuter des tâches personnalisées à différentes étapes du processus de génération. Cet article décrit deux méthodes que vous pouvez utiliser pour étendre le processus de génération [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] :

- Substitution de cibles prédéfinies spécifiques définies dans les cibles communes (*Microsoft. Common. targets* ou les fichiers qu’il importe).

- Substitution des propriétés « DependsOn » définies dans les cibles courantes.

## <a name="override-predefined-targets"></a>Substituer des cibles prédéfinies
Les cibles courantes contiennent un ensemble de cibles vides prédéfinies qui sont appelées avant et après certaines des cibles majeures dans le processus de génération. Par exemple, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] appelle la cible `BeforeBuild` avant la cible principale `CoreBuild` et appelle la cible `AfterBuild` après la cible `CoreBuild`. Par défaut, les cibles vides dans les cibles courantes ne font rien, mais vous pouvez remplacer leur comportement par défaut en définissant les cibles souhaitées dans un fichier projet qui importe les cibles communes. En substituant les cibles prédéfinies, vous pouvez utiliser les tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour avoir plus de contrôle sur le processus de génération.

> [!NOTE]
> Les projets de style SDK ont une importation implicite des cibles *après la dernière ligne du fichier projet*. Cela signifie que vous ne pouvez pas remplacer les cibles par défaut, sauf si vous spécifiez [vos importations manuellement, comme décrit dans Procédure : Utilisez les SDK](how-to-use-project-sdk.md)de projet MSBuild.

#### <a name="to-override-a-predefined-target"></a>Pour substituer une cible prédéfinie

1. Identifiez une cible prédéfinie dans les cibles courantes que vous souhaitez substituer. Consultez le tableau ci-dessous pour obtenir la liste complète des cibles que vous pouvez substituer en toute sécurité.

2. Définissez la ou les cibles à la fin de votre fichier projet, juste avant la balise `</Project>`. Par exemple :

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Générez le fichier projet.

Le tableau suivant répertorie toutes les cibles dans les cibles courantes que vous pouvez substituer en toute sécurité.

|Nom de la cible|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la compilation principale. La plupart des personnalisations sont effectuées dans l’une de ces deux cibles.|
|`BeforeBuild`, `AfterBuild`|Les tâches insérées dans l’une de ces cibles s’exécutent avant ou après tout le reste lors de la génération. **Remarque :**  Les cibles `BeforeBuild` et `AfterBuild` sont déjà définies dans les commentaires à la fin de la plupart des fichiers projet. Vous pouvez ainsi ajouter facilement des événements pré-build et post-build à votre fichier projet.|
|`BeforeRebuild`, `AfterRebuild`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de regénération principale. L’ordre d’exécution des cibles dans *Microsoft.Common.targets* est le suivant : `BeforeRebuild`, `Clean`, `Build`, puis `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de nettoyage principale.|
|`BeforePublish`, `AfterPublish`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après l’appel de la fonctionnalité de publication principale.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la résolution des références d’assembly.|
|`BeforeResGen`, `AfterResGen`|Les tâches insérées dans l’une de ces cibles sont exécutées avant ou après la génération des ressources.|

## <a name="override-dependson-properties"></a>Substituer des propriétés DependsOn
La substitution de cibles prédéfinies est un moyen facile d’étendre le processus de génération. Toutefois, étant donné que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] évalue la définition des cibles de manière séquentielle, il n’existe aucun moyen d’empêcher un autre projet qui importe votre projet de substituer les cibles que vous avez déjà substituées. Ainsi, par exemple, la dernière cible `AfterBuild` définie dans le fichier projet, une fois que tous les autres projets ont été importés, sera celle utilisée pour la génération.

Vous pouvez vous protéger contre les substitutions involontaires de cibles en substituant les propriétés DependsOn utilisées dans `DependsOnTargets` les attributs dans les cibles courantes. Par exemple, la cible `Build` contient une valeur d’attribut `DependsOnTargets` égale à `"$(BuildDependsOn)"`. Prenez en compte ce qui suit :

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Ce code XML indique que pour exécuter la cible `Build`, vous devez d’abord exécuter toutes les cibles spécifiées dans la propriété `BuildDependsOn`. La propriété `BuildDependsOn` est définie de la manière suivante :

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Vous pouvez remplacer cette valeur de propriété en déclarant une autre propriété nommée `BuildDependsOn` à la fin de votre fichier projet. En incluant la propriété `BuildDependsOn` précédente dans la nouvelle propriété, vous pouvez ajouter de nouvelles cibles au début et à la fin de la liste de cibles. Par exemple :

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Les projets qui importent vos fichiers projet peuvent substituer ces propriétés sans remplacer les personnalisations que vous avez apportées.

#### <a name="to-override-a-dependson-property"></a>Pour substituer une propriété DependsOn

1. Identifiez une propriété DependsOn prédéfinie dans les cibles courantes que vous souhaitez substituer. Consultez le tableau ci-dessous pour obtenir la liste des propriétés DependsOn qui sont communément substituées.

2. Définissez une autre instance de la ou des propriétés à la fin de votre fichier projet. Incluez la propriété d’origine (par exemple `$(BuildDependsOn)`) dans la nouvelle propriété.

3. Définissez vos cibles personnalisées avant ou après la définition de la propriété.

4. Générez le fichier projet.

### <a name="commonly-overridden-dependson-properties"></a>Propriétés DependsOn communément substituées

|Nom de la propriété|Description|
|-------------------|-----------------|
|`BuildDependsOn`|Propriété à substituer si vous souhaitez insérer des cibles personnalisées avant ou après l’intégralité du processus de génération.|
|`CleanDependsOn`|Propriété à substituer si vous souhaitez nettoyer la sortie de votre processus de génération.|
|`CompileDependsOn`|Propriété à substituer si vous souhaitez insérer des processus personnalisés avant ou après l’étape de compilation.|

## <a name="see-also"></a>Voir aussi
- [Intégration Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Fichiers .targets](../msbuild/msbuild-dot-targets-files.md)
