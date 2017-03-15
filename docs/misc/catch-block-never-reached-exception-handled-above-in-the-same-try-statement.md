---
title: "Le bloc &#39;Catch&#39; n’a jamais &#233;t&#233; atteint. &lt;exception&gt; g&#233;r&#233; au-dessus dans la m&#234;me instruction &#39;Try&#39; | Microsoft Docs"
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
  - "bc42031"
  - "vbc42031"
helpviewer_keywords: 
  - "BC42031"
ms.assetid: 7d15597c-5988-42ea-a853-63cbf78faaf3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le bloc &#39;Catch&#39; n’a jamais &#233;t&#233; atteint. &lt;exception&gt; g&#233;r&#233; au-dessus dans la m&#234;me instruction &#39;Try&#39;
Un bloc `Catch` du code n’est pas accessible, car il est géré dans un bloc `Try` précédent.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42031  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction redondante.  
  
## Voir aussi  
 [Procédure : interception d’une exception en Visual Basic](http://msdn.microsoft.com/fr-fr/f3063c89-d2bf-49b1-91b5-b87edfb18b95)   
 [Comment : tester du code à l’aide d’un bloc Try...Catch dans Visual Basic](http://msdn.microsoft.com/fr-fr/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Procédure : filtrage des erreurs dans un bloc Catch en Visual Basic](http://msdn.microsoft.com/fr-fr/85964d0a-56e7-4301-a96e-5eaea23b7b9b)   
 [Procédure pas à pas : gestion structurée des exceptions \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/440da655-4b32-490b-8b16-bfe46f41fa76)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)