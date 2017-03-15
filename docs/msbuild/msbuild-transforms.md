---
title: "MSBuild Transforms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, transforms"
  - "transforms [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# MSBuild Transforms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une transformation est une conversion un à un d'une liste d'éléments en une autre.  Outre le fait qu'elle permet à un projet de convertir des listes d'éléments, une transformation permet également à une cible d'identifier un mappage direct entre ses entrées et ses sorties.  Cette rubrique explique les transformations et la manière dont [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] les utilise pour générer des projets plus efficacement.  
  
## Modificateurs de transformation  
 Les transformations ne sont pas arbitraires, mais sont limitées par une syntaxe spéciale dans laquelle tous les modificateurs de transformation doivent être au format %\(*ItemMetaDataName*\).  N'importe quelle métadonnée d'élément peut être utilisée en tant que modificateur de transformation.  En font partie les métadonnées d'élément connues assignées à chaque élément lors de sa création.  Pour obtenir la liste des métadonnées d'éléments connus, consultez [Well\-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Dans l'exemple suivant, une liste de fichiers .resx est transformée en une liste de fichiers .resources.  Le modificateur de transformation %\(nom de fichier\) spécifie que chaque fichier .resources possède le même nom de fichier que le fichier .resx correspondant.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Vous pouvez spécifier un séparateur personnalisé pour une liste d'éléments transformée de la même manière que pour une liste d'éléments standard.  Par exemple, pour séparer une liste d'éléments transformée à l'aide d'une virgule \(,\) au lieu du point\-virgule par défaut \(;\), utilisez le code XML suivant :  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Par exemple, si les éléments de la liste @\(RESXFile\) sont `Form1.resx`, `Form2.resx` et `Form3.resx`, les sorties dans la liste transformée seront `Form1.resources`, `Form2.resources` et `Form3.resources`.  
  
## Utilisation de modificateurs multiples  
 Une expression de transformation peut contenir plusieurs modificateurs, qui peuvent être combinés dans n'importe quel ordre et répétés.  Dans l'exemple suivant, le nom du répertoire qui contient les fichiers est modifié, mais les fichiers conservent le nom et l'extension de leur fichier d'origine.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Par exemple, si les éléments contenus dans la liste `RESXFile` sont `Project1\Form1.resx`, `Project1\Form2.resx` et `Project1\Form3.text`, les sorties dans la liste transformée seront `Toolset\Form1.resx`, `Toolset\Form2.resx` et `Toolset\Form3.text`.  
  
## Analyse de dépendance  
 Les transformations garantissent un mappage un à un entre la liste d'éléments transformée et la liste d'éléments d'origine.  Par conséquent, si une cible crée des sorties qui sont des transformations des entrées, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut analyser les horodatages des entrées et des sorties, et décider s'il faut ignorer, générer ou régénérer partiellement une cible.  
  
 Dans la tâche [Copy Task](../msbuild/copy-task.md) de l'exemple suivant, chaque fichier de la liste d'éléments `BuiltAssemblies` est mappé à un fichier du dossier de destination de la tâche, spécifié à l'aide d'une transformation dans l'attribut `Outputs`.  Si un fichier de la liste d'éléments `BuiltAssemblies` est modifié, la tâche `Copy` s'exécute uniquement pour le fichier modifié, et tous les autres fichiers sont ignorés.  Pour plus d'informations sur l'analyse de dépendance et l'utilisation des transformations, consultez [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## Exemple  
  
### Description  
 L'exemple suivant illustre un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qui utilise des transformations.  Cet exemple suppose qu'il n'existe qu'un seul fichier .xsd dans le répertoire c:\\sub0\\sub1\\sub2\\sub3 et que le répertoire de travail est c:\\sub0.  
  
### Code  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### Commentaires  
 Cet exemple génère la sortie suivante.  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## Voir aussi  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md)