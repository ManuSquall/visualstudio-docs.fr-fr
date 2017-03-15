---
title: "Le type &#39;&lt;nom_type&gt;&#39; ne peut pas h&#233;riter d’un param&#232;tre de type | Microsoft Docs"
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
  - "bc32055"
  - "vbc32055"
helpviewer_keywords: 
  - "BC32055"
ms.assetid: 97af7cad-6e40-41e3-892d-1fbcbd86356d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; ne peut pas h&#233;riter d’un param&#232;tre de type
Une classe ou une interface contient une instruction Inherits \([Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)\) qui spécifie un paramètre de type générique.  
  
 Un type ne peut pas hériter d’un type qui n’est pas encore défini. L’héritage implique la possibilité de réutiliser des membres de la classe de base, qui exige à son tour que ces membres soient définis. Un paramètre de type générique est un espace réservé qui doit être remplacé par un type spécifique fourni par un argument de type. Par conséquent, un type ne peut pas hériter de l’espace réservé.  
  
 **ID d’erreur :** BC32055  
  
### Pour corriger cette erreur  
  
-   Si le type qui hérite doit hériter d’un autre type, utilisez un type spécifique au lieu d’un paramètre de type.  
  
-   Si le type de base doit être représenté par un paramètre de type générique, aucun autre type ne peut en hériter. Supprimez l’instruction Inherits \([Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)\).  
  
## Voir aussi  
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)