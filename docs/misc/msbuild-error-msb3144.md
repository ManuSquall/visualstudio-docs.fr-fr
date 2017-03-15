---
title: "MSBuild Error MSB3144 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3144
**MSB3144 : Pas assez de données fournies pour générer un programme d'amorçage.  Indiquez une valeur pour au moins l'un des paramètres : 'ApplicationFile' ou 'BootstrapperItems'.**  
  
 Cette erreur se produit lorsqu'une quantité insuffisante de données a été fournie pour générer un programme d'amorçage.  Le processus de génération crée un programme d'amorçage vide sans aucun programme d'installation de l'application et aucun package.  
  
### Pour corriger cette erreur  
  
-   Indiquez une valeur pour au moins l'un des paramètres `ApplicationFile` ou `BootstrapperItems`.  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)