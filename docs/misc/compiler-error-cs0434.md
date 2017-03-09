---
title: "Erreur du compilateur CS0434 | Microsoft Docs"
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
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0434
L’espace de noms NamespaceName1 dans NamespaceName2est en conflit avec le type TypeName1 dans NamespaceName3  
  
 Cette erreur se produit quand un type et un espace de noms imbriqué importés ont le même nom qualifié complet. Quand ce nom est référencé, le compilateur ne peut pas faire la distinction entre les deux. Si vous pouvez modifier le code source importé, vous pouvez résoudre l’erreur en modifiant le nom du type ou de l’espace de noms de manière à ce qu’ils soient uniques au sein de l’assembly.  
  
 Le code suivant génère l’erreur CS0434.  
  
## Exemple  
 Ce code crée la première copie du type avec le nom qualifié complet identique.  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## Exemple  
 Ce code crée la deuxième copie du type avec le nom qualifié complet identique.  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## Exemple  
 Ce code fait référence au type avec le nom qualifié complet identique.  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```