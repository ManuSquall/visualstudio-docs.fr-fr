---
title: "MSBuild Error MSB3161 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3161
**MSB3161 : Une dépendance circulaire a été détectée entre les packages générés suivants : '\<package\>'**  
  
 Cet avertissement est généré lorsqu'une dépendance circulaire est détectée dans le graphique des dépendances du package du programme d'amorçage \(par exemple : A→B→C→A\).  Dans ce cas, le programme d'amorçage ne peut pas déterminer le package à installer en premier.  
  
### Pour corriger cette erreur  
  
-   Supprimez la dépendance circulaire, en modifiant les dépendances décrites dans les fichiers du package du programme d'amorçage ou en évitant d'installer l'un des packages interdépendants.  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)