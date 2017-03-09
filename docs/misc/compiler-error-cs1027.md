---
title: "Erreur du compilateur CS1027 | Microsoft Docs"
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
  - "CS1027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1027"
ms.assetid: a6657f0f-5664-47a5-95cf-803f5a0e0c90
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1027
directive \#endif attendue  
  
 Aucune `#endif` [directive de préprocesseur](/dotnet/csharp/language-reference/preprocessor-directives/index) correspondante n’a été trouvée pour une directive `#if` spécifiée. Ou : le compilateur a trouvé une directive `#endregion` alors qu’aucune directive `#region` correspondante ne se trouve dans un bloc `#if`.  
  
 L’exemple suivant génère l’erreur CS1027 :  
  
```  
// CS1027.cs #if true   // CS1027, uncomment next line to resolve // #endif namespace x { public class clx { public static void Main() { } } }  
```