---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3002 | Microsoft Docs"
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
  - "CS3002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3002"
ms.assetid: 34f19735-76d2-4d78-bd52-45989a86fca4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3002
Le type de retour de 'method' n’est pas conforme CLS  
  
 Une méthode [publique](/dotnet/csharp/language-reference/keywords/public), [protégée](/dotnet/csharp/language-reference/keywords/protected) ou `protected` `internal` doit retourner une valeur dont le type est conforme à la spécification CLS \(Common Language Specification\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3002 :  
  
```  
// CS3002.cs [assembly:System.CLSCompliant(true)] public class a { public ushort bad()   // CS3002, public method { ushort a; a = ushort.MaxValue; return a; } private ushort OK()   // OK, private method { ushort a; a = ushort.MaxValue; return a; } public static void Main() { } }  
```