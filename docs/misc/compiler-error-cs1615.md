---
title: "Erreur du compilateur CS1615 | Microsoft Docs"
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
  - "CS1615"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1615"
ms.assetid: 518bb07f-0e3a-4761-9931-66845eb5df1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1615
L’argument 'nombre' doit être passé avec le mot clé 'mot\_clé'  
  
 L’un des mots clés `ref` ou **out** a été utilisé alors que la fonction ne prenait pas de paramètre `ref` ou **out** pour cet argument. Pour résoudre cette erreur, supprimez le mot clé incorrect et utilisez le mot clé approprié qui correspond à la déclaration de la fonction, le cas échéant.  
  
 L’exemple suivant génère l’erreur CS1615 :  
  
```  
// CS1615.cs class C { public void f(int i) {} public static void Main() { int i = 1; f(ref i);  // CS1615 } }  
```