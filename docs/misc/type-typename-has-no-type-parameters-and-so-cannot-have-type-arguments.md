---
title: "Le type &#39;&lt;nom_type&gt;&#39; n’a pas de param&#232;tres de type et donc ne peut pas avoir d’arguments de type | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32045"
  - "vbc32045"
helpviewer_keywords: 
  - "BC32045"
ms.assetid: b86e784c-6718-4585-bd39-2f0982068828
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; n’a pas de param&#232;tres de type et donc ne peut pas avoir d’arguments de type
Une instruction de déclaration ou d’assignation inclut une clause [Of](/dotnet/visual-basic/language-reference/statements/of-clause) lors de l’appel d’un type non générique.  
  
 Par définition, un *type générique* est une classe, une structure, une interface, une procédure ou un délégué qui fonctionne sur des types de données que vous pouvez spécifier par le biais d’un ou plusieurs *paramètres de type*. Quand le code d’utilisation crée un type à partir de ce type générique, il fournit un *argument de type* à chaque paramètre de type. Dans le cadre de la création du type, chaque argument de type remplace toutes les occurrences de son paramètre de type correspondant dans le code généré.  
  
 Les paramètres de type sont définis avec une clause `Of` entre parenthèses, tandis que les arguments de type sont fournis à l’aide d’une clause `Of` entre parenthèses. La clause `Of` n’est utilisée qu’avec des types génériques.  
  
 Les types non génériques n’acceptent pas de paramètres de type, et vous ne pouvez pas spécifier des arguments de type quand vous appelez un tel type.  
  
 **ID d’erreur :** BC32045  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du type que vous utilisez dans l’instruction de déclaration ou d’assignation.  
  
2.  Si vous appelez un type non générique, supprimez la clause `Of` et ses parenthèses, le cas échéant. Ne supprimez pas les parenthèses qui entourent une liste d’arguments standard pour une procédure, un délégué ou un constructeur de classe.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Comment : utiliser une classe générique](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)