---
title: "Erreur du compilateur CS0554 | Microsoft Docs"
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
  - "CS0554"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0554"
ms.assetid: 884db4b2-3a69-4434-9a25-526f596e03c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0554
'routine de conversion' : conversion définie par l’utilisateur vers\/de la classe dérivée  
  
 Les conversions définies par l’utilisateur en valeurs de classe dérivée ne sont pas autorisées. Ce type d’opérateur n’est pas nécessaire.  
  
 Pour plus d’informations sur les conversions définies par l’utilisateur, consultez le chapitre 6 de la spécification du langage C\#.  
  
 L’exemple suivant génère l’erreur CS0554 :  
  
```  
// CS0554.cs namespace x { public class ii { // delete the conversion routine to resolve CS0554 public static implicit operator ii(a aa) // CS0554 { return new ii(); } } public class a : ii { public static void Main() { } } }  
```