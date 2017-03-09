---
title: "Erreur du compilateur CS0455 | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0455
Le paramètre de type 'nom\_paramètre\_type' hérite des contraintes en conflit 'nom\_contrainte\_1' et 'nom\_contrainte\_2'  
  
 Cette erreur se produit principalement dans deux cas : quand vous configurez des contraintes pour que le paramètre de type dérive de deux classes non liées et quand vous configurez des contraintes pour que le paramètre de type dérive d’un type de classe ou d’une contrainte de type référence et d’un type `struct` ou d’une contrainte de type valeur. Pour corriger cette erreur, résolvez le conflit de votre hiérarchie d’héritage.  
  
## Exemple  
 Le code suivant génère l’erreur CS0455.  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```