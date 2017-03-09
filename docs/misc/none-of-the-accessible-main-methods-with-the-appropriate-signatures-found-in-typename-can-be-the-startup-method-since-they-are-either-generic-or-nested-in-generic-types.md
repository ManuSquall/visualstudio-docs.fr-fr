---
title: "Aucune des m&#233;thodes &#39;Main&#39; accessibles avec les signatures appropri&#233;es ayant &#233;t&#233; trouv&#233;es dans &#39;&lt;nom_type&gt;&#39; ne peut &#234;tre la m&#233;thode de d&#233;marrage, car elles sont toutes g&#233;n&#233;riques ou imbriqu&#233;es dans des types g&#233;n&#233;riques. | Microsoft Docs"
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
  - "vbc30796"
  - "BC30796"
helpviewer_keywords: 
  - "BC30796"
ms.assetid: 606b3629-5a92-4c79-ace2-a530cab8c978
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aucune des m&#233;thodes &#39;Main&#39; accessibles avec les signatures appropri&#233;es ayant &#233;t&#233; trouv&#233;es dans &#39;&lt;nom_type&gt;&#39; ne peut &#234;tre la m&#233;thode de d&#233;marrage, car elles sont toutes g&#233;n&#233;riques ou imbriqu&#233;es dans des types g&#233;n&#233;riques.
Une classe, un module ou une structure n’a pas de procédure `Main` capable de tenir le rôle de procédure de démarrage du projet.  
  
 Visual Basic exige que la procédure de démarrage d’un projet ne dépende pas d’arguments de type. Elle doit donc pouvoir accéder à au moins une procédure `Main` qui n’est ni générique ni contenue dans un type générique.  
  
 **ID d’erreur :** BC30796  
  
### Pour corriger cette erreur  
  
-   Définissez au moins l’une des procédures `Main` pour qu’elle ne soit pas générique et ne soit pas contenue dans un type générique.  
  
     ou  
  
-   Dans la page **Propriétés** de votre projet, spécifiez un autre formulaire ou module comme **Formulaire de démarrage** ou **Objet de démarrage**.  
  
## Voir aussi  
 [NIB Procédure : modification des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NIB : Version Visual Basic de Hello, World](http://msdn.microsoft.com/fr-fr/9d030b60-e148-4366-a462-69532f02294c)