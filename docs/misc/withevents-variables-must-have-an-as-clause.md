---
title: "Les variables &#39;WithEvents&#39; doivent comporter une clause &#39;As&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30412"
  - "bc30412"
helpviewer_keywords: 
  - "BC30412"
ms.assetid: 8c941523-8e5d-4bf0-8a52-772ecd5d5592
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les variables &#39;WithEvents&#39; doivent comporter une clause &#39;As&#39;
Vous n’avez pas fourni de clause `As` avec le mot clé `WithEvents`. Déclarez la variable comme classe spécifique capable de déclencher les événements.  
  
 **ID d’erreur :** BC30412  
  
### Pour corriger cette erreur  
  
1.  Ajoutez la clause `As` qui spécifie la classe capable de déclencher les événements.  
  
## Voir aussi  
 [NOT IN BUILD : WithEvents et la clause Handles](http://msdn.microsoft.com/fr-fr/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)