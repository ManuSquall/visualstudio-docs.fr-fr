---
title: "Les arguments de type d&#233;duits pour la m&#233;thode &#39;&lt;nom_proc&#233;dure&gt;&#39; entra&#238;nent les avertissements suivants&#160;: &lt;liste_avertissements&gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de type d&#233;duits pour la m&#233;thode &#39;&lt;nom_proc&#233;dure&gt;&#39; entra&#238;nent les avertissements suivants&#160;: &lt;liste_avertissements&gt;
Une procédure générique est appelée sans fournir d’arguments de type, et les arguments de type déduits produisent un ou plusieurs avertissements.  
  
 En général, lorsque vous appelez un type générique, vous fournissez un argument de type pour chaque paramètre de type défini par le type générique. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si les types déduits entraînent une ambiguïté ou s’ils créent une situation qui pourrait donner des résultats inattendus, le compilateur génère cet avertissement.  
  
 Une *contrainte* sur un type de paramètre limite les arguments de type qui peuvent lui être passés. Par exemple, un paramètre de type peut être contraint à être une classe qui implémente l’interface <xref:System.IComparable%601>. Pour plus d’informations, consultez la section « Contraintes » dans [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC41006  
  
### Pour corriger cette erreur  
  
-   Fournissez des arguments de type à la procédure générique afin que le compilateur n’ait pas besoin de les déduire.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)