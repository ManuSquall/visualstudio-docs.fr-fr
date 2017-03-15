---
title: "Les attributs ne peuvent pas &#234;tre des g&#233;n&#233;riques ou des types imbriqu&#233;s dans des g&#233;n&#233;riques | Microsoft Docs"
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
  - "bc32067"
  - "vbc32067"
helpviewer_keywords: 
  - "BC32067"
ms.assetid: 93ae2848-0a72-4ae5-82a3-32e0a49bb7cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les attributs ne peuvent pas &#234;tre des g&#233;n&#233;riques ou des types imbriqu&#233;s dans des g&#233;n&#233;riques
Un attribut est déclaré en tant que type générique ou dans un type générique.  
  
 Visual Basic et le .NET Framework ne prennent pas actuellement en charge les combinaisons d’attributs et de types génériques. Cela signifie que les limitations suivantes s’appliquent :  
  
-   Un attribut ne peut ni être un type générique, ni être déclaré dans un type générique.  
  
-   Un attribut ne peut pas hériter d’une classe générique, et une classe générique ne peut pas non plus hériter d’un attribut.  
  
-   Quand vous appliquez un attribut, vous ne pouvez pas fournir un argument qui correspond à l’un des éléments suivants :  
  
    -   Type générique  
  
    -   Type construit à partir d’un type générique  
  
    -   Paramètre de type d’un type conteneur  
  
    -   Type construit à partir d’un paramètre de type d’un type conteneur  
  
 **ID d’erreur :** BC32067  
  
### Pour corriger cette erreur  
  
-   Si la déclaration d’attribut inclut le mot clé `Of` et une liste de paramètres de type, supprimez\-les.  
  
-   Si la déclaration d’attribut apparaît à l’intérieur d’un type générique, déplacez\-la à un endroit à l’extérieur d’un type générique.  
  
## Voir aussi  
 <xref:System.Attribute>   
 [NOT IN BUILD : Vue d’ensemble des attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)