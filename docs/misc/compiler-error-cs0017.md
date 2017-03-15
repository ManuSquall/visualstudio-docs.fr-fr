---
title: "Erreur du compilateur CS0017 | Microsoft Docs"
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
  - "CS0017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0017"
ms.assetid: 5e2a3eb3-6f6e-485d-8293-ceabea4d6905
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0017
Plusieurs points d’entrée sont définis dans le programme 'nom\_fichier\_sortie'. Compilez avec l’option \/main pour spécifier le type qui contient le point d’entrée.  
  
 Un programme ne peut avoir qu’une seule méthode [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 Pour résoudre cette erreur, vous pouvez supprimer toutes les méthodes Main de votre code sauf une, ou vous pouvez utiliser l’option du compilateur [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) pour spécifier la méthode Main à utiliser.  
  
 L’exemple suivant génère l’erreur CS0017 :  
  
```  
// CS0017.cs // compile with: /target:exe public class clx { static public void Main() { } } public class cly { public static void Main()   // CS0017, delete one Main or use /main { } }  
```