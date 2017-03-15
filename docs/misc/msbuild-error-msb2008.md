---
title: "MSBuild Error MSB2008 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB2008
**Ce système de projet Visual Studio ne peut pas convertir les projets "{0}".  Il ne permet de convertir que les projets clients C\# et VB.**  
  
 Seuls les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] valides peuvent être convertis à l'aide de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Pour corriger cette erreur  
  
-   Si le projet est un projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vérifiez si le fichier projet a été modifié ou endommagé.  S'il a été modifié ou endommagé, ouvrez le projet dans la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avec laquelle il a été créé, enregistrez\-le, puis essayez à nouveau de le convertir.  
  
-   S'il ne s'agit pas d'un projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], utilisez l'outil approprié pour le convertir.  
  
## Voir aussi  
 [Additional Resources](../msbuild/additional-msbuild-resources.md)