---
title: "MSBuild Error MSB3145 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3145
**MSB3145 : Le paramètre d'entrée de génération '\<propriété\>\=\<valeur\>' n'est ni une URL Web, ni un partage UNC.**  
  
 Cette erreur se produit lorsque la valeur de `SupportUrl`, `ComponentsUrl` ou la propriété de projet `ApplicationUrl` n'est pas valide.  La valeur doit être un URI ou un chemin d'accès UNC valide.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)