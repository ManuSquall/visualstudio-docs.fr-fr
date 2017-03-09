---
title: "Erreur du compilateur CS0573 | Microsoft Docs"
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
  - "CS0573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0573"
ms.assetid: 10ef9625-44f1-4936-ada3-56938357aa01
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0573
'déclaration\_champ' : impossible d’avoir des initialiseurs de champ d’instance dans des structures  
  
 Vous ne pouvez pas initialiser un champ d’instance d’un [struct](/dotnet/csharp/language-reference/keywords/struct). Les champs de types valeur seront initialisés à leurs valeurs par défaut et les champs de type référence seront initialisés à `null`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0573 :  
  
```  
// CS0573.cs namespace x { public class clx { public static void Main() { } } public struct cly { clx a = new clx();   // CS0573 // clx a;            // OK int i = 7;           // CS0573 // int i;            // OK } }  
```