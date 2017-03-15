---
title: "MSBuild Error MSB4133 | Microsoft Docs"
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
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB4133
**MSB4133: Une version des outils par défaut" &lt ; x.x.&gt ; " a été spécifié mais sa définition est introuvable.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ne parvient pas à trouver l'ensemble d'outils qui est défini dans le fichier projet comme `DefaultToolsVersion`.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que `DefaultToolsVersion` est spécifié correctement et que cet ensemble d'outils est défini dans le Registre ou dans le fichier de configuration [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Voir aussi  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)