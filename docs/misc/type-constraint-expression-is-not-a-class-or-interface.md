---
title: "La contrainte de type &#39;&lt;expression&gt;&#39; n’est pas une classe ou une interface | Microsoft Docs"
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
  - "bc32048"
  - "vbc32048"
helpviewer_keywords: 
  - "BC32048"
ms.assetid: 68811886-44ac-43e1-9315-b39857310033
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte de type &#39;&lt;expression&gt;&#39; n’est pas une classe ou une interface
Une liste de contraintes contient une expression qui ne représente pas une contrainte valide sur un paramètre de type.  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Vous pouvez spécifier les exigences suivantes dans toute combinaison :  
  
-   L’argument de type doit implémenter une ou plusieurs interfaces.  
  
-   L’argument de type doit hériter d’une classe au plus.  
  
-   L’argument de type doit exposer un constructeur sans paramètre accessible par le code de création.  
  
-   L’argument de type doit être un type référence ou un type valeur.  
  
 **ID d’erreur :** BC32048  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’expression et ses éléments sont correctement orthographiés.  
  
-   Si l’expression ne répond pas à la précédente liste d’exigences, supprimez\-la de la liste des contraintes.  
  
-   Si l’expression fait référence à une interface ou une classe, vérifiez que le compilateur a accès à cette interface ou classe. Vous devrez peut\-être qualifier son nom et ajouter une référence à votre projet. Pour plus d’informations, consultez la section « Références aux projets » dans [NOTINBUILD : Résolution d’une référence lorsque plusieurs variables ont le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [NOTINBUILD Comment : qualifier un nom d’élément déclaré](http://msdn.microsoft.com/fr-fr/6bd112f5-df6f-42b8-9427-a9225bfcbaab)   
 [How to: Add and Remove Project References](http://msdn.microsoft.com/fr-fr/f51b784d-0bc8-4c19-a898-e560d5ed696b)