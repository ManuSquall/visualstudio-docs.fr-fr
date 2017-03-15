---
title: "MSBuild Error MSB3157 | Microsoft Docs"
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
  - "vsdeploy.chm:13157"
  - "MSBuild.GenerateBootstrapper.UsingProductCulture"
helpviewer_keywords: 
  - "MSB3157"
ms.assetid: ccfcbea4-eb9b-42ae-9908-47079ecc84a7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3157
**MSB3157 : Impossible de faire correspondre la culture '\<culture\>' de l'élément '\<package\>'.  La culture '\<culture\>' sera utilisée à la place.**  
  
 Cet avertissement est généré lorsque le produit spécifié ne peut pas trouver un fichier manifeste de package \(package.xml\) qui utilise la culture spécifiée.  
  
### Pour corriger cette erreur  
  
-   Fournissez le fichier manifeste de package approprié.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)