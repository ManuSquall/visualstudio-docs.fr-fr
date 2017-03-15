---
title: "Avertissement du compilateur&#160;(niveau&#160;2) CS0114 | Microsoft Docs"
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
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;2) CS0114
'function1' masque le membre hérité 'function2'. Pour que la méthode actuelle se substitue à cette implémentation, ajoutez le mot clé override. Sinon, ajoutez le nouveau mot clé.  
  
 Une déclaration figurant dans une classe est en conflit avec une déclaration figurant dans une classe de base. Le membre de la classe de base est donc masqué.  
  
 Pour plus d’informations, consultez [base](/dotnet/csharp/language-reference/keywords/base).  
  
 L’exemple suivant génère l’avertissement CS0114 :  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```