---
title: "Erreur du compilateur CS0730 | Microsoft Docs"
ms.custom: ""
ms.date: "09/30/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0730"
ms.assetid: bf291285-dc1e-4c8d-a449-119004adc088
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0730
Impossible de transférer le type 'type', car il s’agit d’un type imbriqué de 'type'  
  
 Cette erreur est générée quand vous essayez de transférer une classe imbriquée.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0730. Il se compose de deux fichiers sources. Compilez tout d’abord le fichier bibliothèque `CS0730a.cs`, puis le fichier `CS0730.cs` faisant référence au fichier bibliothèque.  
  
```  
// CS0730a.cs // compile with: /t:library public class Outer { public class Nested {} }  
```  
  
```  
// CS0730.cs // compile with: /t:library /r:CS0730a.dll using System.Runtime.CompilerServices; [assembly:TypeForwardedToAttribute(typeof(Outer.Nested))]   // CS0730 [assembly:TypeForwardedToAttribute(typeof(Outer))]   // OK  
```