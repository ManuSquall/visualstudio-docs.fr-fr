---
title: "Erreur du compilateur CS0611 | Microsoft Docs"
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
  - "CS0611"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0611"
ms.assetid: bbd857a0-9454-4438-a21c-fef5bc7eee06
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0611
Les éléments de tableau ne peuvent pas être de type 'type'  
  
 Certains types ne peuvent pas être appliqués à un tableau. Ces types incluent **System.TypedReference** et **System.ArgIterator**.  
  
 L’exemple suivant génère l’erreur CS0611 à la suite de l’utilisation de **System.TypedReference** en tant qu’élément de tableau :  
  
```  
// CS0611.cs public class a { public static void Main() { System.TypedReference[] ao = new System.TypedReference [10];   // CS0611 // try the following line instead // int[] ao = new int[10]; } }  
```