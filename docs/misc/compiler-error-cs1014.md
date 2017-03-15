---
title: "Erreur du compilateur CS1014 | Microsoft Docs"
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
  - "CS1014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1014"
ms.assetid: 60c1e9af-5a0d-4ae0-a2e6-881b0d1535e9
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1014
Accesseur get ou set attendu  
  
 Une déclaration de méthode a été détectée dans une déclaration de propriété. Vous pouvez déclarer uniquement des méthodes `get` et `set` dans une propriété.  
  
 Pour plus d’informations sur les propriétés, consultez [Utilisation de propriétés](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1014.  
  
```  
// CS1014.cs // compile with: /target:library class Sample { public int TestProperty { get { return 0; } int z;   // CS1014  not get or set } }  
```