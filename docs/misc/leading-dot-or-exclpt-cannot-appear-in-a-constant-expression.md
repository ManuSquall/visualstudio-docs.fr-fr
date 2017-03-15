---
title: "Le signe &#171;&#160;.&#160;&#187; ou &#171;&#160;!&#160;&#187; de d&#233;but ne peut pas s’afficher dans une expression constante | Microsoft Docs"
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
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le signe &#171;&#160;.&#160;&#187; ou &#171;&#160;!&#160;&#187; de d&#233;but ne peut pas s’afficher dans une expression constante
L’accès aux membres \(.\) et l’accès aux membres de dictionnaire \(\!\) nécessitent une expression spécifiant l’élément qui contient le membre la plupart du temps, y compris les expressions constantes. La déclaration suivante n’est pas valide.  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **ID d’erreur :** BC30995  
  
### Pour corriger cette erreur  
  
-   Spécifiez l’instance qui contient le membre auquel vous souhaitez accéder.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Comment : déclarer une instance d’un type anonyme \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)