---
title: "Avertissement du compilateur (niveau&#160;1) CS0626 | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0626
La méthode, l’opérateur ou l’accesseur 'method' est marqué comme external et n’a pas d’attribut. Ajoutez un attribut DllImport pour spécifier l’implémentation externe  
  
 Une méthode marquée `extern` doit également être marquée avec un attribut, par exemple [DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic).  
  
 L’attribut spécifie où la méthode est implémentée. Au moment de l’exécution, ces informations sont nécessaires au programme.  
  
 L’exemple suivant génère l’avertissement CS0626 :  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```