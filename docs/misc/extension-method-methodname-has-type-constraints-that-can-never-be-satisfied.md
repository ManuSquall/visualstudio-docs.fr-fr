---
title: "La m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; a des contraintes de type qui ne peuvent pas &#234;tre satisfaites | Microsoft Docs"
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
  - "bc36561"
  - "vbc36561"
helpviewer_keywords: 
  - "BC36561"
ms.assetid: ff42d6e9-611b-407d-a269-f268b36ed277
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; a des contraintes de type qui ne peuvent pas &#234;tre satisfaites
La façon dont les paramètres de type de cette méthode interagissent entre eux les empêche d’être satisfaits. L’exemple suivant de méthode d’extension illustre ceci.  
  
```  
'' Not valid. '<Extension()> _ 'Sub extensionExample(Of T As U, U)(ByVal para1 As T, ByVal para2 As U) 'End Sub  
```  
  
 La méthode étant une méthode d’extension, le compilateur doit pouvoir déterminer le ou les types de données étendus par la méthode en s’appuyant uniquement sur le premier paramètre dans la déclaration de la méthode, `para1`, et l’argument envoyé pour ce paramètre. Quand le premier paramètre fait référence aux paramètres de type générique, `para1 as T`, les contraintes sur les paramètres génériques restreignent l’ensemble de types auquel la méthode s’applique.  
  
 L’applicabilité d’une méthode d’extension est déterminée à partir de l’argument fourni pour le premier paramètre, à savoir `arg1` dans le code suivant.  
  
 `'' Not valid.`  
  
 `'arg1.extensionExample(arg2)`  
  
 Vous devez pouvoir vérifier les contraintes sur tous les paramètres de type générique référencés par le premier paramètre \(`para1`\) en examinant le premier argument \( `arg1`\). Dans `extensionExample`, l’ensemble de types qui est étendu ne peut pas être déterminé uniquement à partir du premier paramètre. Le paramètre de type `T` est limité par le paramètre de type `U`, qui n’est pas référencé par `para1` et qui ne peut pas être déduit à partir d’`arg1`. Par conséquent, l’applicabilité de la méthode à n’importe quel type ne peut pas être vérifiée, et la méthode ne peut jamais être appelée.  
  
 **ID d’erreur :** BC36561  
  
### Pour corriger cette erreur  
  
-   Modifiez la déclaration de type pour supprimer l’interdépendance entre les types.  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)