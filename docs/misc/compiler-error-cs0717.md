---
title: "Erreur du compilateur CS0717 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0717
'classe static' : les classes static ne peuvent pas être utilisées en tant que contraintes  
  
 Les classes static ne peuvent pas être étendues, car elles contiennent uniquement des membres static et non des membres d’instance. Comme elles ne peuvent pas être étendues, elles n’ont aucune utilité en tant que paramètres et contraintes de type, car aucun type ne peut exister qui soit une spécialisation d’une classe static.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0717 :  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```