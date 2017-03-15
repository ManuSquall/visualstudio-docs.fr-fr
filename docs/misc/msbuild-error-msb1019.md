---
title: "MSBuild Error MSB1019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1019
**Le commutateur du journal est incorrect.**  
  
 Le commutateur **\/logger** n'est pas spécifié correctement.  Pour spécifier un journal, vous devez fournir au moins l'assembly de journalisation, ou si vous souhaitez spécifier explicitement le journal à charger, indiquez la classe et l'assembly de journalisation.  Les paramètres du journal sont facultatifs.  
  
### Pour corriger cette erreur  
  
1.  Spécifiez un journal qui utilise à la fois la classe de journalisation et l'assembly de journalisation.  La syntaxe de `<logger>` est la suivante :  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     La syntaxe de `<logger class>` est la suivante :  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     La syntaxe de `<logger assembly>` est la suivante :  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     Les paramètres `<logger parameters>` sont facultatifs et passés au journal exactement comme vous les avez tapés.  
  
     Par exemple : \/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## Voir aussi  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)   
 [Build Loggers](../msbuild/build-loggers.md)