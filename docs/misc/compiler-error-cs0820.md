---
title: "Erreur du compilateur CS0820 | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0820
Impossible d’affecter l’initialiseur de tableau à une variable locale implicitement typée  
  
 Un tableau implicitement typé est un tableau dont le type élément est déduit par le compilateur. Il doit être initialisé à l’aide du modificateur `new`\[\] comme indiqué dans l’exemple de code.  
  
### Pour corriger cette erreur  
  
-   Utilisez le modificateur `new`\[\] avec l’initialiseur de tableau.  
  
-   N’utilisez pas une variable locale implicitement typée.  
  
## Exemple  
 Le code suivant génère l’erreur CS0820 et montre comment initialiser correctement un tableau implicitement typé :  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)