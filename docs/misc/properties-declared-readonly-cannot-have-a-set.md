---
title: "Les propri&#233;t&#233;s d&#233;clar&#233;es &#39;ReadOnly&#39; ne peuvent pas avoir de &#39;Set&#39; | Microsoft Docs"
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
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les propri&#233;t&#233;s d&#233;clar&#233;es &#39;ReadOnly&#39; ne peuvent pas avoir de &#39;Set&#39;
La procédure `Set` écrit la valeur d’une propriété. Les propriétés `ReadOnly` ne peuvent pas être écrites.  
  
 **ID d’erreur :** BC30022  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `ReadOnly` de l’instruction `Property` ou supprimez la procédure `Set` du corps de la propriété.  
  
## Voir aussi  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)