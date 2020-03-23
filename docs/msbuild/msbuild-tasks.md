---
title: Tâches MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633133"
---
# <a name="msbuild-tasks"></a>tâches MSBuild

Une plateforme de génération doit pouvoir exécuter plusieurs actions pendant le processus de génération. MSBuild utilise des *tâches* pour effectuer ces actions. Une tâche est une unité de code exécutable utilisée par MSBuild pour effectuer des opérations de construction atomique.

## <a name="task-logic"></a>Logique de tâche

 Le format de fichier de projet MSBuild XML ne peut pas exécuter entièrement les opérations de construction sur son propre, de sorte que la logique de tâche doit être implémentée en dehors du fichier de projet.

 La logique d’exécution d’une tâche est implémentée en tant que classe .NET implémentant l’interface <xref:Microsoft.Build.Framework.ITask>, définie dans l’espace de noms <xref:Microsoft.Build.Framework>.

 La classe de tâche définit également les paramètres d’entrée et de sortie qui sont disponibles pour la tâche dans le fichier projet. Toutes les propriétés non abstraites non statiques définies publiques exposées par la classe de tâches peuvent être données des valeurs dans le fichier du projet en plaçant un attribut correspondant avec le même nom sur [l’élément de tâche,](../msbuild/task-element-msbuild.md) et en définissant sa valeur comme le montrent les exemples plus tard dans cet article.

 Vous pouvez écrire votre propre tâche en créant une classe managée qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations, voir [Rédaction de tâches](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Exécuter une tâche à partir d’un fichier projet

 Avant d’exécuter une tâche dans votre fichier projet, vous devez d’abord mapper le type inclus dans l’assembly qui implémente la tâche au nom de la tâche avec l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md). Cela permet à MSBuild de savoir où chercher la logique d’exécution de votre tâche lorsqu’elle la trouve dans votre dossier de projet.

 Pour exécuter une tâche dans un fichier de projet MSBuild, créez un `Target` élément avec le nom de la tâche en tant qu’enfant d’un élément. Si une tâche accepte des paramètres, ceux-ci sont transmis en tant qu’attributs de l’élément.

 Les listes d’éléments et les propriétés MSBuild peuvent être utilisés comme paramètres. Par exemple, le code `MakeDir` suivant appelle la `Directories` tâche et `MakeDir` définit la valeur `BuildDir` de la propriété de l’objet égale à la valeur de la propriété :

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Les tâches peuvent également retourner des informations au fichier projet, qui peuvent être stockées dans les éléments ou les propriétés en vue d’une utilisation ultérieure. Par exemple, le code suivant appelle la tâche `Copy` et stocke les informations de la propriété en sortie `CopiedFiles` dans la liste d’éléments `SuccessfullyCopiedFiles`.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Tâches incluses

 MSBuild navires avec de nombreuses tâches telles que [Copy](../msbuild/copy-task.md), qui copie les fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires, et [Csc](../msbuild/csc-task.md), qui compile les fichiers de code source C. Pour une liste complète des tâches disponibles et des informations d’utilisation, voir [référence De tâche](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Tâches écrasées

 MSBuild recherche des tâches à plusieurs endroits. Le premier emplacement est dans les fichiers avec l’extension *. OverrideTasks stockés* dans les annuaires cadre .NET. Les tâches contenues dans ces fichiers remplacent toutes les autres tâches du même nom, notamment les tâches du fichier projet. Le deuxième emplacement est dans les fichiers avec l’extension *. Tâches* dans les annuaires cadre .NET. Si la tâche est introuvable à l’un de ces emplacements, c’est celle contenue dans le fichier projet qui est utilisée.

## <a name="see-also"></a>Voir aussi

- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Rédaction de tâches](../msbuild/task-writing.md)
- [Tâches en ligne](../msbuild/msbuild-inline-tasks.md)
