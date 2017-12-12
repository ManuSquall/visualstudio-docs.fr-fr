---
title: "Tâches MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: "18"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: fc2afbe7b0226cb5983aa3022ff4b24ac31fe7aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-tasks"></a>Tâches MSBuild
Une plateforme de génération doit pouvoir exécuter plusieurs actions pendant le processus de génération. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utilise des *tâches* pour effectuer ces actions. Une tâche est une unité de code exécutable utilisée par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour exécuter des opérations de génération atomiques.  
  
## <a name="task-logic"></a>Logique de tâche  
 Comme le format de fichier projet XML [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ne peut pas exécuter entièrement les opérations de génération seul, une logique de tâche doit être implémentée en dehors du fichier projet.  
  
 La logique d’exécution d’une tâche est implémentée en tant que classe .NET implémentant l’interface <xref:Microsoft.Build.Framework.ITask>, définie dans l’espace de noms <xref:Microsoft.Build.Framework>.  
  
 La classe de tâche définit également les paramètres d’entrée et de sortie qui sont disponibles pour la tâche dans le fichier projet. Toutes les propriétés définissables publiques non statiques et non abstraites exposées par la classe de tâche sont accessibles dans le fichier projet en plaçant un attribut correspondant du même nom dans l’élément [Task](../msbuild/task-element-msbuild.md).  
  
 Vous pouvez écrire votre propre tâche en créant une classe managée qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations, consultez [Écriture de tâches](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Exécution d’une tâche à partir d’un fichier projet  
 Avant d’exécuter une tâche dans votre fichier projet, vous devez d’abord mapper le type inclus dans l’assembly qui implémente la tâche au nom de la tâche avec l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md). Cette opération permet à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de savoir où rechercher la logique d’exécution de votre tâche lorsqu’il la trouve dans votre fichier projet.  
  
 Pour exécuter une tâche dans un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], créez un élément pourvu du nom de la tâche comme enfant d’un élément `Target`. Si une tâche accepte des paramètres, ceux-ci sont transmis en tant qu’attributs de l’élément.  
  
 Les propriétés et les listes d’éléments [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peuvent être utilisées comme des paramètres. Par exemple, le code suivant appelle la tâche `MakeDir` et définit la valeur de la propriété `Directories` de l’objet `MakeDir` égale à la valeur de la propriété `BuildDir` déclarée dans l’exemple précédent.  
  
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
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est fourni avec de nombreuses tâches, par exemple [Copy](../msbuild/copy-task.md), qui copie des fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires et [Csc](../msbuild/csc-task.md), qui compile des fichiers de code source [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Pour obtenir la liste complète des tâches disponibles et les informations sur leur utilisation, consultez [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Tâches substituées  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] recherche des tâches à plusieurs emplacements. Les fichiers portant l’extension .OverrideTasks, stockés dans les répertoires .NET Framework correspondent au premier emplacement. Les tâches contenues dans ces fichiers remplacent toutes les autres tâches du même nom, notamment les tâches du fichier projet. Les fichiers portant l’extension .Tasks, stockés dans les répertoires .NET Framework correspondent au second emplacement. Si la tâche est introuvable à l’un de ces emplacements, c’est celle contenue dans le fichier projet qui est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Écriture de tâches](../msbuild/task-writing.md)   
 [Tâches inline](../msbuild/msbuild-inline-tasks.md)