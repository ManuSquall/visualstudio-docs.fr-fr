---
title: "Erreur du compilateur CS1910 | Microsoft Docs"
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
  - "CS1910"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1910"
ms.assetid: 0fef9727-e56f-451c-9255-ca4e5a26d7c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1910
L’argument de type 'type' n’est pas applicable pour l’attribut DefaultValue  
  
 Pour les paramètres de type objet, l’argument de <xref:System.Runtime.InteropServices.DefaultParameterValueAttribute> doit être `null`, un type intégral, une virgule flottante, `bool`, `string`, `enum` ou `char`. L’argument ne peut pas être de type <xref:System.Type> ou d’un type tableau.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1910.  
  
```  
// CS1910.cs // compile with: /target:library using System.Runtime.InteropServices; public interface MyI { void Test([DefaultParameterValue(typeof(object))] object o);   // CS1910 }  
```