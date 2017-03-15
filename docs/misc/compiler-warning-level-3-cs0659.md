---
title: "Avertissement du compilateur&#160;(niveau&#160;3)&#160;CS0659 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0659"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0659"
ms.assetid: 63435ee6-c92f-4124-95d4-d8f4e5f0af80
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;3)&#160;CS0659
’classe’ se substitue à Object.Equals\(object o\) mais pas à Object.GetHashCode\(\)  
  
 Le compilateur a détecté une substitution de la fonction **Equals**, mais aucune substitution de **GetHashCode**. Une substitution de **Equals** implique que vous souhaitez également substituer **GetHashCode**.  
  
 Pour plus d'informations, consultez  
  
-   <xref:System.Collections.Hashtable>.  
  
-   [Opérateurs d'égalité](../Topic/Equality%20Operators.md)  
  
-   [NIB : Implémentation de la méthode Equals](http://msdn.microsoft.com/fr-fr/30f28aaf-8b9e-46cd-a746-58a12473af2c)  
  
-   <xref:System.Object.GetHashCode%2A>  
  
 L’exemple suivant génère l’avertissement CS0659 :  
  
```  
// CS0659.cs // compile with: /W:3 /target:library class Test { public override bool Equals(object o) { return true; }   // CS0659 } // OK class Test2 { public override bool Equals(object o) { return true; } public override int GetHashCode() { return 0; } }  
```