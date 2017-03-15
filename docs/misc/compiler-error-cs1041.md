---
title: "Erreur du compilateur CS1041 | Microsoft Docs"
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
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1041
Identificateur attendu ; 'keyword' est un mot clé  
  
 Un mot réservé pour le langage C\# a été trouvé alors qu’un identificateur était attendu. Remplacez le [mot\-clé](/dotnet/csharp/language-reference/keywords/index) par un identificateur spécifié par l’utilisateur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1041 :  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## Exemple  
 Quand vous effectuez une importation à partir d’un autre langage de programmation qui n’a pas le même jeu de mots réservés, vous pouvez modifier l’identificateur réservé à l’aide du préfixe @, comme illustré dans l’exemple suivant.  
  
 Les identificateurs avec un préfixe `@` sont appelés identificateurs textuels.  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```