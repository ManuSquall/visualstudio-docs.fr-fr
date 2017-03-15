---
title: "Erreur du compilateur CS0274 | Microsoft Docs"
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
  - "CS0274"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0274"
ms.assetid: bbd2d64e-a756-4713-b9ed-711d50b65e00
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0274
Impossible de spécifier des modificateurs d’accessibilité pour les accesseurs de la propriété ou de l’indexeur 'property\/indexer'  
  
 Cette erreur se produit quand vous déclarez une propriété ou un indexeur avec des modificateurs d’accès sur ses deux accesseurs. Pour résoudre cette erreur, utilisez un modificateur d’accès sur un seul des deux accesseurs. Pour plus d'informations, consultez [Accessibilité des accesseurs](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
 L’exemple suivant génère l’erreur CS0274 :  
  
```  
// CS0274.cs public class MyClass { public int Property   // CS0274 { public get { return 0; } protected set { } } }  
```