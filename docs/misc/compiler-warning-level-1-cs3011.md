---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3011 | Microsoft Docs"
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
  - "CS3011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3011"
ms.assetid: e27ce521-0147-488b-b4a1-1b6fb5168661
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3011
'membre' : seuls les membres conformes CLS peuvent être abstract  
  
 Un membre de classe ne peut pas être à la fois [abstract](/dotnet/csharp/language-reference/keywords/abstract) et non conforme CLS. La spécification CLS spécifie que tous les membres de classe doivent être implémentés. Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS3011 :  
  
```  
// CS3011.cs using System; [assembly:CLSCompliant(true)] public abstract class I { [CLSCompliant(false)] public abstract int M();   // CS3011 // OK [CLSCompliant(false)] public void M2() { } } public class C : I { public override int M() { return 1; } public static void Main() { } }  
```