---
title: "Erreur du compilateur CS0551 | Microsoft Docs"
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
  - "CS0551"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0551"
ms.assetid: fb456ecf-dff3-4e39-b9b3-de23d81dadea
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0551
Il manque l’accesseur 'accessor' dans l’implémentation d’interface explicite 'implementation'  
  
 Une classe qui implémente explicitement une propriété d’interface doit implémenter tous les accesseurs définis par l’interface.  
  
 Pour plus d'informations, consultez [Utilisation de propriétés](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0551.  
  
```  
// CS0551.cs // compile with: /target:library interface ii { int i { get; set; } } public class a : ii { int ii.i { set {} }   // CS0551 // OK int ii.i { set {} get { return 0; } } }  
```