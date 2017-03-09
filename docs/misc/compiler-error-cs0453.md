---
title: "Erreur du compilateur CS0453 | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0453
Le type 'nom\_type' doit être un type valeur non Nullable afin d’être utilisé comme paramètre 'nom\_paramètre' dans le type ou la méthode générique 'identificateur générique'  
  
 Cette erreur se produit quand vous utilisez un argument de type non\-valeur dans l’instanciation d’un type ou d’une méthode générique sur lesquels est appliquée une contrainte **value**. Elle peut également se produire quand vous utilisez un argument de type valeur Nullable. Regardez les deux dernières lignes de code de l’exemple suivant.  
  
## Exemple  
 Le code suivant génère cette erreur.  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```