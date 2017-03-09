---
title: "Erreur du compilateur CS1730 | Microsoft Docs"
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
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1730
Les attributs de l’assembly et du module doivent précéder tous les autres éléments définis dans un fichier à l’exception des clauses using et des déclarations d’alias extern.  
  
 Un attribut appliqué au niveau de l’assembly ne peut pas apparaître après des définitions de type.  
  
### Pour corriger cette erreur  
  
1.  Déplacez l’attribut vers le haut du fichier, mais sous les directives `using` et déclarations d’alias `extern`.  
  
## Exemple  
 Le code suivant génère l’erreur CS1730 :  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## Voir aussi  
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)