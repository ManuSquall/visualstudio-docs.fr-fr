---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS0657 | Microsoft Docs"
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
  - "CS0657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0657"
ms.assetid: d12d2efc-f44e-40e6-b825-5a66ead0c08e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS0657
'modificateur d’attribut' n’est pas un emplacement d’attribut valide pour cette déclaration. Les emplacements d’attributs valides pour cette déclaration sont 'emplacements'. Tous les attributs de ce bloc seront ignorés.  
  
 Le compilateur a trouvé un modificateur d’attribut dans un emplacement non valide. Pour plus d’informations, consultez [Attribute Targets](http://msdn.microsoft.com/fr-fr/59a261f0-1cfb-4aa5-b610-6b735389882c).  
  
 L’exemple suivant génère l’erreur CS0657 :  
  
```  
// CS0657.cs // compile with: /target:library public class TestAttribute : System.Attribute {} [return: Test]   // CS0657 return not valid on a class class Class1 {}  
```