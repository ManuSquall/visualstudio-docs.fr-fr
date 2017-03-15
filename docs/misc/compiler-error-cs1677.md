---
title: "Erreur du compilateur CS1677 | Microsoft Docs"
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
  - "CS1677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1677"
ms.assetid: 8c974669-15c6-4010-8b02-21021bed5af9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1677
Le paramètre 'nombre' ne doit pas être déclaré avec le mot clé 'mot clé'  
  
 Cette erreur se produit lorsque le modificateur de type de paramètre dans une méthode anonyme ne correspond pas à celui utilisé dans la déclaration du délégué, vers lequel vous effectuez un cast de la méthode.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1677 :  
  
```  
// CS1677.cs delegate void D(int i); class Errors { static void Main() { D d = delegate(out int i) { };   // CS1677 // To resolve, use the following line instead: // D d = delegate(int i) { }; D d = delegate(ref int j){}; // CS1677 // To resolve, use the following line instead: // D d = delegate(int j){}; } }  
```