---
title: "&#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration event d’interface | Microsoft Docs"
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
  - "bc30275"
  - "vbc30275"
helpviewer_keywords: 
  - "BC30275"
ms.assetid: bd12c952-c619-4753-8d6d-90ef4086fdc2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration event d’interface
Une instruction `Event` dans une interface contient un mot clé qui n’est pas autorisé, tel que `Implements`. Une interface peut uniquement définir des membres ; elle ne peut pas les implémenter.  
  
 **ID d’erreur :** BC30275  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé de l’instruction de déclaration.  
  
2.  Déplacez l’implémentation des membres d’interface vers une classe qui implémente l’interface.  
  
## Voir aussi  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)