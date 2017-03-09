---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3013 | Microsoft Docs"
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
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3013
Les modules ajoutés doivent être marqués avec l'attribut CLSCompliant pour correspondre à l'assembly  
  
 Un module compilé avec l’option de compilateur [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) a été ajoutée à une compilation avec [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). Toutefois, la conformité du module à la spécification CLS \(Common Language Specification\) ne correspond pas à l’état CLS de la compilation en cours.  
  
 La conformité CLS est indiquée par l’attribut module. Par exemple, `[module:CLSCompliant(true)]` indique que le module est conforme CLS, et `[module:CLSCompliant(false)]` indique qu’il ne l’est pas. La valeur par défaut est `[module:CLSCompliant(false)]`. Pour plus d’informations sur la spécification CLS, consultez [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).