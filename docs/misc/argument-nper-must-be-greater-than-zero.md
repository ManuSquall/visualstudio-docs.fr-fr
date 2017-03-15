---
title: "L’argument &#39;NPer&#39; doit &#234;tre sup&#233;rieur &#224; z&#233;ro | Microsoft Docs"
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
  - "vbrRate_NPerMustBeGTZero"
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument &#39;NPer&#39; doit &#234;tre sup&#233;rieur &#224; z&#233;ro
La fonction `NPer`, qui retourne un `Double` spécifiant le nombre de périodes pour une annuité sur la base de versements fixes périodiques et d’un taux d’intérêt fixe, nécessite un argument supérieur à zéro.  
  
### Pour corriger cette erreur  
  
-   Vérifiez l’orthographe des arguments dans l’expression. Un nom de variable mal orthographié peut créer implicitement une variable numérique initialisée à zéro.  
  
-   Vérifiez les opérations précédentes sur les variables dans l’expression, surtout celles passées dans la procédure en tant qu’arguments à partir d’autres procédures.  
  
## Voir aussi  
 [NOT IN BUILD : Fonction NPer](http://msdn.microsoft.com/fr-fr/56567d16-29f7-4928-b05f-b4cd56d4fd42)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)