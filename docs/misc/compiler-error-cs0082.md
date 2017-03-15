---
title: "Erreur du compilateur CS0082 | Microsoft Docs"
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
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0082
Le type 'type' réserve déjà un membre appelé 'name' avec les mêmes types de paramètres  
  
 Les propriétés au moment de la compilation sont converties en méthodes avec `get_` et\/ou `set_` devant l’identificateur. Si vous définissez votre propre méthode et qu’elle entre en conflit avec le nom de la méthode, une erreur est générée.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0082 :  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Propriétés](/dotnet/csharp/programming-guide/classes-and-structs/properties)