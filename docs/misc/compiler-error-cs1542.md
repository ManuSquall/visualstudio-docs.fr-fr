---
title: "Erreur du compilateur CS1542 | Microsoft Docs"
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
  - "CS1542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1542"
ms.assetid: d7f60aa2-6645-472c-ac12-fa57a09fbd87
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1542
'dll' ne peut pas être ajouté à cet assembly, car il s’agit déjà d’un assembly ; utilisez plutôt l’option '\/R'  
  
 Le fichier référencé avec l’option du compilateur [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) n’a pas été généré avec [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) ; utilisez [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) pour faire référence au fichier dans cette compilation.