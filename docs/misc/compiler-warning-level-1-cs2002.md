---
title: "Avertissement du compilateur (niveau&#160;1) CS2002 | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS2002
Le fichier source 'fichier' a été spécifié plusieurs fois  
  
 Un nom de fichier source a été passé au compilateur plusieurs fois. Vous ne pouvez spécifier un fichier qu’une seule fois au compilateur pour générer un fichier de sortie.  
  
 Vous ne pouvez pas supprimer cet avertissement avec l’option [\/nowarn](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).  
  
 L’exemple suivant génère l’erreur CS2002 :  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 Pour générer cette erreur, compilez l’exemple avec la ligne de commande :  
  
```  
csc CS2002.cs CS2002.cs  
```