---
title: "Les variables locales &#224; l’int&#233;rieur de m&#233;thodes de structures ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;Static&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les variables locales &#224; l’int&#233;rieur de m&#233;thodes de structures ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;Static&#39;
Le modificateur `Static` ne peut pas être utilisé avec des variables locales dans des structures.  
  
 **ID d’erreur :** BC31400  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur `Static` de la variable locale.  
  
2.  Déclarez la variable en tant que variable statique avec une portée plus large.  
  
## Voir aussi  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)