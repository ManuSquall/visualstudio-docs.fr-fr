---
title: "L’interface &#39;&lt;nom_interface&gt;&#39; n’est pas impl&#233;ment&#233;e par cette classe | Microsoft Docs"
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
  - "bc31035"
  - "vbc31035"
helpviewer_keywords: 
  - "BC31035"
ms.assetid: 99ddabb5-20e0-4cf6-a8d4-1ca91f3c7511
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’interface &#39;&lt;nom_interface&gt;&#39; n’est pas impl&#233;ment&#233;e par cette classe
Un membre de cette classe ou structure tente d’implémenter un membre d’une interface que la classe ou structure n’implémente pas.  
  
 **ID d’erreur :** BC31035  
  
### Pour corriger cette erreur  
  
-   Ajoutez une instruction `Implements` au début de la classe ou structure pour qu’elle implémente l’interface appropriée.  
  
-   Supprimez le mot clé `Implements` du membre qui provoque cette erreur.  
  
## Voir aussi  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)