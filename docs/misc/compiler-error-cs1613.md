---
title: "Erreur du compilateur CS1613 | Microsoft Docs"
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
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1613
La classe wrapper de coclasse managée 'class' pour l’interface 'interface' est introuvable \(vous manque\-t\-il une référence d’assembly ?\)  
  
 L’utilisateur a tenté d’instancier un objet COM à partir d’une interface. L’interface présente les attributs **ComImport** et `CoClass`, mais le compilateur ne trouve pas le type donné par l’attribut `CoClass`.  
  
 Pour résoudre cette erreur, essayez l’une des opérations suivantes :  
  
-   Ajoutez une référence à l’assembly qui comprend la coclasse \(le plus souvent, l’interface et la coclasse doivent être dans le même assembly\). Pour plus d’informations, consultez [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) ou [Ajouter une référence, boîte de dialogue](http://msdn.microsoft.com/fr-fr/2feb0fe2-0805-4cc9-8cba-b0315849dfb7).  
  
-   Corrigez l’attribut `CoClass` dans l’interface.  
  
 L’exemple suivant montre une utilisation correcte de **CoClassAttribute** :  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```