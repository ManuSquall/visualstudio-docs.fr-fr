---
title: "Les arguments de type d&#233;duits pour la m&#233;thode ’&lt;nom_proc&#233;dure&gt;’ donnent les erreurs suivantes&#160;: &lt;liste_erreurs&gt; | Microsoft Docs"
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
  - "bc30954"
  - "vbc30954"
helpviewer_keywords: 
  - "BC30954"
ms.assetid: 796592c4-70b7-45be-9322-db09e9095d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de type d&#233;duits pour la m&#233;thode ’&lt;nom_proc&#233;dure&gt;’ donnent les erreurs suivantes&#160;: &lt;liste_erreurs&gt;
Une procédure générique est appelée sans fournir d’arguments de type, et les arguments de type déduits provoquent une ou plusieurs violations de contrainte.  
  
 En général, quand vous appelez un type générique, vous fournissez un argument de type pour chaque paramètre de type défini par le type générique. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si les types déduits ne satisfont pas à une ou plusieurs des contraintes de paramètre de type, le compilateur génère cette erreur.  
  
 Une *contrainte* sur un type de paramètre limite les arguments de type qui peuvent lui être passés. Par exemple, un paramètre de type peut être limité à une classe qui implémente l’interface <xref:System.IComparable%601>. Pour plus d’informations, consultez la rubrique « Contraintes » dans [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **ID d’erreur :** BC30954  
  
### Pour corriger cette erreur  
  
-   Fournissez des arguments de type à la procédure générique pour que le compilateur n’ait pas à les déduire.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)