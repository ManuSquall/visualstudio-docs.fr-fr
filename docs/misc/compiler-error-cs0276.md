---
title: "Erreur du compilateur CS0276 | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0276
'property\/indexer' : les modificateurs d’accessibilité sur les accesseurs ne peuvent être utilisés que si la propriété ou l’indexeur a un accesseur get et un accesseur set  
  
 Cette erreur se produit quand vous déclarez une propriété ou un indexeur avec un seul accesseur et utilisez un modificateur d’accès sur l’accesseur. Pour y remédier, supprimez le modificateur d’accès ou ajoutez un autre accesseur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0276 :  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```