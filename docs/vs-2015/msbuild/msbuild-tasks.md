---
title: Tâches MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dff7c0ce45c71340f3b931e32843adb6a90ea075
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176696"
---
# <a name="msbuild-tasks"></a>Tâches MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Une plateforme de génération doit pouvoir exécuter plusieurs actions pendant le processus de génération. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] utilise des *tâches* pour effectuer ces actions. Une tâche est une unité de code exécutable utilisée par [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pour exécuter des opérations de génération atomiques.  
  
## <a name="task-logic"></a>Logique de tâche  
 Comme le format de fichier projet XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ne peut pas exécuter entièrement les opérations de génération seul, une logique de tâche doit être implémentée en dehors du fichier projet.  
  
 La logique d’exécution d’une tâche est implémentée en tant que classe .NET implémentant l’interface <xref:Microsoft.Build.Framework.ITask>, définie dans l’espace de noms <xref:Microsoft.Build.Framework>.  
  
 La classe de tâche définit également les paramètres d’entrée et de sortie qui sont disponibles pour la tâche dans le fichier projet. Toutes les propriétés définissables publiques non statiques et non abstraites exposées par la classe de tâche sont accessibles dans le fichier projet en plaçant un attribut correspondant du même nom dans l’élément [Task](../msbuild/task-element-msbuild.md).  
  
 Vous pouvez écrire votre propre tâche en créant une classe managée qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations, consultez l’article [Task Writing (Écriture de tâches)](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Exécution d’une tâche à partir d’un fichier projet  
 Avant d’exécuter une tâche dans votre fichier projet, vous devez d’abord mapper le type inclus dans l’assembly qui implémente la tâche au nom de la tâche avec l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md). Cette opération permet à [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] de savoir où rechercher la logique d’exécution de votre tâche lorsqu’il la trouve dans votre fichier projet.  
  
 Pour exécuter une tâche dans un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], créez un élément pourvu du nom de la tâche comme enfant d’un élément `Target`. Si une tâche accepte des paramètres, ceux-ci sont transmis en tant qu’attributs de l’élément.  
  
 Les propriétés et les listes d’éléments [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] peuvent être utilisées comme des paramètres. Par exemple, le code suivant appelle la tâche `MakeDir` et définit la valeur de la propriété `Directories` de l’objet `MakeDir` égale à la valeur de la propriété `BuildDir` déclarée dans l’exemple précédent.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Les tâches peuvent également retourner des informations au fichier projet, qui peuvent être stockées dans les éléments ou les propriétés en vue d’une utilisation ultérieure. Par exemple, le code suivant appelle la tâche `Copy` et stocke les informations de la propriété en sortie `CopiedFiles` dans la liste d’éléments `SuccessfullyCopiedFiles`.  
  
```  
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
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] est fourni avec de nombreuses tâches, par exemple [Copy](../msbuild/copy-task.md), qui copie des fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires et [Csc](../msbuild/csc-task.md), qui compile des fichiers de code source [!INCLUDE[csprcs](../includes/csprcs-md.md)]. Pour obtenir la liste complète des tâches disponibles et les informations sur leur utilisation, consultez l’article [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Tâches substituées  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] recherche des tâches à plusieurs emplacements. Les fichiers portant l’extension .OverrideTasks, stockés dans les répertoires .NET Framework correspondent au premier emplacement. Les tâches contenues dans ces fichiers remplacent toutes les autres tâches du même nom, notamment les tâches du fichier projet. Les fichiers portant l’extension .Tasks, stockés dans les répertoires .NET Framework correspondent au second emplacement. Si la tâche est introuvable à l’un de ces emplacements, c’est celle contenue dans le fichier projet qui est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md)   
 [Task Writing (Écriture de tâches)](../msbuild/task-writing.md)   
 [Inline Tasks (Tâches inline MSBuild)](../msbuild/msbuild-inline-tasks.md)


