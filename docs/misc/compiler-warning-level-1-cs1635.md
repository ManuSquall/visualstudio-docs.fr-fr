---
title: "Avertissement du compilateur (niveau&#160;1) CS1635 | Microsoft Docs"
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
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1635
Impossible de restaurer l’avertissement 'code d’avertissement', car il a été désactivé globalement  
  
 Cet avertissement s’affiche quand vous utilisez l’option de ligne de commande ou le paramètre de projet **\/nowarn** pour désactiver un avertissement pour l’ensemble de l’unité de compilation, mais utilisez `#pragma warning restore` pour tenter de restaurer cet avertissement. Pour résoudre cette erreur, supprimez l’option de ligne de commande ou le paramètre de projet \/nowarn, ou supprimez `#pragma warning restore` pour les avertissements que vous désactivez via la ligne de commande ou les paramètres de projet. Pour plus d’informations, consultez la rubrique [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning).  
  
 L’exemple suivant génère l’erreur CS1635 :  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```