---
title: "&#39;End Get&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Get&#39; correspondant | Microsoft Docs"
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
  - "bc30630"
  - "vbc30630"
helpviewer_keywords: 
  - "BC30630"
ms.assetid: d858076a-9088-4ad0-9766-95029476bf9b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Get&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Get&#39; correspondant
`End Get` est utilisé pour terminer les procédures de propriétés `Get`. La construction `End Get` a été rencontrée à l’extérieur d’une procédure de propriété `Get`.  
  
 **ID d'erreur :** BC30630  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la procédure de propriété `Get` est déclarée après un mot clé `Property` et avant la construction `End Property`.  
  
2.  Vérifiez que la procédure de propriété `Get` commence par le mot clé `Get` et se termine par la construction `End Get`.  
  
## Voir aussi  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/1c138efa-9bc2-44d7-80a0-f3a7c2510264)