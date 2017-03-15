---
title: "Erreur du compilateur CS0138 | Microsoft Docs"
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
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0138
Une directive d’espace de noms using ne peut être appliquée qu’aux espaces de noms ; 'type' est un type, pas un espace de noms  
  
 Une directive [using](/dotnet/csharp/language-reference/keywords/using) accepte uniquement le nom d’un espace de noms en tant que paramètre. Pour plus d'informations, consultez [Espaces de noms](/dotnet/csharp/programming-guide/namespaces/index).  
  
 L’exemple suivant génère l’erreur CS0138 :  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```