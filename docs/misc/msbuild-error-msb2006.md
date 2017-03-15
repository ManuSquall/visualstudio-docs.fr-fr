---
title: "MSBuild Error MSB2006 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB2006
**Le fichier projet ne contient pas l'élément racine \<{0}\>.**  
  
 Le nom de l'élément racine n'est pas orthographié correctement ou n'est pas reconnu par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Pour corriger cette erreur  
  
-   Vérifiez l'orthographe du nom de l'élément.  
  
-   Vérifiez si le fichier projet a été modifié ou endommagé.  S'il a été modifié ou endommagé, ouvrez le projet dans la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avec laquelle il a été créé, enregistrez\-le, puis essayez à nouveau de le convertir.  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)