---
title: "Erreur du compilateur&#160;CS1724 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1724"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1724"
ms.assetid: f25ec28e-c20b-457d-afc2-284494e69dad
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1724
La valeur spécifiée pour l'argument de 'System.Runtime.InteropServices.DefaultCharSetAttribute' n'est pas valide  
  
 Cette erreur est générée par un argument non valide pour la classe <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1724.  
  
```  
// CS1724.cs using System.Runtime.InteropServices; // To resolve, replace 42 with a valid CharSet value. [module:DefaultCharSetAttribute((CharSet)42)]   // CS1724 class C { [DllImport("F.Dll")] extern static void FW1Named(); static void Main() {} }  
```