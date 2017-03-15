---
title: "Avertissement du compilateur (niveau&#160;1) CS3027 | Microsoft Docs"
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
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS3027
'type\_1' n’est pas conforme CLS, car l’interface de base 'type\_2' n’est pas conforme CLS  
  
 Un type non conforme CLS ne peut pas être un type de base pour un type conforme CLS.  
  
## Exemple  
 L’exemple suivant contient une interface avec une méthode qui utilise un type non conforme CLS dans sa signature, ce qui rend le type non conforme CLS.  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3027.  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```