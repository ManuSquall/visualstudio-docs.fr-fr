---
title: Tâches MSBuild | Microsoft Docs
description: Découvrez comment MSBuild utilise des tâches, ou des unités de code exécutable qui effectuent des opérations de génération atomiques, pendant le processus de génération.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b3bb4c1a17cd5d1481be2fa942686bce3861bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918909"
---
# <a name="msbuild-tasks"></a>tâches MSBuild

Une plateforme de génération doit pouvoir exécuter plusieurs actions pendant le processus de génération. MSBuild utilise des *tâches* pour effectuer ces actions. Une tâche est une unité de code exécutable utilisée par MSBuild pour effectuer des opérations de génération atomiques.

## <a name="task-logic"></a>Logique de tâche

 Le format de fichier de projet XML MSBuild ne peut pas exécuter entièrement des opérations de génération, de sorte que la logique de tâche doit être implémentée en dehors du fichier projet.

 La logique d’exécution d’une tâche est implémentée en tant que classe .NET implémentant l’interface <xref:Microsoft.Build.Framework.ITask>, définie dans l’espace de noms <xref:Microsoft.Build.Framework>.

 La classe de tâche définit également les paramètres d’entrée et de sortie qui sont disponibles pour la tâche dans le fichier projet. Toutes les propriétés non statiques définissables publiques exposées par la classe Task peuvent recevoir des valeurs dans le fichier projet en plaçant un attribut correspondant portant le même nom sur l’élément [Task](../msbuild/task-element-msbuild.md) et en définissant sa valeur comme indiqué dans les exemples plus loin dans cet article.

 Vous pouvez écrire votre propre tâche en créant une classe managée qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations, consultez [écriture de tâches](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Exécuter une tâche à partir d’un fichier projet

 Avant d’exécuter une tâche dans votre fichier projet, vous devez d’abord mapper le type inclus dans l’assembly qui implémente la tâche au nom de la tâche avec l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md). Cela permet à MSBuild de savoir où rechercher la logique d’exécution de votre tâche lorsqu’il la trouve dans votre fichier projet.

 Pour exécuter une tâche dans un fichier projet MSBuild, créez un élément avec le nom de la tâche comme enfant d’un `Target` élément. Si une tâche accepte des paramètres, ceux-ci sont transmis en tant qu’attributs de l’élément.

 Les propriétés et les listes d’éléments MSBuild peuvent être utilisées en tant que paramètres. Par exemple, le code suivant appelle la `MakeDir` tâche et définit la valeur de la `Directories` propriété de l' `MakeDir` objet comme étant égale à la valeur de la `BuildDir` propriété :

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

 MSBuild est fourni avec de nombreuses tâches, telles que [Copy](../msbuild/copy-task.md), qui copie des fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires et [CSC](../msbuild/csc-task.md), qui compile des fichiers de code source C#. Pour obtenir la liste complète des tâches disponibles et des informations sur l’utilisation, consultez [référence des tâches](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Tâches écrasées

 MSBuild recherche des tâches à plusieurs emplacements. Le premier emplacement se trouve dans les fichiers avec l’extension *. OverrideTasks* stocké dans les répertoires .NET Framework. Les tâches contenues dans ces fichiers remplacent toutes les autres tâches du même nom, notamment les tâches du fichier projet. Le deuxième emplacement se trouve dans les fichiers avec l’extension *. Tâches* dans les répertoires de .NET Framework. Si la tâche est introuvable à l’un de ces emplacements, c’est celle contenue dans le fichier projet qui est utilisée.

## <a name="see-also"></a>Voir aussi

- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Écriture de tâches](../msbuild/task-writing.md)
- [Tâches inline](../msbuild/msbuild-inline-tasks.md)
