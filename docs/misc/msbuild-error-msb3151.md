---
title: "MSBuild Error MSB3151 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
helpviewer_keywords: 
  - "MSB3151"
ms.assetid: e4766734-2e90-436e-850b-a8a9da535dee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3151
**MSB3151 : L'élément '\<package\>' comprend déjà '\<package\>'.**  
  
 Cet avertissement se produit lorsque vous avez sélectionné deux packages de programme d'amorçage, et un package est inclus dans l'autre \(par exemple, la sélection du package inclus est redondante\).  
  
### Pour corriger cette erreur  
  
-   Désactivez la case à cocher correspondant au package inclus redondant.