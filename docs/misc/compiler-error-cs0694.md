---
title: "Erreur du compilateur CS0694 | Microsoft Docs"
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
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0694
Le paramètre de type 'identifier' porte le même nom que le type conteneur ou la méthode de contenu  
  
 Vous devez utiliser un nom différent pour le paramètre de type, car le nom du paramètre de type ne peut pas être identique au nom du type ou de la méthode qui contient le paramètre de type.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0694.  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## Exemple  
 En plus du cas ci\-dessus, qui implique une classe générique, cette erreur peut se produire avec une méthode :  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```