---
title: "MSBuild Error MSB2009 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB2009
**L'attribut '\<nom attribut\>' de l'élément '\<nom élément\>' n'est pas valide.**  
  
 Le nom de l'attribut n'est pas orthographié correctement ou n'est pas reconnu par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Pour corriger cette erreur  
  
-   Vérifiez l'orthographe du nom de l'attribut.  
  
-   Vérifiez si le fichier projet a été modifié ou endommagé.  S'il a été modifié ou endommagé, ouvrez le projet dans la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avec laquelle il a été créé, enregistrez\-le, puis essayez à nouveau de le convertir.  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)