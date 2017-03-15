---
title: "Plusieurs initialisations de &#39;&lt;nom_membre&gt;&#39; | Microsoft Docs"
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
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Plusieurs initialisations de &#39;&lt;nom_membre&gt;&#39;
Plusieurs initialisations de '\<nom\_membre\>'. Les champs et les propriétés ne peuvent être initialisés qu’une seule fois dans une expression d’initialiseur d’objet.  
  
 Vous ne pouvez affecter une valeur initiale à chaque champ et propriété dans une liste d’initialiseurs d’objet qu’une seule fois. La déclaration suivante n’est pas valide.  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  Vous pouvez utiliser un champ ou une propriété comme valeur initiale pour un autre membre, comme indiqué dans la déclaration suivante.  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **ID d’erreur :** BC30989  
  
### Pour corriger cette erreur  
  
-   Supprimez toutes les initialisations sauf une pour chaque champ ou propriété dans la liste d’initialiseurs d’objet.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Procédures de propriété et Champs](http://msdn.microsoft.com/fr-fr/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)