---
title: "Avertissement du compilateur (niveau&#160;1) CS1707 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1707"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1707"
ms.assetid: 47b6096e-4e4b-4057-b9d7-4a096139267a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1707
Délégué 'nom\_délégué' lié à 'nom\_méthode1' à la place de 'nom\_méthode2' en raison de nouvelles règles de langage  
  
 C\# 2.0 implémente de nouvelles règles pour lier un délégué à une méthode. Des informations supplémentaires qui n’étaient pas prises en compte auparavant sont désormais examinées. Cet avertissement indique que le délégué est maintenant lié à une autre surcharge de la méthode. Vous pouvez vérifier que le délégué doit vraiment être lié à 'nom\_méthode1' plutôt qu’à 'nom\_méthode2'.  
  
 Pour obtenir une description de la façon dont le compilateur détermine la méthode à laquelle lier un délégué, consultez [Utilisation de la variance dans les délégués](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).