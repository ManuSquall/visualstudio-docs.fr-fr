---
title: "Erreur du compilateur CS0594 | Microsoft Docs"
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
  - "CS0594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0594"
ms.assetid: a3d6bde1-db63-4c5c-a425-8c6a39e00999
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0594
La constante à virgule flottante sort de la plage du type 'type'  
  
 Une valeur assignée à une variable à virgule flottante est trop grande pour les variables de ce type de données. Pour plus d’informations sur la plage de valeurs autorisées des types de données, consultez [Tableau des types intégraux](/dotnet/csharp/language-reference/keywords/integral-types-table).  
  
 L’exemple suivant génère l’erreur CS0594 :  
  
```  
// CS0594.cs namespace MyNamespace { public class MyClass { public static void Main() { float f = 6.77777777777E400;   // CS0594, value too large } } }  
```