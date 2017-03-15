---
title: "Avertissement du compilateur (niveau&#160;1) CS0824 | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0824
Le constructeur 'nom' est marqué comme external.  
  
 Un constructeur peut être marqué comme extern. Cependant, le compilateur ne peut pas vérifier que le constructeur existe réellement. Par conséquent, l’avertissement est généré.  
  
### Pour supprimer cet avertissement  
  
1.  Utilisez une directive d’avertissement pragma pour l’ignorer.  
  
2.  Déplacez le constructeur à l’intérieur du type.  
  
## Exemple  
 Le code suivant génère l’avertissement CS0824 :  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [extern](/dotnet/csharp/language-reference/keywords/extern)   
 [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)