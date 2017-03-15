---
title: "Erreur du compilateur CS0061 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0061
Accessibilité incohérente : l’interface de base 'interface 1' est moins accessible que l’interface 'interface 2'  
  
 Une construction [public](/dotnet/csharp/language-reference/keywords/public) doit retourner un objet accessible publiquement.  
  
 L’accessibilité d’interface ne peut pas être restreinte dans une interface dérivée. Pour plus d’informations, consultez [Interfaces](/dotnet/csharp/programming-guide/interfaces/index) et [Modificateurs d'accès](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 L’exemple suivant génère l’erreur CS0061.  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```