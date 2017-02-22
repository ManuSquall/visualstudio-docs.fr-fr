---
title: "How to: Display an Item List Separated with Commas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, separating items with semicolons"
  - "MSBuild, formatting item collections"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# How to: Display an Item List Separated with Commas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous travaillez avec les listes d'éléments dans [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\), il peut être utile d'afficher le contenu de ces listes d'une façon qui soit simple à lire.  Ou, vous pouvez avoir une tâche qui prend une liste d'éléments séparés par une chaîne de séparation particulière.  Dans chacun des deux cas, vous pouvez spécifier une chaîne de séparation pour une liste d'éléments.  
  
## Séparation d'éléments dans une liste avec des virgules  
 Par défaut, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utilise le point\-virgule pour séparer chacun des éléments d'une liste.  Par exemple, considérez un élément `Message` avec la valeur suivante :  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Lorsque la liste d'éléments `@(TXTFile)` contient les éléments App1.txt, App2.txt et App3.txt, le message est :  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Si vous souhaitez modifier le comportement par défaut, vous pouvez spécifier votre propre séparateur.  La syntaxe pour spécifier un séparateur de liste d'éléments est le suivant :  
  
 `@(ItemListName, '<separator>')`  
  
 Le séparateur peut être un caractère unique ou une chaîne et doit être entouré de guillemets simples.  
  
#### Pour insérer une virgule et un espace entre les éléments  
  
-   Utilisez une notation d'élément similaire à la notation suivante :  
  
     `@(TXTFile, ', ')`  
  
## Exemple  
 Dans cet exemple, la tâche [Exec](../msbuild/exec-task.md) exécute l'outil findstr pour rechercher des chaînes de texte spécifiées dans le fichier Phrases.txt.  Dans la commande findstr, comme les chaînes de recherche littérales sont indiquées par le commutateur **\/c:**, le séparateur d'éléments, `/c:`, est inséré entre les éléments de la liste `@(Phrase)`.  
  
 Dans cet exemple, la commande de ligne de commande équivalente est la suivante :  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Items](../msbuild/msbuild-items.md)