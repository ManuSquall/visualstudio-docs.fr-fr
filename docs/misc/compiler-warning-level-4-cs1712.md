---
title: "Avertissement du compilateur (niveau&#160;4) CS1712 | Microsoft Docs"
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
  - "CS1712"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1712"
ms.assetid: d9a8be26-c0ba-41fa-b082-1ce4ba7724b7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS1712
Le paramètre de type 'paramètre\_type' n’a pas de balise typeparam correspondante dans le commentaire XML de 'type' \(contrairement à d’autres paramètres de type\)  
  
 Il manque une balise **typeparam** dans la documentation d’un type générique. Pour plus d'informations, consultez [\<typeparam\>](../Topic/%3Ctypeparam%3E%20\(C%23%20Programming%20Guide\).md).  
  
## Exemple  
 Le code suivant génère l’avertissement CS1712. Pour résoudre cette erreur, ajoutez une balise **typeparam** pour le paramètre de type S.  
  
```  
// CS1712.cs // compile with: /doc:cs1712.xml using System; class Test { public static void Main() {} /// <param name="j"> This is the j parameter.</param> /// <typeparam name="T"> This is the T type parameter.</typeparam> public void bar<T,S>(int j) {}  // CS1712 }  
```