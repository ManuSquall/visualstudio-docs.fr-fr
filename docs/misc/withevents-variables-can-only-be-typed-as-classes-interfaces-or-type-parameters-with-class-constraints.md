---
title: "Les variables &#39;WithEvents&#39; peuvent seulement &#234;tre de type classe, interface ou param&#232;tre de type avec des contraintes de classe | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30413"
  - "bc30413"
helpviewer_keywords: 
  - "BC30413"
ms.assetid: 11ddf207-2760-425f-b4c2-bb9fe6da36ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les variables &#39;WithEvents&#39; peuvent seulement &#234;tre de type classe, interface ou param&#232;tre de type avec des contraintes de classe
Vous avez déclaré une variable de type structure conjointement avec `WithEvents`, ce qui constitue une utilisation non valide du modificateur `WithEvents`.  
  
 **ID d’erreur :** BC30413  
  
### Pour corriger cette erreur  
  
1.  Utilisez `AddHandler` pour gérer les événements définis dans une structure.  
  
## Voir aussi  
 [NOT IN BUILD : WithEvents et la clause Handles](http://msdn.microsoft.com/fr-fr/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)