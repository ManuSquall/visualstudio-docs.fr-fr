---
title: "Erreur du compilateur CS1609 | Microsoft Docs"
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
  - "CS1609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1609"
ms.assetid: 89e112f8-6337-4803-8741-2e38497deb8c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1609
Les modificateurs ne peuvent pas être placés sur des déclarations d'accesseurs d'événement  
  
 Les modificateurs peuvent être placés uniquement sur des déclarations d’événements, et non sur les déclarations d’accesseurs d’événements. Pour plus d'informations, consultez [Utilisation de propriétés](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1609.  
  
```  
// CS1609.cs // compile with: /target:library delegate int Del(); class A { public event Del MyEvent { private add {}   // CS1609 // try the following line instead // add {} remove {} } }  
```