---
title: "Erreur du compilateur CS0681 | Microsoft Docs"
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
  - "CS0681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0681"
ms.assetid: aa51ad94-df0a-481d-aaea-5b4291ebc41c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0681
Le modificateur 'abstract' n’est pas valide dans les champs. Essayez plutôt d’utiliser une propriété.  
  
 Vous ne pouvez pas rendre un champ abstrait. En revanche, vous pouvez faire en sorte qu’une propriété abstraite puisse accéder au champ.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0681 :  
  
```  
// CS0681.cs // compile with: /target:library abstract class C { abstract int num;  // CS0681 }  
  
```  
  
## Exemple  
 Essayez plutôt le code suivant :  
  
```  
// CS0681b.cs // compile with: /target:library abstract class C { public abstract int num { get; set; } }  
```