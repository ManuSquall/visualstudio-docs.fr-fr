---
title: "Les propri&#233;t&#233;s d&#233;clar&#233;es &#39;WriteOnly&#39; ne peuvent pas avoir de &#39;Get&#39; | Microsoft Docs"
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
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les propri&#233;t&#233;s d&#233;clar&#233;es &#39;WriteOnly&#39; ne peuvent pas avoir de &#39;Get&#39;
La procédure `Get` lit la valeur d’une propriété. Les propriétés `WriteOnly` ne peuvent pas être lues.  
  
 **ID d’erreur :** BC30023  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `WriteOnly` de l’instruction `Property` ou supprimez la procédure `Get` du corps de la propriété.  
  
## Voir aussi  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [WriteOnly](/dotnet/visual-basic/language-reference/modifiers/writeonly)