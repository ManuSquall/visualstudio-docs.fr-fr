---
title: "MSBuild Error MSB3156 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3156
**MSB3156 : La validation XML n'a pas réussi pour l'élément '\<package\>' situé dans '\<dossier\>'.**  
  
 Cet avertissement est généré lorsque le manifeste \(product.xml\) ne réussit pas la validation XML.  Les problèmes spécifiques sont répertoriés dans un message d'erreur ultérieur \([MSBuild Error MSB3159](/visual-cpp/misc/msbuild-error-msb3159) ou [MSBuild Error MSB3160](../misc/msbuild-error-msb3160.md)\).  
  
### Pour corriger cette erreur  
  
-   Résolvez les problèmes de validation du manifeste répertoriés dans les messages d'erreur ultérieurs.  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)