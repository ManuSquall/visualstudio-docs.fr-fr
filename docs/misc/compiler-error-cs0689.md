---
title: "Erreur du compilateur CS0689 | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0689
Dérivation impossible à partir de 'identifier', car il s’agit d’un paramètre de type  
  
 Les classes de base ou les interfaces de classes génériques ne peuvent pas être spécifiées par un paramètre de type. Dérivez d’une classe ou interface spécifique, ou encore d’une classe générique spécifique à la place, ou incluez le type inconnu en tant que membre.  
  
 L’exemple suivant génère l’erreur CS0689 :  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```