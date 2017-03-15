---
title: "Erreur du compilateur CS0662 | Microsoft Docs"
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
  - "CS0662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0662"
ms.assetid: 836fa15e-3bf3-4af5-8acf-072d7d731dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0662
'method' ne peut pas spécifier uniquement un attribut Out sur un paramètre ref. Utilisez les deux attributs In et Out ou aucun des deux.  
  
 Une méthode d’interface a un paramètre qui utilise [ref](/dotnet/csharp/language-reference/keywords/ref) avec uniquement l’attribut [Out](frlrfSystemRuntimeInteropServicesOutAttributeClassTopic). Un paramètre `ref` qui utilise l’attribut **Out** doit également utiliser l’attribut [In](frlrfSystemRuntimeInteropServicesInAttributeClassTopic).  
  
 L’exemple suivant génère l’erreur CS0662 :  
  
```  
// CS0662.cs using System.Runtime.InteropServices; interface I { void method([Out] ref int i);   // CS0662 // try one of the following lines instead // void method(ref int i); // void method([Out, In]ref int i); } class test { public static void Main() { } }  
```