---
title: "Les arguments de type sont inattendus, car les attributs ne peuvent pas &#234;tre des g&#233;n&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32066"
  - "vbc32066"
helpviewer_keywords: 
  - "BC32066"
ms.assetid: cd43a92c-33fb-4def-bbf7-527d21bff93c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de type sont inattendus, car les attributs ne peuvent pas &#234;tre des g&#233;n&#233;riques
Un attribut est appliqué à l’aide d’une liste d’arguments de type.  
  
 Visual Basic et .NET Framework ne prennent actuellement pas en charge toute combinaison d’attributs et de types génériques. Cela signifie que les limitations suivantes s’appliquent :  
  
-   Un attribut ne peut pas être un type générique ou être déclaré dans un type générique.  
  
-   Un attribut ne peut pas hériter d’une classe générique et une classe générique ne peut pas non plus hériter d’un attribut.  
  
-   Quand vous appliquez un attribut, vous ne pouvez pas fournir un argument qui correspond à l’un des éléments suivants :  
  
    -   Un type générique.  
  
    -   Un type construit à partir d’un type générique.  
  
    -   Un paramètre de type d’un type conteneur.  
  
    -   Un type construit à partir d’un paramètre de type d’un type conteneur.  
  
 **ID d’erreur :** BC32066  
  
### Pour corriger cette erreur  
  
-   Si les arguments de type doivent être normaux, supprimez le mot clé `Of`. Cette suppression transforme la liste d’arguments de type en liste d’arguments normaux.  
  
-   Si les arguments de type doivent être fournis à des paramètres de type, alors supprimez le mot clé `Of` et tous les arguments de type. Un attribut ne peut pas accepter des arguments de type.  
  
## Voir aussi  
 <xref:System.Attribute>   
 [NOT IN BUILD : Vue d’ensemble des attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)