---
title: "Erreur du compilateur CS2019 | Microsoft Docs"
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
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2019
Type de cible non valide pour \/target : vous devez spécifier 'exe', 'winexe', 'library' ou 'module'  
  
 L’option [\/target](/dotnet/csharp/language-reference/compiler-options/target-compiler-option) du compilateur a été utilisée, mais un paramètre non valide a été passé. Pour résoudre cette erreur, recompilez le programme en utilisant la forme de l’option **\/target** appropriée à votre fichier de sortie.  
  
 L’exemple suivant génère l’erreur CS2017 :  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```