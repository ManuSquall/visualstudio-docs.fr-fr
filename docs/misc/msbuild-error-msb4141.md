---
title: "Erreur MSBuild MSB4141 | Microsoft Docs"
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
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB4141
**MSB4141: MSBuildToolsPath n'est pas spécifié pour le ToolsVersion défini à "&lt ; x.x &gt ;".**  
  
 Un ensemble d'outils personnalisé est défini mais aucune valeur n'est spécifiée pour `MSBuildToolsPath`.  
  
### Pour corriger cette erreur  
  
-   Spécifiez une valeur valide pour `MSBuildToolsPath` lorsque vous définissez un ensemble d'outils personnalisé dans le Registre ou le fichier de configuration [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Voir aussi  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)