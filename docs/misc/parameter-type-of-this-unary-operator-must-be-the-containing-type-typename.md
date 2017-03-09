---
title: "Le param&#232;tre de type de cet op&#233;rateur unaire doit &#234;tre du type conteneur &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type de cet op&#233;rateur unaire doit &#234;tre du type conteneur &#39;&lt;nom_type&gt;&#39;
Une définition d’opérateur unaire spécifie un paramètre avec un type autre que celui de la classe ou structure dans laquelle l’opérateur est défini.  
  
 Quand vous définissez un opérateur dans une classe ou structure, au moins un des paramètres doit être du type de cette classe ou structure. Dans le cas d’un opérateur unaire, l’opérande unique doit être du type de cette classe ou structure.  
  
 **ID d’erreur :** BC33020  
  
### Pour corriger cette erreur  
  
-   Remplacez le type du paramètre par le type de la classe ou structure dans laquelle l’opérateur est défini.  
  
-   Si vous voulez prendre un seul type de données en tant que paramètre et retourner un autre type de données en tant que résultat de l’opération, définissez plutôt un opérateur de conversion.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)