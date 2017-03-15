---
title: "Erreur du compilateur CS0316 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0316
Le nom du paramètre 'nom' est en conflit avec un nom de paramètre généré automatiquement.  
  
 Vous ne pouvez pas utiliser un mot réservé comme nom de paramètre. Dans l’exemple suivant, `value` est un mot réservé dans le contexte d’un accesseur d’indexeur ou de propriété par défaut.  
  
### Pour corriger cette erreur  
  
1.  Modifiez le nom du paramètre.  
  
## Exemple  
 Le code suivant génère l’erreur CS0316 :  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## Voir aussi  
 [Indexeurs](/dotnet/csharp/programming-guide/indexers/index)   
 [Mots clés C\#](/dotnet/csharp/language-reference/keywords/index)