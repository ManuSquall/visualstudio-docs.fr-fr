---
title: "Avertissement du compilateur (niveau&#160;2) CS0440 | Microsoft Docs"
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
  - "CS0440"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0440"
ms.assetid: ade6761f-4d7d-42bc-a0c5-bbb1b987a1aa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0440
La définition d'un alias nommé 'global' n'est pas très judicieuse dans la mesure où 'global::' fait toujours référence à l'espace de noms global et non à un alias  
  
 Cet avertissement est émis quand vous définissez un alias nommé global.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0440 :  
  
```  
// CS0440.cs // Compile with: /W:1 using global = MyClass;   // CS0440 class MyClass { static void Main() { // Note how global refers to the global namespace // even though it is redefined above. global::System.Console.WriteLine(); } }  
```