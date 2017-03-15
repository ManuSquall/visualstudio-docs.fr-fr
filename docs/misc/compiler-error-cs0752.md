---
title: "Erreur du compilateur CS0752 | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0752
Une méthode partielle ne peut pas avoir de paramètres out  
  
 Une méthode partielle ne peut pas avoir de paramètres [out](/dotnet/csharp/language-reference/keywords/out). Les paramètres de sortie ne sont pas autorisés, car si la méthode partielle est supprimée par le compilateur, il n’y a aucune garantie que le paramètre de sortie soit assigné.  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur out du paramètre et utilisez la valeur de retour de la méthode à la place, ou bien supprimez le modificateur partiel de la déclaration de méthode.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0752 :  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)