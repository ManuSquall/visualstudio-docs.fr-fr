---
title: "L’instruction ne d&#233;clare pas une m&#233;thode &#39;Get&#39; ou &#39;Set&#39; | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction ne d&#233;clare pas une m&#233;thode &#39;Get&#39; ou &#39;Set&#39;
Votre instruction ne fournit pas d’instruction de déclaration `Get` ou `Set` autour d’une procédure `Property`. Une propriété est définie comme un bloc de code placé entre des instructions `Property` et `End Property`. À l’intérieur de ce bloc, chaque procédure `Property` apparaît sous forme de bloc interne délimité par une instruction de déclaration et une instruction de fin.  
  
 **ID d’erreur :** BC30576  
  
### Pour corriger cette erreur  
  
-   Fournissez une instruction de déclaration `Get` ou `Set`.  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)