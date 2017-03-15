---
title: "&#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car il s’agit d’une instruction &#39;Declare&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30474"
  - "bc30474"
helpviewer_keywords: 
  - "BC30474"
ms.assetid: 7277e8cc-aa3c-40c3-8682-c8c42d2ee921
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car il s’agit d’une instruction &#39;Declare&#39;
Vous avez tenté de substituer un délégué du nom de la classe de base qui a été déclaré avec une instruction `Declare`.  
  
 **ID d’erreur :** BC30474  
  
### Pour corriger cette erreur  
  
1.  Modifiez le membre substitué pour qu’il ne corresponde plus à une instruction `Declare`.  
  
2.  N’essayez pas de substituer cette méthode.  
  
## Voir aussi  
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)