---
title: "Erreur du compilateur CS0540 | Microsoft Docs"
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
  - "CS0540"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0540"
ms.assetid: 2da2cd4a-0ff1-45ea-bb72-ea078bc95dea
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0540
'interface member' : le type conteneur n’implémente pas l’interface 'interface'  
  
 Vous avez tenté d’implémenter un membre d’interface dans une [classe](/dotnet/csharp/language-reference/keywords/class) qui ne dérive pas de l’[interface](/dotnet/csharp/language-reference/keywords/interface). Vous devez soit supprimer l’implémentation du membre d’interface, soit ajouter l’interface à la liste de classes de base de la classe.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0540.  
  
```  
// CS0540.cs interface I { void m(); } public class Clx { void I.m() {}   // CS0540 } // OK public class Cly : I { void I.m() {} public static void Main() {} }  
```  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0540.  
  
```  
// CS0540_b.cs using System; class C { void IDisposable.Dispose() {}   // CS0540 } class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```