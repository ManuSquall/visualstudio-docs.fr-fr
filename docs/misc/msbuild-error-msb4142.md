---
title: "Erreur MSBuild MSB4142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB4142
**MSB4142: MSBuildToolsPath n'est pas le même que MSBuildBinPath pour ToolsVersion" &lt; x.x&gt;."**  
  
 La définition d'ensemble d'outils spécifie des valeurs différentes pour `MSBuildBinPath` et `MSBuildToolsPath`.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que les valeurs de `MSBuildBinPath` et `MSBuildToolsPath` sont les mêmes dans votre définition d'ensemble d'outils.  
  
## Voir aussi  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)