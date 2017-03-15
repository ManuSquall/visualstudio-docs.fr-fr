---
title: "Le membre &#39;&lt;nom_membre&gt;&#39; ne peut pas &#234;tre initialis&#233; dans une expression d’initialiseur d’objet, car il ne s’agit pas d’un champ ou d’une propri&#233;t&#233; | Microsoft Docs"
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
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_membre&gt;&#39; ne peut pas &#234;tre initialis&#233; dans une expression d’initialiseur d’objet, car il ne s’agit pas d’un champ ou d’une propri&#233;t&#233;
Une liste d’initialiseurs d’objet ne peut pas comprendre de membres partagés, de constantes ni d’appels de méthode. Les membres d’une liste d’initialiseurs doivent être des champs ou des propriétés. De plus, les membres de propriété ne peuvent pas exiger d’arguments.  
  
 **ID d’erreur :** BC30990  
  
### Pour corriger cette erreur  
  
-   Supprimez de la liste d’initialiseurs d’objet l’ensemble des membres partagés, constantes, appels de méthode et propriétés avec paramètres.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Membres partagés en Visual Basic](http://msdn.microsoft.com/fr-fr/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [NOT IN BUILD : Propriétés et procédures de propriété](http://msdn.microsoft.com/fr-fr/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NOT IN BUILD : Propriétés par défaut](http://msdn.microsoft.com/fr-fr/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NotInBuild : Object, membres](http://msdn.microsoft.com/fr-fr/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)