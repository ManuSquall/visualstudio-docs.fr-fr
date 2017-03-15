---
title: "&#39;=&#39; attendu (initialiseur d’objet) | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;=&#39; attendu (initialiseur d’objet)
Pour établir la valeur initiale d’un champ ou d’une propriété dans une déclaration d’initialiseur d’objet, vous devez utiliser un signe égal. Par exemple, la déclaration suivante affecte la valeur initiale « Microsoft » à la propriété `Name` de `client`.  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **ID d’erreur :** BC30984  
  
### Pour corriger cette erreur  
  
-   Ajoutez un signe égal à l’emplacement indiqué dans l’exemple précédent.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Propriétés et procédures de propriété](http://msdn.microsoft.com/fr-fr/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NOT IN BUILD : Procédures de propriété et champs](http://msdn.microsoft.com/fr-fr/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)