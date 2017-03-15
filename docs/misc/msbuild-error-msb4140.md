---
title: "Erreur MSBuild MSB4140 | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB4140
**MSB4140: pas de ToolsVersion  par défaut spécifié dans le Registre ni dans le fichier de configuration.**  
  
 Le projet ne spécifie pas de valeur `ToolsVersion` par défaut.  Par conséquent, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] n'est pas en mesure de déterminer la valeur à utiliser.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous qu'une valeur `DefaultToolsVersion` est spécifiée dans le Registre où les ensembles d'outils sont définis, ou dans un fichier de configuration \(tel que msbuild.exe.config\).  
  
## Voir aussi  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)