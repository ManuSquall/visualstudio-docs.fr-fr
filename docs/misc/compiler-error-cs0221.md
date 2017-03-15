---
title: "Erreur du compilateur CS0221 | Microsoft Docs"
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
  - "CS0221"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0221"
ms.assetid: 97170b49-54f1-4dac-a865-2f9cc6bf55b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0221
La valeur de constante 'value' ne peut pas être convertie en 'type' \(utilisez la syntaxe 'unchecked' pour la remplacer\)  
  
 Une opération d’assignation qui entraînerait une perte de données a été détectée par [checked](/dotnet/csharp/language-reference/keywords/checked), qui est activé par défaut. Corrigez l’assignation ou utilisez [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) pour résoudre cette erreur. Pour plus d'informations, consultez [Checked et unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 L’exemple suivant génère l’erreur CS0221 :  
  
```  
// CS0221.cs public class MyClass { public static void Main() { // unchecked // { int a = (int)0xFFFFFFFF;   // CS0221 a++; // } } }  
```