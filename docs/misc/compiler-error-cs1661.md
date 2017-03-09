---
title: "Erreur du compilateur CS1661 | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1661
Impossible de convertir le bloc de méthode anonyme en type délégué 'type délégué', car les types de paramètres du bloc spécifié ne correspondent pas aux types de paramètres délégués  
  
 Cette erreur se produit si, dans une définition de méthode anonyme, les types de paramètres de la méthode anonyme ne correspondent pas aux types de paramètres délégués. Vérifiez le nombre de paramètres, les types de paramètres et les paramètres ref ou out, puis vérifiez les correspondances exactes.  
  
 L’exemple suivant génère l’erreur CS1661 :  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```