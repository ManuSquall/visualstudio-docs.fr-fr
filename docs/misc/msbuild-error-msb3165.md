---
title: "MSBuild Error MSB3165 | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3165
**MSB3165 : La valeur de l'attribut '\<CléPublique\>' dans '\<package\>' ne correspond pas à celle du fichier '\<fichier\>'.**  
  
 Cet avertissement se produit lorsque la clé publique spécifiée dans le fichier du package du programme d'amorçage ne correspond pas à la signature du package redistribuable sur le disque, ou que le package redistribuable n'est pas signé.  La génération utilise la valeur de clé publique du package redistribuable sur le disque s'il est signé, ou utilise le hachage du package redistribuable sur le disque s'il n'est pas signé.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)   
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)