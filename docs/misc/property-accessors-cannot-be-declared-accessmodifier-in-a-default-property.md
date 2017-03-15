---
title: "Les accesseurs de propri&#233;t&#233; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;modificateur_acc&#232;s&gt;&#39; dans une propri&#233;t&#233; &#39;Default&#39; | Microsoft Docs"
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
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les accesseurs de propri&#233;t&#233; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;modificateur_acc&#232;s&gt;&#39; dans une propri&#233;t&#233; &#39;Default&#39;
Une [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) ou une [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) dans une propriété par défaut inclut le mot clé `Private`.  
  
 Ni une propriété par défaut, ni ses procédures de propriété \(`Get` ou `Set`\) ne peuvent être `Private`.  
  
 **ID d’erreur :** BC31107  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Private` de l’instruction `Get` ou `Set`, ou supprimez `Default` de l’[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement).  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)