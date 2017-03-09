---
title: "L’argument de type &#39;&lt;nom_argument_type&gt;&#39; est d&#233;clar&#233; &#39;MustInherit&#39; et ne satisfait pas la contrainte &#39;New&#39; pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32082"
  - "BC32082"
helpviewer_keywords: 
  - "BC32082"
ms.assetid: 597e5944-a61b-4858-ada5-efb80b27f26b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument de type &#39;&lt;nom_argument_type&gt;&#39; est d&#233;clar&#233; &#39;MustInherit&#39; et ne satisfait pas la contrainte &#39;New&#39; pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39;
Un type générique est appelé avec une classe `MustInherit` comme argument de type, alors que le paramètre de type correspondant est déclaré avec la contrainte `New`.  
  
 La contrainte `New` requiert que le type passé dans l’argument de type correspondant prenne en charge la création d’objets. Toutefois, une classe *abstraite*, c’est\-à\-dire une classe déclarée comme `MustInherit`, n’expose pas de constructeurs car vous ne pouvez pas créer d’objets à partir de celle\-ci.  
  
 **ID d’erreur :** BC32082  
  
### Pour corriger cette erreur  
  
1.  Si la classe utilisée dans l’argument de type ne doit pas être abstraite, supprimez le mot clé `MustInherit` de sa déclaration.  
  
2.  Si la classe utilisée dans l’argument de type doit être abstraite, mais ne doit pas être utilisée pour construire le type générique, passez une autre classe dans l’argument de type.  
  
3.  Si le paramètre de type correspondant ne doit pas créer d’objets du type qui lui est passé, supprimez la contrainte `New` de sa déclaration.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)