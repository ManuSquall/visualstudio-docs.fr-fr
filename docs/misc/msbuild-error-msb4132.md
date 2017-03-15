---
title: "MSBuild Error MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB4132
**MSB4132: La version des outils "' &lt ; version&gt ;'" n'est pas reconnue.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a trouvé un ensemble d'outils qui correspond à la valeur spécifiée pour `ToolsVersion`.  
  
### Pour corriger cette erreur  
  
-   Spécifiez une valeur valide pour `ToolsVersion` dans la balise de projet, ou sur la ligne de commande si vous utilisez le commutateur **\/ToolsVersion** de MSBuild.  
  
## Voir aussi  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)