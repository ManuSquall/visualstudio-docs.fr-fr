---
title: "Erreur du compilateur CS0123 | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0123
Aucune surcharge pour 'method' ne correspond au délégué 'delegate'  
  
 Une tentative de création d’un délégué a échoué, car la signature correcte n’a pas été utilisée. Les instances d’un délégué doivent être déclarées avec la même signature que celle de la déclaration delegate.  
  
 Vous pouvez corriger cette erreur en ajustant la signature de la méthode ou du délégué. Pour plus d'informations, consultez [Délégués](/dotnet/csharp/programming-guide/delegates/index).  
  
 L’exemple suivant génère l’erreur CS0123.  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```