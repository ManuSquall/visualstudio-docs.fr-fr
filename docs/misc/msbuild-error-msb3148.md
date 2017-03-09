---
title: "MSBuild Error MSB3148 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3148
**MSB3148 : Aucun chemin de sortie spécifié dans les paramètres de génération.**  
  
 Cette erreur se produit lorsqu'un chemin de sortie null ou non valide est spécifié ; par exemple, si `OutputPath=""` dans le fichier projet.  La valeur par défaut du chemin de sortie est `CurrentDirectory`.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que `OutputPath` n'est pas vide, ou qu'il n'est pas inclus dans le fichier projet.  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)