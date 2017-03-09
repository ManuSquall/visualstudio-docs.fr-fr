---
title: "Trop de clients pour cette DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Trop de clients pour cette DLL
La bibliothèque de liens dynamiques \(DLL\) de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] autorise uniquement l’accès à un nombre limité d’applications hôtes. Votre application et les autres applications qui sont des hôtes [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] \(dont certaines sont accessibles par votre application\) tentent toutes d’accéder à la DLL [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en même temps.  
  
### Pour corriger cette erreur  
  
-   Réduisez le nombre d’applications ouvertes accédant à [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Voir aussi  
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)