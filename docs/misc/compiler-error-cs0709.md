---
title: "Erreur du compilateur CS0709 | Microsoft Docs"
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
  - "CS0709"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0709"
ms.assetid: 91040f55-a060-4cc3-b830-f6b771af28d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0709
'derived class' : dérivation impossible à partir de la classe static 'base class'  
  
 Vous ne pouvez ni instancier une classe statique, ni dériver de celle\-ci. Autrement dit, une classe statique ne peut pas agir en tant que classe de base pour toute autre classe.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0709.  
  
```  
// CS0709.cs // compile with: /target:library public static class Base {} public class Derived : Base {}   // CS0709  
```