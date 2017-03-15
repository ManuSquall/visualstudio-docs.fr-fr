---
title: "How to: Clean a Build | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, cleaning a build"
  - "directories [.NET Framework], for output items"
  - "output, removing items"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Clean a Build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous nettoyez une génération, tous les fichiers intermédiaires et de sortie sont supprimés, seuls les fichiers projet et fichiers composants étant conservés.  À partir des fichiers projet et des fichiers composants, il est possible alors de générer de nouvelles instances des fichiers intermédiaires et des fichiers de sortie.  La bibliothèque des tâches courantes fournie avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclut une tâche [Exec](../msbuild/exec-task.md) que vous pouvez utiliser pour exécuter les commandes système.  Pour plus d'informations sur la bibliothèque des tâches, consultez [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## Création d'un répertoire pour les éléments de sortie  
 Par défaut, le fichier .exe, créé lorsque vous compilez un projet, est placé dans le même répertoire que les fichiers projet et les fichiers sources.  Cependant, les éléments de sortie sont généralement créés dans un répertoire séparé.  
  
#### Pour créer un répertoire pour les éléments de sortie  
  
1.  Utilisez l'élément `Property` pour définir l'emplacement et le nom du répertoire.  Par exemple, créez un répertoire nommé `BuiltApp` dans le répertoire qui contient les fichiers projet et les fichiers sources:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Utilisez la tâche [MakeDir](../msbuild/makedir-task.md) pour créer le répertoire si celui\-ci n'existe pas.  Par exemple :  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## Suppression des éléments de sortie  
 Avant de créer de nouvelles instances de fichiers intermédiaires et de fichiers de sortie, il se peut que vous souhaitiez effacer toutes les instances précédentes des fichiers intermédiaires et des fichiers de sortie.  Utilisez la tâche [RemoveDir](../msbuild/removedir-task.md) pour supprimer du disque un répertoire et tous les fichiers et répertoires qu'il contient.  
  
#### Pour supprimer un répertoire et tous les fichiers contenus dans le répertoire  
  
-   Utilisez la tâche `RemoveDir` pour supprimer le répertoire.  Par exemple :  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## Exemple  
 L'exemple de projet de code suivant contient une nouvelle cible, `Clean`, qui utilise la tâche `RemoveDir` pour supprimer un répertoire et tous les fichiers et répertoires qu'il contient.  De même, dans cet exemple, la cible `Compile` crée un répertoire séparé pour les éléments de sortie qui sont supprimés lorsque la génération est nettoyée.  
  
 `Compile` est définie comme cible par défaut et, par conséquent, est utilisé automatiquement, à moins que vous ne spécifiiez une cible différente.  Vous utilisez le commutateur de ligne de commande **\/target** pour spécifier une cible différente.  Par exemple :  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Le commutateur **\/target** peut être abrégé en **\/t** et spécifier plusieurs cibles.  Par exemple, pour utiliser la cible `Clean`, puis la cible `Compile`, tapez :  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Exec Task](../msbuild/exec-task.md)   
 [MakeDir Task](../msbuild/makedir-task.md)   
 [RemoveDir Task](../msbuild/removedir-task.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Targets](../msbuild/msbuild-targets.md)