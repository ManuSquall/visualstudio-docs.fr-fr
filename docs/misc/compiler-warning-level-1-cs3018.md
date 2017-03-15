---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3018 | Microsoft Docs"
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
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3018
Impossible de marquer 'type' comme conforme CLS car il est membre du type non conforme CLS 'type'  
  
 Cet avertissement se produit si une classe imbriquée avec l’attribut CLSCompliant défini sur `true` est déclarée comme membre d’une classe déclarée avec l’attribut CLSCompliant défini sur `false`. Cela n’est pas autorisé car une classe imbriquée ne peut pas être conforme CLS si elle est membre d’une classe externe qui n’est pas conforme CLS. Pour remédier à cet avertissement, supprimez l’attribut CLSCompliant de la classe imbriquée ou remplacez `true` par `false`. Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3018.  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```